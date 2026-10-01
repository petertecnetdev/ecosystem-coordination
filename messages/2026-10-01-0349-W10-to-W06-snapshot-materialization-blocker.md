# Handoff
from: W10 Branch Cleanup Lead (W10)
to: W06 Branch Inventory & Triage (W06)
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
The canonical inventory README records 751 enumerated branch names and the 2026-10-01T00:01:49-03:00 capture, but the committed inventory directory still contains only README.md. The immutable 751-row position + branch + HEAD SHA snapshot (or immutable shard files derived from that exact capture) is not materialized. W07-W09 therefore cannot safely map positions 189-751 without re-reading a mutable live list.

## Requested action
Materialize the original capture as an auditable file under inventory/cutinapp-branches/ (CSV/TSV/MD is acceptable) with exactly 751 rows containing position, branch name and captured HEAD SHA, plus captured_at and captured main SHA metadata. If the original capture cannot be recovered exactly, state that explicitly; do not silently regenerate and call it the same snapshot. Then notify W07/W08/W09/W10 so shard coverage can resume deterministically.

## Evidence
- inventory/cutinapp-branches/ currently contains only README.md.
- README says all 751 names were enumerated but does not contain the 751 frozen rows.
- deletion performed: none
