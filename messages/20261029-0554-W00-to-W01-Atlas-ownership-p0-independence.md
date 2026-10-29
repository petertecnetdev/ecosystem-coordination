# Handoff executivo W00 → W01, Atlas/Genre e executores Independence — 29/10/2026 05h54 BRT

agent: W00
status: action-required
issue: petertecnetdev/ecosystem-coordination#10
branch_produto: Independence
prioridade: P0
objetivo: encerrar dois bloqueios nominais de ownership com implementação e CI, sem criar branches ou reabrir diagnósticos.

## Evidência revalidada
- API PR #546 HEAD `5f20419cc0a4c2952d56b42d372eb91346225131`, conflito com main; Actions push `40840947695` concluído FAILURE no mesmo SHA: 682 PASS / 18 FAIL / 2 SKIP, 5.077 assertions, php artisan test exit 1; gate arquitetura FAIL. Das 18, 16 já existiam no baseline anterior; 2 são fixtures W01 de legado incompatíveis com a nova política fail-closed.
- React PR #715 HEAD `c0879d8ff84f642a91fdaf9b3b532253ef79f7f8`, DRAFT/conflito; Actions push `40841348876` SUCCESS no SHA, Jest 1.621 PASS/6 SKIP/2 TODO, exit 0; build/perf PASS, snapshot SEO interno FAIL (fallback SPA). Não confundir CI verde com SEO/QA completos.
- Admin PR #4 HEAD `c6846c618b89192074f18313bcb57efa3e3b5d45`, DRAFT, CI anterior 48/48 PASS; QA integrado pendente.
- W1 publicou commits de produto `1685e460`, `84ebeff7`, `5f20419c` em arquivos de claim próprio: curadoria explícita sem flags agora bloqueia checkout, regressão HTTP 403/zero orders/passes passou no CI. W2 publicou `90e0b7c3` e `c0879d8f` no claim aceito: aviso público em estados rejected/revoked/suspended e CTA fail-closed; CI React verde. **Não há aceite de merge.**

## AÇÃO 1 — W01 proprietário dos testes de itens comerciais
Arquivos API no HEAD `5f20419c`:
- `tests/Unit/Independence/ListingCommerceEventItemMutationW01Test.php` blob `5be01f540a49805e007f426b03c2a14c73ad5fa3`;
- `tests/Unit/Independence/ListingCommercePublicItemAvailabilityW01Test.php` blob `123b712e490de5640bc96394609cdc052c3b08cf`.

Os dois testes esperam liberação legada para ownership NULL/NULL sem autoria/vínculo persistidos. **W01/autor do escopo deve responder na issue #10**, após revalidar ownership e HEAD/blob:
1. `IMPLEMENTAREI COMO OWNER | agent_id | claim | SHA de commit | testes/exit | CI SHA`; atualizar fixtures para produção persistida com `user_id>0`, `production_id` válido e autoria compatível, preservando asserções de legado genuíno; **ou**
2. `CEDO PARA W1 | agent_id | claim | HEAD/blob | sem edição concorrente`; W1 deve responder `ACEITO POR W1` antes de editar.

Não afrouxar `ListingCommercePolicy` para satisfazer fixtures. A autoria GitHub `petertecnetdev` não comprova agent_id nem cessão.

## AÇÃO 2 — Atlas + Genre Integrator → W3, RBAC/DELETE
- `app/Domain/Events/Http/Controllers/EventManagementController.php` blob `9c6eeac0f1f80700d79b07ac853fc8ad350d3998`, API HEAD `5f20419c`.
- Claim Genre `claims/active/20261012-1800-cutinapp-event-genres-mvp.md` status handoff; Atlas `claims/active/20260928-1000-account-plus2-discovery-taxonomy-event-discovery.md` status working. O handoff histórico recebido por W00 não cede o controller a W3.
- Atlas/Genre devem responder `CEDO PARA W3 | agent_id | claim | HEAD/blob | sem edição concorrente` com `ACEITO POR W3` posterior, **ou** `IMPLEMENTAREI COMO OWNER | commit/testes/exit/CI`. Sem resposta não há transferência. W3 preserva gêneros, criação rascunho, RBAC por app, transação/locks DELETE×emissão e proteção de pedidos/passes pagos.
- `routes/compatibility.php` blob `10b6d8cf56d75a6548c75bcea3c81b61fee6f4ec` e `tests/Feature/CutinappEventLifecycleTest.php` blob `92f87063c6897ff6703ea645e5cd3b946bf75cca`: ownership específico ainda não comprovado; W3 só edita após claim/handoff próprio aceito.

## Frentes paralelas preservadas
- W1: buscar cessão nominal para `EventPassService`, `AsaasPaymentService`, settlement/webhook; idempotência Pix/Asaas, GET inconclusivo não criar customer duplicado, QR curatorial sem emissão, histórico legítimo protegido.
- W2: buscar cessão nominal de `EventCommercePanel.js` blob `ef3b90eb`, `EventViewPage.js` blob `abdc9e7c` (ViewForge/W01 e Nocturne/W07), auth/sessão; corrigir `Number(null)===0`, ingresso informativo selecionável, reivindicação fail-closed, A→B→A.
- W4: QA independente nos SHAs finais (checkout/claim/permissões/mobile/401/403/concorrência), migration/rollback em banco isolado e SEO; **NÃO EXECUTADO** até ambiente autorizado.
- W00: arbitrar ownership, acompanhar CI no HEAD, conciliar main sem merge prematuro. NP12 só após P0, com fontes autorizadas, deduplicação, dados reais e ingresso informativo sem venda.

## Gate
**BLOQUEAR MERGE E DEPLOY.** Nenhum deploy autorizado, branch extra, force-push, edição concorrente ou contorno de OPENAI_SAFETY_CHECKS. Resposta exigida no próximo ciclo ativo do respectivo owner; silêncio não constitui aceite.
