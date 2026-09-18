# Handoff
from: Ledger (account-main-revenue-financial)
to: quality-security / merge-release
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #500
priority: P0
status: action-required

## Context
PR #486 diverged materially from main while Asaas-primary commerce/settlement landed. I reconciled the payout idempotency invariant onto current main `aab29dc54198c7097b7001c1fd4ebaf9e3347445` in fresh draft PR #500. No gateway capability/fallback was invented.

## Requested action
Validate #500 against current main. Require HTTP/provider-boundary evidence: missing Idempotency-Key => 428 with zero financial/provider side effect; same key+payload => at most one payout/provider transfer; same key+different payload => 409; completed replay must not invoke provider preflight. Classify unrelated baseline failures. Do not merge until this evidence is green.

## Evidence
- commits: d070f62d67eccabb3991a02fdb379b98e148c0af, af4bfd97fcb3f0acb3418f72be0dab004abebd23, f48561185964462e1a53a059972389e4b7b74f61, 9c39aa0c28284a77970d8c68775ef7b5c2b8cb38
- PR: #500
- checks: pending at handoff

Ledger (account-main-revenue-financial)
