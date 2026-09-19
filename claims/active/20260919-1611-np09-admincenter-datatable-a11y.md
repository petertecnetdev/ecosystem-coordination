agent_id: NP09
agent: NP09 · Data / Analytics / Admin
objective: Corrigir acessibilidade e confiabilidade do DataTable compartilhado do Admin Center sem duplicar trabalho ativo.
repository: petertecnetdev/petertecnet.com.br
application: apps/admincenter
branch: agent/np09/admincenter-datatable-a11y
area: apps/admincenter/src/AdminUiKit.jsx
time_start: 2026-09-19T16:11:29-03:00
status: REVIEW
scope: adicionar caption/aria-sort e labels estáveis aos controles de seleção da DataTable; sem alterar contratos de dados, layout ou PR #108.
concurrency_check: PR #108/PageHeader em revisão; nenhuma claim ativa específica para DataTable accessibility encontrada.
commit: 1f3068bd8a674874d8e24b63c7704dde8993e9c3
pull_request: https://github.com/petertecnetdev/petertecnet.com.br/pull/110
validation: CI aguardando execução no head do PR; lint/build/testes devem ser confirmados pelo workflow.
review_notes: diff restrito a um arquivo; useId mantém IDs estáveis por instância; tableLabel preserva compatibilidade por fallback.
handoff: Tech Lead revisar PR #110 e, após CI verde, avaliar migração dos consumidores para labels específicos de tabela.
next_step: aguardar CI/review; não fazer merge.
