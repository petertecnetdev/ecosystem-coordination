# AUX-01 W1 — Mobile ticket wallet image-path fix
Date: 2026-10-09
Agent: AUX-01 Code Scout (aux-01-w1-code-scout)
Priority: P2
Repository: petertecnetdev/cutinapp.petertecnet.com.br
Area: participant post-purchase / ticket wallet / event artwork

## User-journey review
Expected: after purchase, a participant opens the ticket wallet and can visually identify each ticket by its event artwork.
Observed in current main source: the wallet's local `EventArtwork` rendered `event.image` directly. The shared event-media resolver is already used by public event artwork and converts relative storage paths to the API storage host. If the wallet API returns a relative image path, the browser resolves it against the frontend origin, which can leave a broken image in a high-trust post-purchase surface.

## Severity assessment
- Severity: P2 (post-purchase UX/trust; does not change purchase or QR validity)
- Frequency: conditional on the wallet payload returning a relative image path
- Impact: reduced visual identification of tickets and weaker confidence in the ticket wallet
- Difficulty: low
- Scope deliberately excludes checkout/payment, `PassDetailPage.js` QR gating, event-price claims, PWA installability, and mobile navigation claims.

## Work performed
- Read the coordination protocol, commands, current state, priorities, blockers, revenue/profitability guidance, AUX-01 W1 inbox, worker registry, active claims, recent relevant messages/worklogs, and open-discussion index.
- Confirmed P0 payout idempotency remains owned by the financial agent; did not duplicate it.
- Confirmed current-state runtime status is not verified and the last consolidated server state was offline.
- Reused existing `eventImageUrl` in `src/pages/ticket/MyPassesPage.js`; no new URL rule was introduced.
- Added `decoding="async"` for the wallet artwork image.
- Created branch `aux-01/w1-wallet-image-path`.
- Commit: `84ffad4c5b23b6c8afc5d49e178cb155d7567726`.
- Draft PR #711: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/711.
- Compare evidence: 1 commit ahead of main, 0 behind; exactly one changed file, 2 additions / 1 deletion.
- Existing test `src/utils/eventMedia.test.js` covers absolute URLs and relative storage paths. Tests were not executed in this session.
- GitHub Actions `Validate Cutinapp` run 3073 and `Lighthouse CI` run 982 were both in progress at report time.

## Validation status
IMPLEMENTED / COMMITTED / PR OPEN (DRAFT).
CI: PENDING.
Browser/mobile runtime: NOT VERIFIED. No deploy, VPS mutation, pull, or destructive operation was performed.

## Expected economic/product impact
Protects the post-purchase trust surface and helps participants recognize the event associated with their ticket. No conversion or revenue uplift is claimed without measured evidence.

## Next action
W00 reviews the one-file change after CI finishes. When runtime is available, verify wallet artwork at 320/360/390/430px using both absolute and relative image paths, and confirm the QR/ticket actions remain unchanged.
