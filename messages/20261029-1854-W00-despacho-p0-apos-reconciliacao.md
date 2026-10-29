# [agent:W00] Despacho Independence P0 — 29/10/2026 18h54 BRT

status: ACTION_REQUIRED; MERGE BLOQUEADO; sem branch nova/deploy/bypass OPENAI_SAFETY_CHECKS.
Fontes: COMMANDS.md blob 3f3e61ba; issues #10/#12, claims/active, PRs API #546 React #715 Admin #4; QA W4 comentário #6509115192.

## Evolução comprovada
- Conciliação de main na Independence por operador interativo, não merge de release: API 463c4cd5 (pais 888337f6 + d960738b), React 7b9fa7f9 (pais d4703a67 + 9b5502cd). Ambos PRs mergeable=true, 0 behind. API 248 ahead, React 135 ahead, Admin 17 ahead.
- API #546 HEAD bd5b6eecf30b8c0cf8d6c31c578e5c559c710c0c, Actions #40957899468: 708 PASS / 25 FAIL / 2 SKIP, 5265 assertions; PHPUnit exit 1 e architecture enforcement exit 1 (duas falhas já nas 25). Runner operacional. Desde 17h54: 28→25 FAIL por 2 fixtures W01 (commit 3735ffbc) e 1 line-up W3 (commit bd5b6eec).
- W1 commits 0b2d43ca + 6117cc37: AsaasPaymentService.php blob 341fd0d4 e teste blob d710b78f; 22/22 unitários simulados PASS, RECEIVED sem billingType reconhecido não liquida. Gateway real e concorrência não executados.
- W3 commit bd5b6eec: tests/Feature/CutinappLineupNotificationLifecycleTest.php blob e15934bc, convite solo pending sem notificação, band confirmed notifica; teste HTTP PASS.
- React #715 HEAD 7b9fa7f9f6d753a92d3a2e8e1f27b7cb8cd0afbe, Validate #40954318666 SUCCESS, 1674 PASS / 6 SKIP / 2 TODO, Jest/build/lint exit 0; SEO snapshot global-readiness interno exit 1. Epoch A→B→A ainda falha na inspeção estática. Admin #4 c6846c61 draft, 48 PASS históricos.
- Branches remotas antes/depois: API 4/4, React 9/9, Admin 2/2. Sem merge final, deploy, MySQL isolado/rollback, browser ou NP12 operacional nesta rodada.

## Ordens exclusivas
- W1: validar claims e obter ownership exclusivo de app/Services/AsaasCommerceWebhookService.php blob eb6710a7ff0622027f1e2575598e8acc176867e7 + teste concorrente; se claim de outro owner, CEDO+ACEITO antes de editar. startReceipt usa insertOrIgnore + leitura processed_at sem reserva atômica: hipótese de replay concorrente, sem exploração reproduzida. Implementar reserva atômica, idempotência e teste com DB isolado. Cobrar validação de valor/referência remota antes de liquidação. Não tocar Ledger sem handoff. Commit/testes/exit/CI SHA.
- W2: auth React HEAD 7b9fa7f9: src/context/AuthContext.js blob 78917a5a; src/utils/authTokenStorage.js blob 25bbc63d; src/utils/authSessionSync.js blob 79b446dc. Só editar após CEDO+ACEITO por arquivo, owner/claim/HEAD/blob e ausência de concorrência. Epoch monotônico a cada set/clear, respostas /me tardias e 401/403 não revertem A→B→A; Jest + reivindicação fail-closed. Sem cessão, somente testes de arquivo livre e bloqueio nominal.
- W3: EventManagementController.php blob 9c6eeac0 reservado Atlas claim d5d61027 WORKING e Genre b826161a HANDOFF; sem CEDO+ACEITO não editar. Com cessão, autoria/proveniência comercial server-side no store, duplicate sem herdar autorização, RBAC app-scoped, 10 regressões 403 sem falsificar legacy_organizer. Sem cessão, uma regressão lifecycle/social em arquivo livre, claim+commit+CI. AgentChat/IA fora do P0.
- W4: QA independente nos SHAs exatos, PASS/FAIL/NÃO EXECUTADO para API/React, checkout/QR curatorial, reivindicação A→B→A, permissões, mobile 320/360/390/430, SEO, webhook replay, MySQL isolado migrations/rollback. NP12 somente após P0: fontes autorizadas, dedupe, dados reais, ingressos informativos sem venda, logs e monitoramento.

## Dependência executiva
Owner @petertecnetdev + Atlas/Genre: CEDO PARA W3 | cedente/agent_id | claim | HEAD bd5b6eec | EventManagementController.php blob 9c6eeac0 | SEM CONCORRÊNCIA; depois ACEITO POR W3. Alternativa: IMPLEMENTAREI COMO OWNER | agent_id | claim | SHA código | testes/exit | CI SHA. Resolver separadamente cedentes auth→W2. Não inferir transferência de handoff genérico.

## Release
API 25 FAIL, SEO interno FAIL, autoria/epoch/concorrência e QA/NP12 pendentes. PRs mergeable não equivalem a aprovação. Bloquear merge para main e deploy. W00: commit apenas de coordenação; testes próprios não executados, exit N/A; nenhum commit próprio de produto. Próximo passo executivo único: @petertecnetdev decidir cessão Atlas/Genre→W3 ou patch do owner.
