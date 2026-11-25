# AUX-03 W3 — Worklog 2026-11-25 — transparência comercial da landing

## Objetivo
Preparar uma resposta comercial precisa para a objeção “quanto custa?” sem inventar taxas ou repetir a copy já existente do PR #724.

## Área
Aquisição de produtores, landing pública, copy comercial e conversão.

## Coordenação consultada
- CURRENT_STATE.md, PRIORITIES.md e BLOCKERS.md.
- orchestration/STATE.md e WORKER_REGISTRY.md.
- Assignments AUX-03 W1, W2 e W3.
- Claim e worklog AUX-03 W3 de 24/11.
- Estados abertos dos PRs #724, #725, #726 e #727 e reviews associados.
- Configuração comercial atual em api.petertecnet.com.br/config/subscriptions.php.
- Metricool brand settings e agenda 25/11–02/12.

## Confirmado
- Assignment AUX-03 W3 anterior está DONE e permite fallback à função-base; nenhum override W00 READY/CLAIMED foi encontrado no arquivo W3.
- W1 está BLOCKED e W2 AVAILABLE.
- API main config/subscriptions.php, blob 380033cdb502c34896b907ae2209c91e31f7f14f: Cutinapp subscription_enabled=false, monetization_model=transaction_fee e plans=[].
- A configuração consultada não especifica taxa/percentual, quem paga, tarifas adicionais nem prazo de repasse.
- PRs #724, #725, #726 e #727 continuam abertos; nenhum review retornado na consulta.
- PR #727 registra dependência de #724 ou do mesmo release.
- Issue #643 continua aberta.
- Metricool brand 7119630 retornou somente gbpData; Instagram não consta em networksData.
- Agenda Metricool de 25/11 a 02/12 retornou vazia.

## Hipótese
A falta de explicação comercial da taxa por transação pode gerar objeção antes do cadastro, mas não há pesquisa/analytics que comprovem esse atrito ou sua magnitude. O bloqueio de runtime público continua mais fundamental.

## Trabalho realizado
1. Consultei a fonte de coordenação e assignment AUX-03.
2. Validei diretamente o modelo comercial na API main.
3. Revalidei PRs de landing, cadastro, onboarding e SEO.
4. Preparei FAQ e resposta para WhatsApp/Direct, sem informar valores não confirmados.
5. Defini condições obrigatórias para publicação e métrica intermediária de FAQ → CTA.
6. Evitei repetir prospecção, mensagens pós-evento, sequência D+1/D+2/D+4 e campanhas anteriores.

## Entregável
deliverables/AUX-03/20261125-1048-AUX-03-faq-transparencia-comercial-produtores.md

## Canal e CTA
Canal: landing /for-producers e atendimento WhatsApp/Direct.
CTA da landing: Cadastrar minha produção (já previsto no PR #724).
CTA comercial: Quero confirmar as condições do meu evento.

## Métrica principal
Produtores únicos originados na landing que publicam o primeiro evento em até 7 dias após criar a produção.
Métrica intermediária proposta: cliques únicos no CTA após abrir a FAQ / aberturas únicas da FAQ.
Baseline: N/D.

## Evidências
- API config/subscriptions.php, blob 380033cdb502c34896b907ae2209c91e31f7f14f.
- PRs #724–#727 abertos; sem reviews retornados.
- Issue #643 aberta.
- Metricool brand 7119630: apenas GBP; agenda 25/11–02/12 vazia.
- CURRENT_STATE.md ainda tem consolidação operacional antiga de 30/10; BLOCKERS.md lista FIN-P0-001, mas não contém issue #643.

## Próxima ação
W00/conta principal confirmar percentual/valor, responsável pelo pagamento, tarifas adicionais e prazo/regras de repasse. Depois, incorporar a FAQ ao PR #724 ou ao mesmo release de #727, validar mobile e medir FAQ → CTA → cadastro → primeira publicação.

## Precisa da conta principal
SIM — validar condições comerciais e liberar publicação da copy.

## Estado final
COPY_DRAFT_READY — COMMERCIAL_FACTS_PARTIALLY_CONFIRMED — FEE_DETAILS_UNVERIFIED — HANDOFF_REQUIRED — NOT_PUBLISHED — NOT_DEPLOYED.
