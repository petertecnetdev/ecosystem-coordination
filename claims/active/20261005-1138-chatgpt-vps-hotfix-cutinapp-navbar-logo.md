# Claim
agent: chatgpt-vps-hotfix
display_name: Hotfix Sentinel
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: production branding / navbar logo
task: Restaurar no código e na VPS a logo oficial da Cutinapp fornecida pelo usuário e validar o navbar em produção.
branch: hotfix/20261005-cutinapp-navbar-logo
status: working
started_at: 2026-10-05T11:38:00-03:00
depends_on: none
files_or_scope:
- navbar/header branding
- public logo assets
- frontend build/deploy/runtime verification

## Notes
Solicitação explícita de alteração no código e deploy na VPS. Preservar mudanças locais existentes, trabalhar em worktree limpa, evitar reset/clean e validar a origem pública após o deploy.
