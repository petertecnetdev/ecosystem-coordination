# Cutinapp Branch Inventory

Snapshot: 2026-10-01T00:01:49-03:00
Repository: petertecnetdev/cutinapp.petertecnet.com.br
Observed branch count: 751
Stable order: lexicographic branch name as returned by GitHub branch search.
W06 shard: positions 1-188 inclusive (first quarter; ceil(751/4)).

## Methodology
For every branch, capture branch name + HEAD SHA first. Triage then enriches with HEAD author/date, compare(main...HEAD), merge-base, ahead/behind, exclusive commits, changed files/areas, PR association/state and recency. Classification vocabulary is fixed: ACTIVE_PROTECTED, ALREADY_MERGED, EXACT_DUPLICATE, SUPERSEDED, UNIQUE_USEFUL_REVIEW, STALE_UNCLEAR, SAFE_DELETE_CANDIDATE.

SAFE_DELETE_CANDIDATE requires affirmative evidence: zero exclusive commits OR exact/equivalent content demonstrably in main/canonical branch, plus PR/compare review. Age/name alone never qualifies. No deletion is authorized by this inventory.

Exact duplicate grouping is HEAD-SHA based first; patch-equivalence is a second pass. Historical merge does not imply runtime deployment.

## Snapshot progress
All 751 branch names were enumerated through GitHub pagination (100 x 7 + 51). HEAD-SHA enrichment has started from the stable first page; shard triage is incremental because compare/PR/file evidence is required before destructive recommendations.

## Early evidence from W06 shard
- `agent/np07-t1/register-password-friction`, `agent/np08-t3/cutinapp-sharing-fallback-metadata`, and `agent/np13-t1/event-duplication-calendar-safety` all point to HEAD `5ad6a414c2586d5b76c6061bc6214a9757e0d0f2`. Compare against current main reports ahead=0, behind=985 and merge-base=HEAD. Classification: EXACT_DUPLICATE group, canonical temporarily the lexicographically first branch; content is ALREADY_MERGED into main. These are strong SAFE_DELETE_CANDIDATE inputs, but deletion remains prohibited until consolidated manifest + explicit authorization.
- `activation/direct-first-ticket-publication` HEAD `34012ef8cb14ace1cb2e922bd4c200a87f2d09c0`: compare reports diverged, ahead=2, behind=1774. UNIQUE_USEFUL_REVIEW; do not delete. Exclusive work includes activation flow taking first batch directly to publication. Needs patch-equivalence review against newer activation branches/main before reuse.
- `agent/cutinapp-growth-conversion-global-location` HEAD `36bf814633c8d64a74fc98cabc150f946d80b178`: diverged, ahead=4, behind=283. UNIQUE_USEFUL_REVIEW pending patch-equivalence; exclusive history includes international postal/location support. Route to global/discovery reviewer before discard.
- `agent/growth-event-description-editor` HEAD `4618a0c9ffee47aad97cf85d0f903aa94e1ed88a`: diverged, ahead=3, behind=242. UNIQUE_USEFUL_REVIEW pending patch-equivalence; exclusive history includes formatted event description editor/public rendering. Route to event/editor reviewer before discard.

## Next action
Continue W06 positions 1-188, enriching each with compare + PR + changed-file evidence; group same-SHA branches immediately, then run patch-equivalence review for divergent branches. W07-W10 should consume this snapshot/order rather than create a competing branch ordering.
