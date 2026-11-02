# AUX-03 W3 — 2026-11-02 10:11 BRT — Reel de aquisição para o primeiro evento

- **Objetivo:** captar produtores que já planejam um evento e conduzi-los a uma conversa qualificada sobre a publicação do primeiro evento na Cutinapp.
- **Área:** aquisição de produtores, Instagram, conteúdo e ativação.
- **Oportunidade:** o conteúdo de 01/11 já cobriu checklist de divulgação, guia de compra para participantes e abordagem comercial de agenda recorrente. Esta execução não repete esses materiais; usa um Reel de preparação do primeiro evento e CTA por Direct.
- **Obstáculo atacado:** landing de produtores ainda apresenta oferta comercial contraditória na main; enviar tráfego para ela antes da revisão pode interromper a conversão.

## Coordenação consultada / não duplicação
Consultei `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, assignment `orchestration/assignments/AUX-03/W3.md`, plano `plans/CUTINAPP_COLD_START_GROWTH.md`, claims concluídos do checklist Instagram W1 e do guia de ingressos, worklog e entregável de agenda recorrente de 01/11 e commits recentes do repositório. `CURRENT_STATE.md` ainda está consolidado em 30/10; usei os commits/worklogs de 01/11 como evidência mais recente. Não encontrei claim ativo W3 que cubra este roteiro.

## Confirmado
- Frontend `main/src/pages/ProducerLandingPage.js` contém “trial de 30 dias”, “plataforma por assinatura” e CTAs “Iniciar trial grátis”.
- API `main/config/subscriptions.php` define Cutinapp com `subscription_enabled=false`, `monetization_model=transaction_fee` e `plans=[]`.
- PRs #724, #725 e #726 aparecem abertos na consulta atual; não foi confirmado merge.
- Metricool brand 7119630 retorna apenas `gbpData`; Instagram publisher não está conectado nessa marca. Consulta de posts agendados de 02/11 a 09/11 retornou lista vazia.
- Métricas de ações do Google Business Profile retornaram 0 no período consultado; não interpretar como prova de ausência total de tráfego orgânico.
- A home pública abriu no navegador de pesquisa somente com shell JavaScript e `/for-producers` não pôde ser carregada por essa ferramenta; isso não prova indisponibilidade global.
- Busca pública por eventos indexados da Cutinapp não retornou resultados nos termos usados; o conteúdo não inventa eventos reais.

## Hipótese
CTA por Direct pode capturar interesse e qualificar o produtor sem encaminhá-lo à landing ainda não corrigida/validada. Sem respostas, cadastros ou eventos publicados medidos.

## Trabalho realizado / entregável
Criei roteiro de Reel vertical de 25 segundos, direção visual, legenda, sequência de três Stories, resposta inicial de Direct, CTA e regras de distribuição. O conteúdo:
- evita repetir o carrossel de checklist de divulgação de 01/11;
- evita repetir a campanha de agenda recorrente de 01/11;
- não cita evento, artista, data, preço, depoimento ou resultado não confirmado;
- não promete trial, assinatura, taxa zero, alcance ou venda;
- orienta não usar telas fictícias e não encaminhar a landing até revisão do PR #724 e QA mobile.

**Entregável:** `deliverables/AUX-03/20261102-W3-reel-primeiro-evento-direct-cta.md`

## Canal, CTA e métrica
- **Canal:** Instagram Reels + Stories; publicação manual após aprovação, pois Metricool não confirma integração publicadora do Instagram.
- **CTA:** enviar `PRIMEIRO EVENTO` no Direct.
- **Métrica principal:** produtores qualificados que publicam primeiro evento em até 7 dias ÷ produtores qualificados que enviam a palavra-chave.
- **Métrica intermediária:** DMs qualificadas por 1.000 contas alcançadas.
- **Atribuição manual:** `ig_reel_primeiro_evento_20261102`.
- **Baseline:** N/D; conteúdo não publicado, sem alcance ou conversão medidos.

## Evidências
- Landing atual: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/ProducerLandingPage.js
- Configuração comercial da API: https://github.com/petertecnetdev/api.petertecnet.com.br/blob/main/config/subscriptions.php
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- PR #726: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- Metricool brand settings e posts agendados consultados em 02/11/2026.
- Página pública: https://cutinapp.petertecnet.com.br/ e https://cutinapp.petertecnet.com.br/for-producers

## Próxima ação
1. Conta principal aprovar e publicar manualmente/conectar Instagram ao Metricool.
2. Responder aos DMs qualificados e registrar cidade/data, produção criada e evento publicado.
3. Integrar/revisar PR #724 e validar a landing mobile antes de inserir link em bio ou CTA com destino público.

- **Precisa da conta principal:** SIM — aprovação/acesso de publicação e revisão/QA/merge do PR #724.
- **Produto alterado:** não.
- **Instagram/Stories publicados ou agendados:** não.
- **Mensagens enviadas:** não.
- **Merge/deploy/VPS:** não.
- **Estado final:** COPY_READY — NOT_SCHEDULED — NOT_PUBLISHED — NO_OUTREACH_SENT — NOT_DEPLOYED.
