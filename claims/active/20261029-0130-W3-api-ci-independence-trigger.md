# Claim exclusivo W3 — gatilho API CI Independence
agent: W3
display_name: W3 — Desbloquear API e CI Independence
repository: petertecnetdev/api.petertecnet.com.br
area: P0 CI / gatilho push Independence
task: adicionar exclusivamente Independence ao filtro push.branches de api-ci.yml
branch: Independence
status: working
started_at: 2026-10-29T01:30:00-03:00
depends_on: ecosystem-coordination#10, decisão W00 comentário 6487516009
files_or_scope:
- .github/workflows/api-ci.yml
head_at_claim: 64227cb83c672edb1fad21052f1e86db07c13d75
blob_at_claim: 9db3e3bc41b1e46e535e24187c3b1010e283ef2f
owner: W3
aceite: W3 aceita a atribuição específica de W00 de 29/10/2026 00h57 BRT

## Limites e critérios
- Exclusividade verificada na listagem de claims ativos da coordenação em 29/10 01h30 BRT: nenhum claim específico do api-ci.yml encontrado. Claim W03 de administrator-w03-ci.yml é de outro arquivo.
- Alterar apenas a lista push.branches para acrescentar Independence; preservar workflow_dispatch, pull_request, jobs, gates e permissões.
- Revalidar HEAD/blob imediatamente antes do update; se houver concorrência ou conflito, interromper.
- Validar mudança estática e registrar commit SHA, novo blob, diff, run_id/head_sha/jobs/logs/exit ou bloqueio operacional de Actions.
- A autorização excepcional permite o commit mínimo de gatilho antes de PHPUnit, pois serve para iniciar o próprio CI; não representa CI aprovado nem autoriza release.
- Não tocar RBAC, rotas, serviços W1/NP12, main do produto, produção, branches extras, merge/deploy ou contornar limites de ferramentas.
- Issue de acompanhamento: https://github.com/petertecnetdev/ecosystem-coordination/issues/10
