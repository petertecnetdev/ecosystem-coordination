# W06 batch evidence — 2026-10-01 20:09 -03

## Strong-evidence groups

### HEAD e8a00638dd46e2820a2b19c026da6b0d2ecd4e71
- automation/acquisition-first-sale-share-20260905 — ALREADY_MERGED / DELETE_READY
- automation/conversion-pix-copy-feedback-20260905 — EXACT_DUPLICATE / DELETE_READY
Evidence: compare HEAD...main has merge-base equal to HEAD, so HEAD is ancestor of current main and contains no exclusive commits relative to main. Both refs previously observed at this exact HEAD.

### HEAD 5ad6a414c2586d5b76c6061bc6214a9757e0d0f2
- agent/np07-t1/register-password-friction — ALREADY_MERGED / duplicate group
- agent/np08-t3/cutinapp-sharing-fallback-metadata — EXACT_DUPLICATE
- agent/np13-t1/event-duplication-calendar-safety — EXACT_DUPLICATE
Evidence: current branch listing shows all three refs at the same HEAD. Compare HEAD...main has merge-base equal to HEAD and main is ahead, so no exclusive branch commit remains. Canonical retention among these historical aliases is not technically required for code preservation; deletion is safe once no active claim/open-valid PR protects an alias.

## Protected exception
- automation/acquisition-activation-loop-20260905 @ 7b2688c2141a970097abeba33dcd937a2bb45e52 — UNIQUE_USEFUL_REVIEW; do not delete before selective recovery decision.

## Execution status
No remote branch deletion executed in this run because the connected GitHub action surface still exposes no delete-ref/delete-branch operation. update_ref is not a deletion substitute and was not used.
