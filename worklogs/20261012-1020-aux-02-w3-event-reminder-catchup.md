# Worklog — AUX-02 W3 — Event reminder scheduler catch-up

- date: 2026-10-12
- agent: aux-02-w3-integrations
- display_name: Reliability Forge
- priority: P1
- repository: petertecnetdev/api.petertecnet.com.br
- source_sha: 14447fa8c6d038e8ce007e4ebfab0dfd5dea97f1
- status: blocked

## Problem and evidence
The Cutinapp ticket-holder reminder command runs every five minutes (app/Console/Kernel.php). EventReminderCommand.php selects events only when start_date is in [now + 115 minutes, now + 125 minutes]. A scheduler interruption that covers this ten-minute eligibility window means a participant with a valid pass never receives event_starts_soon. The command already checks AppNotification for an existing event_starts_soon notification, so extending the eligible window to (now, now + 125 minutes] enables catch-up while the event is still upcoming without intentionally resending already persisted reminders.

Example: an event starting at 12:00 is eligible only around 09:55–10:05 under the current code. If the scheduler is offline 09:50–10:30, the 10:30 run excludes that event despite 90 minutes remaining.

## Proposed minimal implementation
- app/Console/Commands/EventReminderCommand.php: compute a single timezone-aware now; use start_date > now and start_date <= now + 125 minutes for attendee reminders.
- Keep the existing app_id, is_published, is_cancelled, pass status and per-user notification existence checks.
- Add feature regression: event starts in 90 minutes with an eligible pass; first command run creates exactly one event_starts_soon notification; second run does not create another; cancelled/refunded passes and cancelled events receive none.
- No migration, no live notifications, no production transactions.

## Work performed and checks
- Read coordination protocol, commands, current state, priorities, blockers, assignment AUX-02/W3 and active claims.
- Inspected app/Console/Kernel.php, app/Console/Commands/EventReminderCommand.php, EventProducerCommunicationService.php, EventPass.php, AppNotification.php, and tests.
- Verified no active claim or matching issue/PR for this specific event reminder catch-up.
- Created a coordination claim and API implementation branch.
- Attempted a narrow source update, but the connector rejected the write. No API code was changed; PHPUnit was not executed.
- An attempt to update the claim status was also rejected; the claim content still says working and must be reconciled by W00.

## Git
- API branch: agent/aux02-w3/event-reminder-catchup-20261012 (no code commit)
- Coordination branch: coord/aux-02-w3-event-reminder-catchup-20261012
- Coordination claim: claims/active/20261012-1020-aux-02-w3-integrations-event-reminder-catchup.md
- API PR: none

## Next action
W00 should assign an authorized writer to implement and test the minimal change, then update the claim to completed/handoff. Do not deploy directly to VPS. No duplicate Direct issue #533 or payout FIN-P0-001 work.

Reliability Forge (aux-02-w3-integrations)
