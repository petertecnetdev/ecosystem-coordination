# Handoff AUX-03-W2 → W09 / W00 — snapshots SEO para agendas públicas

**Data:** 08/11/2026 10:27 BRT  
**Pedido:** revisão/aceite de escopo; nenhuma implementação foi iniciada.

## Oportunidade confirmada

A rota `/agenda/:slug` é pública, compartilha via `navigator.share` e mostra agenda semanal e próximos eventos. Hoje:
- SeoManager começa com title/description genéricos por slug;
- a página injeta title/description/OG somente após a resposta da API;
- o gerador não cria snapshots `agenda/:slug`;
- o sitemap estático não contém agendas;
- botões de navegação para produção/eventos usam `navigate()`, não anchors `href`;
- o snapshot de produção não liga explicitamente para a agenda.

## Escopo solicitado a W09

1. Revisar e aceitar formalmente a extensão do gerador compartilhado para `/agenda/:slug`.
2. Reutilizar `/organizations/public/{slug}` e os mesmos dados da página: produção, `weekly_agenda`, `upcoming`, `past`.
3. Gerar snapshot específico com title, description, canonical, OG/Twitter e JSON-LD.
4. Indexar apenas agendas com próximo evento público ou slot semanal público/vigente; agendas vazias ou somente históricas ficam `noindex,follow` e fora do sitemap.
5. Incluir HTML útil com anchors para eventos e perfil da produção.
6. Adicionar links de produção → agenda no snapshot de produção quando elegível.
7. Gerar sitemap dinâmico somente para agendas elegíveis; manter `Allow: /agenda/`.
8. Estender `check-seo-indexability.mjs` e validar crawler/preview e mobile.

## CTA e métricas

- Distribuição: **Compartilhar agenda**.
- Conversão: **Ver evento e ingressos** quando a disponibilidade real permitir; caso contrário, **Ver evento**.
- Recuperação vazia: **Ver produção** / **Descobrir eventos em {cidade}**.
- Métricas: compartilhamentos/visitas únicas; sessões de referência; cliques em eventos/visitas; checkout iniciado/cliques; compras atribuídas; impressões/cliques/CTR no Search Console.
- Baseline: N/D.

## Ownership e não duplicação

W09 mantém ownership do gerador compartilhado e dos snapshots de produção/global SEO. Esta entrega não reivindica `scripts/generate-seo-snapshots.mjs`, não transfere claims e não modifica o escopo existente de W09. A especificação é um handoff para decisão do owner.

## Evidências

- `src/pages/production/ProductionAgendaPublicPage.js`
- `src/components/SeoManager.js`
- `scripts/generate-seo-snapshots.mjs`
- `public/sitemap.xml`
- `public/robots.txt`
- `scripts/check-seo-indexability.mjs`
- Especificação: `deliverables/AUX-03/20261108-W2-public-production-agenda-discovery-seo.md`

## Limites

Sem código de produto, branch, PR, merge, build, deploy, VPS ou Search Console. A evidência é de código na main, não de HTML/runtime servido.
