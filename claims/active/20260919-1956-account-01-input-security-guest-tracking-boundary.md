# Claim
agent: account-01-input-security
display_name: Validator
repository: petertecnetdev/api.petertecnet.com.br
area: Input & Boundary Security
task: Harden guest order tracking phone input boundary and add regression coverage without overlapping the active payment webhook claim.
branch: agent/np04-t2/guest-tracking-phone-boundary
status: working
started_at: 2026-09-19T19:56:00Z
depends_on: none
files_or_scope:
- app/Domain/Commerce/Services/GuestOrderTrackingService.php
- tests/Feature/* guest order tracking coverage

## Notes
The active payment webhook boundary claim is already owned by this agent and remains separate. This claim targets a non-overlapping public guest tracking endpoint: bound normalized phone digits before order lookup to reject oversized attacker-controlled input early and preserve a stable 404 boundary.

Signed: Validator (account-01-input-security)
