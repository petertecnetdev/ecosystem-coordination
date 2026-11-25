# Claim — AUX-03 W3 — FAQ de transparência comercial para produtores

agent: AUX-03-W3
status: completed
area: producer acquisition / landing conversion / commercial copy
repository: petertecnetdev/ecosystem-coordination
deliverable: deliverables/AUX-03/20261125-1048-AUX-03-faq-transparencia-comercial-produtores.md
worklog: worklogs/20261125-1048-AUX-03-W3-faq-transparencia-comercial.md

## Objetivo
Reduzir uma possível objeção de preço com copy transparente e fundamentada na configuração comercial atual da Cutinapp.

## Feito
- Consultada coordenação e assignments AUX-03.
- Validado diretamente config/subscriptions.php na API main: subscription_enabled=false, monetization_model=transaction_fee, plans=[].
- Confirmado que a fonte não especifica taxa, responsável pelo pagamento, tarifas adicionais ou repasse.
- Revalidados PRs #724–#727 como abertos e sem reviews retornados; issue #643 permanece aberta.
- Consultado Metricool: Instagram não consta como rede conectada no retorno e agenda 25/11–02/12 vazia.
- Produzido FAQ, resposta comercial, CTA e critérios de disclosure.

## Guardrails
- Não inventar percentuais, valores, trial, tarifas ou prazos.
- Não publicar FAQ antes de validar as condições comerciais.
- Não enviar mensagens comerciais.
- Não editar PRs, código, CURRENT_STATE.md ou BLOCKERS.md.
- Não fazer merge, build, deploy ou acesso à VPS.

## Métrica
Principal: produtores únicos originados na landing que publicam primeiro evento em até 7 dias após criar a produção.
Intermediária proposta: CTA clicks após FAQ open; instrumentação ainda não implementada.
Baseline N/D.

## Próxima ação
W00/conta principal validar fee, pagador, tarifas adicionais e repasse; decidir incorporação no PR #724 e sincronização com #727.

## Estado
completed — copy preparada e handoff realizado; publicação e envio não executados.
