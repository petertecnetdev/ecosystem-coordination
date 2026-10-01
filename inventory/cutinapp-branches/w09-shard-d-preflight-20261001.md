# W09 Branch Auditor D — API preflight 2026-10-01

Scope: positions 565–751. Canonical snapshot v2 and snapshot-v3-current.csv were not present at start of run, so this is PREPARATION evidence from the current GitHub branches API only, not final positional classification.

## API preparation

Fetched current branch API pages 6, 7 and 8 (covering the live lexical region that intersects the expected final quarter). The live list exposes strong branch-explosion families including:

- `perf/react-stability-57-{fix,notifications,v3}`
- `perf/render-diagnostics-60-{v2,v3}` plus unsuffixed branch
- `perf/resource-hints-20260906{-v2}`
- `perf/scroll-main-thread-20260919` + `perf/scroll-main-thread-v2-20260919`
- `profitability/pix-navbar-cta{-v2}`
- `refactor/shared-api-v1` + `refactor/shared-api-v1-current`
- numerous `w08/*` one-fix branches
- `w01/production-public-compact-overlay` and `w06/event-flyer-globalize-20260928` share exact HEAD `609df19157954ea18f4ba292c9b4651ad735fd61`.

## Confirmed evidence independent of positional snapshot

1. `w01/production-public-compact-overlay` and `w06/event-flyer-globalize-20260928`
   - exact same HEAD: `609df19157954ea18f4ba292c9b4651ad735fd61`
   - compare main...HEAD: status=behind, ahead_by=0, behind_by=103, merge-base=HEAD, files=[]
   - preparation classification: `EXACT_DUPLICATE` + `ALREADY_MERGED`; safe-delete candidate after canonical snapshot confirms shard membership and final review.

2. `temp-unused`
   - HEAD `410f4d4bf9c6dae676bbc982bc2ead9867df43d9`
   - compare main...HEAD: status=behind, ahead_by=0, behind_by=1885, merge-base=HEAD, files=[]
   - preparation classification: `ALREADY_MERGED`; safe-delete candidate after canonical snapshot confirms shard membership and final review.

## Root-cause signal

The API list itself demonstrates repeated creation of alternative branches for the same intent using suffixes `v2`, `v3`, `fix`, `main`, `mainline`, `current`, `final`, and dated reruns. This is consistent with agents/automation creating a new branch for iterative attempts instead of updating an existing branch/PR, combined with lack of post-merge cleanup.

Recommended permanent hygiene for W10 review:

1. enable auto-delete head branch after merged PR where branch is not protected/reused;
2. agent branch TTL + explicit review queue before deletion;
3. require reuse/update of existing branch/PR for same work item unless divergence is documented;
4. naming convention containing worker/work-item ID rather than free-form suffix proliferation;
5. retain main protection and forbid force updates;
6. periodic hygiene report: total branches, merged-but-retained, no-PR stale, duplicate HEAD groups, age buckets and active protected branches.

## Safety

No branch deleted; no force push/reset/clean; no deploy/VPS.

## NEXT_ACTION

When `snapshot-v2-20261001-0511.csv` or `snapshot-v3-current.csv` is published, bind positions 565–751 to this preparation, batch compare all 187 tips against main, group duplicate HEAD/patches and merged PRs, then publish the final structured shard classification and W10 handoff.
