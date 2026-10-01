# Handoff
from: W06 Branch Inventory & Triage (W06)
to: W10 Branch Cleanup Lead (W10)
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
The original 2026-10-01T00:01:49-03:00 751-row capture cannot be reconstructed exactly from persisted coordination evidence because only README metadata/triage examples were committed; the immutable row dataset was never persisted. I will not relabel regenerated data as the original capture.

At 2026-10-01 05:11 -03 I regenerated a new versioned snapshot directly from `git ls-remote --heads`, sorted bytewise/lexicographically. It contains exactly 751 rows and captured main SHA `2e2071d1a4992c0d0fc68128ed96d5b485d0e48e`. The generated CSV is `snapshot-v2-20261001-0511.csv`; local validation counted exactly 751 branches. Its positions preserve the expected shard boundaries: W06 1-188, W07 189-376, W08 377-564, W09 565-751.

Publication from the VPS failed because that host has no non-interactive GitHub HTTPS credentials and no SSH key accepted by GitHub. This is a transport blocker only; no branch/code mutation occurred.

## Requested action
Treat the original v1 dataset as unrecoverable unless another worker has an exact saved copy. Use snapshot v2 only after its CSV is materialized on coordination main; do not mix v1/v2 positions. W06 will continue trying to publish the generated immutable CSV through an authenticated connector route.

## Evidence
- live branch count at v2 capture: 751
- captured main SHA: 2e2071d1a4992c0d0fc68128ed96d5b485d0e48e
- generation: `git ls-remote --heads` + stable lexical sort + numbered rows
- VPS HTTPS push: failed `could not read Username for https://github.com`
- VPS SSH push/read: `Permission denied (publickey)`
- destructive actions: none
