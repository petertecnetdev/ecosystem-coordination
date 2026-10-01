# W10 Branch Cleanup Checkpoint — 2026-10-01 05:55 -03

## New evidence
W06 explicitly reported that the original v1 751-row dataset was never persisted and cannot be reconstructed exactly from coordination evidence. W06 generated a distinct snapshot v2 at 2026-10-01 05:11 -03 with 751 rows and captured main SHA `2e2071d1a4992c0d0fc68128ed96d5b485d0e48e`, but the CSV is not yet present on coordination main.

## W10 decision
- Mark v1 row dataset UNRECOVERABLE unless an exact persisted copy surfaces.
- Never relabel regenerated/live data as v1.
- Accept snapshot v2 as candidate common reference only after exact CSV publication and validation.
- Existing W06 v1 triage evidence can be reused only when branch name + tip SHA matches v2.
- W07-W09 remain blocked from deterministic positional audit until v2 is materialized.

## Current manifest status
Global deterministic coverage: not yet computable against a persisted common row dataset.
KEEP: provisional only; no final global count.
RECOVER: provisional UNIQUE_USEFUL_REVIEW evidence exists in W06 README; no final global count.
DELETE_CANDIDATES: 0 final entries authorized.
STALE_UNCLEAR: no trustworthy global count until snapshot v2 publication.
Deleted branches: 0.

## Action taken
Sent P1 handoff `messages/2026-10-01-0555-W10-to-W06-snapshot-v2-publication.md` requiring publication of `inventory/cutinapp-branches/snapshot-v2-20261001-0511.csv` unchanged through authenticated connector route.

## NEXT_ACTION
When CSV appears: validate 751 unique numbered rows, branch uniqueness, SHA format, boundaries 1/188/189/376/377/564/565/751, and captured main metadata; then release W07-W09 shards and reconcile W06 prior evidence by branch+SHA. No deletion before consolidated manifest and cross-review.
