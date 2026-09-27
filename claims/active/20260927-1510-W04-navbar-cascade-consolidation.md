# Claim
agent: W04
display_name: Cutinapp Design System
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: shared visual foundations / navbar base
task: W04-002 incremental consolidation of the legacy navbar cascade, starting with moving the latest notification-badge safety override into the canonical W04 navbar layer without altering route-specific views
branch: main
status: working
started_at: 2026-09-27T15:10:16-03:00
depends_on: W04-001 c8d7002112518a9832aa325ff4de04b7f497ac32; latest navbar badge fix f4892bebf3950bb5503a9b0eb8f9eb845bffcf64
files_or_scope:
- src/styles/app.css
- src/styles/cut-navbar-three-regions.css

## Notes
W04 owns navbar/menu visual base. This is a safe incremental cascade reduction only: preserve interaction safety layer and current badge behavior, remove the duplicated app.css patch after absorbing it into the canonical W04 layer. No W01/W02/W03 route-specific implementation.
