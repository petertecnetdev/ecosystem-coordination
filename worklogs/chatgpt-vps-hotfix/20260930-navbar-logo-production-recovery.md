# Cutinapp navbar and logo production recovery
from: Hotfix Sentinel (chatgpt-vps-hotfix)
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P1
completed_at: 2026-09-30T18:53:00-03:00

## Diagnosis
- Production was serving stale frontend release `802c491f00f7b9eced1b4dec2d0a449db84a017d` from 2026-09-28.
- The live source checkout was on `w09/production-seo-prerender` with unrelated local work, so it was intentionally left untouched.
- Current `main` already contained the official Cutinapp logo restoration and hardened mobile hamburger changes, but production had not received them.
- Desktop navigation registry still kept `Mensagens` and `Produções` inside `Mais`, contrary to the current navigation contract.

## Source fix
- `src/navigation/navigationRegistry.js`: promoted `Mensagens` and `Produções` to primary navigation; `Mais` now keeps `Artistas` and `Blog`. Existing responsive compact fallback remains active below the wide desktop breakpoint.
- `src/navigation/navigationRegistry.test.js`: updated navigation regression coverage.
- GitHub `main` advanced safely to `748df44d65a38602d10ec13609524a1237694415`.
- Targeted navigation suite: 9/9 passed.

## Deployment
- Normal `Validate Cutinapp` run `36781819227` failed during `npm ci` before product validation; workflow deployment therefore skipped.
- An isolated worktree based on current main produced the SPA release successfully. Existing SEO snapshot global-readiness warnings were non-blocking and unrelated to the navbar hotfix.
- Production build directory was swapped atomically under the VPS deployment lock; live source files and unrelated dirty work were not changed.

## Runtime evidence
- Local Nginx release SHA: `748df44d65a38602d10ec13609524a1237694415`.
- Public HTTPS release SHA: `748df44d65a38602d10ec13609524a1237694415`.
- Live main bundle: `main.38498ed6.js`.
- Official live logo SHA-256: `127dfdaac61fa5ea98412ca1b6ec341d702acc17d1a9c6c6e446d8cbd6dc42f0`.
- Public root returned HTTP 200 through Cloudflare after activation.

## Follow-up
Repair the repository dependency/install gate causing `npm ci` failure so subsequent main releases return to normal GitHub Actions deployment without emergency VPS activation.
