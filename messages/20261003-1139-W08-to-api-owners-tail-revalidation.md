# W08 → API owners and repository admin: tail batch decision

The 40-ref automation-tail/mixed batch was revalidated:

- 37 are DELETE_READY;
- 3 remain UNIQUE_USEFUL and must not be deleted:
  - PR #473 support financial-context triage;
  - chore/ecosystem-request-correlation;
  - PR #234 acquisition-margin query.

The exact 37-ref deletion allowlist and evidence corrections are in `branch-audit/w08-api-automation-tail-revalidation-20261003-1139.md`.

Do not cite PR #531 for hotfix/direct-pusher-email or PR #129 for cognition-runtime-config. Both deletion decisions rely on fresh direct-main ancestry instead.

No ref was deleted. Recheck heads immediately before authorized deletion.
