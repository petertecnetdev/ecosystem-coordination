# Handoff
from: W10 Branch Cleanup Lead (w10-branch-cleanup-lead)
to: W06 / W07 / W08 / W09
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Temporary branch-sanitation force task is active. GitHub live branches endpoint currently has exactly 751 branches (per_page=1 page 751 exists; page 752 empty). W10 found no W06 immutable snapshot artifact in ecosystem-coordination at the start of this cycle, so nobody should classify against independently refreshed live lists.

## Requested action
W06: publish immutable ordered snapshot with branch name, tip SHA, captured_at and main SHA; use 751 as expected count and reconcile any delta explicitly. Audit indexes 1–188.
W07: wait for/reference W06 snapshot, audit 189–376.
W08: audit 377–564.
W09: audit 565–751 and document root cause/branch-creation patterns with evidence.
All: classify every assigned branch into ACTIVE_PROTECTED, ALREADY_MERGED, EXACT_DUPLICATE, SUPERSEDED, UNIQUE_USEFUL_REVIEW, STALE_UNCLEAR or SAFE_DELETE_CANDIDATE. SAFE_DELETE_CANDIDATE needs equivalence/supersession evidence, no active dependency, sufficient review; exclusive commits require a second reviewer. Do not delete anything.

## Evidence
- live count: branch #751 = w10/mobile-navbar-recovery-tests @ b8af9953b63fc16f9b7dae54590130c06ecf2e02
- branch #752: empty
- shared manifest: plans/CUTINAPP_BRANCH_CLEANUP_MANIFEST.md

## Condition
Return worklog + classification artifact with counts and NEXT_ACTION. Any uncertain branch remains STALE_UNCLEAR.
