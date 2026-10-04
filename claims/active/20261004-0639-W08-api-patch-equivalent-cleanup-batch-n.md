# W08 API patch-equivalent branch cleanup batch N

- Worker: W08
- Repository: petertecnetdev/api.petertecnet.com.br
- Status: CLAIMED
- Scope: exact-tree duplicate payment-retry refs only
- Preserve: fix/commerce-card-payment-retry @ 1fb6d0ba52c616b22558abcff9abc9c6dfd22511
- Delete candidates after immediate revalidation:
  - feat/commerce-card-payment-retry @ f2db3565630c5492fe7ad839ec0ab330b877acc5
  - fix/commerce-card-payment-recovery @ eacdf3c64aaa25f1fede882b1e47b374f4b58870
- Proof: all three commit objects have identical tree SHA d2ea75ffb4695b52948e803b964d706ca0ea93de.
- Exclusions: open PR heads, W07 prefixes/claims, main, staging, develop, agent/*, preserve/*, quality/*.
- Safety: workflow exact-head guard; no force push, update_ref deletion, deploy, VPS, or new branches.
