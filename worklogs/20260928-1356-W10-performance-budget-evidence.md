# W10 Worklog — Performance budget evidence

worker: W10 — REGRESSAO VISUAL, PERFORMANCE E QUALIDADE DAS VIEWS
date: 2026-09-28
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Problems found
- Production runtime remains on release `802c491f` while VPS `main` has advanced, so W10-005 remains P0.
- The performance gate enforced initial JS but did not print the measured initial payload/headroom, active CSS footprint, or largest JS chunk, limiting trendability.
- VPS Git remote is HTTPS and still requires interactive authentication, so direct `git push origin main` cannot complete non-interactively.

## Implementation
- Updated `scripts/check-performance-budget.js` directly on the VPS main worktree.
- Added explicit initial-JS gzip measurement versus the existing 250 KiB budget and percentage used.
- Added active CSS gzip footprint and largest active JS chunk output.
- No threshold was relaxed.

## Validation / VPS evidence
- `node --check scripts/check-performance-budget.js`: PASS.
- `git diff --check`: PASS.
- `CUTINAPP_PERF_BUILD_DIR=/var/www/cutinapp.petertecnet.com.br/build npm run perf:budget`: PASS.
- Total JS: 130 active chunks / 1.13 MiB gzip.
- Initial JS: 121 KiB / 250 KiB = 48.5%.
- Active CSS: 69 chunks / 315 KiB gzip.
- Largest JS chunk: 294 KiB gzip.
- `npm run smoke:runtime`: PASS, 2 critical assets healthy; release `802c491f`.

## Commit / push / deploy
- VPS main commit: `a5de208a` (`test(perf): expose startup budget headroom`).
- Push: BLOCKED; VPS HTTPS GitHub remote requires interactive authentication. Local main is ahead of `origin/main`; no force/reset/rebase was performed.
- Deploy/restart: not performed because release identity is already divergent and this change only affects QA tooling.

## Pending / requests
- W05/release: restore authenticated non-interactive VPS→GitHub push and reconcile stale production release identity.
- After transport recovery, publish accumulated VPS-first commits, run CI, and trend the newly exposed startup metrics.

## Expected impact
Earlier detection of startup payload/CSS growth and clearer evidence for Core Web Vitals regressions without weakening performance budgets.
