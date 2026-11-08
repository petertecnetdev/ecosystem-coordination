# AUX-03 — Descoberta orgânica e compartilhamento de agendas públicas de produções

**Data:** 08/11/2026  
**Worker:** AUX-03-W2 — SEO, Blog & Public Discovery  
**Prioridade:** P2 — aquisição orgânica e distribuição de eventos  
**Estado:** OPPORTUNITY_CONFIRMED — IMPLEMENTATION_SPEC_READY — NOT_IMPLEMENTED

## Objetivo

Transformar `/agenda/:slug` em uma landing pública compartilhável e rastreável, capaz de levar visitantes da agenda de uma produção aos eventos publicados e, quando houver disponibilidade, à compra de ingressos.

## Área

SEO de páginas públicas, Open Graph/Twitter, sitemap, links internos, compartilhamento orgânico, descoberta de eventos e conversão participante → evento → checkout.

## Confirmado — oportunidade encontrada

A rota pública `/agenda/:slug` já existe e não é apenas uma tela interna:

1. `src/App.js` registra `/agenda/:slug` com `ProductionAgendaPublicPage`.
2. `src/pages/production/ProductionAgendaPublicPage.js` consulta o endpoint público existente `cutinappService.publicProduction(slug)`, que retorna a produção, agenda semanal, próximos eventos e eventos anteriores.
3. A página apresenta programação semanal, próximo evento, filtros de próximos/hoje/7 dias/anteriores, botão de copiar link e compartilhamento nativo via `navigator.share`.
4. A página altera title, meta description e Open Graph somente depois de receber os dados da API, em `useEffect`.
5. A rota `/agenda/:slug` no `SeoManager.js` começa com título e descrição genéricos derivados do slug. O componente `SeoHead` também aplica os metadados por `useEffect`.
6. Os botões de navegação para produção e eventos usam `navigate(...)`; não são links HTML `<a href>`. Botões de copiar, compartilhar e filtrar são ações e devem continuar como botões.
7. O gerador `scripts/generate-seo-snapshots.mjs` produz snapshots para eventos, produções, artigos, artistas, perfis, itens e descoberta por cidade. Não há builder nem escrita de snapshot para `agenda/:slug`.
8. O corpo do snapshot atual de produção contém link para a própria página pública, mas não contém link explícito para a agenda pública.
9. `public/robots.txt` permite rastreamento de `/agenda/`.
10. `public/sitemap.xml` contém apenas sete rotas institucionais/core; não contém URLs dinâmicas `/agenda/:slug`.
11. `scripts/check-seo-indexability.mjs` valida as rotas core e prefixos privados, mas não verifica agendas públicas nem a coerência entre snapshots de agenda e sitemap.

**Limite da evidência:** os pontos acima foram confirmados no código da branch `main`. Não consultei Google Search Console nem validei o HTML servido em produção nesta execução. Portanto, não afirmo que agendas estejam ausentes do índice do Google, que previews sociais estejam quebrados em todos os serviços ou que exista perda de tráfego mensurada.

## Oportunidade de aquisição

A página de agenda já tem uma ação de distribuição nativa. O ciclo esperado é:

**Produção publica datas → compartilha a agenda no WhatsApp/Instagram → participante abre a agenda → escolhe um evento → acessa detalhes/ingressos.**

A oportunidade não exige inventar uma nova funcionalidade nem criar eventos artificiais. Ela consiste em tornar crawler-visible e indexável, quando houver conteúdo real, uma página que já existe e já foi construída para ser compartilhada.

## Hipótese

Uma prévia com nome da produção, próximo evento real e imagem correta pode elevar a confiança e a abertura dos links compartilhados. Links HTML rastreáveis e snapshots específicos também podem facilitar a descoberta dos eventos relacionados.

Não há teste A/B, baseline ou uplift comprovado.

## Recomendação de implementação — handoff ao owner do gerador compartilhado (W09)

O gerador `scripts/generate-seo-snapshots.mjs` tem ownership/claims ativos de W09 para SEO global e páginas públicas de produção. Esta entrega **não altera o gerador nem transfere ownership**. Solicita-se ao owner W09 avaliar e aceitar o escopo `/agenda/:slug` antes de editar o arquivo compartilhado.

### 1. Fonte de dados

Reutilizar o endpoint já consumido pela página:

`cutinappService.publicProduction(slug)` → `/organizations/public/{slug}`.

A lista de produções públicas já é obtida pelo gerador em `fetchAllProductions()`. Para enriquecer as agendas, W09 deve confirmar se o payload de listagem já contém os campos necessários. Se não contiver, usar o endpoint público por slug com concorrência limitada e timeout; não criar endpoint novo sem necessidade comprovada.

Campos já consumidos pela página:
- `production`;
- `weekly_agenda` / `weeklyAgenda`;
- `upcoming`;
- `past`.

### 2. Regra de indexabilidade

Não gerar páginas de agenda em massa apenas porque a produção existe.

Considerar uma agenda elegível para indexação quando tiver pelo menos:
- um evento público em `upcoming`; ou
- ao menos um slot de programação semanal com evento público válido e vigente.

Se houver somente eventos anteriores, sem próximo evento nem slot semanal vigente, manter a página acessível ao visitante, mas aplicar `noindex,follow` e não incluí-la no sitemap.

Slug inexistente ou produção não pública não deve receber snapshot válido. O comportamento HTTP/404 deve ser tratado pelo mecanismo de rotas/servidor, sem criar página fictícia.

Não confundir slot semanal vazio com evento publicado. Não incluir convites, rascunhos, eventos cancelados ou dados não públicos.

### 3. Snapshot específico de agenda

Criar builder próprio para `agenda/{slug}`, sem alterar a semântica dos snapshots de evento, produção ou períodos de cidade.

**Title recomendado:**
`Agenda de {production.name} | Próximos eventos na Cutinapp`

**Meta description:**
- Com próximo evento: `Confira a agenda de {production.name}. Próximo evento: {nextEvent.title}, {data formatada}.`
- Somente com programação semanal válida: `Veja a programação semanal de {production.name} na Cutinapp e acompanhe os eventos publicados.`

Truncar a descrição sem cortar palavras e sem inventar disponibilidade, preços ou atrações.

**Canonical:**
`https://cutinapp.petertecnet.com.br/agenda/{slug}`

**Open Graph e Twitter:**
- `og:title`, `og:description`, `og:type=website`, `og:url`, `og:site_name`;
- `og:image` e `og:image:alt`;
- `twitter:card=summary_large_image`, `twitter:title`, `twitter:description`, `twitter:image`;
- imagem: flyer do próximo evento real → capa pública da produção → logo público → logo oficial da Cutinapp;
- resolver URL absoluta HTTPS e não usar imagem de outro evento/produção.

### 4. Conteúdo HTML e links rastreáveis

O snapshot deve conter conteúdo útil, não apenas metadados:
- breadcrumb Cutinapp → Produções → {produção} → Agenda;
- H1 com nome real da produção;
- cidade/UF somente quando publicadas no perfil;
- programação semanal somente com slots públicos válidos;
- próximos eventos reais em ordem de data;
- data, local público e link do evento;
- CTA para a página pública da produção.

Na UI React, transformar destinos de navegação em links reais `<Link>`/ `<a href>` mantendo a aparência mobile-first:
- Ver produção → `/production/{slug}/public`;
- Ver evento → `/event/{event.slug}`.

Manter como `button` as ações de copiar link, compartilhar e alternar filtros.

No snapshot da produção, incluir link para `/agenda/{slug}` somente quando a agenda for elegível. Isso cria caminho HTML entre perfil da produção e agenda.

### 5. Schema.org

Usar `CollectionPage` para a página de agenda, com:
- `name`, `description`, `url`;
- `mainEntity` como `Organization` da produção, com dados públicos;
- `ItemList` somente para eventos públicos futuros realmente incluídos no HTML;
- `BreadcrumbList`.

Não emitir `ItemList` vazio. Não declarar `EventSeries` sem evidência de série/evento recorrente estruturado. Não inferir endereço, preço, disponibilidade, integrantes ou quantidade de eventos.

### 6. Sitemap e robots

- Manter `Allow: /agenda/` no `robots.txt`.
- Gerar URLs `/agenda/{slug}` no sitemap apenas quando a agenda passar a regra de conteúdo atual.
- Não cadastrar slugs manualmente nem listar agendas vazias/past-only.
- Usar `lastmod` apenas quando houver timestamp real e confiável da produção/agenda/evento; caso contrário, omitir.
- Estender `check-seo-indexability.mjs` para validar formato, duplicidade, origem canônica, elegibilidade e ausência de rotas privadas.
- Não usar `robots.txt` para esconder uma página que precisa ser rastreada para ler `noindex`.

## Copy pronta para estado vazio

**Título:** A programação ainda não foi publicada.

**Texto:** A produção ainda não anunciou novas datas. Consulte o perfil da produção ou descubra outros eventos disponíveis na região.

**CTA principal:** Ver produção → `/production/{slug}/public`.

**CTA secundário:** Descobrir eventos em {cidade} → `/eventos/{citySlug}`; quando não houver cidade pública, usar `/eventos`.

Não exibir essa copy para agenda que possua programação semanal válida ou evento futuro publicado.

## Canal e CTA

**Canal:** perfil público da produção → agenda compartilhável → WhatsApp/Instagram/Direct → participante → página de evento → checkout.

**CTA de distribuição:** Compartilhar agenda (já existe na página).  
**CTA de conversão:** Ver evento e ingressos, somente quando o status real indicar ingresso gratuito/disponível; nos demais estados, Ver evento.  
**CTA de recuperação para agenda vazia:** Ver produção / Descobrir eventos na região.

## Métricas

Instrumentar/consultar antes de afirmar resultado:
1. `agenda_share_started` / visualizações únicas de agenda.
2. Sessões de referência de links compartilhados / compartilhamentos iniciados.
3. `agenda_event_click` / sessões únicas de agenda.
4. `agenda_checkout_started` / cliques em evento originados da agenda.
5. Compras atribuídas à agenda, quando a atribuição estiver disponível.
6. Search Console: impressões, cliques, CTR e páginas indexadas para `/agenda/`.

**Baseline:** N/D. Nenhuma métrica foi acessada nesta execução.

## Critérios de aceite

- [ ] Agenda com evento futuro: snapshot com title/description/canonical/OG/Twitter específicos.
- [ ] Agenda apenas com programação semanal válida: snapshot e indexação conforme regra de conteúdo.
- [ ] Agenda vazia ou somente histórica: noindex/follow, fora do sitemap, sem ItemList vazio.
- [ ] Snapshot contém H1, dados públicos e anchors para produção/eventos.
- [ ] UI mantém ações de compartilhar/copiar como botões e usa anchors para navegação.
- [ ] Snapshot de produção aponta para agenda elegível.
- [ ] Imagens OG são absolutas, HTTPS e correspondem à produção/evento.
- [ ] JSON-LD válido, sem dados inventados ou privados.
- [ ] Sitemap sem duplicidades, sem agenda vazia e com canonical correto.
- [ ] HTML inicial contém conteúdo/meta específicos sem depender da execução do React.
- [ ] Preview testado em WhatsApp/Meta Sharing Debugger e navegador mobile 320/360/390/430.
- [ ] PR #692 e snapshots atuais de evento/produção/artista/blog permanecem sem regressão.

## Coordenação e não duplicação

- `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `COMMANDS.md`, `REVENUE_TARGET.md`, `PROFITABILITY_PLAN.md`, `claims/active/`, `claims/completed/`, `worklogs/`, `messages/` e assignments AUX-03 foram consultados.
- O registro geral de estado ainda tem consolidação antiga de 30/10; commits e worklogs de 04–07/11 foram usados para complementar.
- A entrega de 07/11 sobre páginas vazias cidade/período é diferente e não foi repetida.
- Claim ativo W09 abrange `/production/:slug/public` e o gerador compartilhado; a agenda `/agenda/:slug` não aparece no escopo explícito desses claims. Como o mesmo arquivo é compartilhado, W09 deve aceitar o novo escopo antes de implementação.
- O claim AUX-03-W2 de metadados da landing de produtores/PR #727 não foi alterado.

## Próxima ação

1. W09 revisar e aceitar/recusar formalmente a extensão do gerador para `/agenda/:slug`.
2. Conta principal coordenar a prioridade e a integração do sitemap/snapshots.
3. Após aceite, implementar snapshot, links HTML e sitemap dinâmico.
4. Executar smoke SEO, QA de crawler/preview e matriz mobile.
5. Medir compartilhamentos → visitas → cliques em eventos → checkout.

## Precisa da conta principal?

**SIM** — para coordenar o owner W09 do gerador compartilhado e autorizar a integração no produto.

## Limites desta entrega

Nenhum código do produto foi alterado. Nenhuma branch, commit ou PR de produto foi criado. Nenhum merge, build, deploy, acesso à VPS, publicação social ou consulta ao Search Console foi realizado.
