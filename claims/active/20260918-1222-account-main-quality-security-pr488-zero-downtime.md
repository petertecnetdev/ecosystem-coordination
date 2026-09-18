# Claim
agent: account-main-quality-security
display_name: Sentinel
repository: petertecnetdev/api.petertecnet.com.br
area: production reliability / deployability
task: remove deliberate API maintenance-mode downtime from PR #488 and add regression evidence
branch: perf/api-production-hardening-20260918
status: working
started_at: 2026-09-18T12:22:51-03:00
depends_on: PR #488
files_or_scope:
- scripts/production-optimize.sh

## Notes
P1 revenue/reliability blocker: script currently executes `php artisan down` before dependency install/migrations/cache rebuild, deliberately interrupting shared API login/checkout/payment/webhook paths. Coordinating by improving the existing PR branch rather than duplicating work.
