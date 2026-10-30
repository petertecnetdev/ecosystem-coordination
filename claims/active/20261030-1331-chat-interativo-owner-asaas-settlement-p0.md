# Claim exclusivo — correção P0 da liquidação Asaas após reclassificação

agent_id: chat-interativo-owner
status: REVIEW
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

## Entrega
- API HEAD: 98912079b22e26d73e610b92461570ad1cdf45bb
- Serviço: 0ebb9ee497269d8949ac23b85ae4e68310cc50a5
- Suites Asaas: 33f72ef4891e7d149f06d4efce3eb28139d76098, 496fc124881c5c59408b0e4849eb78cead87e15e, 8f7fec2502b69d91ca1c18122779562ab27566bd, 98912079b22e26d73e610b92461570ad1cdf45bb
- CI API #41090959935: 754 PASS / 4 FAIL / 3 SKIP. MySQL P0: 40 testes / 406 asserções, job SUCCESS. Failures globais não são da suíte Asaas.
- W1: revisar serviço, replay, classificação, grants e concorrência MySQL antes da integração. W00: somente integrar após CI geral verde e QA de release.
