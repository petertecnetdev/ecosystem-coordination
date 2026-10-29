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

## Entrega W1 — 29/10/2026 ~12h18 BRT
- ACEITO W1 registrado na issue #10 comentário 6500448127, após revalidar HEAD/blob e ausência de claim concorrente.
- Commits de produto somente na API Independence: `e1f0a942` (gate de titularidade no EventPassService), `fdd2867c` (regressões HTTP), `08d05385` (notificação específica), `407122b8` (informational_only e preço desconhecido), `751332df` (regressão ticket informativo), `6c8f99e8` (alinhar teste ao schema real).
- HEAD API final `6c8f99e8a6dd3cb54f0c950016f92aa81f320f37`; blobs `EventPassService.php=20d3c7c11d5c8eb372df41f2870b536ee48fffdc`, `CutinappCourtesyOwnershipBoundaryW1Test.php=7a71e6e4adadfa62abec5b858f6fa6d06b3470cb`.
- GitHub Actions push [#40899744122](https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/40899744122), job 123538439699: **FAILURE**, `php artisan test` **687 PASS / 28 FAIL / 2 SKIP, 5.096 asserções, exit 1**; arquitetura 7 PASS / 2 FAIL, exit 1 (já incluídas nas 28). PHP syntax PASS, testes novos W1 **5/5 PASS**.
- Baseline anterior [#40892243764](https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/40892243764) HEAD 890fa141: 692 PASS / 18 FAIL / 2 SKIP, exit 1. **Dez falhas novas** em fixtures antigas de cortesias/portaria/fluxos que esperavam HTTP 201 para fichas sem proveniência; agora recebem 403. Não mascarar a regressão nem relaxar fail-closed.
- Testes MySQL isolado, concorrência simultânea e navegador: NÃO EXECUTADOS. Não foi feito merge/deploy/main/produção.
- Estado: **em-revisao-bloqueado** até reconciliar autorização de novos eventos de produtor e fixtures legítimas sem aceitar NULL/NULL sem prova de origem. Owner de arbitragem: W00; não editar arquivos de terceiros sem claim/cessão.
- **UMA PRÓXIMA AÇÃO:** W00 designar owner/claims específicos para reconciliar a persistência de proveniência no fluxo de criação legítima e as dez fixtures HTTP antigas, exigindo patch e CI sem flexibilizar ListingCommercePolicy.
