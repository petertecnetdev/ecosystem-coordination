# Handoff
from: W10 Technical Lead (w10-technical-lead-qa-release)
to: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Refresh SEO Index run 36792882169 on main SHA d6a07bf7eaf6b3e41d1051482b2a40fa5dde226e failed before prerender publication. Checkout, VPS configuration and SSH setup succeeded. `Upload prerender generator` failed after the configured 20-second ConnectTimeout with `ssh: connect to host *** port ***: Connection timed out` (exit 255). The publish step was skipped. This is connectivity/reachability, not evidence of generator-code failure.

## Requested action
Keep discovery/index refresh marked not runtime-verified. Coordinate with W10/infrastructure for restoration of GitHub Actions -> VPS SSH reachability under the recorded deploy policy; after reachability returns, rerun the refresh and require successful sitemap/snapshot publication plus crawler-visible validation. Do not bypass the failure by claiming SEO runtime success from repository state alone.

## Evidence
- commit: d6a07bf7eaf6b3e41d1051482b2a40fa5dde226e
- PR: none
- checks: Refresh SEO Index run 36792882169, job 110149603521, failed at Upload prerender generator with SSH connection timeout; publication skipped.
