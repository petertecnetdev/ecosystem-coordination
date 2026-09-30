# Worklog — W09
worker: W09 Discovery SEO Automation
time: 2026-09-30T02:48:00-03:00
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Problem found
Crawler-visible Event snapshots are not global-ready and can misattribute organizer identity. `scripts/generate-seo-snapshots.mjs` hardcodes Sao Paulo/pt-BR, defaults missing country to BR, and maps an external organizer without Production slug to Cutinapp SITE_URL.

## Impact
P1 SEO correctness: crawlers can receive geographic/organization facts not present in source data, weakening structured-data trust and global discovery. Runtime React SEO had already been hardened, so snapshot/runtime semantics can diverge.

## Actions
- Read COMMANDS/CURRENT_STATE/PRIORITIES/BLOCKERS and active claims.
- Registered claim before code scope.
- Confirmed VPS `petertecnetserver` offline.
- Inspected current public robots/sitemap and SEO snapshot generator.
- Sent W10 release/regression handoff.
- Closed claim as blocked rather than leaving orphan ownership or making an unsafe full-file replacement.

## Evidence
coordination commits: df2286893f37407d6a2b3d964951f29b2ac1e891, a3a576f4f170795aa932dcfa1e6bcf113b9b5e59, 0e00b84b251e1dc41e990ef5115e996e7ef02250, 79a4798f573fd1ec84843a14ac45349fc472d64e
code commit: none
build/test: not run; no command runner available and VPS offline
runtime_verified: false
pending_deploy_vps: false (no code change)

## NEXT_ACTION
Reclaim immediately when safe patch/local checkout is available. Fix generator identity/country semantics, make locale/timezone configurable or event-aware without inventing geography, add regression fixture for non-BR + external organizer, generate snapshots/build, and validate crawler-served JSON-LD.
