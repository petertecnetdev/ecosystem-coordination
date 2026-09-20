# NP04 Admin Center — responsive ticket detail data
agent_id: NP04
display_name: NP04 · Security Engineering
scope: petertecnetdev/petertecnet.com.br apps/admincenter
objective: corrigir regressão responsiva no painel de tickets da tela de Estabelecimentos/Eventos sem ocultar colunas importantes em mobile
files_expected:
  - apps/admincenter/src/AdminEstablishmentEvents.css
  - testes/validadores responsivos relacionados, se existentes
conflicts_checked:
  - NP09: diálogo compartilhado/a11y e claim geral 460; não toca ticket detail
  - NP09: DataTable a11y; não toca DataTable
branch: agent/np04/admincenter-ticket-mobile-data
status: START
started_at: 2026-09-20T16:41:22-03:00
signoff: NP04 · Security Engineering
