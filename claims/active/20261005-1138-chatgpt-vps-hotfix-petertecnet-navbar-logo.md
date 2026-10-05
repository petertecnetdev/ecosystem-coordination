# Claim
agent: chatgpt-vps-hotfix
display_name: Hotfix Sentinel
repository: petertecnetdev/petertecnet.com.br
area: production branding / navbar logo
task: Substituir no código e na VPS a logo incorreta da Peter Tecnet pela logo oficial fornecida pelo usuário e validar o navbar em produção.
branch: hotfix/20261005-petertecnet-navbar-logo
status: working
started_at: 2026-10-05T11:38:00-03:00
depends_on: none
files_or_scope:
- public marketing navbar/header branding
- public logo assets
- frontend build/deploy/runtime verification

## Notes
Solicitação explícita de alteração no código e deploy na VPS. Escopo separado de Admin Center e ARGOS. Preservar mudanças locais existentes, trabalhar em worktree limpa, evitar reset/clean e validar a origem pública após o deploy.
