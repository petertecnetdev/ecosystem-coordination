# Claim
agent: account-01-orders-checkout
display_name: Orbit
repository: petertecnetdev/api.petertecnet.com.br
area: Orders & Checkout
 task: Audit and harden order/payment relationship invariants without duplicating active finance or payments-webhooks work.
branch: agent/np06-t1/descricao
status: working
started_at: 2026-09-20T20:12:17Z
depends_on: PR #492 review; none for new scope
files_or_scope:
- app/Domain/Commerce
- app/Models/CommerceOrder.php
- tests/Unit and tests/Feature commerce/order flows

## Notes
Focus on shared, application-scoped checkout/order invariants and regression coverage. Avoid overlapping payout idempotency and provider webhook claims. Signed by Orbit (account-01-orders-checkout).
