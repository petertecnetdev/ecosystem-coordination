# W06 — Cutinapp branch inventory / shard 1 — run 11

## Snapshot refresh
- Repository: petertecnetdev/cutinapp.petertecnet.com.br
- Ordering: lexicographic branch name, same deterministic shard methodology as prior run.
- GitHub branch pagination still occupies pages 1–8 at 100/page; page 9 is empty. No deletion performed.
- Current main observed by compare API: `2e2071d1a4992c0d0fc68128ed96d5b485d0e48e`.

## Incremental classifications / evidence

| Branch | HEAD | ahead/behind main | PR evidence | Files/area | Classification | Destination |
|---|---|---:|---|---|---|---|
| `agent/np02/event-editor-view-parity` | `ff2ac040` | +2 / -536 | PR #606 CLOSED+MERGED 2026-09-22, merge `0b499127` | EventExperienceEditorSurface CSS/JS | `ALREADY_MERGED` | retain only until final patch-equivalence sweep; then deletion-manifest candidate |
| `agent/np02/event-public-network-recovery` | `9fb980fc` | +3 / -414 | PR #627 CLOSED+MERGED 2026-09-23, merge `a7685ee2` | EventViewPage, EventCommercePanel, EventCommunitySection | `ALREADY_MERGED` | retain only until final patch-equivalence sweep; then deletion-manifest candidate |
| `agent/np02/fastix-competitive-100` | `0e4b26f0` | +0 / -379; merge-base == HEAD | not required to establish ancestry | no remaining diff | `ALREADY_MERGED` | strong deletion-manifest candidate; no exclusive commits |
| `agent/np02/production-follow-state` | `52aa50fe` | +4 / -568 | PR lookup still pending | ProductionPublicPage, production CSS, CutinappService + social-follow test | `UNIQUE_USEFUL_REVIEW` | preserve; request frontend/service review before reuse/discard |
| `agent/np02/redeploy-after-health-fix` | `d7dc60d9` | +1 / -534 | pending | deploy-vps workflow only (+1 line) | `STALE_UNCLEAR` | preserve until patch-equivalence/workflow-history check |
| `agent/np02/redeploy-after-marker-fallback` | `7a5a296a` | +1 / -533 | pending | deploy-vps workflow only (1+/1-) | `STALE_UNCLEAR` | preserve until patch-equivalence/workflow-history check |

## Important interpretation
Merged PR state is evidence that work was accepted historically, but branches with non-zero current compare diff are NOT yet promoted to `SAFE_DELETE_CANDIDATE`; final deletion manifest still requires patch/content-equivalence against current main or a verified superseding branch. This avoids treating squash/rebase ancestry differences as proof of unused work.

## Counts added/confirmed this run
- `ALREADY_MERGED`: 3
- `UNIQUE_USEFUL_REVIEW`: 1
- `STALE_UNCLEAR`: 2
- `SAFE_DELETE_CANDIDATE`: 0 newly asserted
- remote branches deleted: 0

## Handoff
W07/W09: inspect `agent/np02/production-follow-state` before any discard decision. It contains four commits of production public follow-state/service behavior plus a dedicated social-follow test and remains materially divergent from current main.

## NEXT_ACTION
Continue shard 1 after these `agent/np02/*` entries: resolve PR association and patch equivalence for production-follow-state and the two redeploy branches, then proceed lexicographically through `agent/np03*`, `agent/np07*`, `agent/np08*`, etc. Group identical HEADs before per-branch deep comparison. Do not delete branches.
