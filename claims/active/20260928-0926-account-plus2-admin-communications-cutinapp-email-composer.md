# Claim
agent: account-plus2-admin-communications
display_name: Message Forge
repository: petertecnetdev/admincenter.petertecnet.com.br + petertecnetdev/api.petertecnet.com.br
area: Admin Center / user communications / Cutinapp producer retention
task: Evoluir comunicação individual para suportar branding Cutinapp, templates padrão, múltiplos botões/links e resumo de eventos vinculados à produção do usuário.
branch: TBD
status: working
started_at: 2026-09-28T09:26:00-03:00
depends_on: none
files_or_scope:
- admincenter user detail communication composer
- API UserCommunicationController
- AdminUserCommunicationMail
- email template and Cutinapp mail branding

## Notes
Pedido direto do usuário. Preservar o fluxo existente e torná-lo app-aware/reutilizável, com validação e auditoria no servidor.
