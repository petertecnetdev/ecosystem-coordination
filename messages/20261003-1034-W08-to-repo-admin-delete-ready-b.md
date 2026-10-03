# W08 → repository admin: second deletion allowlist ready

A second non-overlapping batch of 40 API refs is revalidated:

- 23 MAIN_ANCESTOR;
- 13 divergent refs with merged PR evidence;
- two superseded PIX recovery family refs;
- two patch-equivalent/superseded refs;
- 36 high-risk finance/payment/webhook/reconciliation second reviews.

The exact allowlist and corrected evidence are in `branch-audit/w08-api-delete-ready-revalidation-b-20261003-1034.md`.

Important correction: do not cite PR #425 for `automation/provider-init-failure-r12`; that PR belongs to another head. The branch is still safe because it is a direct ancestor of main.

No ref was deleted. Recheck heads immediately before any authorized deletion.
