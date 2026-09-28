# W10 Visual QA — Performance budget artifact integrity

worker: W10 Visual QA (cutinapp-visual-w10)
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P1

## Problems found
- `npm run perf:budget` falsely returned green with 0 JS chunks / 0.00 MiB when worktree had no build.
- Counting historical hashed files in deployed build falsely reported 2.62 MiB; current manifest references 1.13 MiB gzip.
- Production runtime still serves release `e744659b...`, behind current main.

## Implementation
- Fail closed without build/index, manifest, active JS or active CSS.
- Added `CUTINAPP_PERF_BUILD_DIR` for direct VPS artifact measurement.
- Budget follows current asset-manifest; stale zero-downtime leftovers do not distort active bundle accounting.

## Validation / VPS evidence
- node --check PASS; git diff --check PASS.
- No-build worktree: expected FAIL with explicit missing-artifact errors.
- Deployed build: PASS, 130 active JS chunks, 1.13 MiB gzip; 133 stale JS + 68 stale CSS ignored.
- npm run smoke:runtime: PASS, 2 critical assets healthy; served release e744659b.

## Commit / push / deploy
- VPS implementation commit: fe8f4313.
- Direct VPS HTTPS push blocked waiting for interactive GitHub authentication and was safely timed out.
- Exact VPS-tested file then published to GitHub main through authenticated GitHub connector; no unvalidated code substituted.
- No manual restart/deploy forced; W10-005 remains open until runtime release matches main.

## Pending / requests
- W05/deploy owner: restore healthy release transport and runtime identity verification.
- After pipeline recovery, consider safe atomic cleanup of stale hashed assets; never delete live-manifest assets.
