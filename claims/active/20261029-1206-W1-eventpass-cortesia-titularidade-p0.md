# Claim exclusivo W1 — Emissão de cortesias: titularidade comercial fail-closed P0

agent: W1
repository: petertecnetdev/api.petertecnet.com.br
branch: Independence
status: working
started_at: 2026-10-29T12:06:00-03:00
issue: petertecnetdev/ecosystem-coordination#10
related_pr: petertecnetdev/api.petertecnet.com.br#546
handoff: messages/20261029-1050-W00-to-W1-W2-W3-desbloqueio-p0.md (decisão condicional W00 11h50)
scope: Bloquear emissão de NOVAS cortesias/QR sem titularidade e proveniência comercial, preservando passes já emitidos e cortesias legítimas.
files_or_scope:
- app/Services/EventPassService.php
- tests/Feature/CutinappCourtesyOwnershipBoundaryW1Test.php (arquivo novo)

## Verificação antes de assumir
- API Independence HEAD: 890fa14114179b7c87ecd4491d5814ac71a2196a (PR #546).
- Blob EventPassService.php: 7e895e5c6ef059e08334a2ad2bdf550fa1821b11.
- Revisados 180 itens em claims/active (179 claims + .gitkeep), os claims amplos relacionados a eventos, Atlas/Genre, comércio W1, Asaas, pagamentos/ledger, RBAC e QR frontend, além de COMMANDS.md, issues #10/#12 e handoff W00.
- Nenhum claim ativo encontrado que inclua app/Services/EventPassService.php ou a criação do teste W1 indicado; o claim W03 de QR é exclusivamente React PassDetailPage, Atlas/Genre cobrem taxonomia/event editor, e W1 anterior cobre arquivos distintos.
- A atribuição W00 é condicional, não cessão presumida de outro owner. Nenhuma autoria Git foi interpretada como ownership.
- ACEITO POR W1 | claim 20261029-1206-W1-eventpass-cortesia-titularidade-p0 | HEAD 890fa14114179b7c87ecd4491d5814ac71a2196a | blob 7e895e5c6ef059e08334a2ad2bdf550fa1821b11 | SEM CONCORRÊNCIA identificada nos claims e handoffs verificados.

## Critérios
- Reusar ListingCommercePolicy::allowsLegacyOrVerified para novas emissões gratuitas; recusar unclaimed/pending/rejected, NULL/NULL sem proveniência, curadoria informativa e app_id cruzado.
- Preservar lock transacional do evento e ticket, limites e idempotência por usuário, sem alterar carteira, QR/check-in ou passes pagos já persistidos.
- Testes HTTP para negações e cortesia legítima; validar CI oficial no novo SHA.
- Sem editar arquivos de outros owners, main, merge, deploy, produção, NP12 ou contornar OPENAI_SAFETY_CHECKS.
