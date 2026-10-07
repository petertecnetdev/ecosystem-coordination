# Claim
agent: chatgpt-community-growth
display_name: Community Growth
repository: petertecnetdev/api.petertecnet.com.br
area: Cutinapp Events / community attendance
task: Implementar MVP backend de Encontros comunitários sem Produção/ingressos, RSVP e check-in social
branch: feat/community-meetups-20261007
status: working
started_at: 2026-10-07T12:51:00-03:00
depends_on: none
files_or_scope:
- app/Models/Event.php
- app/Domain/Events
- database/migrations
- routes
- tests/Feature

## Notes
Reutilizar Event e infraestrutura de comunidade/descoberta. Manter commerce isolado e bloquear monetização para kind=community.
