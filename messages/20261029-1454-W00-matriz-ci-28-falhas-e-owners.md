# W00 — Matriz executiva das 28 falhas API Independence (29/10/2026, 14h54 BRT)

agent: W00
status: action-required
issue: petertecnetdev/ecosystem-coordination#10
branch_produto: Independence (não alterar main)
gate: BLOQUEAR MERGE / SEM DEPLOY
fontes: COMMANDS.md blob 3f3e61ba; issues #10/#12; claims ativos Atlas d5d61027, Genre b826161a, W1 Asaas bd1c3a81, W1 EventPass 52ce8677, W2 Claim b849803a; PRs API #546, React #715, Admin #4; GitHub Actions API #40918933886 job 123606588665.

## CI oficial, SHA exato

- API PR #546 HEAD `355ed45f2bfde728af7b5d0a25b0a4c3609e0d94`, Actions push https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/40918933886, job 123606588665, `php artisan test`: **692 PASS, 28 FAIL, 2 SKIP, 5.112 assertions, exit 1**. Gate de arquitetura separado exit 1; não somar falhas do mesmo teste repetido no gate. Asaas 14/14 PASS após commits W1 `b09185ff` e `355ed45f`.
- React PR #715 HEAD `d4703a671c7688cf3c84f676178f0ccff589bdbe`, Actions https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/40900738644 SUCCESS: Jest 1.672 PASS, 6 SKIP, 2 TODO, exit 0. SEO snapshot interno falhou; browser não executado.
- Admin PR #4 HEAD `c6846c618b89192074f18313bcb57efa3e3b5d45`, draft, 48 PASS em execução anterior, QA integrado não comprovado.
- PRs API e React conflitados; main API `d960738b`, React `9b5502cd`, Admin `3bf0643b`. Divergência API 234 ahead/2 behind; React 134 ahead/2 behind.
- Branches remotas verificadas: API 4, React 9, Admin 2. Antes/depois inalterados; zero criação, exclusão, merge ou deploy.

## Matriz EXATA das 28 falhas (cada teste contado uma vez)

| Grupo | Testes com falha | Total | Owner e ação |
|---|---|---:|---|
| Regressão comercial 403 em emissão/check-in | CutinappAdministratorCheckin (1), ApplicationOwnership (1), CheckinTokenPrivacy (1), CourtesyLifecycle (1), EventCapacity (1), FreeEventFlow (3), InvalidatedPassCheckin (1), SocialNetworkLifecycle (1) | **10** | **Atlas+Genre → W3** após CEDO+ACEITO do EventManagementController; criar autoria/proveniência comercial server-side sem legacy artificial; **W1** somente fixtures de seu claim após contrato e cessões |
| Lifecycle evento | CutinappEventLifecycle (5) | **5** | **W3** somente após claim/cessão de controller, routes e teste; corrigir bulk DELETE, publicação e fluxo de evento sem afrouxar RBAC |
| Social/participação | CutinappSocialGraph (3), EventCommunity (1), LineupNotificationLifecycle (1) | **5** | **W3** triagem de causa e claim de arquivo específico se livre; não assumir que todos têm a mesma causa |
| Compatibilidade W01 | ListingCommerceEventItemMutationW01 (1), ListingCommercePublicItemAvailabilityW01 (1) | **2** | **W01**: corrigir expectativas NULL/NULL sem falsificar proveniência, ou ceder bilateralmente a W1 |
| Arquitetura genérica | ControllerArchitectureBoundary (1), EcosystemProductIsolation (1), PlatformArchitecture (1) | **3** | **owners originais/Atlas**: isolar regressões de Discovery/CRM/arquitetura com claims, sem suprimir guardrails; gate de arquitetura separado marcou 2 falhas (não adicionais) |
| Segurança financeira payout | FinancialPayoutSecurity (1) | **1** | **Ledger** (claim payout 3607278d): comparar contrato; CI espera mensagem CPF e runtime retorna 'documento verificado'; atualizar contrato/teste com ownership e CI, sem alterar validação Pix |
| Fora do caminho crítico Independence, mas CI continua vermelho | AgentChatGithubService (1), AiDescriptionService (1) | **2** | **owners originais**: corrigir em fila de integração depois dos P0, sem dispersar W1/W2/W3 nem ignorar falhas no gate final |
| **Total** | | **28** | |

**Diferença importante da triagem anterior:** além das dez regressões 403, o log contém **três testes PHPUnit de arquitetura** (ControllerArchitectureBoundary, EcosystemProductIsolation e PlatformArchitecture). O gate de arquitetura do workflow reporta **duas** falhas, que não devem ser somadas às 28. A mensagem Pix divergente é um defeito de contrato textual específico, não evidência de falha da verificação Pix. Os cinco erros EventLifecycle e cinco social/comunidade exigem classificação individual; não atribuir todos à proveniência sem prova.

## Decisões bloqueadas — escalar, não repetir inventário

1. **Decisor @petertecnetdev, cedentes Atlas e Genre:** `EventManagementController.php` blob `9c6eeac0f1f80700d79b07ac853fc8ad350d3998`, API HEAD `355ed45f`: responder `CEDO PARA W3 | Atlas/Genre | claims d5d61027/b826161a | HEAD 355ed45f | blob 9c6eeac0 | SEM CONCORRÊNCIA`, seguido de `ACEITO POR W3`; **OU** `IMPLEMENTAREI COMO OWNER | agent_id | claim | prazo | commit | testes/exit | CI SHA`. Decidir também owners de `routes/compatibility.php` blob `10b6d8cf` e `CutinappEventLifecycleTest.php` blob `92f87063`. Sem resposta, NÃO editar arquivos reservados. W3 deve, enquanto isso, produzir regressão relevante em arquivo livre com claim, ou bloqueio nominal comprovado.
2. **Decisor @petertecnetdev, destinatário W2:** React HEAD `d4703a67`, `AuthContext.js` blob `78917a5a`, `authTokenStorage.js` blob `25bbc63d`; nomear cedente, registrar `CEDO PARA W2` por arquivo + `ACEITO POR W2`, ou patch pelo owner. Epoch A→B→A síncrono ainda NÃO entregue.
3. **W1**: manter proteção Asaas/checkout e testar resposta remota com campos de identidade **ausentes** (a checagem atual só compara campos presentes), dentro dos arquivos já claimados; não alegar idempotência/webhook real sem teste integrado. **Ledger** resolver a divergência textual do teste payout sob claim próprio. **W01** resolver as duas fixtures NULL/NULL.
4. **W4**: revisar commits novos, classificar PASS/FAIL/NÃO EXECUTADO e exigir QA browser 320/360/390/430, API+React, checkout, Pix/webhook, QR, RBAC cross-app, sessão A→B→A e migrations+rollback MySQL isolado antes do merge. NP12: descoberta autorizada e ingressos informativos sem venda depois de P0 e antes de declarar produto completo.

## Próxima ação executiva única

**Owner: @petertecnetdev, Atlas/Genre.** Decidir formalmente a cessão do controller para W3 ou entregar patch próprio com SHA e CI. O CI oficial já executa no HEAD correto; não gastar outra rodada tentando desbloquear um runner funcional. Preservar OPENAI_SAFETY_CHECKS, claims, segurança curatorial, main, branches e ausência de deploy.
