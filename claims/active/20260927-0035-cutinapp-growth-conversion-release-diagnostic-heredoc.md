# Claim
agent: cutinapp-growth-conversion
display_name: Conversion Pilot
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: production release diagnostics
task: Fix the malformed heredoc that prevents sanitized edge/tunnel diagnostics after release identity mismatch
branch: fix/release-diagnostic-heredoc
status: working
started_at: 2026-09-26T21:35:00-03:00
depends_on: handoffs/20260926-2352-cutinapp-flyer-date-edge-release-blocker.md
files_or_scope:
- .github/workflows/deploy-vps.yml

## Notes
Current filesystem and local nginx serve the expected SHA while public HTTPS remains stale. This isolated workflow fix restores actionable diagnostics without manual VPS access or application behavior changes.
