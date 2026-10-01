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
All 751 branch names were enumerated through GitHub pagination (100 x 7 + 51). HEAD-SHA enrichment/triage is proceeding lexicographically through W06 positions 1-188. Compare evidence uses the current remote main at review time, so behind counts can increase while classification remains evidence-based.

## Evidence from W06 shard
- `agent/np07-t1/register-password-friction`, `agent/np08-t3/cutinapp-sharing-fallback-metadata`, and `agent/np13-t1/event-duplication-calendar-safety` all point to HEAD `5ad6a414c2586d5b76c6061bc6214a9757e0d0f2`. Compare against main reports ahead=0 and merge-base=HEAD. Classification: EXACT_DUPLICATE group; content ALREADY_MERGED. Strong SAFE_DELETE_CANDIDATE inputs, but deletion remains prohibited until consolidated manifest + explicit authorization.
- `agent/np13-t2/wallet-refresh-after-checkout` HEAD `5c603c26a4ef06f2c6c8ba05294fd63f4308ae49`, author Peter Tecnet, 2026-09-17T20:50:04Z. Current compare: behind, ahead=0, behind=983, merge-base=HEAD, no changed files; no PR found for this head. Classification: ALREADY_MERGED. Destination: retention not required for code preservation; candidate for final delete manifest after W10 confirms no operational reason to protect the branch.
- `activation/direct-first-ticket-publication` HEAD `34012ef8cb14ace1cb2e922bd4c200a87f2d09c0`: diverged, ahead=2, behind=1774. UNIQUE_USEFUL_REVIEW; do not delete. Exclusive work includes activation flow taking first batch directly to publication. Needs patch-equivalence review against newer activation branches/main before reuse.
- `agent/cutinapp-growth-conversion-global-location` HEAD `36bf814633c8d64a74fc98cabc150f946d80b178`: diverged, ahead=4, behind=283. UNIQUE_USEFUL_REVIEW pending patch-equivalence; exclusive history includes international postal/location support. Route to global/discovery reviewer before discard.
- `agent/growth-event-description-editor` HEAD `4618a0c9ffee47aad97cf85d0f903aa94e1ed88a`: diverged, ahead=3, behind=242. UNIQUE_USEFUL_REVIEW pending patch-equivalence; exclusive history includes formatted event description editor/public rendering. Route to event/editor reviewer before discard.
- `ai/pix-validity-round11` HEAD `f65a1b41f49109fd2e4290c534997d77b3080504`, 2026-09-09T21:25:20Z. Current compare is diverged (+3/-1357) because the historical branch commits are not ancestors of today's main; files differ in checkout/order recovery. However PR #447 for this exact head was MERGED on 2026-09-09 (`c4745bc7...`) and describes the same three commits/feature. Classification: ALREADY_MERGED, with patch-drift noted; candidate for final delete manifest only after W10 confirms current main intentionally evolved the affected checkout code.
- `asset-transfer-logo-20260927` HEAD `b502690741343c155b15c7235d08f25ddd815448`, 2026-09-27T10:57:36Z. Current compare: behind, ahead=0, behind=171, merge-base=HEAD, no changed files; no PR found. Classification: ALREADY_MERGED. Despite the branch name, its HEAD commit is `seo: avoid unsupported worldwide availability claim` touching `public/index.html`; destination is final delete-manifest candidate, not asset recovery.
- `auto/cutinapp-event-availability-status` HEAD `975c10985d386f64dd05c74bf4068949443ca0ed`, 2026-09-10T05:01:20Z. Current compare diverges (+1/-1351) and shows EventPage drift, but PR #453 for this exact head was MERGED on 2026-09-10 (`2099eaab...`). Classification: ALREADY_MERGED with patch-drift; candidate for final delete manifest after current EventPage equivalence/supersession is accepted.
- `automation/acquisition-activation-loop-20260905` HEAD `7b2688c2141a970097abeba33dcd937a2bb45e52`, 2026-09-06T02:12:37Z. Current compare diverges (+1/-1907), touching `src/pages/event/EventManagePage.js`, but PR #80 for this exact head was MERGED on 2026-09-06 (`4f85205d...`) and records the activation→share→sales-monitor telemetry/CTA. Classification: ALREADY_MERGED with substantial historical drift; do not resurrect the old commit directly. Candidate for final delete manifest after confirming newer EventManagePage owns the intended behavior.

## Next action
Continue W06 positions 1-188 through the remaining `automation/*` names. For old merged PR branches that now compare as diverged, retain the explicit `ALREADY_MERGED + patch-drift` distinction and never cherry-pick historical commits solely because current Git ancestry reports `ahead>0`. Group same-SHA branches immediately, then run patch-equivalence review for branches without merged-PR evidence. W07-W10 should consume this snapshot/order rather than create a competing branch ordering.
