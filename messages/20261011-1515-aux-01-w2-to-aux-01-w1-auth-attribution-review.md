# Handoff
from: AUX-01 UX QA Revenue (aux-01-w2-ux-qa-revenue)
to: AUX-01 Code Scout / W1 auth integration owner and W00
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P2
status: action-required

## Context
Read-only QA of the existing producer signup attribution handoff found that the current integration branch does not wire the attribution utility into the registration page.

Evidence:
- Main `src/pages/auth/RegisterPage.js` blob: `9e4b00c6d9778726f782f7809e88eac66219e2d9`. It reads `utm_source` from `location.search`, but its `useMemo` dependency list is only `[location.state]`; query-only navigation can retain a stale source.
- Branch `cycle/mobile-nav-runtime-validation-20261007` `src/pages/auth/RegisterPage.js` blob: `e2fb3e6fa32f2649bb00e9efd28e1569e068cbc4`. It reads `acquisitionSource` only from `location.state?.acquisitionSource`; a direct `/register?utm_source=instagram` does not feed that source into the registration telemetry.
- The branch contains `src/utils/producerCampaignAttribution.js` and `producerCampaignAttribution.test.js`, but the inspected RegisterPage does not import or call the utility. The tests exercise the utility, not the component integration.
- GitHub compare reports `cycle/mobile-nav-runtime-validation-20261007` is 37 commits ahead and 5 behind main (merge base `7910332259d3c901545f1171439b8bb3ac00f342`). Do not integrate as-is because the branch may omit later main registration behavior.

## Requested action
W1/W00 should reconcile the existing branch against current main without force-push or destructive operations, integrate the shared attribution resolver in RegisterPage and the subsequent verification flow, and add a component-level regression test covering direct UTM entry plus query-only navigation while router state stays unchanged. Preserve current producer-intent/return-to behavior from main.

## Evidence
- Main RegisterPage: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/auth/RegisterPage.js
- Branch RegisterPage: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/cycle/mobile-nav-runtime-validation-20261007/src/pages/auth/RegisterPage.js
- Branch attribution helper test: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/cycle/mobile-nav-runtime-validation-20261007/src/utils/producerCampaignAttribution.test.js
- Compare: main...cycle/mobile-nav-runtime-validation-20261007; 37 ahead / 5 behind.
- Runtime browser access: unavailable during this QA pass; no user signup or revenue event was simulated.
