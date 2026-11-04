# AUX-03 — Plano de ativação do funil de produtores (go-live)

**Data:** 04/11/2026  
**Owner:** AUX-03  
**Prioridade:** P1 — conversão e ativação  
**Estado:** RUNBOOK_READY — PUBLICATION_BLOCKED_BY_ACCOUNT_MAIN

## Objetivo
Destravar a passagem de materiais de aquisição já preparados para interações reais, leads qualificados e publicação do primeiro evento. Esta entrega consolida o trabalho existente; não cria outro Reel, Story ou playbook concorrente.

## Confirmado
1. O pacote W1 de três Stories para pesquisa de produtores (03/11) está pronto, mas o worklog registra NOT_SCHEDULED — NOT_PUBLISHED. Não há respostas ou métricas de Story registradas.
2. O playbook AUX-03 de respostas ao Direct está concluído e depende da publicação dos Stories. Nenhuma DM foi enviada.
3. A marca Metricool cutinapp (ID 7119630) retorna apenas gbpData; não há instagramData na conexão consultada. A consulta de posts agendados de 04/11 a 11/11/2026 retornou data vazia.
4. PR #724 (oferta/CTA da landing), #725 (retorno de produtores já autenticados) e #726 (CTA do primeiro evento no onboarding) continuam abertos, não integrados e mergeable. PR #727 (metadados SEO da landing) continua aberto em draft e declara dependência do #724.
5. A API consultada em main define Cutinapp com subscription_enabled=false, monetization_model=transaction_fee e plans=[]. O bloco consultado não informa percentual de taxa.
6. A raiz pública da aplicação é uma SPA; a resposta acessível ao crawler apresenta 'Ative o JavaScript para usar a Cutinapp'. A rota /for-producers não foi recuperada pela ferramenta de navegação nesta consulta. Isso não prova indisponibilidade para navegadores reais.
7. A busca pública de 04/11 não localizou uma página de evento Cutinapp indexada que pudesse ser usada como exemplo real. Isso não prova que não existam eventos no banco ou em links não indexados.

## Hipótese
O maior obstáculo demonstrável no momento não é falta de novas peças criativas: é a ausência de publicação/distribuição confirmada e de um caminho público de conversão já validado. Enquanto os materiais permanecem não publicados e a conta Instagram não aparece conectada ao Metricool, não há dados para distinguir falta de interesse de falta de exposição.

## Decisão desta execução
Interromper a produção de novas peças genéricas e concentrar a próxima ação na ativação dos materiais já existentes. Evitar duplicar:
- Stories de pesquisa W1 (03/11);
- playbook de respostas ao Direct AUX-03 (03/11);
- Reel 'Primeiro Evento' (02/11);
- piloto de agenda recorrente (01/11);
- cartão de preparação do primeiro evento (31/10).

## Runbook de 48 horas — execução pela conta principal
### Gate 1 — caminho público (conta principal)
- Revisar e decidir integração de #724, #725 e #726 após QA funcional/mobile.
- Integrar #727 no mesmo release ou depois de #724, conforme dependência registrada no PR.
- Testar em smartphone real: landing → cadastro/login → criação da produção → criação/revisão do evento → publicação.
- Não enviar tráfego pago nem divulgar oferta até confirmar que a copy visível e os metadados refletem o modelo comercial vigente.

### Gate 2 — distribuição (conta principal)
- Publicar os três Stories W1 já preparados, inserindo os stickers nativos do Instagram.
- Registrar alcance e votos após 24 horas.
- Confirmar acesso autorizado ao Instagram Direct. Responder somente a quem iniciar interação voluntária.
- Se a conta principal preferir usar Metricool, conectar Instagram Business/Page e confirmar que instagramData aparece antes de agendar. Não tentar publicar Instagram pela conexão atual, que só expõe GBP.

### Gate 3 — conversão (AUX-03 após liberação)
- Aplicar o playbook de Direct de 03/11 sem reescrever respostas já aprovadas.
- CTA único: **PREPARAR** — solicitar orientação para preparar o primeiro evento.
- Qualificar o próximo evento, cidade e estágio; não pedir documentos ou dados financeiros no Direct.
- Só encaminhar link público depois de a conta principal validar o fluxo real de cadastro/publicação.

## Rastreador mínimo (sem dados sensíveis)
Uma linha por campanha e coorte. Não registrar CPF, documentos, dados bancários ou dados pessoais desnecessários.

| Data | Origem/campanha | Alcance Story 3 | Respostas | Produtores qualificados | Produções criadas | Eventos publicados em 7 dias | Primeiras vendas em 30 dias |
|---|---|---:|---:|---:|---:|---:|---:|
| 04/11/2026 | ig_story_pesquisa_produtores_20261103 | N/D | N/D | N/D | N/D | N/D | N/D |

Definições:
- **Resposta:** interação voluntária identificável (resposta à caixa ou DM iniciada pela pessoa); votos de enquete são indicador separado.
- **Lead qualificado:** pessoa que confirma ser produtora/iniciante e informa uma próxima produção ou intenção concreta.
- **Produção criada:** registro real no produto, não apenas conversa.
- **Evento publicado:** página pública acessível e autorizada pelo produtor.
- **Primeira venda:** pedido pago/confirmado conforme registro oficial do produto; não inferir a partir de intenção ou checkout iniciado.

## CTA e métrica
- **CTA:** responder **PREPARAR** nos Stories/Direct.
- **Métrica principal:** produtores qualificados que publicam o primeiro evento em até 7 dias ÷ produtores qualificados que responderam à campanha.
- **Indicador de distribuição:** respostas voluntárias ÷ alcance do Story 3 (janela de 24h).
- **Indicador de negócio:** produtores com primeira venda em até 30 dias ÷ produtores com evento publicado.
- **Baseline:** N/D; os Stories ainda não têm publicação/Insights confirmados.

## Próxima ação
Conta principal executar Gates 1 e 2. AUX-03 assume respostas, qualificação e acompanhamento somente depois de acesso autorizado ao Direct e de um caminho público validado.

## Precisa da conta principal?
**SIM — bloqueio explícito:** revisão/integração dos PRs, validação mobile do caminho público, publicação dos Stories e acesso autorizado ao Direct.

## Limites
Nenhuma mensagem foi enviada, nenhum Story/Reel foi publicado, nenhum contato foi abordado, nenhum PR foi integrado e nenhuma VPS foi acessada nesta execução.