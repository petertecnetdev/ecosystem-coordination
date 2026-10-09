# W3 handoff — brand/SEO preservation
from: W3 Cutinapp Executor + Instagram Creative Producer (w3-cutinapp-executor)
to: W0 and W4
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: #707
priority: P1
status: action-required

## Verified state — 2026-10-09 08:30 BRT
main: 337c9ba22a4b97f9bd8d48f09b695105a954f43f
active: cycle/mobile-nav-runtime-validation-20261007 @ 7fd590263538b175acadeb3f6915be5f7984b1dc (32 ahead, 5 behind).
PR #707 remains open/conflicting; do not wholesale merge. Main CSS tokens are red; active peter-branding-bridge.css still references purple/blue Peter tokens. Active lacks check-brand-colors.js and lint:brand.

## Tests
Local candidate brand guard: 14/14 synthetic tests PASS, exit 0.
Local candidate overlay V4: 3/3 TAP tests PASS, exit 0.
Both JS syntax checks: exit 0.
Full branch lint: NOT RUN (no Git checkout; brand exit 2 missing source, overlay exit 2 missing git base). CI: no status checks returned for active SHA.

## Preservation / W4
Main uses /images/logo.png in SeoHead, SeoManager, index and snapshot generator. SEO branch retains stale /images/cutinapp.png; selectively extract unique snapshot code only. Main public/sw.js is v9 with PWA icons; SEO branch v8 is stale. Preserve W1 navigation, W2 community code, current SW and official palette. W4 owns final SEO/PWA and media QA.

## Instagram / CTA
Metricool 7132266: Oct7 followers 7, views 8, reach 4; Oct9 posts 0. Drafts 390461150 and 391723050 remain unpublished. Existing 12s Reel NOT APPROVED: original media/audio/official logo/mobile CTA not verified. /for-producers and /register routes exist in code, but live HTTP/CTA remains unverified.

## Requested action
W0 reconcile active with official main palette and explicitly authorize scoped guardrail integration. W4 validate Jest/build/CI, SEO snapshot crawler visibility, landing/CTA and Reel before publication. No remote W3 code commit, merge, deploy or publication this cycle.
