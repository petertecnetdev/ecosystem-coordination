# AUX-03 — Worklog 2026-11-23 10:11 BRT

## Objetivo
Melhorar a correspondência da landing de produtores com buscas comerciais por plataforma de eventos e ingressos, sem inventar benefícios, taxas ou condições.

## Área
Aquisição de produtores, SEO on-page, landing page e conversão.

## Oportunidade
O PR #727 usa o title “Plataforma para produtores de eventos | Cutinapp”. A expressão descreve o público, mas deixa de fora “eventos e ingressos”, intenção comercial observada em páginas concorrentes da SERP. O PR #724 já ajusta a copy visível ao modelo por transação; a recomendação precisa manter os dois coerentes.

## Trabalho realizado
- Consultei CURRENT_STATE.md, PRIORITIES.md e BLOCKERS.md; a consolidação de CURRENT_STATE/PRIORITIES segue datada de 30/10 e BLOCKERS.md não espelha a issue #643.
- Revisei PRs #722, #724, #727 e #726 no repositório Cutinapp. Todos seguem abertos na consulta.
- Revisei os patches de #724 e #727 e confirmei que #727 depende de #724 ou do mesmo release.
- Pesquisei resultados públicos para “Cutinapp eventos ingressos”, “Cutinapp Peter Tecnet” e site:cutinapp.petertecnet.com.br; nenhuma página Cutinapp apareceu nos resultados retornados. Tratei isso como sinal limitado, não como prova de desindexação.
- A abertura direta da home Cutinapp retornou HTTP 530 pela ferramenta; não foi possível validar o runtime público.
- Comparei a linguagem de intenção em páginas de AppTicket, Tikat e Tiketa, sem copiar claims.
- Propus title de 60 caracteres e meta description de 144 caracteres, mantendo a ressalva de taxas por transação.
- Publiquei comentário editorial no PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727#issuecomment-7102233714
- Não criei artigo adicional, não alterei código/branch, não fiz merge/build/deploy, não acessei VPS, não publiquei conteúdo nem contatei produtores.

## Entregável
deliverables/AUX-03/20261123-1011-AUX-03-seo-snippet-landing-produtores.md

## Canal
Google Search → landing pública de produtores.

## CTA
“Cadastrar minha produção”, definido no PR #724; ainda não validado no runtime público.

## Métrica
Primária: primeiros eventos publicados por produtores originados da busca orgânica na landing.
Intermediárias: impressões, CTR, sessões orgânicas, cliques no CTA e cadastros iniciados.
Baseline: N/D; Search Console/Analytics não consultados.

## Evidências
- PR #727 aberto: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- PR #724 aberto: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #722 aberto: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- PR #726 aberto: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- Comentário de revisão: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727#issuecomment-7102233714
- SERP consultada em 23/11/2026: https://appticket.com.br/ ; https://tikat.com.br/ ; https://www.tiketa.com.br/produtores
- Home Cutinapp: HTTP 530 na consulta desta execução.

## Próxima ação
Owner #727 avaliar snippet; coordenar merge com #724; resolver #643; validar title/description/canonical/JSON-LD/CTA em mobile; medir Search Console após publicação.

## Precisa da conta principal
SIM — revisão da oferta, coordenação do release e validação pública.

## Estado
SEO_REVIEW_POSTED_TO_PR727 — WAITING_OWNER_REVIEW — NOT_MERGED — NOT_PUBLISHED — NO_PRODUCT_CODE_CHANGED.
