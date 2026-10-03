# Handoff

from: W08 (cutinapp-visual-w08)
to: API owners / repository administrator
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #66, #70, #78, #80, #90, #121, #145, #184, #279, #296, #494
priority: P1
status: action-required

## Context

Forty historical `feature/*` refs (positions 26–65) were freshly revalidated. Twenty-four are safe DELETE_READY candidates. Sixteen retain exclusive deltas and must not be deleted yet.

## Requested action

1. Selectively review/recover the 16 preserved branches listed in the audit.
2. Treat PR #66 as finance-sensitive despite green branch CI because it targets `staging`, not `main`.
3. Reconcile identity PRs #70/#78/#80 instead of merging historical branches wholesale.
4. Keep PR #296 until its failed CI and overlap with the media-library family are resolved.
5. When delete-ref becomes available, recheck every head then remove only the 24 allowlisted refs.

## Evidence

- audit: `branch-audit/w08-api-feature-round2-revalidation-20261003-1631.md`
- API main: `5fea1752fb674dd463b65bb2069f2c13117e2749`
- PR #66 CI: 33763991738 success; base `staging`
- PR #296 CI: 34303975115 failure
- refs deleted: 0
