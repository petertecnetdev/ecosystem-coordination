# Claim exclusivo W00 — regressão HTTP de ficha pública sem proveniência

agent: W00
repository: petertecnetdev/api.petertecnet.com.br
branch: Independence
status: working
started_at: 2026-10-29T07:50:00-03:00
issue: petertecnetdev/ecosystem-coordination#10
related_pr: petertecnetdev/api.petertecnet.com.br#546
scope: somente corrigir a fixture do teste HTTP de ficha pública para comprovar fail-closed NULL/NULL e legado explicitamente identificado.
files_or_scope:
- tests/Feature/Independence/PublicItemUnclaimedHttpTest.php

## Ownership e não concorrência
- HEAD inicial API `0f69a425c945b83e2154b668a6f386f2a455e879`; blob do teste `5d14f6e815ae6225ea773f8b683cfdba7c004cdb`.
- Arquivo criado em `35947d47b17a3bb1ea7e01d82e15f1ab141f9f97`, commit sem `agent_id` explícito. Inspeção de claims/active e issue #10 não identificou claim específico concorrente; W4 reportou a mesma pendência de owner.
- W00 assume **somente este teste**, não transfere claims W01, W1, Atlas, Genre ou financeiro. Se aparecer ownership anterior comprovado, suspender novas edições e arbitrar.
- Mudança mínima: exigir disponibilidade false antes de marcar proveniência; declarar `listing_source=legacy_organizer` e `verification_status=legacy_owner_record` nas duas entidades persistidas; então preservar true no legado legítimo, false em unclaimed e 404 cross-app.
- Não editar `ListingCommercePolicy.php`, controller, outros testes, main ou produção. Não afrouxar fail-closed.
- Gate: publicar commit real e conferir GitHub Actions no HEAD exato; QA W4; sem merge/deploy.
