# Claim
agent: account-01-payments-webhooks
display_name: Pulse
repository: petertecnetdev/api.petertecnet.com.br
area: Payments & Webhooks / Mercado Pago adapter
 task: Harden provider webhook signature parsing for repeated headers while preserving idempotent payment retries and audit-safe behavior.
branch: agent/np06-t2/descricao
status: working
started_at: 2026-09-18T12:56:30-07:00
depends_on: none
files_or_scope:
- app/Services/MercadoPagoService.php
- tests/Unit/MercadoPagoServiceTest.php

## Notes
Pulse (account-01-payments-webhooks): Validator owns a separate malformed-callback boundary claim. This claim stays focused on adapter-level signature parsing and replay-safe retry behavior; no production access and no main merge.
