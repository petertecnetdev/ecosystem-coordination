# AUX-03 W3 — Worklog 2026-11-23 — sequência de ativação do primeiro evento

## Objetivo
Preparar uma sequência curta de lifecycle para recuperar produtores que já criaram a produção, mas ainda não publicaram o primeiro evento.

## Área
Ativação de produtores, onboarding, conversão e lifecycle.

## Coordenação consultada
- CURRENT_STATE.md, PRIORITIES.md e BLOCKERS.md.
- orchestration/STATE.md, WORKER_REGISTRY.md e assignments AUX-03 W1/W2/W3.
- Worklog e claim AUX-03 W3 de 22/11 sobre prospecto Bolshoi Pub.
- Entregável W2 de 23/11 sobre SEO da landing e artigo W2 de 22/11 sobre escolha de plataforma.
- Commits recentes de ecosystem-coordination.
- PRs #724, #725, #726 e #727 e issues #637/#643 no repositório Cutinapp.
- Metricool brand settings e agenda 23–30/11.

## Confirmado
- W3 concluiu a assignment de landing e voltou à função-base.
- PR #724 mantém CTA "Cadastrar minha produção", origem de aquisição e referência a producer_production_created.
- PR #725 trata de usuários já autenticados que acionam cadastro de produtor.
- PR #726 prioriza "Criar primeiro evento" / "Revisar primeiro evento" e documenta as rotas de criação, edição e assinatura do termo.
- PR #726 informa que o termo vigente é necessário para publicar; recebimentos são necessários para venda de ingressos pagos.
- PR #727 segue aberto em Draft e depende de #724 ou do mesmo release.
- Issue #643 permanece aberta; a verificação de runtime não recebeu GO.
- Issue #637 já está claimada para persistência de atribuição; não criar uma trilha paralela.
- W2 publicou em 23/11 uma recomendação de SEO snippet; W2 publicou em 22/11 um artigo sobre escolha de plataforma. Não repetimos esses temas.
- Metricool: marca Cutinapp identificada; networksData retornou somente GBP; agenda consultada de 23 a 30/11 retornou vazia.
- Não foi consultado CRM, consentimento, analytics de produtores ou provedor de e-mail.

## Hipótese
Lembretes condicionados ao estado real do onboarding podem reduzir abandono entre produção criada, evento iniciado, termo aceito e publicação. Não há dados de abandono ou conversão que comprovem essa hipótese.

## Trabalho realizado
1. Mapeei estados e rotas já documentados em #724/#726.
2. Especifiquei três contatos em D+1/D+2/D+4 com e-mails, CTAs e deep links baseados nas rotas descritas no PR #726.
3. Preparei alternativa WhatsApp apenas com opt-in.
4. Defini regras de supressão, consentimento, deduplicação e parada após publicação.
5. Defini métrica primária de primeiro evento publicado em até sete dias e métricas intermediárias.
6. Diferenciei telemetria existente/referenciada de nomes de eventos ainda propostos.
7. Registrei dependência de validação de deep links, runtime e consentimento.
8. Não enviei mensagens nem implementei automação.

## Entregável
deliverables/AUX-03/20261123-1039-AUX-03-sequencia-ativacao-primeiro-evento.md

## Canal e CTA
- Canal: e-mail; WhatsApp apenas com opt-in válido.
- D+1 CTA: Criar meu primeiro evento.
- D+2 CTA: Assinar termo para publicar.
- D+4 CTA: Revisar meu primeiro evento.

## Métrica principal
Percentual de produtores da coorte de primeira produção criada que publicam seu primeiro evento em até sete dias.

Baseline: N/D; não há acesso a analytics nesta execução.

## Evidências
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- PR #726: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- Issue #637: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/637
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- Metricool brand 7119630; schedule query 23–30/11 retornou vazio.

## Próxima ação
Conta principal/W00 confirma provedor e consentimento, valida rotas autenticadas e runtime, e confirma telemetria de evento criado/publicado. Depois disso, executar piloto pequeno com coorte mensurável.

## Precisa da conta principal
SIM — aprovação de canal/consentimento, validação de runtime/deep links e autorização de envio.

## Estado final
COPY_READY — TRIGGER_SPEC_READY — METRICS_DEFINED — INSTRUMENTATION_UNVERIFIED — NOT_IMPLEMENTED — NOT_SENT — NOT_DEPLOYED.
