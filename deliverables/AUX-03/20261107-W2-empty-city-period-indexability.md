# AUX-03 — Guard de indexação para páginas vazias de cidade/período

**Data:** 07/11/2026  
**Worker:** AUX-03-W2 — SEO, Blog & Public Discovery  
**Prioridade:** P2 — qualidade de indexação e descoberta orgânica  
**Estado:** DIAGNOSIS_CONFIRMED — IMPLEMENTATION_HANDOFF_READY — NOT_IMPLEMENTED

## Objetivo

Evitar que a geração de snapshots da Cutinapp publique páginas de descoberta sem eventos para períodos específicos como páginas indexáveis e sem conteúdo útil, preservando a indexação das páginas que realmente oferecem eventos.

## Área

SEO técnico diretamente ligado à aquisição orgânica; páginas públicas de descoberta por cidade e período; links internos; conteúdo de agenda.

## Oportunidade confirmada

No arquivo `scripts/generate-seo-snapshots.mjs` da `main` (blob `b94de8800be96b236faff3cc08539f986cab55fd`):

1. `applySeo()`, linhas 266–282, sempre injeta `<meta name="robots" content="index, follow, max-image-preview:large">`; não recebe uma diretiva por página.
2. `buildDiscoverySnapshot()`, linhas 635–655, aplica esse padrão a todas as páginas de descoberta.
3. Para cada cidade encontrada, o loop de linhas 745–760 gera sempre quatro rotas: `hoje`, `amanha`, `fim-de-semana` e `proximos-7-dias`.
4. Cada rota é gravada mesmo quando o filtro `eventMatchesPeriod()` retorna uma lista vazia.
5. `discoveryBody()`, linhas 627–633, renderiza uma lista vazia e a página da cidade sempre recebe links para hoje, amanhã e fim de semana, sem verificar se existem eventos nesses períodos.
6. `discoverySchema()` declara `ItemList` com `numberOfItems: events.length`, inclusive quando o valor é zero.

Resultado: uma cidade com eventos publicados em algum momento pode gerar até quatro snapshots temporais vazios em cada build. Esses snapshots recebem robots indexável, canonical próprio, ItemList vazio e podem ser descobertos pelos links internos da página da cidade.

**Limite da evidência:** confirmei a lógica no código. Não tive acesso ao Google Search Console nem provei que o Google já indexou URLs vazias. O risco é de geração/indexabilidade; não é uma afirmação de perda de ranking ou de indexação efetiva.

## Confirmado — prevenção de duplicidade

- A consulta de `orchestration/assignments/AUX-03/W2.md` mostra W2 em `AVAILABLE`, sem assignment de implementação ativo.
- O claim ativo genérico `claims/active/20261009-1600-AUX-03-W3.md` é de aquisição de produtores, não cobre geração de páginas de cidade/período.
- A entrega W3 de 07/11 sobre sequência pós-cadastro está concluída e trata lifecycle de produtores; não foi repetida.
- PR #692 está **merged** e trata a preservação de previews sociais de eventos encerrados. Esta entrega é distinta: páginas de descoberta temporal vazias.
- PRs #724–#727 seguem abertos/não integrados na consulta atual; #727 permanece draft. Não alterei landing, copy comercial, links Markdown do blog ou metadados de artistas.
- `CURRENT_STATE.md` e `PRIORITIES.md` ainda refletem uma consolidação antiga (30/10); os commits e worklogs recentes de 05–07/11 foram consultados para complementar o estado.

## Hipótese

Reduzir páginas temporais vazias indexáveis e links internos para esses destinos pode concentrar rastreamento e sinais internos nas páginas com inventário real, melhorar a precisão da promessa do snippet e evitar que visitantes cheguem a agendas sem resultados.

Não há baseline ou evidência de uplift de tráfego/conversão.

## Recomendação de implementação — encaminhamento ao owner do gerador compartilhado (W09)

Não alterei o gerador, pois o trabalho anterior de AUX-03 identificou W09 como owner do snapshot compartilhado. Solicito implementação coordenada pelo owner.

### 1. Permitir robots por snapshot

Alterar `applySeo()` para aceitar uma opção com default idêntico ao comportamento atual:

```js
const applySeo = (baseHtml, {
  title,
  description,
  canonical,
  image,
  imageAlt = "Cutinapp",
  jsonLd,
  body,
  robots = "index, follow, max-image-preview:large",
}) => {
  // ...
  html = replaceMeta(html, "robots", robots);
  // ...
};
```

### 2. Páginas temporais sem eventos

Em `buildDiscoverySnapshot()`, aplicar `noindex,follow` somente quando `city && period && events.length === 0`. Manter `index,follow` para páginas com pelo menos um evento real.

Para páginas vazias:
- descrição factual: `Não há eventos publicados para este período em {cidade}. Consulte a agenda completa na Cutinapp.`
- corpo com estado vazio legível e link para `/eventos/{cidade}`;
- não emitir ItemList vazio; manter BreadcrumbList;
- manter HTTP 200 e permitir rastreamento para que o crawler leia o noindex.

Não aplicar noindex indiscriminadamente à página principal de eventos, a páginas de cidade com inventário, eventos individuais, produções ou artistas.

### 3. Links internos condicionais

Calcular os conjuntos filtrados de cada período uma única vez. A página base `/eventos/{cidade}` deve linkar para hoje, amanhã e fim de semana somente quando o conjunto correspondente tiver pelo menos um evento.

Não deixar a página vazia criar ciclos de links para outros períodos vazios. O estado vazio deve oferecer retorno à página base da cidade.

### 4. Sitemap

Verificar o gerador de sitemap/refresh index separado. Se ele incluir URLs temporais vazias, excluí-las enquanto estiverem com noindex. Não bloquear esses caminhos em robots.txt: o crawler precisa acessar a página para descobrir a diretiva noindex.

### 5. Escopo preservado

- Não modificar o fluxo de snapshots históricos de eventos sociais coberto pelo PR #692.
- Não mudar o canonical das páginas com eventos.
- Não filtrar eventos históricos do arquivo público nesta tarefa.
- Não inventar eventos, cidades ou categorias.
- Não editar `SeoManager.js`, PR #727, blog ou perfil artístico.

## Copy pronta para estado vazio

**Título visual:** Nenhum evento publicado para este período.  
**Texto:** Não encontramos eventos publicados em {cidade} neste período. Consulte a agenda completa para ver outras datas e experiências disponíveis.  
**CTA:** Ver agenda completa de {cidade}.  
**Destino:** `/eventos/{citySlug}`.

## Canal, CTA e métricas

**Canal:** Google Search → landing de eventos por cidade/período → página de evento → detalhes/ingressos.

**CTA principal das páginas com inventário:** abrir um evento real da lista.  
**CTA de estado vazio:** Ver agenda completa de {cidade}.

**Métrica técnica de aceite:** zero snapshots temporais vazios com robots indexável.

**Métricas de negócio a acompanhar:**
- cliques em eventos / sessões das páginas de cidade;
- sessões orgânicas nas páginas de cidade com inventário;
- impressões, cliques e CTR no Search Console para rotas `/eventos/{cidade}/{período}`;
- visitas de páginas de evento originadas em páginas de cidade.

Baseline: N/D. Não houve acesso ao Search Console nem medição de conversões nesta execução.

## Critérios de aceite

- [ ] Cidade com evento hoje: página hoje indexável, ItemList com item real e link visível.
- [ ] Cidade sem evento hoje, mas com evento amanhã: página hoje noindex/follow e sem link a partir da página base; página amanhã indexável e linkada.
- [ ] Cidade sem eventos no fim de semana: página fim-de-semana noindex/follow, estado vazio útil e retorno à agenda da cidade.
- [ ] Página temporal vazia não publica ItemList com `numberOfItems: 0`.
- [ ] Páginas com eventos preservam title, description, canonical, OG e JSON-LD atuais.
- [ ] Páginas vazias permanecem rastreáveis; não bloquear em robots.txt.
- [ ] Sitemap não lista rotas temporais com noindex, caso essas rotas sejam incluídas pelo gerador.
- [ ] PR #692 / snapshots sociais de eventos encerrados não sofrem regressão.
- [ ] Testes cobrem cidade com zero, um e múltiplos eventos por período.
- [ ] Build e refresh SEO executados em fixture controlada e, após autorização, contra dados públicos.

## Próxima ação

W09 / owner do gerador compartilhado: implementar a diretiva robots configurável, o estado vazio e links condicionais; validar sitemap e snapshots. Conta principal: priorizar/autorizar a alteração se o owner compartilhado não tiver assignment vigente.

## Precisa da conta principal?

**SIM** — para coordenar o owner W09 e autorizar integração do gerador compartilhado. Nenhuma ação de VPS ou deploy foi realizada nesta entrega.

## Estado final

`DIAGNOSIS_CONFIRMED — HANDOFF_COMMITTED — PRODUCT_CODE_NOT_CHANGED — NO_BRANCH — NO_PRODUCT_PR — NOT_MERGED — NOT_DEPLOYED — GSC_NOT_ACCESSED — CONVERSION_NOT_MEASURED`.
