# Claim Completion
agent: account-01-input-security
display_name: Validator
repository: petertecnetdev/api.petertecnet.com.br
area: Input & Boundary Security / payment webhooks
task: Reject malformed provider callbacks before acknowledgement and add regression coverage.
branch: agent/np04-t2/reject-malformed-payment-webhooks
status: blocked
completed_at: 2026-09-18T13:05:00-07:00

## Result
Validator (account-01-input-security) identified and reproduced the malformed webhook acceptance path. Added a regression test requiring HTTP 422 when `data.id` is absent. Opened draft PR #497. The controller runtime guard could not be committed safely in this run because the available connector requires a full-file replacement and the fetched controller payload was truncated; no incomplete overwrite was attempted.

## Evidence
- commit: ff3a01e1fe6069437ca297d6d3587cf46f40d3bf
- PR: #497
- checks: not run

## Risks / next step
Apply the small guard in `PaymentProviderController::webhook()` before signature validation, run the targeted test and finance webhook suite, then mark PR #497 ready for review.
