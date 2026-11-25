# Handoff AUX-03 W3 → W00 — FAQ de transparência comercial

**Data:** 2026-11-25 10:48 BRT  
**Prioridade:** P1 — conversão da landing de produtores  
**Status:** COPY_DRAFT_READY — precisa validação comercial

## Contexto confirmado
A API main `config/subscriptions.php` (blob `380033c`) define Cutinapp com `subscription_enabled=false`, `monetization_model=transaction_fee` e `plans=[]`. A fonte não especifica percentual, pagador da taxa, tarifas adicionais ou repasse.

PR #724 continua aberto e remove trial/assinatura obrigatória da copy; #727 continua aberto e depende de #724 ou do mesmo release. PR #725 e #726 também permanecem abertos. Nenhum review foi retornado nesta consulta. Issue #643 permanece aberta.

## Entregável
`deliverables/AUX-03/20261125-1048-AUX-03-faq-transparencia-comercial-produtores.md`

Inclui:
- FAQ “Existe mensalidade para começar?”;
- FAQ “Como funciona a taxa por transação?”;
- guardrail para não anunciar trial;
- resposta de objeção para WhatsApp/Direct;
- CTA e métrica;
- lista de fatos que precisam ser confirmados antes de publicação.

## Decisão solicitada à conta principal
Confirmar:
1. percentual/valor da taxa;
2. quem paga;
3. tarifas adicionais do meio de pagamento, se houver;
4. prazo/regras de repasse;
5. regras de cancelamento/estorno relevantes ao custo.

Após a confirmação, decidir incorporar o bloco no PR #724 e manter #727 no mesmo release, conforme dependência registrada no PR.

## Métrica
Principal: produtores únicos originados na landing que publicam primeiro evento em até 7 dias após criar produção.
Intermediária: CTA clicks após abertura da FAQ (eventos propostos, não implementados).

## Guardrails
Não publicar copy, enviar mensagens, alterar PR/código, integrar, construir ou implantar sem validação/autorização. Sem VPS.

## Próxima ação
W00 devolver condições comerciais confirmadas e decisão de integração. AUX-03 poderá então revisar a copy e acompanhar a conversão após GO público.
