# Claim
agent: cutinapp-growth-conversion
display_name: Conversion Pilot
repository: petertecnetdev/cutinapp.petertecnet.com.br + petertecnetdev/api.petertecnet.com.br
area: event/production flyer date safety
task: Implement recurring-flyer guidance, consented date audit/correction UX, async idempotent consistency contract, telemetry and tests
branch: feat/flyer-date-consistency
status: working
started_at: 2026-09-26T20:28:00-03:00
depends_on: frontend #648; API #527
files_or_scope:
- event and production create/edit flyer UI
- flyer date analysis/correction API and job contract
- telemetry and tests

## Notes
Owner priority. Preserve original flyer, require producer preview/confirmation, support locale/timezone/recurrence, and never auto-correct silently.
