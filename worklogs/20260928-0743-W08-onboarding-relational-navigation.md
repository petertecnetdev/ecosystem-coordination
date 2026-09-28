# W08 worklog — onboarding relational navigation

- Worker: W08 — Navigation Weaver
- Item: W08-018
- Priority: P1
- Status: VERIFIED_CODE_NOT_DEPLOYED
- Completed: 2026-09-28T07:43:00-03:00

## Problem found
The assisted onboarding table exposed the production name and producer email but ended with the email-resend mutation. Operators had to repeat both searches manually while diagnosing activation progress.

## Implementation
- Added “Abrir produção” using the existing global production-admin search.
- Added “Abrir produtor” using the existing user-admin search.
- Initialized the production-admin query from an encoded `?q=` parameter.
- Omitted each action safely when the corresponding name or email is absent.
- Preserved onboarding creation, handoff/resend, permissions, pagination and API contracts.
- Added no requests to the source page and changed no shared W04 primitive.

## Files
- `src/pages/admin/AssistedProducerOnboardingPage.js`
- `src/pages/admin/ApplicationAdminProductionsPage.js`

## Git
- Branch: `w08/onboarding-relational-navigation`
- Commits: `6387818d07b1464758c2e9a81b8533d292c39dcd`, `51b8230eda22cdf730a70dd2cf1ba0bcc048b692`
- PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/690
- Merge: `e744659b44d514df0fdf7f67431320c044cc9da1`

## Tests and evidence
- PR Validate 36410332347: success
- PR Lighthouse 36410332210: success
- Main Validate 36410632047: success
- Main Lighthouse 36410632159: success
- Deploy 36410817451: failed at `Fetch frontend build environment`.
- `Build frontend on GitHub runner`, `Deploy application` and `Health check` were skipped.

## Expected impact
Reduces operational friction between producer activation status and the two related administrative entities, accelerating investigation and handoff without extra request fan-out.

## Pending / requests
- W05/release owner: investigate the recurring frontend build-environment fetch failure and rerun the validated release.
- Production availability remains unverified until deploy and health check both succeed.
