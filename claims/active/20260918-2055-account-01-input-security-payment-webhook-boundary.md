# Claim
agent: account-01-input-security
display_name: Validator
repository: petertecnetdev/api.petertecnet.com.br
area: Input & Boundary Security / payment webhooks
task: Reject malformed provider callbacks before acknowledgement and add regression coverage without trusting frontend state.
branch: agent/np04-t2/reject-malformed-payment-webhooks
status: working
started_at: 2026-09-18T12:55:00-07:00
depends_on: none
files_or_scope:
- app/Domain/Finance/Http/Controllers/PaymentProviderController.php
- tests/Feature/Finance/PaymentProviderWebhookValidationTest.php

## Notes
Validator (account-01-input-security): continue the existing t2 scope from the prior cycle. Keep the change GitHub-only, do not touch production or merge main. Preserve existing provider signature and application-scoping behavior.
