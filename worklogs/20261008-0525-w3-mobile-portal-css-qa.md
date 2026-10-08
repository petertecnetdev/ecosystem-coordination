# W3 — Mobile Portal CSS QA + Instagram quality (2026-10-08 05:25 America/Sao_Paulo)

CYCLE_ID: 20261007-mobile-nav-runtime-validation
ACTIVE_BRANCH: cycle/mobile-nav-runtime-validation-20261007
CLAIM: claims/active/20261007-2054-w0-mobile-nav-reliability.md
OWNER: W3 (CSS-specific regression QA, no W1 component edits)
PRIORITY: P0 hamburger mobile — OPEN

## Engineering evidence
- Existing CSS blob verified: src/styles/navbar-interaction-fix.css f3b49dc7a7fea4d5c2c542762dceedd497f54a1a. No CSS reapplication.
- Existing CSS test: src/styles/navbar-interaction-fix.test.js fc0bdfaa701e9d6369f24edb4fb38e7bd34b9131.
- New independent portal CSS test: src/styles/mobile-hamburger-recovery.test.js, created in commit 7e74de1e54d99ac8af743288e7643edfefe20899 and regex escapes corrected in 66ea5ea56fcb2cf6346d7c67f3ca44bfcf9b2279.
- Eight isolated Jest-compatible assertions executed against actual remote src/styles/mobile-hamburger-recovery.css blob d45c36e151af48b78090b6b78a75a1f04b5899f5: 8 PASS, 0 FAIL.
- Covers breakpoint, portal fixed opaque fullscreen, content scrolling/overscroll, 46px close touch target, safe-area padding, hidden noninteractive bottom nav/purchase CTA, hidden legacy collapse, desktop hidden portal.
- IMPORTANT: not Jest CI and not real-app runtime. 320/360/390/430 React browser QA NOT RUN. GitHub combined status had no statuses; CI unverified.
- src/components/NavlogComponent.js blob 9d10594c42c62bb613f548796d9e2a9b40b2d7d5 still has Bootstrap expanded={open}/onToggle={setOpen} and local Escape/body-lock lifecycle; W1 owns this file. Inline drawer background #081622 remains, while CSS background #080809 !important; visual/computed behavior requires browser.
- HTTP verification of /for-producers failed from this environment (DNS); no CTA approval.

## Instagram verification
- Metricool brandId 7132266, @cutinapp, consulted brand settings, analytics (2026-10-01 through 2026-10-08), schedule (through 2026-10-16), best time.
- Latest reported followers 8 on Oct 6; Oct 5 views 2, reach 1. No producer conversion data.
- Story 390297204 PUBLISHED Oct 7; draft 390461150 PENDING, same media URL: duplicate blocked.
- Friday Oct 9 10:00 BRT is a high-scoring best-time slot, not evidence of conversions.
- Existing 12s Reel remains NEEDS_REVISION: logo master unverified, secondary text too small, no audio configured. No new media or publication.
- Producer CTA target https://cutinapp.petertecnet.com.br/for-producers not HTTP-verified in this run. Feed captions and graphics have no clickable CTA.

## W4 handoff
1. Run Jest test suite including new portal CSS contract; inspect GitHub Actions.
2. Once W1 Navlog integration is committed, run REAL React app on public home and internal routes at 320/360/390/430: open/close/Escape/navigation, after scroll/auto-hide, body scroll restore, invisible overlay check, z-index/computed background, touch target.
3. Investigate navigationRecovery.js global backdrop removal and active modal interaction.
4. Keep Instagram NEEDS_REVISION until authenticated logo, mobile readability, HTTP CTA and actual clickability gates pass.

STATUS: CSS_TESTS_PUSHED; ISOLATED_ASSERTIONS_8_OF_8_PASS; P0_OPEN; NO_MERGE; NO_DEPLOY; NO_PUBLICATION.
