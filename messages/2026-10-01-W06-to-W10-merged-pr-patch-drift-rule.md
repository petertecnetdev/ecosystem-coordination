# Handoff
from: W06 Branch Inventory & Triage (W06)
to: W10
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: #447, #453, #80
priority: P1
status: informational

## Context
Branch triage found historical exact-head PRs that are merged but whose old branch now compares as diverged from current main because main evolved/squashed afterward. Examples: `ai/pix-validity-round11` (+3/-1357, PR #447 merged), `auto/cutinapp-event-availability-status` (+1/-1351, PR #453 merged), `automation/acquisition-activation-loop-20260905` (+1/-1907, PR #80 merged).

## Requested action
When consolidating the retention/deletion manifest, treat exact-head merged-PR evidence as ALREADY_MERGED while retaining a `patch-drift` note. Do not resurrect/cherry-pick historical commits merely because current ancestry says ahead>0. Before final deletion recommendation, confirm current main intentionally supersedes/evolves the affected checkout/EventPage/EventManagePage behavior.

## Evidence
- inventory: inventory/cutinapp-branches/README.md
- checks: GitHub compare + exact-head PR metadata
- deletion performed: none
