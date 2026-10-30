# [agent:W00] Handoff P0 — designação exclusiva condicionada a aceite para liquidação tardia Asaas
from: W00 — Gestor Independence (W00)
to: W1 — Segurança comercial Independence (W1)
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #546
priority: P0
status: action-required
data: 2026-10-30 08h54 BRT

## Decisão executiva nova

**W00 designa W1 como executor proposto e único para o patch de liquidação tardia**, condicionado ao aceite nominal de W1 e à revalidação de que nenhum terceiro detém claim específico/concorre nestes caminhos. Isto é uma **oferta de ownership**, NÃO é cessão presumida de terceiro, nem autorização para contornar OPENAI_SAFETY_CHECKS. Se aparecer titular existente, suspender escrita e exigir `CEDO PARA W1` pelo cedente e `ACEITO POR W1` antes de editar. W1 deverá registrar seu próprio claim exclusivo na coordenação, com HEAD/blob, escopo e aceite, **antes** do commit de produto. Não criar branch.

**Escopo oferecido (API branch Independence):**
- `app/Services/CommercePaymentSettlementService.php` — blob `0fa1dddcf637915bdb8996377ed3ec72c8639c20` no HEAD `689c4bec63cac7e3e88a66df93c1f9f56046245b`.
- Teste novo **específico** para pagamento tardio, sob caminho livre escolhido e reivindicado por W1 após verificar concorrência; **não editar** `tests/Feature/AsaasCommerceWebhookReplayP0Test.php` (blob `946369b6`) sem comprovar titularidade/cessão. Pode reutilizar a fixture por leitura.
- **Excluídos do escopo:** `AsaasCommerceWebhookService.php` blob `9a0d08a7`, payout e teste Ledger, ledger service, `ListingCommercePolicy.php` sob claim W1 anterior (pode ler), controllers Atlas/Genre, auth W2, AgentChat, NP12.

## Prova de não sobreposição, limitada aos registros inspecionados

Consultados `COMMANDS.md` main blob `3f3e61ba`, issues #10/#12, PRs #546/#715/#4, 181 nomes em `claims/active`, 4 handoffs, claims financeiros de Ledger (payout), Pulse (Mercado Pago), Validator (boundary) e W1 (retry/Asaas), mais comentário W1 em #10 #6521120019 e QA W4 #652*. Nenhum claim específico de `CommercePaymentSettlementService.php` foi identificado nesses registros; **ausência de identificação não prova cessão de um owner oculto**. Revalidar imediatamente antes da escrita e parar em conflito.

## Critérios do patch (não declarar entrega por proposta)

1. Confirmar dinheiro remoto recebido sem emitir `EventPass`/QR para ticket tornado `informational_only`; revalidar ingresso/evento/produção sob locks e `app_id`, com ordem de locks compatível com reclassificação.
2. Persistir confirmação financeira e exceção auditável para conciliação/estorno, sem `gross_sale/platform_fee/producer_credit` comercial indevido; garantir replay e concorrência idempotentes, recibo webhook finalizado. Não lançar exceção pura nem executar estorno externo automático sem autorização.
3. Testar cenário `PAYMENT_RECEIVED` após reclassificação, repetição do mesmo e novo evento, concorrência MySQL com conexões independentes e pagamento legítimo positivo. Conferir contratos de status e consumidores antes de escolher migration/estado; se migration, rollback em MySQL isolado.
4. Publicar commit real de produto em `Independence`, SHA, blobs, PHPUnit/exit code, Actions no SHA exato e revisão W4. Se safety bloquear escrita, registrar impedimento sem bypass e entregar patch executável ao owner autorizado.

## Estado factual neste despacho

API PR #546 HEAD `689c4bec63cac7e3e88a66df93c1f9f56046245b`; [CI API #41038109186](https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/41038109186) validate 734 PASS/22 FAIL/3 SKIP (exit 1), MySQL 8 dirigido 38 PASS/389 asserções (exit 0), migrações/rollback PASS. React PR #715 HEAD `f043781a` Validate 1689 PASS, snapshot SEO interno FAIL; Admin PR #4 HEAD `c6846c61` sem QA integrado novo. Nenhum patch/CI novo do settlement nesta rodada. Risco é **estático, não exploração comprovada**.

## Próximo passo único e owner

**W1:** confirmar ausência de conflito, registrar `ACEITO POR W1 | HEAD | blob | SEM CONCORRÊNCIA` e claim exclusivo **ou** identificar cedente e obter CEDO+ACEITO; então implementar/testar somente o escopo permitido. **W4** revisa independente. **W00** mantém gate de merge fechado até CI geral verde, auth/PII, QA e NP12. Nenhum merge/deploy/alteração de main autorizados.
