# AUX-03 W3 — 2026-11-01 10:34 BRT — Piloto de aquisição para agenda recorrente

- **Objetivo:** abrir conversas qualificadas com produtores de casas/pubs que trabalham com programação recorrente e conduzi-los ao primeiro evento publicado.
- **Área:** aquisição de produtores, comunicação comercial e ativação.
- **Oportunidade:** os materiais AUX-03 recentes já cobrem prospecção genérica, chamada NOVEMBRO, qualificação de lead, preparação do primeiro evento, bio Instagram, checklist de divulgação e conteúdo de segurança para participantes. Esta execução testa uma proposta diferente: reduzir retrabalho de agenda recorrente e reaproveitamento de edições.

## Coordenação e não duplicação
Consultei CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims/active/, claims/completed/, orchestration/STATE.md, orchestration/assignments/AUX-03/W1.md, orchestration/assignments/AUX-03/W3.md, plans/CUTINAPP_COLD_START_GROWTH.md e worklogs AUX-03 de 28/10 a 01/11. Não alterei os PRs de landing, onboarding ou atribuição; não abri claim de código e não dupliquei os materiais W1/W2 de hoje.

## Confirmado
- API config/subscriptions.php: Cutinapp está com subscription_enabled=false, monetization_model=transaction_fee e plans=[].
- Frontend main/src/pages/ProducerLandingPage.js ainda exibe “trial de 30 dias”, “plataforma por assinatura” e CTAs “Iniciar trial grátis”. O PR #724 corrige a inconsistência, mas continua open, draft=false, mergeable=true, merged=false. PRs #725 e #726 também permanecem abertos e sem merge.
- src/pages/production/ProductionAgendaManager.js e src/components/EventSeriesLauncher.js em main contêm fluxos de agenda semanal/séries e duplicação de eventos. Presença no código não equivale a runtime validado em produção.
- Site oficial do Luxury Club apresenta agenda recorrente (quarta, sexta e sábado) e indica atualização da experiência. A página mostra evento em 24/10/2026, data passada; não foi usado como evento futuro.
- Ficha pública da La Fyesta Pub identifica bar com entretenimento em Goiânia; nenhum evento futuro específico foi validado.
- Metricool brand cutinapp ID 7119630, timezone America/Sao_Paulo; networksData retorna apenas gbpData, sem Instagram publicador confirmado. Consulta de agendamentos 01/11–08/11 retornou lista vazia.
- Home pública foi aberta pelo navegador de pesquisa com shell “Ative o JavaScript”; /for-producers não pôde ser carregada pela ferramenta. Isso não prova indisponibilidade global.

## Hipótese
Produtores com agenda semanal/quinzenal/mensal podem responder melhor a uma proposta de reaproveitamento de edições do que a uma chamada genérica para cadastrar um evento. Não há resposta, cadastro ou ativação medidos.

## Trabalho realizado / entregável
Criei um kit de abordagem individual, sem link e sem alegações de evento ativo:
- primeira mensagem específica para Luxury Club, baseada apenas na agenda recorrente exibida publicamente;
- primeira mensagem para La Fyesta Pub, sem inventar programação ou evento;
- resposta de qualificação após a palavra-chave AGENDA (frequência, próxima data confirmada, cidade e formato de entrada);
- próximo passo de conversa/demonstração, condicionado à validação do acesso mobile;
- um follow-up único após 72h;
- regras para consentimento, autorização de publicação e não prometer taxas/trial/alcance.

**Entregável:** [deliverables/AUX-03/20261101-W3-piloto-agenda-recorrente-prospectos.md](../deliverables/AUX-03/20261101-W3-piloto-agenda-recorrente-prospectos.md)

## Canal, CTA e métrica
- **Canal:** WhatsApp comercial ou Instagram Direct oficial, contato individual após verificação do canal.
- **CTA:** responder AGENDA.
- **Métrica principal:** leads qualificados que criam produção e publicam primeiro evento em até 7 dias ÷ leads qualificados que responderam AGENDA.
- **Métricas intermediárias:** respostas AGENDA, contatos qualificados, conversa com responsável, produções criadas e eventos publicados.
- **Baseline:** N/D. Nenhuma mensagem foi enviada e nenhuma conversão foi medida.

## Evidências
- API config: https://github.com/petertecnetdev/api.petertecnet.com.br/blob/main/config/subscriptions.php
- Frontend landing: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/ProducerLandingPage.js
- Agenda recorrente: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/production/ProductionAgendaManager.js
- Duplicação/séries: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/components/EventSeriesLauncher.js
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- PR #726: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- Luxury Club oficial: https://luxuryclub.com.br/
- Ficha pública La Fyesta Pub: https://www.econodata.com.br/consulta-empresa/33372751000198-show-bar-food-music-drinks-ltda
- Metricool brand settings e consulta de agendamentos 01/11–08/11, 01/11/2026.

## Próxima ação
1. Conta principal revisar/integrar PR #724 após CI e QA mobile.
2. Validar /for-producers em smartphone real, 4G/5G e Wi-Fi.
3. Verificar canais oficiais e autorizar o contato individual com os prospectos.
4. Executar piloto sem disparo em massa; registrar resposta AGENDA → lead qualificado → produção criada → primeiro evento publicado.

- **Precisa da conta principal:** SIM — revisão/integração do PR #724, validação real da landing e autorização/acesso aos canais de contato.
- **Produto alterado:** não.
- **Instagram/GBP publicado ou agendado:** não.
- **Mensagens enviadas:** não.
- **Merge/deploy/VPS:** não.
- **Estado final:** COPY_READY — PROSPECTS_RESEARCHED — NOT_SENT — NOT_PUBLISHED — NOT_DEPLOYED.
