# Cutinapp Branch Cleanup Manifest

status: IN_PROGRESS
repository: petertecnetdev/cutinapp.petertecnet.com.br
coordinator: W10 Branch Cleanup Lead
reference_count: 751
reference_observed_at: 2026-09-30T23:59:00-03:00
snapshot_owner: W06
snapshot_artifact: PENDING — not present in ecosystem-coordination when W10 started this cycle

## Safety gate
NO REMOTE BRANCH DELETION AUTHORIZED. No branch enters final DELETE_CANDIDATES by age, prefix or missing PR alone. Commits exclusive to a branch require specific second review before final deletion candidacy.

## Worker partitions
- W06: inventory + first quarter (target indexes 1–188 once immutable snapshot is published)
- W07: second quarter (189–376)
- W08: third quarter (377–564)
- W09: fourth quarter + root cause (565–751)
- W10: conflict resolution, cross-review, consolidation, final safety gate

Partitions are index-based against the W06 immutable ordered snapshot. Do not independently repartition against a changing live branch list.

## Required classes
ACTIVE_PROTECTED; ALREADY_MERGED; EXACT_DUPLICATE; SUPERSEDED; UNIQUE_USEFUL_REVIEW; STALE_UNCLEAR; SAFE_DELETE_CANDIDATE.

## Consolidated manifests
### KEEP
Pending worker evidence. ACTIVE_PROTECTED branches belong here. No inferred entries yet.

### RECOVER
Pending worker evidence. UNIQUE_USEFUL_REVIEW branches must include branch, tip SHA, unique commits/files, relevant tests, architectural decision and selective integration strategy. Prefer clean integration branch/cherry-pick; never blind historical merge.

### DELETE_CANDIDATES
Pending worker evidence and cross-review. Eligible only with merge/patch equivalence or identified supersession, no active dependency, sufficient review, and second review for exclusive commits.

### STALE_UNCLEAR
Pending worker evidence. Any uncertainty stays here and is not deletable.

## Coverage
classified: 0 / 751 (0.0%)
KEEP: 0
RECOVER: 0
DELETE_CANDIDATES: 0
STALE_UNCLEAR: 0
other classified intermediate states: 0

## Cross-review rule
Before final DELETE_CANDIDATES:
1. sample merged/duplicate/superseded groups across workers;
2. every branch with commits not reachable from main receives a named second reviewer;
3. disagreement or missing evidence => STALE_UNCLEAR;
4. deletion remains blocked until explicit user authorization after final manifest.

## Prevention policy draft
Subject to W09 root-cause evidence:
- enable auto-delete head branch after merged PR where safe;
- naming convention by worker/topic, with one active branch/PR per task;
- agents reuse existing task branch/PR instead of creating run-number branches;
- TTL only as review trigger, never automatic deletion of unreviewed work;
- protect main; no force push;
- scheduled branch hygiene report: total open branches, age buckets, no-PR count, merged-head count, duplicate-tip count;
- periodic manual cleanup based on auditable manifest.

## NEXT_ACTION
W06 publish immutable 751-branch snapshot (ordered name + tip SHA + captured_at + main SHA). W07-W09 audit only their index ranges from that snapshot and publish per-branch evidence. W10 then consolidates manifests and assigns cross-review/second-review samples before any destructive authorization request.
