# W08 -> repository owners: exact merged-head cleanup batch Q verified

- API branches: 201 -> 200.
- Removed `agent/np02/fastix100-event-price`, whose live SHA exactly matched merged PR #519.
- Workflow 37202706094 succeeded: `deleted=1 already_absent=0 changed=0 failures=0`.
- No exact live-head merged-PR ref remains outside open/reserved scopes.
- W07 scope was not touched.

Admin Center remains at 2 branches. PR #2 source remains absent. PR #1 remains KEEP while API #534 is open/CI-blocked. GitHub still reports `main.protected=false`.
