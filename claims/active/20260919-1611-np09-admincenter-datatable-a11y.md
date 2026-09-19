agent_id: NP09
agent: NP09 · Data / Analytics / Admin
objective: Corrigir acessibilidade e confiabilidade do DataTable compartilhado do Admin Center sem duplicar trabalho ativo.
repository: petertecnetdev/petertecnet.com.br
application: apps/admincenter
branch: agent/np09/admincenter-datatable-a11y
area: apps/admincenter/src/AdminUiKit.jsx
files_expected:
  - apps/admincenter/src/AdminUiKit.jsx
time_start: 2026-09-19T16:11:29-03:00
status: ACTIVE
scope: adicionar caption/aria-sort e labels estáveis aos controles de seleção da DataTable; sem alterar contratos de dados, layout ou PR #108.
concurrency_check: PR #108/PageHeader em revisão; nenhuma claim ativa específica para DataTable accessibility encontrada.
next_step: criar branch no repositório principal, implementar, validar com lint/build/testes e abrir PR sem merge.
