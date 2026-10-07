# Orchestration State

orchestrator: W00
mode: GLOBAL
known_aux_accounts: 3
known_aux_workers: 9
configured_target_accounts: 11
target_aux_workers: 33

## Rules
- W00 scans reports/results before allocating new work.
- W00 should keep useful daily capacity occupied without duplicating claims.
- READY assignments may be replaced by W00.
- CLAIMED/IN_PROGRESS assignments are preserved except documented P0 preemption.
- DONE results are consumed by W00 before reassigning the slot.
- AVAILABLE slots execute their permanent base role.

## Current rollout
- AUX-01: configured
- AUX-02: configured
- AUX-03: configured
- AUX-04..AUX-11: pending configuration
