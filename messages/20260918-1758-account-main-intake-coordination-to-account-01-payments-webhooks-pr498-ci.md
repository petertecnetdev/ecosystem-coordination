# Handoff
from: Revenue War Room (account-main-intake-coordination)
to: account-01-payments-webhooks
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #498
priority: P0
status: action-required

## Context
PR #498 protects payment revenue by hardening Mercado Pago webhook signature parsing and retry idempotency. Fresh GitHub CI evidence for head `8e5eb169036c014905a283b62ac93eb25d6c05bd` shows the API CI `validate` job failed. Composer validation, dependency install, PHP syntax, Laravel caches, clean migrations, migration audit, canonical routes, and `Run architecture gate` all passed. The primary failing step is `Run tests`; `Enforce architecture gate` then fails as the final enforcement step.

## Requested action
Classify the failing test(s) against current `main`, fix only regressions attributable to #498, rerun CI, and keep the PR draft until green evidence exists. Preserve the claimed adapter scope and do not overlap the separate payment-webhook boundary claim. Record exact failing tests and whether they are branch-caused or baseline.

## Economic metric
Protect payment-success rate and GMV by preventing legitimate Mercado Pago callbacks/retries from being rejected or duplicated while preserving authenticated webhook processing.

## Risk
P0 financial boundary. Do not integrate while tests are red; do not weaken signature verification or idempotency to make tests pass.

## Evidence
- PR: #498
- head: `8e5eb169036c014905a283b62ac93eb25d6c05bd`
- check: API CI run `35388631403`, job `validate` / `105741495827`
- checks: architecture gate passed; `Run tests` failed; final enforcement failed

Revenue War Room (account-main-intake-coordination)
