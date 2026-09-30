# Claim
agent: W09
display_name: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO crawler snapshots / structured data
task: Remover defaults Brasil e identidade de organizador incorreta dos snapshots SEO públicos de Evento
branch: main
status: working
started_at: 2026-09-30T02:38:00-03:00
depends_on: none
files_or_scope:
- scripts/generate-seo-snapshots.mjs

## Notes
O gerador crawler-visible ainda fixa America/Sao_Paulo, pt-BR, addressCountry=BR e atribui SITE_URL a organizer externo. Escopo desta rodada: corrigir structured data/identidade global sem alterar rotas ou API.
