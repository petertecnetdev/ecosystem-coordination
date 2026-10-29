# W00 — Decisão executiva de reconciliação P0 (Independence)
agent: W00
emissao: 2026-10-29 12:54 America/Sao_Paulo
status: action-required
issue: petertecnetdev/ecosystem-coordination#10
escopo: API PR #546, React PR #715, Admin PR #4 somente segurança
branch: Independence (API/React); coordenação main
deploy: proibido sem ordem específica

## Evidência revalidada nos HEADs exatos
- API Independence `6c8f99e8a6dd3cb54f0c950016f92aa81f320f37`: Actions push #40899744122 job 123538439699, PHPUnit 687 PASS / 28 FAIL / 2 SKIP, exit 1; arquitetura 7 PASS / 2 FAIL, exit 1. Os cinco testes novos de emissão W1 PASS. PR #546 aberto/conflitado.
- React Independence `d4703a671c7688cf3c84f676178f0ccff589bdbe`: Actions #40900738644, Jest 1672 PASS / 6 SKIP / 2 TODO, exit 0, workflow SUCCESS. SEO snapshots internos FAIL; browser não executado. PR #715 draft/conflitado.
- Admin #4 `c6846c618b89192074f18313bcb57efa3e3b5d45`: CI anterior 48 PASS, QA integrado pendente.
- main API `d960738b8428443a269074d2f2338529178159e6`; main React `9b5502cdf2dca098bc73a465d58d7274b596d0a4`. Não houve merge.
- Branches remotas conferidas: API 4, React 9, Admin 2. Nenhuma criação/exclusão.

## Diagnóstico novo de causa raiz — não mascarar dez falhas
- `app/Services/Independence/ListingCommercePolicy.php` blob `0a0f8adffbca90a7ce5e50db13a3cd929a8c3416` só libera NULL/NULL com proveniência explícita `legacy_organizer` + `legacy_owner_record` nas DUAS entidades, vínculo persistido e ausência de fonte externa. Outras fichas requerem titularidade e autorização comercial verificadas. Isso é o gate correto, NÃO reabrir NULL/NULL genérico.
- `app/Domain/Events/Http/Controllers/EventManagementController.php` blob `9c6eeac0f1f80700d79b07ac853fc8ad350d3998`, método `store()` linhas 146–184, cria rascunho, mas NÃO persiste proveniência comercial server-side para evento criado por produtor autenticado. A produção criada via fluxo próprio também não recebe comprovação suficiente em todos os caminhos. Assim, `EventPassService::claim()` protegido agora devolve 403 onde testes antigos esperavam 201.
- Dez falhas novas de fixtures HTTP de cortesia/check-in/fluxos após o gate W1, incluindo `CutinappAdministratorCheckinTest.php` blob `6a8ae4e7`, `CutinappApplicationOwnershipTest.php` `f4909db2`, `CutinappCheckinTokenPrivacyTest.php` `b8cc1eb0`, `CutinappCourtesyLifecycleTest.php` `f5ac48b4`, `CutinappEventCapacityTest.php` `3317c33e`, `CutinappFreeEventFlowTest.php` `79e0ec68` (3 cenários), `CutinappInvalidatedPassCheckinTest.php` `78264550` e `CutinappSocialNetworkLifecycleTest.php` `057d8395`. Há 18 outras falhas preexistentes a classificar separadamente; duas são arquitetura. A lista é dos testes afetados, não uma autorização para editá-los.
- **Não marcar eventos NOVOS como `legacy_organizer`/`legacy_owner_record` para forçar aprovação**: isso falsificaria proveniência. Definir contrato auditável de criação própria/autorização comercial no servidor, consistente com a política, produção e evento, sem confiar em campos do cliente. Criar regressões para produtor legítimo vs ficha curatorial, app cruzado, autorização revogada, checkout e emissão.

## Decisões por owner — executar em paralelo sem duplicação
1. **@petertecnetdev + Atlas (`account-plus2-discovery-taxonomy`) + Genre Integrator (`cutinapp-event-genres-20261012`)**: dependência CRÍTICA. Controller `EventManagementController.php` blob `9c6eeac0` está sob claim Atlas `d5d61027` WORKING e Genre `b826161a` HANDOFF. Responder **CEDO PARA W3 | agent_id | claim | HEAD 6c8f99e8 | blob 9c6eeac0 | sem concorrência**; W3 deve registrar **ACEITO POR W3** antes de editar. Alternativa: owner original registrar **IMPLEMENTAREI COMO OWNER | prazo | commit | testes | CI** e implementar. Sem resposta, W3 NÃO editar. Arbitragem também necessária para `routes/compatibility.php` blob `10b6d8cf` e `CutinappEventLifecycleTest.php` blob `92f87063`.
2. **W3**: após CEDO+ACEITO, corrigir contrato server-side de proveniência de criação legítima e RBAC app-scoped (sem `hasProfile('Administrador')` global), DELETE×emissão com lock/transação e publicação explícita. Não alterar sem ownership. Enquanto bloqueado, mapear 18 falhas basais, conflitos main, trabalhar apenas arquivos livres com claim exclusivo; NÃO AgentChat/IA/NP12.
3. **W1**: preservar gate `EventPassService.php` blob `20d3c7c1` e seus 5 testes PASS. Após contrato W3 definido, obter claims/cessões por teste e reconciliar **somente** as fixtures legítimas acima, mantendo cenários curatoriais 403 e cross-app. Não alterar `EventManagementController` nem atribuir proveniência legada falsa. Continuar Pix/Asaas, idempotência, webhook/ledger dentro dos claims existentes. Caso ownership de fixtures não seja comprovável, registrar bloqueio nominal e pedir cessão.
4. **W2**: correção 401/403 entregue `d4703a67` e revalidada por W4. Próximo P0: A→B→A síncrono na mesma aba exige epoch monotônico em AuthContext/authTokenStorage **sob outro owner**; identificar owner, obter CEDO+ACEITO específico com HEAD/blob, implementar somente após aceite. Não repetir testes já aprovados nem tocar auth alheio.
5. **W4**: QA independente; conferir no novo SHA API as 10 regressões e 18 falhas basais, emitir PASS/FAIL/NÃO EXECUTADO por fluxo. Priorizar HTTP integrado GET /me→POST, A→B→A, emissão/QR/checkout/Asaas, cross-app RBAC, browser 320/360/390/430 e MySQL isolado migrations/rollback; não alegar execução sem logs.

## Critérios de release
CI API+React nos SHAs exatos verde (incluindo arquitetura), SEO snapshot esclarecido, conflitos resolvidos, revisão W4, teste MySQL/rollback e QA funcional antes de merge. Curadoria automatizada NP12 permanece parte da entrega completa, mas conectores aguardam P0. Sem merge/deploy, branch extra, bypass de OPENAI_SAFETY_CHECKS ou alteração de main.

**UMA ação executiva imediata: @petertecnetdev/Atlas/Genre formalizar cessão do controller para W3 ou assumir patch com SHA e CI. Owner do desbloqueio: mantenedor `petertecnetdev`.**


## Adendo executivo W00 — 29/10/2026 13:54 BRT — defeito preciso e decisão de ownership

### Evidências frescas (GitHub, sem alteração do produto)
- API PR #546 HEAD `ca66a7ad268830f612c1513a79b81cba95bff91c`, base `9ecbf884`, mergeable=false. Push Actions #40908847797: **689 PASS / 28 FAIL / 2 SKIP, 5.102 asserções, exit 1**; 10 falhas novas de proveniência, 18 basais (2 arquitetura incluídas, não somar novamente). Commit W1 `ca66a7ad` acrescentou dois testes Asaas aprovados, sem novas falhas.
- React PR #715 HEAD `d4703a671c7688cf3c84f676178f0ccff589bdbe`, base `fe4de92f`, DRAFT, mergeable=false. Actions #40900738644: 1.672 PASS, exit 0; snapshots SEO falharam internamente e navegador não foi executado.
- Admin PR #4 HEAD `c6846c618b89192074f18313bcb57efa3e3b5d45`, DRAFT, mergeable=true; 48 PASS em CI anterior, sem QA integrado.
- `COMMANDS.md` blob `3f3e61ba` lido; issue #10 já atribuída ao mantenedor `petertecnetdev`; W1/W2/W3/W4 reportaram em #10 às 13:12/13:18/13:30/13:42, respectivamente. Nenhum aceite Atlas/Genre→W3 ou auth→W2 apareceu nesses registros.

### Novo detalhe técnico confirmado no HEAD da API
- `EventManagementController::store()` atribui `created_by_user_id` **somente no ramo community**. No ramo commercial, valida `ownedProduction()` e cria `Event::create($data)` sem definir a autoria no servidor. Esse fato se soma à ausência de proveniência comercial persistida; não basta corrigir fixtures nem simplesmente preencher um marcador legado.
- `ListingCommercePolicy::canSell()` exige `ownership_status=verified` com `manual_approved`, `ownership_verified_at`, `commerce_authorized_at` e concessões ativas coerentes nas duas entidades; `allowsLegacyOrVerified()` aceita legado apenas com proveniência legada explícita. **Não** conceder `manual_approved` automaticamente a qualquer usuário que consiga criar um evento; isso equivaleria a contornar a verificação humana. Corrigir autoria auditável e estabelecer um caminho explícito e legítimo de autorização comercial para self-create, sem permitir venda de fichas curatoriais.
- Verificar no patch do owner o fluxo `duplicate()`: atualmente replica o evento de origem e seus campos de verificação, exigindo revisão para impedir herança indevida de autorização para nova edição. Achado estático, não exploração reproduzida.

### Arbitragem exigida — sem silêncio como cessão
1. **Owner decisório: @petertecnetdev; cedentes: Atlas/Genre.** `app/Domain/Events/Http/Controllers/EventManagementController.php` blob `9c6eeac0f1f80700d79b07ac853fc8ad350d3998` no HEAD API `ca66a7ad`. Registrar `CEDO PARA W3 | Atlas/Genre | claim d5d61027/b826161a | HEAD ca66a7ad | blob 9c6eeac0 | sem concorrência` e `ACEITO POR W3`, **ou** owner publicar patch próprio com SHA, testes e CI. Incluir decisão separada sobre `routes/compatibility.php` blob `10b6d8cf` e `tests/Feature/CutinappEventLifecycleTest.php` blob `92f87063`.
2. **Owner decisório: @petertecnetdev; destinatário: W2.** React HEAD `d4703a67`: `src/context/AuthContext.js` blob `78917a5a`, `src/utils/authTokenStorage.js` blob `25bbc63d` (dependência `authSessionSync.js` blob `79b446dc`). Nomear cedente operacional, obter `CEDO PARA W2` por arquivo com HEAD/blob e `ACEITO POR W2`; alternativa: owner original implementar epoch monotônico com Jest/CI. Sem transferência, W2 não tocar auth.
3. **W3, assim que autorizado:** corrigir autoria server-side de evento comercial e contrato de proveniência/commerce sem autoaprovação de fichas não verificadas; RBAC app-scoped e exclusão concorrente. Testar criação comercial legítima vs curatorial, cross-app e revogação. **W1**, após esse contrato, conciliar fixtures com claims e preservar testes Asaas/QR. **W4** validar CI/QA independentemente.
4. **W00:** nenhuma edição do controller/auth até CEDO+ACEITO; escalar ao mantenedor já assignee da issue #10. Sem commits de produto W00, MySQL/browser, merge ou deploy nesta rodada.

**Gate:** BLOQUEAR MERGE. Próxima ação executiva única: decisão expressa de ownership do controller por `petertecnetdev`, liberando W3 ou entregando patch próprio. Curadoria NP12 somente após gates P0.
