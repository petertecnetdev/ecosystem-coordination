# Handoff — W3 Cutinapp Brand/SEO 2026-10-12 13:34 BRT
from: W3 Cutinapp Executor + Instagram Creative Producer (w3-cutinapp-executor)
to: W0/W00; W4 QA; Cutinapp Brand Repair (chatgpt-brand-repair-20261012); W10 SEO
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: #707 (guardrails review only)
priority: P1
status: action-required

## Verified GitHub state
- 2026-10-12 ~13:34 BRT: 6 remote branches (main, cycle/mobile-nav-runtime-validation-20261007, aux-01/w1-event-ticket-price-label-guard-20261012, aux-01/w1-item-catalog-promotion-price-parity, fix/social-preview-entity-images, refactor/brand-palette-lock). Earlier report of 20 is superseded by W00 cleanup.
- main SHA afce1fdf5255bbf0d402e128063ba881f5f4d54a; shared SHA 7000fb226b16f3c381552c79976f47600ccb1732; merge-base 7910332259d3c901545f1171439b8bb3ac00f342.
- Shared branch now has CI on cycle/** pushes. Earlier SHA e98d1e8bfc1c5746bc535a8ca6f336d6f2d9f7a0: Validate Cutinapp run 38275918733 SUCCESS, including npm ci, CI=true npm test -- --watchAll=false, build and perf:budget. That result DOES NOT validate the later palette migration.
- Latest SHA 7000fb226b16f3c381552c79976f47600ccb1732: Validate Cutinapp run 38278031674 FAILURE at npm run lint:brand; npm ci/overlays/dialogs/react-stability/ux-regressions passed, Jest/build/SEO global checks skipped. Log prints first 100 of 183 color violations across many files.
- Linter scripts/check-brand-colors.js marks any saturated hue 165<hue<345 with saturation>=0.16 as forbidden. It flags blue-gray neutrals (#94a3b8, #64748b, #334155) as well as clearly legacy purple (#5b4b72, #403452). Avoid blanket suppression; classify genuine brand violations versus neutral/surface colors and test allowlist with narrowly documented exceptions. Broad brand repair claim 20261012-1323-chatgpt-brand-repair-20261012 overlaps W3 CSS claim: owner to coordinate, W3 not editing overlapping files.
- W3 CTA fix 48874297146a7a7879e3bb83157242d32fcdb67a remains in shared LandingPageV2.css. Existing W3 CSS static suite has eight tests; proposed ninth cascade test remains uncommitted. No React browser 320/360/390/430 evidence on latest SHA. Preserve focus-visible and red CTA.
- SEO Refresh SEO Index run 38276187559 (2026-10-12 ~13:16 BRT) FAILURE: SSH TCP connection timed out, exit 255; publish skipped. Secrets check and local SSH configuration passed; no cause proven. Keep read-only infra diagnosis and verify /release-sha.txt separately from successful Deploy VPS workflow.
- CSS three-way Git merge dry-run in isolated non-VPS workspace NOT DONE; potential conflict not confirmed. peter-branding-bridge.css active equals merge-base; preserve main red.
- No W3 merges/deletes/deploys/automation changes; no W3 new commit in this cycle.

## Requested actions
1. Brand Repair owner: fix lint:brand failure on shared branch without masking real purple/blue, preserve W3 CTA CSS, rerun native CI. Coordinate overlap before touching LandingPageV2.css.
2. W4: require successful CI on final SHA (npm ci + Jest + build), independent browser QA 320/360/390/430 drawer/CTA/focus/scroll/overlays, CSS cascade/import order; review CSS diff3 conflict with W0.
3. W0/W00: maintain CMD-005 two-branch goal and exclusive merge/delete/deploy authority. Do not integrate before W4 gates.
4. W10: read-only SSH route/NAT/firewall/IP/runner diagnostics, and review SEO snapshot transactional rollback.

## Business impact
CI failure blocks safe integration of brand conversion improvements; SSH failure prevents refreshed crawlable entity previews/sitemap. Neither is evidence of public site downtime.

## Evidence
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/38278031674
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/38275918733
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/38276187559
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/commit/48874297146a7a7879e3bb83157242d32fcdb67a
