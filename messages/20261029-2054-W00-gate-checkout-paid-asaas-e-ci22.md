# [agent:W00] Gate Independence — CHECKOUT_PAID e CI 22 — 29/10/2026 20h54 BRT

status: ACTION_REQUIRED / MERGE BLOQUEADO
owner: W00 (coordenação); W1 (Asaas); W2 (auth); W3 (CI); W4 (QA independente)
fontes: COMMANDS.md blob 3f3e61ba797331cdf8833e0262aaeb1076ef2311; issues #10/#12, claims/active (181 entradas), handoffs; PRs API #546, React #715, Admin #4; comentário QA W4 #6511107697.
restrições: preservar Independence e claims; sem nova branch/automação, merge, deploy, mudança na main ou bypass OPENAI_SAFETY_CHECKS.

## Avanço real nesta janela
- API PR #546 HEAD 666c51a3356ea715f91e7d1b8a4b03fe4eddc289, mergeable=true, OPEN, não merged. Commit W3 de produto 666c51a3, teste social com unicidade solo e aceite HTTP de convite. Actions push #40974189433, job 123798049918: **720 PASS / 22 FAIL / 2 SKIP / 5345 assertions; PHPUnit exit 1; arquitetura 2 FAIL, exit 1 (já contadas nas 22)**. Runner funcional. Migrações CI SQLite PASS, não MySQL. Redução 24→22 FAIL.
- W1 entregou commits 0442ef13 (confirmação remota de PAYMENT_*), ab358cef (regressões) e dfb6f945 (correção sintática). Serviço Asaas blob cee02a75f6ab3cf63c83c7d30208f4a9d80caf62; teste blob 72f0f107660507c95713cfd8348409d6af7872b2. 9 testes Asaas replay PASS em SQLite/Http::fake. Não prova gateway remoto ou concorrência MySQL.
- React PR #715 HEAD 3ccc323dda72ee6b52e61620a0a4056618e12c28, DRAFT, mergeable=true, CI Validate #40965446872 SUCCESS, 1678 PASS / 6 SKIP / 2 TODO, Jest/build/perf exit 0; snapshot SEO interno FAIL. A→B→A síncrono não fechado. Admin PR #4 HEAD c6846c618b89192074f18313bcb57efa3e3b5d45, DRAFT, QA integrado pendente.
- Branches remotas consultadas nesta rodada: API 4, React 9, Admin 2; main API d960738b, React 9b5502cd, Admin 3bf0643b. Nenhuma ref modificada, excluída ou integrada.

## Novo P0 demonstrado por inspeção estática — owner W1
Em `app/Services/AsaasCommerceWebhookService.php`, método `processCheckoutEvent()` (aprox. linhas 188–248), blob cee02a75:
1. `CommercePayment::where('provider','asaas')->when($checkoutId !== '', ...)->latest('id')->first()` **não filtra checkout quando checkout.id está vazio**; pode selecionar o último pagamento Asaas, independentemente do evento.
2. `CHECKOUT_PAID` chama `settlement->confirm($payment, [...])` diretamente, sem validação remota `GET /payments/{id}` nem vínculo obrigatório checkout/payment/order/app/valor visível nesse ramo.
3. O ramo `PAYMENT_*` recebeu proteção, mas os 9 testes de replay não demonstram proteção equivalente de `CHECKOUT_PAID`.
4. `CommercePaymentSettlementService::confirm()` aceita certos campos ausentes na comparação, segundo revisão estática W4; não editar esse arquivo sem claim/cessão.

**Classificação:** falha estática no contrato fail-closed; explorabilidade e autenticação efetiva da entrada não auditadas, nenhuma exploração reproduzida. Não declarar vulnerabilidade explorada. Correção exigida W1: rejeitar checkout.id ausente, impedir fallback para último pagamento, verificar referência/checkout id/ordem/app/valor/status via evidência confiável de pagamento remoto e assegurar zero settlement, ledger ou EventPass quando a prova faltar. Cobrir checkout.id vazio, id divergente, payload forjado/incompleto, resposta remota inconclusiva, cross-app e pagamento legítimo, com testes e CI no HEAD exato. Claim aceito de W1 para serviço+teste de webhook; revalidar claim e blob antes de escrever. Não alterar settlement/ledger sem cessão.

## Ownership bloqueado e escalonamento
- **W3**: `app/Domain/Events/Http/Controllers/EventManagementController.php` blob 9c6eeac0f1f80700d79b07ac853fc8ad350d3998, Atlas claim d5d61027 WORKING e Genre b826161a HANDOFF. Exigir `CEDO PARA W3` + `ACEITO POR W3`, com agent_id/claim/HEAD/blob/sem concorrência, OU patch direto do owner com testes/CI. Corrigir autoria comercial server-side, duplicate sem herdar grants e regressões 403. Enquanto isso, W3 atuar em teste/arquivo livre de regressão Independence com claim, sem AgentChat/IA.
- **W2**: React `AuthContext.js` blob 78917a5a, `authTokenStorage.js` blob 25bbc63d e `authSessionSync.js` blob 79b446dc no HEAD 3ccc323d. Sem cessão bilateral identificada; exigir cedentes nominais, CEDO+ACEITO por arquivo ou patches diretos dos owners. Implementar epoch monotônico e regressões A→B→A síncrono após ownership.
- **W4**: auditar CHECKOUT_PAID após W1; manter matriz PASS/FAIL/NÃO EXECUTADO para CI, checkout/QR curatorial, reivindicação, RBAC, navegador 320/360/390/430, MySQL concorrente e rollback isolado. Não confundir mocks/SQLite com produção.
- **NP12**: segue obrigatório; retomar descoberta por fontes autorizadas, ingressos informativos sem venda, deduplicação e operação somente depois dos P0, antes de declarar Independence entregue.

## Gate e próximo passo
**BLOQUEAR MERGE/DEPLOY.** Sem CI API verde no HEAD, sem A→B→A e autoria comercial corrigidos, sem QA integrado/browser/MySQL/rollback, sem NP12 validada. Próxima ação executiva única: **W1 corrigir CHECKOUT_PAID fail-closed no serviço já claimado, publicar commit real e testes específicos com CI no SHA exato; W4 revisar independentemente**. Decisões de ownership Atlas/Genre e auth escaladas a @petertecnetdev.

W00 nesta rodada: este commit é somente de coordenação; 0 commits próprios de produto, 0 testes locais (exit N/A), 0 merges, 0 deploys.