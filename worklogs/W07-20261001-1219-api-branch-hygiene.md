# W07 — API Branch Hygiene

agent: W07
repository: petertecnetdev/api.petertecnet.com.br
captured_at: 2026-10-01T12:19:48-03:00
status: in-progress

## Verified inventory facts
- GitHub branches endpoint was paged through page 8; page 8 is empty, so current inventory spans pages 1–7.
- `main` HEAD: `5fea1752fb674dd463b65bb2069f2c13117e2749`.
- Exact duplicate HEAD families are already visible and must be grouped before any deletion decision (examples: `artist-upgrade-temp*`; generic-onboarding hardening variants; producer-media-library variants; platform-core variants).
- No branch was deleted, rewritten, force-pushed or deployed.

## High-risk UNIQUE_USEFUL_REVIEW candidates
### agent/np04-t2/reject-malformed-payment-webhooks
HEAD `ff3a01e1fe6069437ca297d6d3587cf46f40d3bf`.
Compare to main: diverged; ahead 1 / behind 277; merge-base `076f339f494605108ba11f4c78d2b7cfb29be9c0`.
Exclusive file: `tests/Feature/Finance/PaymentProviderWebhookValidationTest.php` (+18).
Classification: UNIQUE_USEFUL_REVIEW (financial/webhook safety; second review mandatory).
Recovery strategy: inspect test intent against current provider webhook validation and selectively port only missing assertions; do not merge historical branch wholesale.

### agent/np10-t3/idempotent-webhook-receiver
HEAD `974802089f3ad0328b62a843e2e877dd120b1fde`.
Compare to main: diverged; ahead 1 / behind 277; merge-base `076f339f494605108ba11f4c78d2b7cfb29be9c0`.
Exclusive file: `app/Domain/Integration/Models/WebhookReceipt.php` (+34).
Classification: UNIQUE_USEFUL_REVIEW (idempotency/data model; second review mandatory).
Recovery strategy: compare against current webhook receipt/idempotency architecture and migrations before any selective integration.

## Snapshot publication blocker
The API connector returned all branch pages, but its response representation is truncated for large pages and the remote processing device was offline, so a byte-stable CSV + SHA-256 could not be generated safely in this cycle without fabricating unseen rows. Continue next cycle; do not disable automation. Canonical snapshot publication remains pending, not skipped.

## NEXT_ACTION
1. Generate the canonical CSV from paginated GitHub API once a complete byte-preserving processing path is available; include position, branch, head_sha, captured_at, total, main_sha and SHA-256.
2. Batch group duplicate HEADs and family supersession.
3. Compare financial/auth/security exclusive heads first and hand off any apparently lost P0 to W10.
4. Keep all exclusive high-risk branches protected from deletion until second review.

Signed: W07 (API BRANCH HYGIENE)
