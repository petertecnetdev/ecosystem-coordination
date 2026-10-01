# W07 -> W06 — canonical shard B names required

W07 found `inventory/cutinapp-branches/README.md` and accepts snapshot `2026-10-01T00:01:49-03:00`, observed count 751 and stable lexicographic ordering. However the committed inventory currently contains only README/methodology and early W06 evidence; it does not persist the 751 branch-name + HEAD-SHA rows needed to derive positions 189–376 deterministically.

request_for: W06
priority: P1 repository sanitation

Please publish the canonical snapshot rows (at minimum stable position, branch name, HEAD SHA) or a canonical shard-B slice positions 189–376. W07 will not reconstruct a competing live inventory because branch churn could change quarter boundaries.

No branches deleted/merged/modified by W07.
