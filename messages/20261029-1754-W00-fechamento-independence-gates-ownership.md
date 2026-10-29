# W00 — fechamento Independence: estado verificável e arbitragem de ownership — 29/10/2026 ~17h54 BRT

agent: W00
status: action-required
escopo: Independence P0 exclusivamente; nenhuma branch/automação adicional
fonte: COMMANDS.md blob 3f3e61ba; issues #10/#12 e comentários até QA W4 #6507848184; claims/active Atlas d5d61027, Genre b826161a; PRs API #546, React #715, Admin #4
decisão: BLOQUEAR MERGE / SEM DEPLOY

## Evidências NOVAS desde 16h54

1. **W1 — correção financeira real:** commits API `2e0fe4df72af82159b08a572ca1ec14464070e03` e `c6d767487b249edaf105677a44af71466192937a`, Asaas `app/Services/AsaasPaymentService.php` blob `5af328f936c522c0d8428a7d368e675e47ebd504`; teste blob `6d2581d729ee20087fec6441968e309e016c019d`. GET com `totalCount` contraditório ou paginação incompleta falha fechado, sem POST; 20/20 testes Asaas simulados PASS. Não comprovado gateway remoto, webhook/replay nem concorrência financeira.
2. **W3 — correção P0 real e QA W4 dirigido:** commits `b5c3fcfda031c587676376d9e6c1468bf6c2e79d` e `888337f6a21907c7bccb55ca682a91bbfd5bc54c`. `EventCommunityController.php` blob `7341594aff235e2495ff0865042a29affb46f33a`; teste `CutinappEventCommunityTest.php` blob `0a139a2c674a225b6fda438a1d81a42f57cc8c61`. Mesma autorização `canModeratePost` no GET e DELETE, incluindo criador de encontro sem produção; teste HTTP novo PASS, revisado W4. Claim W3 #6507665369 encerrado.
3. **CI API no HEAD exato `888337f6a21907c7bccb55ca682a91bbfd5bc54c`:** Actions push [40950098207](https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/40950098207), job `123715611804`, COMPLETED/FAILURE: 700 PASS, 28 FAIL, 2 SKIP, 5.211 assertions, PHPUnit exit 1; enforcement arquitetura exit 1 (2 já contidas nas 28). Runner funcional; não reabrir investigação de runner. As 28 falhas continuam classificadas na matriz [20261029-1454](20261029-1454-W00-matriz-ci-28-falhas-e-owners.md): 10 comerciais, 5 lifecycle, 5 social, 2 W01, 3 arquitetura, 1 payout, 1 AgentChat, 1 IA.
4. **React PR #715:** HEAD `d4703a671c7688cf3c84f676178f0ccff589bdbe`, Actions [40900738644](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/40900738644) SUCCESS: 1.672 PASS / 6 SKIP / 2 TODO, Jest/build exit 0. SEO snapshot interno falha (não mascarar); QA browser ausente. **Admin PR #4:** HEAD `c6846c618b89192074f18313bcb57efa3e3b5d45`, DRAFT, 48 PASS anterior, QA integrado ausente.

## Duas decisões de ownership com saída binária, sem transferência tácita

**A. Owner decisor @petertecnetdev; cedentes Atlas e Genre; executor W3.** `EventManagementController.php` blob **`9c6eeac0f1f80700d79b07ac853fc8ad350d3998`**, API HEAD **`888337f6`**. Atlas claim `20260928-1000-account-plus2-discovery-taxonomy-event-discovery.md` WORKING; Genre `20261012-1800-cutinapp-event-genres-mvp.md` HANDOFF. A palavra HANDOFF não é cessão bilateral. Escolher e registrar **uma** opção: (1) `CEDO PARA W3 | cedente/agent_id | claim origem | HEAD 888337f6 | caminho/blob | SEM CONCORRÊNCIA`, depois `ACEITO POR W3` e claim exclusivo; (2) `IMPLEMENTAREI COMO OWNER | agent_id | claim | prazo | SHA de código | testes/exit | CI SHA`. Entrega: autoria/proveniência comercial verificada pelo servidor em store, duplicate sem herdar autorização, RBAC app-scoped e correção das dez regressões comerciais sem falsificar `legacy_organizer` ou liberar fichas curatoriais. `routes/compatibility.php` e `CutinappEventLifecycleTest.php` exigem ownership próprio antes de edição.

**B. Owner decisor @petertecnetdev; cedente auth nominal; executor W2.** React HEAD **`d4703a67`**: `src/context/AuthContext.js` blob `78917a5aad3980acb93d309c8b29cd70c017acbe`; `src/utils/authTokenStorage.js` blob `25bbc63dbfcfbcdaede5a0541a56755fa8a3dc6b`; `src/utils/authSessionSync.js` blob `79b446dc56c9deaac043723477a518396820958c`. Para **cada** arquivo, `CEDO PARA W2 | cedente/agent_id | claim | HEAD/blob | SEM CONCORRÊNCIA` + `ACEITO POR W2`, ou `IMPLEMENTAREI COMO OWNER | agent_id | prazo | SHA | Jest/build exit | CI SHA`. Entrega: epoch monotônico a cada set/clear; resposta /me tardia e 401/403 não podem reverter sessão A→B→A síncrona na mesma aba; testes de usuário/app/logout.

## Trabalho executável em paralelo, sem aguardar o decisor

- **W1:** manter claim financeiro e priorizar regressão de webhook replay/idempotência e confirmação Pix/Asaas server-side, com evidência de zero cobrança duplicada; não editar Ledger/Atlas/Genre/W01 sem cessão. Preservar proibição de checkout e QR para fichas curatoriais não verificadas.
- **W2:** enquanto auth reservado, preparar testes de contrato de reivindicação em arquivos comprovadamente livres mediante claim; não tocar auth, não reabrir correções GET /me e 401/403 já aprovadas; não conectar NP12.
- **W3:** correção de comunidade concluída, **não repetir**. Próxima rodada: se sem cessão do controller, escolher UMA falha P0 entre os cinco lifecycle ou cinco social com arquivo efetivamente livre e claim exclusivo, classificar causa por log e entregar patch+regressão, ou documentar bloqueio nominal por arquivo. Não dispersar em AgentChat/IA.
- **W4:** QA independente dos novos SHAs; registrar PASS/FAIL/NÃO EXECUTADO, não confundir teste HTTP com browser. Após correções, exigir checkout, reivindicação, RBAC cross-app, mobile 320/360/390/430, SEO, MySQL isolado + rollback, idempotência/webhook/QR. NP12: fontes autorizadas, deduplicação, informação real, ingressos informativos sem venda, logs/monitoramento antes de declarar produto completo.

## Release / branches

PRs API #546 e React #715 conflitados, sem CI API verde; Admin #4 draft. API `main` d960738b, 243 ahead/2 behind; React `main` 9b5502cd, 134 ahead/2 behind; Admin `main` 3bf0643b, 17 ahead/0 behind. Branches remotas API 4, React 9, Admin 2; nenhum merge, exclusão, criação ou deploy. Não executar migrations/rollback em produção; exigido MySQL isolado com snapshot e teste de rollback antes do release. Sem bypass de `OPENAI_SAFETY_CHECKS`.

**Próximo passo executivo único: @petertecnetdev obter decisão bilateral A (Atlas/Genre → W3) OU patch do owner.** Em paralelo, W1/W2/W3/W4 seguem as tarefas acima. W00 nesta rodada: somente coordenação; nenhum teste local, exit N/A; commits de produto são de W1/W3 e não atribuídos a W00.
