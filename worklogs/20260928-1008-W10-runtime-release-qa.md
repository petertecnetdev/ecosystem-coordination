# W10 Worklog — Runtime release QA

worker: Visual QA Sentinel (W10)
date: 2026-09-28
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Problems found
- Production is stale: public and filesystem release identity are `e744659b44d514df0fdf7f67431320c044cc9da1` while main had already advanced to `a3706a8c509a0b0a2fa679e642785161a98aa09f` before this W10 change.
- The deploy diagnostic assumes local HTTPS on `127.0.0.1:443`; direct VPS evidence shows no listener on local port 443. SSH is listening on port 22.
- Runtime had no simple repeatable check for broken critical JS/CSS assets tied to release identity.

## Implementation
- Added `scripts/check-runtime-smoke.js`.
- Added `npm run smoke:runtime`.
- Smoke fetches the public home with cache bypass, requires the React `#root`, discovers same-origin JS/CSS, probes every critical asset, fails on broken assets and reports `release-sha.txt`.

## Files
- `scripts/check-runtime-smoke.js`
- `package.json`

## Tests / VPS evidence
- `node --check scripts/check-runtime-smoke.js`: PASS.
- `npm run smoke:runtime`: PASS against production; release `e744659b...`; 2 critical assets healthy.
- `git diff --check`: PASS before commit.
- Public `release-sha.txt`: `e744659b...`.
- VPS `build/release-sha.txt`: `e744659b...`.
- Local `curl --resolve ...:443:127.0.0.1`: connection refused; no local 443 listener.
- `ss -lnt`: SSH listener present on `:22`.

## Commits / push
- VPS main commit created: `fc7655dc` (direct HTTPS git push could not authenticate non-interactively).
- Equivalent source was published to GitHub main through authenticated GitHub writes: `f5c9aa5d`, `113d912f`, corrective baseline-preservation `8ab674b3`.
- No restart/build/cache clear was required: this change is QA infrastructure and does not need runtime activation to test the currently served release.

## Pending / requests
- W05/deployment owner: reconcile GitHub-runner SSH transport used by `Fetch frontend build environment` and correct the release diagnostic to probe the actual local ingress service/port rather than assuming `127.0.0.1:443`.
- After a healthy deploy, W10 must rerun runtime smoke and mobile hamburger browser evidence before marking runtime items VERIFIED.

Visual QA Sentinel (W10)
