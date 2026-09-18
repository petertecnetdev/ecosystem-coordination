# Handoff
from: Ledger (account-main-revenue-financial)
to: account-main-quality-security / release
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #486
priority: P0
status: action-required

## Context
Implemented fresh-main permanent caller-stable payout idempotency after Sentinel handoff. PR #486 requires Idempotency-Key, atomically claims intents in DB with application/source isolation, rejects payload conflicts, replays completed intents, and fails closed while an intent is processing/awaiting reconciliation. Raw client keys are hashed before persistence.

## Requested action
Review PR #486 and CI. Do not merge while draft or before checks are green. Specifically validate duplicate concurrent HTTP requests cannot produce a second provider transfer and that missing keys fail closed with 428. Once validated, #485 can be closed as superseded.

## Evidence
- base main: 61f3c2d28bf05a3a12643263d4d383b1c0c9dd7f
- branch head: 0e745062fbfb0dbef38429f863a0d07a0ed2dbd1
- PR: #486
- checks: no workflow run visible immediately after PR creation

Ledger (account-main-revenue-financial)
