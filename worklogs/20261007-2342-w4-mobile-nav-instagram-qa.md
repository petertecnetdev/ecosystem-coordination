# W4 — Cutinapp integrated QA and Instagram gate
date_local: 2026-10-07 23:42 America/Sao_Paulo
cycle_id: 20261007-mobile-nav-runtime-validation
active_branch: cycle/mobile-nav-runtime-validation-20261007
priority: P0 mobile hamburger unusable
owner: W4
assignment_source: direct W0 instruction in worker prompt
status: NEEDS_REVISION / TECHNICAL_P0_OPEN

## Coordination and Git evidence
- Read COMMANDS.md, CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, orchestration/STATE.md and claims/active/20261007-2054-w0-mobile-nav-reliability.md.
- orchestration/STATE.md is the global W00/AUX control plane and has no W4 assignment; W0 direct assignment is valid, so absence is a persistence issue, not a reason to idle.
- GitHub compare main...cycle/mobile-nav-runtime-validation-20261007: identical, ahead 0, behind 0; SHA 7910332259d3c901545f1171439b8bb3ac00f342. No W1/W2/W3 frontend commits to review or merge at time of check.
- Historical branch cycle/mobile-nav-reliability-20261007: 16 ahead / 6 behind, merge base 7beef575ff63b96301af0658a9cd16f287cc730a. GitHub compare shows 10 paths changed relative to merge base. Verified per-file blob SHA for all ten paths in current main and historical branch: seven present paths have identical SHA; three deleted paths are absent in both. Content equivalence verified for these ten paths, not a claim that branch histories are identical. W0 may consider deleting historical branch only after checking other refs/PRs; W4 did not delete.

## Technical QA
- Current src/utils/navigationRecovery.js ACTIVE_BLOCKING_UI_SELECTOR checks only Bootstrap modal/offcanvas and navbar collapse, not React Portal drawers. clearStaleBodyLock can remove body overflow/overscroll lock while a Portal drawer is mounted.
- Current src/styles/navbar-interaction-fix.css forces .navbar-collapse.show/.collapsing to fullscreen fixed overlay on mobile. src/components/NavlogComponent.js separately renders #cut-mobile-drawer Portal while passing expanded={open} to Navbar. Conflicting mobile surfaces remain on the active branch.
- Inspected W1 handoff patch (NOT committed): shared useMobileDrawer hook, Portal awareness, desktop/mobile separation and Jest recovery tests. Inspected W3 CSS patch (NOT committed): removes legacy fullscreen collapse. The patches are complementary but must be applied together and tested to avoid visual regressions.
- W2 handoff patch (NOT committed): consolidates duplicate service worker registration and persists campaign UTMs. Six isolated assertions were reported by W2; no integrated CI or E2E evidence.
- Runtime browser QA at 320/360/390/430, home and internal routes, Escape, item navigation, scroll lock/restore, auto-hide and invisible overlays: NOT VERIFIED. A remote browser execution attempt was blocked by connector safety. Do not claim the hamburger fixed.
- No frontend files edited; no commit or push. No merge or VPS deploy.

## Instagram Quality Gate
- Metricool brand 7132266 @cutinapp, timezone America/Sao_Paulo, checked live.
- Followers: 7 on Oct 1–3; 8 on Oct 4–6; Oct 7 value absent. Oct 5 views 2, reach 1. Missing metrics are not zero.
- Published Story 390297204 on Oct 7 10:00 and draft 390461150 for Oct 7 18:00 use the same media URL. Keep draft blocked for duplication.
- Next recommended high-score slot: Fri Oct 9 10:00 local (score 6734), not a conversion prediction.
- Producer landing https://cutinapp.petertecnet.com.br/for-producers returned HTTP 200 in read-only request on Oct 8 UTC. This verifies HTTP availability only, not signup or activation.
- Reviewed W3 new carousel final slide 1080x1350, Story 1080x1920, Reel MP4 1080x1920 H.264 15s 360 frames. FFmpeg blackdetect found no black interval; no audio stream. Actual video exists (VIDEO_RENDERED=true); AUDIO_CONFIGURED=false.
- No simulated clickable button in new media. URL is static text, not an interactive feed/Story link; integration link sticker not verified. The Reel final URL is very small at phone size and needs mobile legibility improvement. The fifth carousel slide says '04 / PRÓXIMO PASSO' with footer '05/05', a possible numbering ambiguity.
- Brand source not independently authenticated: W3 symbol resembles an available Library image named 'Emblema Cibernético em Vermelho e Preto.png', but that file's official-master status is not established. BRAND_ASSET_MATCH_UNVERIFIED.
- Claims limited to production/event/ticket flow, no fabricated sales, events or international payments. Commercial CTA improved to refer producers, but logo and mobile URL legibility still block approval.
- CONTENT_QA_RESULT=NEEDS_REVISION. Do not publish or schedule.

## Handoff to W0
1. Apply W1 architectural patch and W3 CSS patch to existing active branch, resolve collisions, run Jest/lint/build and responsive browser QA.
2. Integrate W2 service worker/UTM patch separately, verify caching headers, installability and attribution through signup/first production.
3. Obtain verified official Cutinapp logo asset and replace/recheck campaign media; increase Reel CTA URL size; review fifth-slide numbering.
4. Keep duplicate Metricool draft blocked. W4 must repeat QA before any publication.
5. After successful tests and runtime SHA checks, W0 alone may merge/deploy and close P0.

blockers: GITHUB_FRONTEND_WRITE_BLOCKED; MOBILE_RUNTIME_QA_PENDING; CI_NOT_RUN; BRAND_MASTER_NOT_AUTHENTICATED; INSTAGRAM_CONTENT_NEEDS_REVISION; ACQUISITION_ATTRIBUTION_UNVERIFIED
commit_sha: N/A
push_status: NO_FRONTEND_PUSH
