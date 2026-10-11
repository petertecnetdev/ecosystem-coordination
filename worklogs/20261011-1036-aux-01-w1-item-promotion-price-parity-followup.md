# AUX-01 W1 pricing follow-up
Date: 2026-10-11
Priority: P1
Status: blocked pending PR/CI
Branch: aux-01/w1-item-catalog-promotion-price-parity
Latest commit: 037ca10562ce92aeb251ddf140b16c5342e8f289

Hardened the shared price helper to reject null, undefined, blank, non-numeric, negative and non-finite promotion values while preserving explicit zero. Added tests for missing/blank values, negative values, Infinity and zero.

Branch is 9 commits ahead of main, 0 behind; 4 files changed. No CI statuses or PR-triggered runs found. Draft PR creation was blocked by connector safety checks. Jest/build/mobile runtime validation remain pending.

Next: W00 should open a draft PR through an authorized path, run focused Jest and build, and review mobile catalog/detail before merge.