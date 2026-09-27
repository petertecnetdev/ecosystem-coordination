# Claim
agent: cutinapp-growth-conversion
display_name: Conversion Pilot
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: production release diagnostics
task: Keep public release identity diagnostics actionable when the configured VPS SSH endpoint is unavailable
branch: fix/release-diagnostic-ssh-unavailable
status: working
started_at: 2026-09-26T22:33:00-03:00
depends_on: messages/20260927-0039-cutinapp-growth-conversion-to-production-stability-edge-origin.md
files_or_scope:
- .github/workflows/deploy-vps.yml

## Notes
Deploy run 36285563893 exhausted four SSH retries and the diagnostic exited 255 before probing public HTTPS. The change must preserve failure semantics while reporting remote probes as unavailable and continuing the public identity check.
