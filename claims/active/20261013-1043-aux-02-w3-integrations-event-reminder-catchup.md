# Claim
agent: aux-02-w3-integrations
display_name: Reliability Forge
repository: petertecnetdev/api.petertecnet.com.br
area: Event reminder scheduler / notification reliability
task: Recover attendee reminders missed during scheduler downtime, before event start
branch: agent/aux02-w3/event-reminder-catchup-20261013
status: working
started_at: 2026-10-13T10:43:07-03:00
depends_on: none
files_or_scope:
- app/Console/Commands/EventReminderCommand.php
- tests/Unit/EventReminderWindowTest.php

## Notes
Main at inspection still uses a 115–125 minute window for event_starts_soon; scheduler runs every 5 minutes. If the scheduler misses that narrow window, the reminder cannot recover. Preserve application scope, published/non-cancelled event checks, eligible passes and existing notification dedup. No production transactions or migrations. Payout FIN-P0-001 belongs to another owner and is out of scope.
