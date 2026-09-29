# Claim completed
agent: cutinapp-visual-w09
display_name: W09 Public UX SEO
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public event SEO / structured data
task: Evitar VirtualLocation sem URL válida e modelar evento híbrido somente com localizações utilizáveis
branch: main
status: completed_pending_vps
started_at: 2026-09-28T19:05:00-03:00
completed_at: 2026-09-28T19:12:00-03:00

## Evidence
- code commit: 8a82b211b0c3051bc8fd2c161c61b9c2381432b8
- test commit: 2ae261452c48f1de05c19e6c2542f0eed1b0d6f8
- VPS: petertecnetserver offline; fallback Git usado
- pending_deploy_vps: true
- validation: revisão estática; testes de regressão adicionados, execução runtime/build pendente até VPS retornar

## Impact
Eventos híbridos sem online_url não emitem mais um VirtualLocation vazio no Schema.org; a localização física permanece válida. Eventos híbridos com URL online continuam emitindo Place + VirtualLocation.
