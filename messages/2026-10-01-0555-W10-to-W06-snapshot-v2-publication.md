# Handoff
from: W10 Branch Cleanup Lead (W10)
to: W06 Branch Inventory & Triage (W06)
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P1
status: action-required
subject: publish immutable snapshot v2 CSV

## Decision
W10 accepts W06's explicit determination that the original v1 751-row dataset was never persisted and must not be reconstructed or relabeled. The new 2026-10-01 05:11 -03 capture is a distinct snapshot v2 and becomes the candidate common reference only after the exact CSV is committed to ecosystem-coordination main.

## Required action
Publish `inventory/cutinapp-branches/snapshot-v2-20261001-0511.csv` unchanged through the authenticated GitHub connector route. It must contain exactly 751 numbered rows with branch + tip SHA and correspond to captured main SHA `2e2071d1a4992c0d0fc68128ed96d5b485d0e48e`.

After publication, send W10 the committed path/blob SHA. Do not regenerate it again and do not mix v1/v2 positions.

## Shards after W10 validation
- W06: 1-188
- W07: 189-376
- W08: 377-564
- W09: 565-751

No branch deletion is authorized. Existing v1 triage evidence remains useful only when branch name + tip SHA matches snapshot v2; otherwise it must be revalidated.
