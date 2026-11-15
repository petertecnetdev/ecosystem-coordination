# Claim
agent: AUX-03-W2
display_name: AUX-03 SEO & Public Discovery
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO editorial / public discovery / producer acquisition
task: Create a concrete SEO acquisition asset focused on producers while runtime validation is unavailable.
branch: fix/aux03-producer-seo-offer-truth-20261102
status: pending_lighthouse_and_pr724_integration
started_at: 2026-10-08T16:00:00+03:00
depends_on: none
files_or_scope:
- public producer acquisition landing/content
- editorial SEO content and internal linking
- no generic technical audit

## Notes
Current coordination state marks Cutinapp release readiness NOT_READY and runtime/VPS unavailable. P0 payout idempotency remains owned elsewhere; do not duplicate it. Current priorities classify high-intent commercial SEO and public landing pages as P1. The repository search did not expose indexed Cutinapp files, so no application-code mutation is being made in this cycle.


## Continuation — 2026-11-02
- Narrow implementation scope: only the `PRODUCER_SEO` constant for `/for-producers` in `src/components/SeoManager.js`.
- Confirmed API truth: Cutinapp `subscription_enabled=false`, `monetization_model=transaction_fee`, `plans=[]`.
- Removed stale 30-day trial and mandatory-subscription language from title, meta description and WebPage/Service JSON-LD.
- Branch: `fix/aux03-producer-seo-offer-truth-20261102`.
- PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727 (draft; Validate Cutinapp SUCCESS; Lighthouse CI still in progress at latest check).
- The change does not modify W09's `/production/:slug/public` metadata functions, event SEO utilities, `SeoHead.js` or global snapshot generator. It is limited to the separate producer landing route.
- Dependency: integrate only with or after PR #724 so visible landing copy and metadata change together.
- Worklog: `worklogs/20261102-1104-AUX-03-W2-producer-seo-metadata.md`.
- Deliverable: `deliverables/AUX-03/20261102-W2-seo-metadados-landing-produtores.md`.
- NEXT_ACTION: wait for Validate/Lighthouse; then request review. Account principal is required for integration and live/mobile QA.


## Revalidação AUX-03-W2 — 2026-11-15
- PR #727 permanece OPEN e NÃO MERGED; sua dependência comercial PR #724 também permanece OPEN.
- Validate Cutinapp run `41459268768`: job frontend concluído com SUCCESS; inclui lint, testes, build e perf budget.
- Lighthouse CI run `41459268813`: job lighthouse concluído com SUCCESS.
- Esses resultados confirmam os checks desses runs, não integração nem publicação.
- Estado atualizado: `CHECKS_PASS — WAITING_PR724_INTEGRATION_AND_REVIEW — NOT_MERGED — NOT_DEPLOYED`.
- Próxima ação: W00/conta principal revisar a integração coordenada de #724 + #727; após merge, validar metadados servidos e mobile.
