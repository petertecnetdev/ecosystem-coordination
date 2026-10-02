# W09 evidence — agent/np03/admincenter-browser-matrix

captured_at: 2026-10-01T22:38:32-03:00
repository: petertecnetdev/petertecnet.com.br
main_baseline: 3457f7ae1115ea4a4d3d05abd2584c42fc77ea98

## Branch
- branch: `agent/np03/admincenter-browser-matrix`
- HEAD: `aed43ebbc11eb1b61ece87f36ca1d8d6eaaf703c`
- compare vs main: diverged; ahead=1; behind=524; merge-base=`4726ad0c1ccd86dbae3edb8b8ece8c80d08a3a45`
- exclusive file: `apps/admincenter/scripts/validate-admin-shell-v2-browser.mjs`
- exclusive patch: expands browser viewport matrix (1280 naming, 1024 tablet, iPhone 430 and 390 cases).
- open PR for branch: none.

## Architecture / useful-code disposition
The PeterTecnet website `main` no longer contains `apps/admincenter/scripts/validate-admin-shell-v2-browser.mjs`, so merging/cherry-picking this historical Admin Center commit into the website repository would resurrect misplaced architecture.

The dedicated repository `petertecnetdev/admincenter.petertecnet.com.br` currently contains `scripts/validate-admin-shell-v2-browser.mjs` with the same expanded nine-case viewport matrix and additional robustness improvements (4 attempts and DOM-result acceptance despite Chromium runner warnings). Therefore the useful behavior from this historical branch is already present in the canonical Admin Center repository in a more evolved form.

## Classification
`SUPERSEDED` / `SAFE_DELETE_CANDIDATE`.

Objective reason: the only exclusive website-repo change belongs to Admin Center; that path is absent from website main; its useful viewport-matrix behavior exists in the dedicated Admin Center repository in a more evolved implementation. No recovery into website main is appropriate.

Useful-code destination: `petertecnetdev/admincenter.petertecnet.com.br:scripts/validate-admin-shell-v2-browser.mjs`.

Deletion remains contingent on an actual authenticated delete-ref capability and final active-claim protection check. Do not move refs as a substitute for deletion.
