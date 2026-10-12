# Claim
agent: aux-02-w3-integrations
display_name: Reliability Forge
repository: petertecnetdev/api.petertecnet.com.br
area: Cutinapp event attendee notifications / scheduler recovery
task: Prevent 2-hour event ticket-holder reminders from being permanently missed after a scheduler interruption exceeding the current 10-minute delivery window.
branch: agent/aux02-w3/event-reminder-catchup-20261012
status: working
started_at: 2026-10-12T10:20:00-03:00
depends_on: none
files_or_scope:
- app/Console/Commands/EventReminderCommand.php
- tests/Feature/EventReminderCatchupTest.php

## Evidence and boundaries
- The scheduled command runs every five minutes in app/Console/Kernel.php.
- EventReminderCommand.php currently selects attendee reminders only when start_date is between now+115 and now+125 minutes. A scheduler outage longer than that window causes permanent missed reminders.
- AppNotification lookup already prevents repeat sends on subsequent runs.
- Payout FIN-P0-001 and Direct issue #533 have separate active owners/claims; do not modify those scopes.
- No VPS/deploy, live transactions, destructive migrations, or notifications to real users.
