# AUX-03-W2 — Cluster editorial para aquisição de produtores — 2026-10-26

owner: AUX-03-W2
priority: P1 (conversão dependente de PRs) / P2 (editorial)
status: EDITORIAL_PACKAGE_COMMITTED — NOT_PUBLISHED
area: SEO editorial / blog / páginas públicas / aquisição e ativação
repository: petertecnetdev/ecosystem-coordination

## Objetivo
Transformar três ativos editoriais preparados anteriormente em um percurso publicável e mensurável até a landing de produtores e o primeiro evento, sem acumular novo artigo redundante.

## Coordenação e oportunidade
Consultados CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims/active/, worklogs/, orchestration/STATE.md, orchestration/assignments/AUX-03/W2.md, plano de cold start e entregável editorial 25/10. Assignment W2 AVAILABLE. Claim ativo 20261008-1600-AUX-03-W2-seo-public-discovery.md permanece do próprio worker.

PRs conferidos em 26/10: #722 (links Markdown) OPEN/ready/mergeable, #724 (oferta landing) OPEN/ready/mergeable, #725 (redirecionamento produtor) OPEN/draft/mergeable. Nenhum está merged. Não houve mudança nos escopos de W3 ou W09.

Oportunidade: reduzir dispersão do conteúdo pronto, criar navegação de intenção entre divulgação, precificação, escolha de plataforma e /for-producers, e definir critérios claros para publicar sem links quebrados ou alegações comerciais incorretas.

## Trabalho realizado / entregável
Criado e enviado o documento:
- deliverables/AUX-03/20261026-W2-kit-publicacao-cluster-produtores.md
- Commit: 94091319635cc7181f3713475e454e2ae0fb69a2
- URL: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261026-W2-kit-publicacao-cluster-produtores.md

Conteúdo: mapa de três artigos já preparados, três inserções editoriais prontas com dependências de publicação, CTA comercial padronizado, pacote CMS completo para o artigo Instagram (title/description/H1/slug/canonical/OG/BlogPosting), plano de links internos e descoberta, gate de publicação mobile/crawler-visible, eventos e fórmulas de mensuração.

## Confirmado
- O artigo completo de Instagram está no repositório de coordenação desde 25/10, ainda não publicado.
- Os outros dois temas estão registrados em worklogs 11/10 e 12/10; seus corpos completos não foram verificados nesta execução.
- A main consultada de BlogArticlePage.js ainda trata links Markdown como texto; PR #722 contém a alteração.
- A main consultada da landing ainda anuncia assinatura/trial; PR #724 busca corrigir.
- Metadata do artigo na main é aplicada após carregamento no cliente; não se comprovou HTML crawler-visible no runtime.
- Pesquisa pública e acesso ao site não permitiram validar inventário CMS ou eventos reais; não foram inventados dados.
- Sem merge, deploy, publicação, conversão medida ou mudança na VPS.

## Hipótese
Uma trilha editorial entre três intenções complementares e um CTA coerente para /for-producers pode aumentar visitas qualificadas e primeiros eventos publicados. Sem evidência de uplift.

## Recomendação / CTA / métricas
Canal: blog Cutinapp / busca orgânica / links internos.
CTA: Conheça a Cutinapp para produtores → /for-producers, condicionado à correção #724.
Métrica principal: primeiros eventos publicados atribuídos aos artigos em janela de 30 dias.
Métrica intermediária: cliques únicos nos CTAs / sessões dos artigos; cadastros concluídos atribuídos.
Baseline: indisponível; instrumentação não verificada.

## Evidências
- PR #722: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- Código blog main: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/blog/BlogArticlePage.js
- Landing main: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/ProducerLandingPage.js
- Artigo anterior: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261025-W2-artigo-divulgar-evento-instagram.md

## Próxima ação e conta principal
1. Conta principal revisar/integrar #722 e #724 após QA; W3 segue responsável por #725.
2. Conferir inventário CMS, aprovar imagem oficial e publicar artigo Instagram com metadata e QA mobile.
3. Recuperar e revisar corpos dos dois artigos complementares antes de publicá-los.
4. Habilitar links cruzados apenas após URLs 200, canonical e rastreamento confirmados.
5. Medir CTR e primeiras publicações de eventos com atribuição válida.

Conta principal necessária: SIM.
NEXT_ACTION: liberar gates de publicação e publicar primeiro artigo com medição.
