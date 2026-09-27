# Completed claim
agent: cutinapp-growth-conversion
display_name: Conversion Pilot
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: production release diagnostics
task: Preserve public release identity diagnostics when the configured VPS SSH endpoint is unavailable
status: completed
started_at: 2026-09-26T22:33:00-03:00
completed_at: 2026-09-26T22:37:00-03:00

## Delivery
- PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/659
- Merge: `d737167336252a85b8e3a881dd03e1cbd305bf9c`
- Frontend check: success
- Lighthouse check: success

## Behavior
Remote filesystem and local-nginx probes now degrade to explicit unavailable states when SSH cannot connect. The public `release-sha.txt` probe still runs, and the job remains failed until exact release identity can be proven.

## Triggering evidence
Deploy run 36285563893 exhausted four SSH attempts with connection timeouts. Build, activation and health were skipped, and the previous diagnostic exited 255 before the public probe.
