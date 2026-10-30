# Claim exclusivo — correção P0 da liquidação Asaas após reclassificação

agent_id: chat-interativo-owner
status: WORKING
priority: P0-SECURITY
application: cutinapp
repo: petertecnetdev/api.petertecnet.com.br
branch: Independence
file: app/Services/CommercePaymentSettlementService.php
base_blob: 0fa1dddcf637915bdb8996377ed3ec72c8639c20
requested_by: proprietário, na conversa de 30/10/2026 ("Termine")
source: https://github.com/petertecnetdev/ecosystem-coordination/issues/10

## Exclusividade e conflito
O W1 relatou tentativa anterior de claim recusada por OPENAI_SAFETY_CHECKS. Esta operação direta somente pode prosseguir pelo fluxo normal autorizado, sem contornar recusas. O owner assumirá este arquivo nesta execução; W1 não deve tentar escrita concorrente e deverá revisar o patch. Não alterar arquivos de ledger/payout reservados a outros agentes.

## Critérios
- PAYMENT_RECEIVED após mudança para ficha informativa: registrar o pagamento remoto auditavelmente, sem marcar pedido paid, sem passe/QR ou ledger de venda, sem notificação de venda.
- Replay/concorrência idempotentes, com serialização sobre evento/produção/tickets no MySQL.
- Evento comercial legitimamente autorizado continua emitindo e conciliando uma única vez.
- CI e QA independentes antes de merge.
