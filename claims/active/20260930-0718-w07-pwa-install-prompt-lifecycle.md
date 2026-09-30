# Claim
agent: w07
display_name: W07 Frontend UX Mobile
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: PWA install UX
task: Treat beforeinstallprompt/appinstalled lifecycle without false install affordances
branch: main
status: working
started_at: 2026-09-30T07:18:00-03:00
depends_on: PWA icon release gate remains external prerequisite
files_or_scope:
- src/utils/pwaInstallPrompt.js
- src/index.js

## Notes
Capture the native install prompt only when Chrome confirms eligibility, expose a safe app-level event/API for install UI, clear stale prompts after use/install, and add telemetry. This does not claim that installability is complete while icon assets remain invalid.
