# AUX-03 — Worklog 2026-11-12 10:09 BRT — Posicionamento por público e visibilidade de marca

## Objetivo
Encontrar uma ação de crescimento que não repita os guias de 10–11/11 e melhore a clareza da Cutinapp para participantes, produtores, artistas e organizadores.

## Área
SEO de marca, página pública de produto Peter Tecnet, copy, conversão e distribuição.

## Oportunidade
A página `/plataformas/cutinapp` já possui base técnica de SEO e conteúdo institucional. O H1 atual é apenas “Cutinapp”; headline e descrição falam de eventos/ingressos, mas não há uma seção explícita que explique a proposta por público. Isso permite melhorar posicionamento sem criar mais um artigo.

## Coordenação consultada
- Li `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `claims/README.md` e `COMMANDS.md`.
- Consultei worklog e handoff AUX-03 de 11/11 às 10:21, além do kit de página de evento de 11/11 às 10:15.
- `CURRENT_STATE.md` permanece com consolidação de 30/10; complementei com GitHub atual, PRs, issue P0 e consulta pública.
- O guia de descoberta de eventos de 11/11 e o kit de página de evento de 11/11 não foram repetidos.
- PRs #724, #725, #726 e #727 seguem OPEN/NOT MERGED; #727 Draft, conforme consulta atual.
- Issue P0 #643 segue aberta e documenta divergência do SHA servido pelo Nginx/HTTPS. A consulta direta de 12/11 à home Cutinapp retornou HTTP 530.
- A página Peter Tecnet `/plataformas/cutinapp` abriu, mas a extração pública mostrou apenas título/imagem; não validei visualmente o conteúdo completo ou mobile.
- No repositório Peter Tecnet, `src/seoEntities.js` já contém title, description, headline, benefícios, intenções e FAQ para Cutinapp.
- `scripts/generate-seo-pages.mjs` já gera HTML estático, canonical, OG/Twitter, JSON-LD SoftwareApplication/WebApplication, Product, BreadcrumbList e sitemap para a página de plataforma. Não recomendei recriar essa infraestrutura.
- A página gerada tem H1 com apenas o nome da plataforma e não contém bloco explícito por público. O novo trabalho é editorial/posicionamento, não auditoria técnica genérica.
- Metricool brand `cutinapp` ID 7119630 contém somente `gbpData`, sem `instagramData`. Analytics 13/10–12/11 retornou 0 para métricas disponíveis de posts/fotos/avaliações/ações e linhas vazias para keywords e posts.
- Google Business Profile exige contato presencial com clientes durante os horários declarados; marcas e negócios somente online são exemplos de inelegibilidade. A condição real de atendimento presencial da Peter Tecnet não foi confirmada. Nenhum post GBP foi criado.
- A busca `site:cutinapp.petertecnet.com.br` não retornou resultado nesta consulta; a busca exata “Cutinapp” + “Peter Tecnet” retornou o GitHub da organização. Não é prova conclusiva de desindexação; Search Console não foi acessado.
- `BLOCKERS.md` consultado lista FIN-P0-001, mas não espelha a issue pública P0 #643; handoff a W00 para reconciliação.

## Confirmado
- O site Peter Tecnet já tem página de produto com metadados e Schema.org; preservar e melhorar a mensagem, não duplicar.
- O domínio Cutinapp retornou HTTP 530 nesta consulta.
- O GBP conectado não tem métricas de atividade reportadas pelo Metricool no período consultado; a elegibilidade permanece desconhecida.

## Hipótese
Uma mensagem que separa claramente os quatro públicos pode aumentar compreensão e encaminhar melhor os visitantes para a ação adequada. Sem teste A/B ou conversões medidas.

## Trabalho realizado
1. Analisei a entidade Cutinapp em `src/seoEntities.js`.
2. Analisei o gerador estático `scripts/generate-seo-pages.mjs` e confirmei os metadados, Schema.org e sitemap existentes.
3. Verifiquei o estado público do domínio Cutinapp e a página de produto Peter Tecnet.
4. Consultei Metricool e métricas GBP no período de 30 dias.
5. Verifiquei a regra oficial de elegibilidade GBP.
6. Preparei H1, hero, seção por público, CTAs e critérios de implementação, sem editar o código de W3.

## Entregável
`deliverables/AUX-03/20261112-AUX-03-posicionamento-por-publico-cutinapp.md`

## Canal
Busca de marca/intenção → página de produto Peter Tecnet → Cutinapp → evento ou cadastro de produção.

## CTA
Participante: Explorar eventos. Produtor: Cadastrar minha produção. Marca: Conhecer a Cutinapp. Destinos Cutinapp somente após GO.

## Métricas
Impressões/cliques de marca, cliques da página Peter Tecnet para Cutinapp, cliques por CTA, cadastro de produtores, primeiro evento em 7 dias, sessões de participantes que chegam a evento/checkout. Baseline N/D.

## Evidências
- Cutinapp runtime HTTP 530: https://cutinapp.petertecnet.com.br/
- Issue P0 #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- Entidade SEO: https://github.com/petertecnetdev/petertecnet.com.br/blob/main/src/seoEntities.js
- Gerador SEO estático: https://github.com/petertecnetdev/petertecnet.com.br/blob/main/scripts/generate-seo-pages.mjs
- Página de produto Peter Tecnet: https://petertecnet.com.br/plataformas/cutinapp
- Google Business Profile eligibility: https://support.google.com/business/answer/13763036?hl=pt-BR

## Próxima ação
W00 reconciliar #643 em BLOCKERS.md; conta principal/infra resolver o serving; W3 revisar a copy e implementar pelo fluxo Git autorizado; conta principal confirmar elegibilidade presencial do GBP antes de qualquer uso desse canal.

## Precisa da conta principal?
SIM.

## Estado final
COPY_PACKAGE_READY — WORKLOG/CLAIM/HANDOFF_PENDING — PUBLIC_RUNTIME_NO_GO — NO_PRODUCT_CODE — NO_POSTS — NO_MERGE — NO_DEPLOY — NO_VPS_ACCESS — CONVERSION_NOT_MEASURED.
