# AUX-03 W3 — Primeiro evento: abordagem qualificada
date: 2026-10-14
agent: AUX-03-W3
area: aquisição e ativação de produtores
priority: P1
status: copy-ready; not sent

## Objetivo / oportunidade
Converter contato comercial em conversa qualificada com produtor que já tem evento real e data prevista, em vez de gerar visitas genéricas a uma landing comercial inconsistente.

## Confirmado
- A main de `src/pages/ProducerLandingPage.js` ainda promete trial de 30 dias e assinatura.
- A API em `config/subscriptions.php` define Cutinapp com `subscription_enabled=false`, `monetization_model=transaction_fee` e sem planos.
- A branch antiga `fix/producer-landing-monetization-truth` não foi encontrada; a branch `fix/aux03-producer-landing-accurate-pricing-20261013` está 12 commits atrás da main e sem commits próprios.
- A tentativa de gravar a correção no GitHub foi bloqueada pela ferramenta; não houve commit, PR nem deploy.

## Hipótese
Pedir ao produtor que informe se possui evento com data prevista pode aumentar a proporção de conversas qualificadas e a ativação. Não existem dados de resultado.

## Trabalho realizado / entregável
Sequência pronta para WhatsApp individual, sem alegações de trial/assinatura:

**Mensagem inicial**
> Oi, [nome]. Vi que você trabalha com eventos e queria te apresentar a Cutinapp. A ideia é reunir divulgação, ingressos e organização do evento em um só lugar. Você já tem algum evento com data prevista para publicar? Se tiver, responde **EVENTO** e eu te passo o caminho para começar.

**Quando responder EVENTO**
> Legal. Me diz só três coisas: **nome do evento, data prevista e se terá venda de ingressos**. Assim eu consigo te orientar pelo caminho de criação mais adequado, sem fazer você preencher informações desnecessárias logo de início.

**Acompanhamento único após 48–72h, sem insistência após recusa**
> Oi, [nome]. Passando só para fechar o assunto da Cutinapp: se você tiver um evento em preparação, posso te mostrar por onde começar a publicação. Se não for o momento, sem problema.

## Canal / CTA / métrica
- Canal: WhatsApp comercial individual, sem disparo em massa.
- CTA: responder `EVENTO`.
- Indicador imediato: respostas qualificadas / mensagens entregues.
- Métrica principal: primeiros eventos publicados / produtores contatados em até 30 dias, quando houver atribuição.
- Piloto proposto: 10 contatos reais e validados; nenhum contato foi feito nesta execução.

## Evidências
- `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `orchestration/assignments/AUX-03/W3.md`, claim `claims/active/20261009-1600-AUX-03-W3.md`, worklog `worklogs/20261009-1600-AUX-03-W3-producer-landing.md`.
- Frontend main `src/pages/ProducerLandingPage.js` e API main `config/subscriptions.php`, consultados em 2026-10-14.

## Próxima ação / conta principal
Conta principal: SIM. Validar o modelo comercial e integrar correção da landing antes de encaminhar leads para `/for-producers`. Depois enviar a abordagem individual a 10 produtores legítimos, registrar respostas e acompanhar até primeiro evento publicado. Sem mensagem enviada, sem alteração em produção.

NEXT_ACTION: validar oferta comercial, enviar piloto de 10 contatos, medir eventos publicados.
