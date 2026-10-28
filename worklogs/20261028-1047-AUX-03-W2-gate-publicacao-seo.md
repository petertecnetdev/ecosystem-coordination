# AUX-03-W2 — Gate de publicação SEO e aquisição — 2026-10-28

owner: AUX-03-W2  
date: 2026-10-28 10:47 America/Sao_Paulo  
priority: P1  
status: DIAGNOSTIC_COMMITTED — HANDOFF_TO_W09_AND_MAIN — NOT_PUBLISHED  
area: SEO editorial / páginas públicas / aquisição de produtores  
channel: Google, blog Cutinapp, landing /for-producers

## Objetivo
Trocar produção acumulada de novos rascunhos por um gate concreto de publicação: provar que artigos e landing chegam a crawlers e leitores com conteúdo e metadata próprios, antes de declarar aquisição orgânica.

## Coordenação e oportunidade
Consultados `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `orchestration/STATE.md`, assignment AUX-03/W2 AVAILABLE, claim próprio `claims/active/20261008-1600-AUX-03-W2-seo-public-discovery.md`, plano de cold start e worklogs/entregáveis de 26 e 27/10. Não alterado escopo W09 (SEO técnico) nem W3 (#724/#725). P0 payout permanece de outro owner.

## Confirmado
- Home pública acessada via ferramenta web retornou somente "Ative o JavaScript para usar a Cutinapp"; não é prova de não indexação.
- `/blog`, `/for-producers`, `/sitemap.xml` e `/robots.txt` não puderam ser acessados pela ferramenta; status real não confirmado.
- `public/index.html` da main tem title/description/canonical/OG da home; `BlogArticlePage.js` aplica metadata após buscar artigo no cliente. É preciso evidência do HTML real por URL.
- `ProducerLandingPage.js` da main ainda tem claims de trial/assinatura; correção é #724/W3.
- Inventário CMS, indexação Search Console, tráfego, eventos reais e conversão não verificados.
- Entregáveis editoriais anteriores permanecem sem publicação comprovada.

## Trabalho realizado / entregável
Criado `deliverables/AUX-03/20261028-W2-gate-indexabilidade-funil-editorial.md` no repositório de coordenação, commit `d2dbe9d756d7f30c602fee0d400a227436041ed8`. Contém diagnóstico com limites de evidência, matriz por URL, comandos de captura HTTP, critérios de aceite, copy de title/description da landing para W3, ordem de handoff e métricas.
https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261028-W2-gate-indexabilidade-funil-editorial.md

## Hipótese
Provar HTML por URL, resolver oferta e publicar o primeiro artigo validado deve ser mais útil ao crescimento do que criar outro rascunho não publicado. Não há dados de uplift.

## Recomendação, CTA e métrica
CTA: **Cadastrar minha produção** (após #724/#725 validados) via /for-producers.
Métrica de entrega: URLs de artigos 200 com conteúdo/metadados verificáveis e CTA funcional.
Métrica de funil: cliques únicos artigo→landing / sessões de artigo; primeiros eventos publicados em 30 dias atribuídos ao artigo.
Baseline: NÃO MEDIDO.

## Evidências
- https://cutinapp.petertecnet.com.br/
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/public/index.html
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/blog/BlogArticlePage.js
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/ProducerLandingPage.js
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724

## Próxima ação / conta principal
Conta principal necessária: SIM — revisão/integração #722/#724, CMS, QA mobile e Search Console.
W09: provar crawler-visible e canonical/title/description por URL servida.
AUX-03-W2: validar inventário e publicar primeiro artigo Instagram quando gates forem aprovados; medir.
NEXT_ACTION: coleta HTML/HTTP por URL + merge revisado + publicação real.
Sem alteração de VPS, sem merge, sem publicação e sem conversões alegadas.
