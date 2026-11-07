# AUX-03 W3 — Worklog 2026-11-07 — Sequência pós-cadastro para primeiro evento

## Objetivo
Aumentar a ativação de produtores já cadastrados, conduzindo a produção criada até a publicação do primeiro evento em até sete dias.

## Área
Aquisição e conversão de produtores, onboarding, comunicação lifecycle e primeira publicação.

## Oportunidade
Os trabalhos recentes cobriam landing, prospecção, Stories/Direct e prioridade do CTA no onboarding. Faltava uma sequência de comunicação pós-cadastro, segmentada pelo estado real do produtor. O foco desta execução foi somente essa etapa, sem produzir outra campanha genérica nem repetir a prospecção dos eventos de Raphaela Gentil e Taberna Music Pub.

## Trabalho realizado
- Consultei CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims/README.md, claims/active/, worklogs recentes, orchestration/STATE.md, WORKER_REGISTRY.md e assignments AUX-03/W1-W3.
- Confirmei W3 em fallback para sua função-base; o assignment W3 anterior está DONE e não há novo assignment READY.
- Verifiquei o claim genérico ativo de AUX-03-W3 (20261009-1600-AUX-03-W3.md) e não alterei nem sobrescrevi o claim existente. Esta entrega é um artefato de comunicação lifecycle, sem alteração de código ou conflito de arquivos de produto.
- Consultei diretamente os PRs #724, #725, #726 e #727: todos continuam abertos e não integrados; #727 permanece draft. Registrei os SHAs e estados consultados.
- Li o diff de #726 e o arquivo ProducerOnboardingPage.js no HEAD 45ad350c. Confirmei os caminhos de criação/revisão do evento, assinatura do termo e configuração de recebimentos; confirmei que a interface diferencia preparação do evento, publicação e venda de ingressos pagos.
- Li o diff de #725 para entender a preservação do destino /production/create e da origem de aquisição no cadastro.
- Consultei Metricool: marca cutinapp, ID 7119630, timezone America/Sao_Paulo, conexão retornada somente com gbpData; Instagram não aparece em networksData. Agendamentos de 07/11 a 14/11: lista vazia. Não publiquei nem agendei conteúdo.
- Preparei sequência de cinco mensagens com assunto, copy, CTA e destinos, mas condicionada a estados do onboarding. Incluí supressão após publicação/descadastro, regras de consentimento e orientação para não receber documentos/dados financeiros por mensagem.
- Não enviei e-mail/WhatsApp, não configurei automação, não alterei código, não fiz merge ou deploy e não acessei a VPS.

## Entregável
deliverables/AUX-03/20261107-W3-sequencia-ativacao-primeiro-evento.md

## Canal
E-mail e WhatsApp com consentimento aplicável; ainda não configurados nesta execução.

## CTA
Principal: **Criar primeiro evento**. Condicionais: **Ler e assinar termo**, **Configurar recebimentos** (somente quando houver intenção de vender ingressos pagos) e **Responder AJUDA**.

## Métrica principal
Taxa de primeiro evento publicado em 7 dias = produtores com primeiro evento efetivamente publicado até 7 dias após criação da produção ÷ produtores com produção criada no período.

Baseline: N/D. Nenhum envio ou conversão foi medido.

## Evidências
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724 — open, not merged; head 37456fc39fb40a9dcd626f563d2e085c808f1d1c.
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725 — open, not merged; head eb2fb6880d524dbe726134a8d98b634f1e716705.
- PR #726: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726 — open, not merged; head 45ad350c45b8dd4d34a0634c792c8cedbc803b21.
- PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727 — open, draft, not merged; head b745b97ecfe1753cddb6aa34d3f3da6ffe1ca72e.
- Assignment AUX-03/W3: orchestration/assignments/AUX-03/W3.md.
- Metricool brand 7119630: somente gbpData; scheduled posts 07/11–14/11 vazios.

## Hipótese
Mensagens acionadas por estado e com um próximo passo único podem reduzir a confusão entre evento, termo e recebimentos e aumentar a publicação do primeiro evento. Sem dados de coorte, o impacto permanece não medido.

## Próxima ação
Conta principal/owner de CRM e integrações: aprovar a copy, validar os destinos na versão servida, mapear os gatilhos aos estados reais da API/onboarding e implementar envio com consentimento, idempotência, descadastro e supressão após publicação. Depois medir coortes de sete dias.

## Precisa da conta principal?
SIM — aprovação, runtime verificado, provedor de envio autorizado e telemetria.

## Estado final
DELIVERABLE_COMMITTED — WORKLOG_COMMITTED — CLAIM_COMPLETED — HANDOFF_SENT — NOT_CONFIGURED — NOT_SENT — NO_PRODUCT_CODE_CHANGE — NOT_MERGED — NOT_DEPLOYED — NO_VPS_ACCESS — CONVERSION_NOT_MEASURED.
