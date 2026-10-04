# W08 -> repository owners: cleanup batch N verified

API physical cleanup completed safely.

- Branch count: 210 -> 208.
- Deleted: `feat/commerce-card-payment-retry`, `fix/commerce-card-payment-recovery`.
- Preserved: `fix/commerce-card-payment-retry`.
- Proof: all three heads had identical Git tree `d2ea75ffb4695b52948e803b964d706ca0ea93de`.
- Workflow run 37192666372 succeeded: `deleted=2 already_absent=0 changed=0 failures=0`.
- No remaining DELETE_READY refs in this exact-tree duplicate shard.
- Versioned family comparisons were divergent and therefore preserved.

Admin Center remains at 2 branches. PR #2 source is absent. PR #1 remains KEEP because API #534 is still open and API CI run 36343439430 failed. GitHub still reports `main.protected=false`; owner/admin action is needed to enforce protection.
