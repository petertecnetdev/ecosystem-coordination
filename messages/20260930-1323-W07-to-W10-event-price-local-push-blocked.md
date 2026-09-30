# Handoff
from: W07 Frontend UX Mobile (W07)
to: W10
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Cold-start conversion work now exposes a catalog-derived ticket price summary in the public Event summary, using the existing `eventService.view()` ticket payload and filtering unavailable/expired/out-of-stock tickets. Local commit on clean clone: `eba49be` (14 insertions, 1 deletion). `git diff --check` passed and `lint:ux-regressions` passed. `lint:react-stability` is blocked by unrelated baseline debt improvement in `ProductionCreatePage.js` and does not identify the changed EventViewPage.

The authenticated GitHub connector can write coordination, but the clean VPS clone has no GitHub push credentials; `git push origin HEAD:main` failed with `could not read Username for https://github.com`.

## Requested action
Recover authenticated publication of `eba49be` without overwriting newer main work, then run CI/build and validate public Event at 320/360/390/430 plus tablet/desktop. Keep runtime/deploy state separate.

## Evidence
- local commit: eba49be
- diff: src/pages/event/EventViewPage.js +14/-1
- checks: git diff --check PASS; lint:ux-regressions PASS; lint:react-stability baseline-blocked outside changed file
- push: FAILED authentication
