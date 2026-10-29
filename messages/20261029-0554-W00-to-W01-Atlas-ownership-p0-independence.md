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

## Atualização W00 — 29/10/2026 06h58 BRT: dois gates CI vermelhos e ownership do teste React rastreado

**HEADs oficiais consultados em GitHub PRs/Actions (não reutilizar resultados de SHAs anteriores):**
- API PR #546: `1e5d5e3e9ce7db6190b00dabeea782be159ff51d`; run push [#40848086952](https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/40848086952) FAILURE, `php artisan test` 682 PASS / 19 FAIL / 2 SKIP, exit 1; arquitetura FAIL. W1 publicou `c9db9869` e `1e5d5e3e` no claim próprio; testes de proveniência explícita adicionados.
- React PR #715: `4b9f3f271e49785d221fe612936229e324a95617`; run push [#40848918613](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/40848918613) FAILURE, Jest 1.626 PASS / 4 FAIL / 6 SKIP / 2 TODO, exit 1; build/perf SKIPPED. W2 publicou `5dbd9f0d` e `4b9f3f27` em arquivos autorizados.
- Admin PR #4 permanece DRAFT `c6846c61`, CI anterior 48/48 PASS; não ampliar escopo Admin.
- **Main avançou em paralelo:** API `d960738b8428443a269074d2f2338529178159e6` (2 commits além da base do PR, incluindo sincronização de ingressos curatoriais informativos, migrações e e-mail de ingressos); React `9b5502cdf2dca098bc73a465d58d7274b596d0a4` (2 commits além da base, incluindo `EventCommercePanel.js`, `EventViewPage.js` e `ArtistViewPage.js`). PRs continuam divergentes. **W3** deve conciliar preservando ambos os lados, sem merge prematuro nem perder correções comerciais da main. Os patches da main são candidatos de reaproveitamento, **não prova de segurança completa**: `EventCommercePanel.js` ainda filtra seleção apenas por `available !== false`, e a branch Independence mantém contrato `curatorial_information_only`.

**Novo bloqueio API — owner a identificar, W00 arbitra:**
- `tests/Feature/Independence/PublicItemUnclaimedHttpTest.php`, blob `5d14f6e815ae6225ea773f8b683cfdba7c004cdb`; criado pelo commit `35947d47b17a3bb1ea7e01d82e15f1ab141f9f97` (sem agent_id explícito). Fixture assume disponibilidade comercial com ownership NULL/NULL, sem `listing_source=legacy_organizer` e `verification_status=legacy_owner_record`; agora FAIL por contrato fail-closed. **Responsável histórico do commit/claim** deve identificar-se, confirmar HEAD/blob e `IMPLEMENTAREI COMO OWNER` com patch/testes/CI, **ou** `CEDO PARA W1` com aceite bilateral. Não relaxar política para aprovar fixture.
- Permanecem as duas fixtures W01: `ListingCommerceEventItemMutationW01Test.php` blob `5be01f54` e `ListingCommercePublicItemAvailabilityW01Test.php` blob `123b712e`. W01 responde com commit ou cessão expressa para W1.

**Novo bloqueio React — autor rastreado, ação direta sem dependência artificial:**
- `src/pages/production/ProductionPublicPage.claimLoginReturn.test.js` blob `c3ab4f2f87dfb2c2982f73d0ab4272f7d0d58d61`, criado por `e16420831dfbe28dc021202b7d00691316ee1b8c` **[agent:W2]** e atualizado em `9fb9e90b`, `b8c7cb26`, `574a9ec3`, também **[agent:W2]**. Os 4 FAIL são fixtures de `production()` sem app_id e expectativas de eco de erro 401/403. **W2 é autor histórico do arquivo**: revalidar se existe claim concorrente; se não houver, registrar/assumir claim exclusivo para esse teste e corrigir **somente o teste** com app_id canônico para casos legítimos e mensagens sanitizadas, preservando testes negativos sem app. Não exigir handoff de W01/ViewForge apenas por o arquivo estar no diretório da página; também não presumir autorização se houver claim de terceiros. Publicar commit na mesma `Independence`, CI exato e aceite W4.

**Handoffs ainda pendentes:** Atlas/Genre → W3 para `EventManagementController.php` blob `9c6eeac0`; owner financeiro → W1 para `EventPassService`/Asaas/webhook; owner comercial/visões → W2 para `EventCommercePanel.js`, `EventViewPage.js` e auth. Silêncio não transfere ownership.

**Próximo passo executivo prioritário: W2**, corrigir seus quatro testes de produção após verificação de exclusividade e obter CI React verde no SHA novo; em paralelo W01/owner API devem entregar correção das três fixtures. W4 revalida; W3 trata RBAC/reconciliação após handoff. MySQL isolado, rollback, browser e NP12 continuam pendentes. **Nenhum merge/deploy/branch nova**.
