# W09 Worklog — Production crawler SEO snapshots

worker: W09 (cutinapp-visual-w09)
status: IMPLEMENTING
repository: petertecnetdev/cutinapp.petertecnet.com.br
point: W09-003

## Problems found
- Public Production entity metadata is client-side while Event already has crawler snapshots.
- SEO snapshot generator assumed `addressCountry=BR` when absent.
- SEO snapshot generator defaulted all date logic to `America/Sao_Paulo`.

## Evidence / contract confirmation
- Live public API `/organizations/public?per_page=2&page=1` returned `organizations` paginator with `data`, `last_page` and Production fields including `slug`, `name`, `description`, `city`, `uf`, `country`, `location_public`, `logo`, `background`.
- Existing frontend service confirms `/organizations/public` and `/organizations/public/:slug` are public contracts.

## Implementation prepared
- `scripts/generate-seo-snapshots.mjs`: paginate public Productions; generate `/production/:slug/public/index.html`; entity-specific title/description/canonical/OG image; ProfilePage + Organization JSON-LD; crawler-visible body; cleanup generated production snapshots; marker counts productions.
- Removed implicit BR country from Event/discovery schema.
- Changed implicit timezone default to UTC while allowing `CUTINAPP_SEO_TIME_ZONE` override.

## Tests
- `node --check scripts/generate-seo-snapshots.mjs`: PASS.
- `git diff --check`: PASS.
- diff: 68 insertions, 5 deletions.
- Full `npm ci && npm run build && generator` did not complete on the authorized host; process became blocked with no output and was terminated. This is not treated as a code pass or failure.

## Commit / push / PR / deploy
- Code commit: pending full runtime validation.
- Push/PR: pending; deliberately not pushed without build + generated HTML evidence.
- Deploy: not applicable yet.

## Economic impact expected
Makes public producer/Production links useful to social crawlers and search engines without JavaScript, improving organic discovery, trust and producer acquisition while removing Brazil-only structural assumptions.

## Pending / requests
- Next W09 cycle: run clean build/generator, inspect generated Production HTML, reread coordination/main, commit and push if safe.
- W05: preserve W09 ownership of SEO generator work until handoff/completion.
