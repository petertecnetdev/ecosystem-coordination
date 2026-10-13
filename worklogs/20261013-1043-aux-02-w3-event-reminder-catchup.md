# AUX-02 W3 — Event reminder catch-up audit
date: 2026-10-13
agent: aux-02-w3-integrations
display_name: Reliability Forge
priority: P1
repository: petertecnetdev/api.petertecnet.com.br
status: blocked

## Evidence
- Main `app/Console/Commands/EventReminderCommand.php` computes a reminder window from now+115 minutes through now+125 minutes.
- `app/Console/Kernel.php` runs `platform:remind-events` every five minutes with `withoutOverlapping()`.
- A scheduler outage exceeding the 10-minute selection window can permanently skip an attendee reminder.
- Existing `AppNotification` existence check prevents repeated reminders in ordinary sequential runs; it does not by itself prove concurrency-safe uniqueness.
- `AppNotificationService::sendToUser()` persists a notification and catches broadcast/email transport errors, so the immediate defect is the selection window, not transport delivery.

## Deterministic reproduction
With scheduler invocation at 2026-10-13 10:00 America/Sao_Paulo:
| Event start | Minutes away | Current 115–125m | Proposed 0–125m (exclusive lower) |
| --- | ---: | --- | --- |
| 12:00 | 120 | selected | selected |
| 11:30 | 90 | skipped | selected |
| 10:15 | 15 | skipped | selected |
| 10:00 | 0 | skipped | skipped |
| 12:05 | 125 | selected | selected |
| 12:06 | 126 | skipped | skipped |

## Proposed minimal correction
In `EventReminderCommand::handle()`, use a single captured timezone-aware `now`; select events with `start_date > now` and `start_date <= now + 125 minutes`, preserving the existing `app_id`, `is_published`, `is_cancelled`, eligible EventPass statuses, and `event_starts_soon` notification lookup. Add focused tests for catch-up, future cutoff, started events, repeated scheduler invocations, and application isolation. Verify that old events never receive a late reminder. Do not run real transactions or migrations.

## Git and blocker
- API branch created: `agent/aux02-w3/event-reminder-catchup-20261013`.
- API code write attempt: blocked by connector safety checks; no API commit and no functional PR.
- PHPUnit: not executed. The table above is a deterministic logic simulation, not a PHPUnit result.
- Claim: `claims/active/20261013-1043-aux-02-w3-integrations-event-reminder-catchup.md`.
- No direct VPS deployment.

## Handoff
Owner: W00 / authorized API maintainer.
Next action: implement minimal query-window change on a reviewed API branch, add regressions, run focused PHPUnit and CI, then open functional PR. Keep claim blocked until implementation can proceed.
