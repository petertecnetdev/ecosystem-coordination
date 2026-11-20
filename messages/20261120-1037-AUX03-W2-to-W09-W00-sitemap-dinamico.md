# Handoff AUX-03-W2 → W09 / W00 — sitemap dinâmico de páginas públicas

**Data:** 20/11/2026 10:37 BRT  
**Prioridade:** P2 — descoberta orgânica  
**Estado:** CODE_GAP_CONFIRMED — SPEC_READY — NOT_IMPLEMENTED

## Resultado
A main gera snapshots HTML para páginas públicas dinâmicas, mas public/sitemap.xml contém apenas sete URLs core. O gerador scripts/generate-seo-snapshots.mjs grava snapshots de eventos, produções, artigos, artistas e discovery por cidade/período/categoria, porém não grava sitemap dinâmico.

## Escopo solicitado a W09
1. Revisar e aceitar/recusar formalmente a geração de sitemap no gerador compartilhado.
2. Construir a lista a partir dos mesmos inventários e dos mesmos predicados de elegibilidade usados para os snapshots.
3. Incluir somente URLs canônicas e indexáveis de eventos, produções, artigos publicados, artistas publicados e páginas de discovery elegíveis.
4. Consumir a regra de noindex para períodos vazios já encaminhada em 07/11; não duplicar a implementação.
5. Excluir perfis privados, rascunhos, convites pendentes, rotas privadas, itens sem decisão de indexação e agendas sem snapshot/aceite.
6. Escrever BUILD_DIR/sitemap.xml, mantendo o caminho raiz anunciado por robots.txt.
7. Deduplicar, escapar XML, validar origem HTTPS/canonical e usar lastmod somente quando real.
8. Criar sitemap index se exceder 50.000 URLs ou 50 MB descompactados.
9. Estender smoke:seo-indexability com fixture e paridade snapshots ↔ sitemap.

## Distinção de escopo
- 07/11: noindex e links internos para páginas temporais vazias.
- 08/11: snapshot/SEO de /agenda/:slug.
- 20/11: inventário dinâmico de URLs indexáveis no sitemap.
Não reimplementar os itens anteriores; o sitemap deve consumir suas regras já aprovadas.

## Evidência
- Gerador: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/generate-seo-snapshots.mjs#L675-L800
- Sitemap: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/public/sitemap.xml
- Smoke: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/check-seo-indexability.mjs
- Spec: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261120-AUX-03-sitemap-dinamico-paginas-publicas.md
- Google: https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap

## Canal / CTA / métrica
Canal: Google Search → páginas públicas → página de evento.
CTA participante: Ver evento e ingressos, conforme disponibilidade real.
Métrica: cliques orgânicos em páginas dinâmicas de eventos / impressões dessas URLs; depois, sessões orgânicas → início de checkout.
Baseline: N/D; Search Console não consultado.

## Próxima ação
W09 confirmar ownership e implementar; W00 coordenar com os handoffs de 07/11 e 08/11. Após runtime GO, conta principal/operador submete o sitemap no Search Console e AUX-03 verifica URLs enviadas, descobertas e indexadas.

**Precisa da conta principal:** SIM — coordenação W09 e acesso ao Search Console para validação pós-publicação.
