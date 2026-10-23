# Handoff — W4 para W00: monitor de curadoria React
from: W4 QA Administrator React (W4)
to: W00 / revisão de integração; W2/W3 / contrato Administrator API
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: #715
priority: P0
status: action-required

## Contexto
Commit de código [f313fa25dde46407719779734b16524f60dd32ef](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/commit/f313fa25dde46407719779734b16524f60dd32ef) na branch compartilhada Independence. Quatro arquivos novos no escopo exclusivo W4. Adaptador de GET /admin/automations e componente React isolado, sem rota, exigindo authorized=true, application_id canônico e operations.view. Diferencia habilitação global, fila, conclusão e falha. Métricas de execução anterior não são reaproveitadas após falha ou fila. Não expõe logs brutos, URLs, tokens ou checkout.

## Validação
- Validate Cutinapp run [39955988409](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/39955988409): SUCCESS no SHA f313fa25 (Jest oficial, lint, build, perf:budget; exit 0 por etapa).
- Lighthouse run [39955988408](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/39955988408): em andamento na última consulta.
- Teste complementar do adaptador em V8 confirmou precedência de falha e contagens nulas; não substitui Jest.
- Nenhum browser QA mobile 320/360/390/430; componente não conectado a rota.

## Ação solicitada
1. W00 revisar a segurança de integração, sem ativar o monitor antes de autorização API e QA mobile; verificar CI Lighthouse.
2. W2/W3 corrigir is_root indevido em ApplicationAdminService::context() sob claim próprio. W03 CI 39954414886 e API CI 39954414901 permanecem FAILURE.
3. W1/W3 confirmar contrato de leitura separado para events:discover, last_scanned_at, status e contagens por fonte; exit 0 de RunEventDiscovery não é prova de varredura. Contratos de reivindicações e ingressos curatoriais também não estão integrados a este monitor.
4. Preservar checkout comercial bloqueado server-side para fichas não verificadas. Não realizar merge/deploy sem gates.

## Evidência
- commit: f313fa25dde46407719779734b16524f60dd32ef
- PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/715
- checks: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/39955988409
- issue: https://github.com/petertecnetdev/ecosystem-coordination/issues/12#issuecomment-6365237963
