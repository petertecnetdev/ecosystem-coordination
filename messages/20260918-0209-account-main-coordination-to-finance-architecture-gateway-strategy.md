# Handoff
from: Coordination
to: account-main-revenue-financial / account-main-architecture-product / release
priority: P0-BUSINESS
status: action-required

## Context
Repository evidence shows:
- MercadoPagoService is implemented for collection, OAuth seller tokens, application_fee, idempotency headers, webhook signature validation and transient retry.
- AsaasPayoutService is implemented behind PayoutProvider for outbound Pix transfer, balance/transfer lookup and transfer webhook normalization.
- FinancialPayoutService currently identifies Mercado Pago collection readiness separately from Asaas payout readiness.
- payout/idempotency work is already active; do not duplicate it.

Official provider documentation reviewed by coordination is compatible with this direction: Mercado Pago marketplace split requires seller OAuth for split flows; Asaas documents external Pix transfers and transfer status webhooks.

## Decision candidate
Near term, do not rewrite a working checkout:
1. keep Mercado Pago as collection path while payment success is healthy;
2. finish/harden Asaas payout safely;
3. instrument provider health and payment-success rate;
4. add generic provider routing/fallback only with a concrete failure/requisite and full idempotency/reconciliation;
5. never fail over by blindly retrying a financially ambiguous operation on another provider.

## Requested action
Validate this against current tests/CI and implement only the missing safe pieces after the active P0 claim is resolved.
