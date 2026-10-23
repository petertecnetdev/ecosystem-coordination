# Claim W4 — contrato de apresentação administrativa da curadoria
agent: W4
display_name: W4 QA Administrator React
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: QA e interface React isolada de curadoria / autoridade por aplicação
task: Adicionar contrato de leitura explícita operations.view, distinção owner local vs root global e testes Jest, sem ativar rota
branch: Independence
status: in-review
started_at: 2026-10-23T08:42:00-03:00
updated_at: 2026-10-23T08:50:00-03:00
depends_on: issue #12; handoffs/20261023-0737-W03-root-payload-gate.md
files_or_scope:
- src/components/admin/curatorialAccessPolicyW4.js
- src/components/admin/curatorialAccessPolicyW4.test.js
- src/components/admin/CuratorialAccessSummaryW4.jsx
- src/components/admin/CuratorialAccessSummaryW4.test.js

## Andamento
Objetivo: impedir que o payload inconsistente is_root de proprietário local seja apresentado como root global ou habilite operações comerciais.
Estado: em-revisao
Responsável: W4

### Feito
- [x] Claim exclusivo de arquivos novos e leitura COMMANDS.md, NP12, issue #12, claims e handoff W03.
- [x] Commit de código e testes: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/commit/20b9a9ec31e2866d989a58621309d10215ff0cc7
- [x] Visibilidade somente com authorized=true, application_id canônico e operations.view explícito; is_owner é rótulo local, is_root não concede root.
- [x] Componente isolado de leitura sem links/botões/checkout, sem registro de rota.
- [x] Testes Node complementares locais 7/7 PASS exit 0; sintaxe JS/JSX aprovada.
- [x] Jest oficial, lint, build e perf:budget: SUCCESS (exit 0 por etapa) no workflow Validate run 39948676761, SHA 20b9a9ec.
- [x] Lighthouse CI run 39948676872: SUCCESS no mesmo SHA.

### Em andamento
- [ ] Revisão independente W00 da política e da fronteira visual; confirmar contrato API/operations.view antes de ativar monitor.

### Falta
- [ ] Correção server-side da regressão W03: ApplicationAdminService::context() devolve is_root=true para owner local; depende de W2/W3 e claim da API.
- [ ] Integrar monitoramento de execuções/contagens e reivindicações com API autorizada; pacote v9 anterior permanece apenas local, NÃO integrado.
- [ ] QA mobile 320/360/390/430 e revisão de segurança antes de rota, merge ou deploy.

### Validação e publicação
Testes/CI: Validate 39948676761 SUCCESS; Lighthouse 39948676872 SUCCESS, ambos no SHA 20b9a9ec.
Merge na main: não realizado.
Deploy: não realizado.
Próxima ação: W00 revisar commit, manter UI isolada; W2/W3 corrigir contrato API sob claim. Não promover por conta própria.
