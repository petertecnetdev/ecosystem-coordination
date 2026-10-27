# AUX-03-W2 — SEO editorial de páginas de evento — 2026-10-27

owner: AUX-03-W2
date: 2026-10-27 10:38 America/Sao_Paulo
priority: P1/P2
status: ARTICLE_COMMITTED — NOT_PUBLISHED — RUNTIME_NOT_VERIFIED
area: SEO editorial / blog / páginas públicas / aquisição de produtores
repository: petertecnetdev/ecosystem-coordination

## Objetivo
Criar ativo editorial novo, de intenção comercial próxima à ativação, que ensine produtores a preparar páginas públicas de eventos com informação confiável, compartilhamento e descoberta orgânica.

## Oportunidade e coordenação
Lidos CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims/active/, worklogs/ recentes, orchestration/STATE.md e assignment AUX-03/W2 (AVAILABLE). Claim ativo próprio: claims/active/20261008-1600-AUX-03-W2-seo-public-discovery.md. O cluster de 26/10 já cobre escolha de plataforma, preço de ingresso e Instagram; este artigo cobre uma quarta intenção, distinta: criar a página pública do evento. Consulta de código no repositório de coordenação por temas próximos não retornou duplicação textual. Não alterados escopos W09 (SEO técnico) nem W3 (landing/cadastro).

## Confirmado
- PR #722 (links editoriais) em 27/10: open, draft=false, merged=false.
- PR #724 (oferta landing) em 27/10: open, draft=false, merged=false.
- PR #725 (retorno cadastro produtor) em 27/10: open, draft=false, merged=false.
- Tentativa de abrir a home pública via ferramenta web em 27/10 retornou HTTP 530; não é prova de indisponibilidade geral.
- Pesquisa pública restrita a domínio não revelou eventos ou artigos verificáveis nesta execução. Inventário CMS, indexação e tráfego não foram comprovados.
- Google Search Central recomenda páginas únicas por evento e dados reais de nome, data e local; o artigo genérico usa BlogPosting, não Event.
- Nenhum dado de eventos, preços, cidades ou resultados foi inventado.

## Trabalho realizado / entregável
Criado no GitHub:
- deliverables/AUX-03/20261027-W2-artigo-pagina-evento-google.md
- Commit: 7eac882f20edbd87dd51e37674a08d6d19e49fbb
- URL: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261027-W2-artigo-pagina-evento-google.md

O pacote contém artigo original completo, H1, title, description, slug, canonical proposto, OG, BlogPosting, intenção e termos, checklist mobile-first, links condicionais, regras de indexação e métricas. Não cria branch para relatório nem altera aplicação ou VPS.

## Hipótese
Buscas sobre como criar uma página de evento podem atrair produtores mais próximos da publicação do primeiro evento. Não há volume de busca, baseline ou conversão verificados.

## Recomendação / CTA / métrica
- Canal: blog Cutinapp / Google / compartilhamento editorial.
- CTA: **Conheça a Cutinapp para produtores** → /for-producers, SOMENTE após integração e validação da oferta #724.
- Métrica intermediária: cliques únicos artigo→landing / sessões do artigo.
- Métrica de negócio: primeiros eventos publicados em 30 dias por produtores atribuídos ao artigo.
- Medição: pendente; nenhum uplift alegado.

## Evidências
- PR #722: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- Google Event markup: https://developers.google.com/search/docs/appearance/structured-data/event?hl=pt-BR
- SEO dev guide: https://developers.google.com/search/docs/fundamentals/get-started-developers

## Próxima ação e conta principal
1. Conta principal revisar PRs #722/#724 e QA mobile; W3 mantém #725.
2. Conferir inventário CMS e conteúdo similar, depois revisar e aprovar o novo artigo.
3. Confirmar página pública acessível, metadados/canonical e imagem OG oficial; publicar com data real.
4. Medir cliques no CTA e primeiros eventos publicados atribuídos; não anunciar resultado sem analytics.

Conta principal necessária: SIM, para revisão, acesso ao CMS, publicação e validação do destino.
NEXT_ACTION: inventário CMS + gates #722/#724 + publicação verificada.
