# AUX-03 W2 — Sitemap dinâmico para páginas públicas da Cutinapp

**Data:** 2026-11-20 10:37 BRT  
**Worker:** AUX-03-W2 — SEO, Blog & Public Discovery  
**Prioridade:** P2 — descoberta orgânica e cobertura de URLs públicas  
**Estado:** CODE_GAP_CONFIRMED — IMPLEMENTATION_SPEC_READY — HANDOFF_W09 — NOT_IMPLEMENTED

## 1. Objetivo

Fazer o sitemap da Cutinapp representar o inventário público realmente gerado pelo build: eventos, produções, artigos publicados, artistas públicos e páginas de descoberta elegíveis. O sitemap deve refletir URLs canônicas e indexáveis, sem incluir páginas privadas, vazias, noindex ou rotas sem conteúdo.

## 2. Área e oportunidade

SEO ligado diretamente à aquisição orgânica, páginas públicas, descoberta de eventos, produtores e artistas.

A main já gera snapshots HTML para entidades e rotas públicas dinâmicas, mas o sitemap versionado continua limitado às páginas institucionais principais. O inventário dinâmico pode ser encontrado por links internos, porém não é enumerado no sitemap atual.

**Esta entrega é complementar, não uma repetição, de dois handoffs anteriores:**
- 07/11: páginas cidade/período sem eventos devem receber noindex e não aparecer no sitemap.
- 08/11: snapshots e compartilhamento da rota /agenda/:slug, que depende de aceite W09.

O escopo de hoje é a geração de um sitemap que acompanhe os snapshots públicos indexáveis já produzidos. Não reabre as regras de agenda nem a correção de páginas temporais vazias.

## 3. Confirmado — evidência na main

Repositório: petertecnetdev/cutinapp.petertecnet.com.br  
Branch: main  
SHA da referência consultada: 6db85d5f80c14acd2ed185ebf9e4afa535e14288  
Gerador: b94de8800be96b236faff3cc08539f986cab55fd  
Sitemap: 2b64332876a613f354de221264eb5dfbe0bbb53a  
Validador: d7364471440b4675074efd5445ee3df14a844009

### 3.1 Sitemap estático

public/sitemap.xml contém apenas sete URLs:
- /
- /for-producers
- /eventos
- /event
- /productions
- /artists
- /blog

Não há entradas dinâmicas para eventos, produções, artigos individuais, artistas individuais, cidades, períodos ou categorias.

### 3.2 Snapshots dinâmicos já gerados

Em scripts/generate-seo-snapshots.mjs:
- linhas 675–692: carrega inventários públicos de eventos, produções, artigos e artistas;
- linhas 694–719: escreve snapshots de eventos, produções, artigos e artistas;
- linhas 721–730: também escreve snapshots de perfis e itens de evento;
- linhas 733–789: escreve descoberta global, páginas por cidade, período e categoria;
- linhas 790–793: grava apenas o marcador .cutinapp-seo-snapshots com contagens.

O fluxo termina sem escrever sitemap dinâmico. A existência de snapshots não equivale a inclusão dessas URLs no sitemap.

### 3.3 Validador atual

scripts/check-seo-indexability.mjs:
- declara seis rotas comerciais core em CORE_PUBLIC_PATHS (linha 7);
- valida formato, origem, duplicidade, query/hash e prefixos privados das URLs presentes;
- verifica presença das rotas core (linhas 34–62).

Não há teste de paridade entre snapshots gerados e sitemap, nem fixture que confirme a inclusão/exclusão de URLs dinâmicas conforme sua elegibilidade.

### 3.4 Limites da evidência

- Confirmado no código: o sitemap versionado é estático e não enumera o inventário dinâmico.
- Não confirmado: quantas páginas dinâmicas existem hoje no build ou na produção.
- Não confirmado: quais dessas URLs já foram descobertas ou indexadas pelo Google.
- Search Console não foi consultado nesta execução.
- A abertura pública de /sitemap.xml não pôde ser validada pelo navegador de pesquisa; não declarar runtime validado.

## 4. Hipótese

A ausência de URLs dinâmicas no sitemap pode reduzir a facilidade de descoberta e atualização de páginas comerciais em um site com inventário variável. Os links internos ainda podem permitir que o Google encontre essas páginas, portanto não se afirma que estejam fora do índice ou sofrendo perda mensurada.

## 5. Recomendação de implementação — handoff ao owner W09

O arquivo scripts/generate-seo-snapshots.mjs é compartilhado e possui ownership de SEO global/W09. AUX-03-W2 não altera o gerador nem transfere ownership. W09 deve aceitar o escopo antes de editar.

### 5.1 Uma fonte de verdade

Durante o mesmo build que produz os snapshots, construir uma coleção explícita de URLs indexáveis a partir dos mesmos dados e das mesmas regras de elegibilidade usadas para escrever cada snapshot.

Não reconstruir o inventário por scraping nem manter uma lista manual de slugs.

Proposta de grupos:
1. Core: preservar as URLs institucionais/comerciais atuais.
2. Eventos: somente eventos públicos com slug/canonical válidos e aprovados pela política de indexação.
3. Produções: somente perfis públicos elegíveis, sem dados privados.
4. Blog: somente artigos com status === "published" e conteúdo válido.
5. Artistas: somente perfis publicados e elegíveis, sem convites pendentes.
6. Descoberta: /eventos, cidades, períodos e categorias apenas quando a página for elegível e tiver conteúdo público real.
7. Agendas: somente depois de W09 implementar e aceitar o snapshot de /agenda/:slug e sua regra de elegibilidade.

### 5.2 Exclusões obrigatórias

- URLs com noindex.
- Páginas temporais de cidade sem eventos, conforme handoff de 07/11.
- Perfis privados /profile/:id (prefixo atualmente bloqueado em robots).
- Dashboards, autenticação, checkout, gestão e rotas privadas.
- Convites pendentes, rascunhos, conteúdo não publicado e dados não públicos.
- Itens de comércio/evento até existir uma decisão explícita de indexação para esse tipo de página.
- Agendas sem snapshot e sem regra de elegibilidade aprovada.

Não usar robots.txt para tentar canonicalizar. O sitemap deve listar somente a URL canônica desejada e deve concordar com o rel=canonical do snapshot.

### 5.3 XML e manutenção

- Gerar em BUILD_DIR/sitemap.xml depois da geração dos snapshots, preservando o caminho raiz esperado por robots.txt.
- Usar URLs absolutas HTTPS do host canônico https://cutinapp.petertecnet.com.br.
- Escapar caracteres XML e codificar UTF-8.
- Deduplicar por URL canônica; não incluir query nem fragmento.
- Incluir lastmod somente quando houver timestamp real e confiável de alteração significativa (updated_at/data equivalente). Não usar generated_at como se fosse modificação do conteúdo.
- Manter ordem estável para reduzir diffs desnecessários.
- Se o inventário exceder 50.000 URLs ou 50 MB descompactados por arquivo, dividir em sitemaps e criar sitemap index.
- Manter robots.txt apontando para o sitemap index ou sitemap raiz correto.

### 5.4 Testes e aceite

1. Fixture com evento, produção, artigo publicado, artista publicado e cidade com eventos: todas as URLs elegíveis aparecem uma vez.
2. Artigo em rascunho, artista não publicado, perfil privado e item não autorizado: não aparecem.
3. Cidade/período vazio ou noindex: não aparece, preservando o handoff de 07/11.
4. Toda URL do sitemap usa o host canônico, HTTPS, sem query/hash e com canonical equivalente no snapshot.
5. Nenhuma URL privada, duplicada, sem snapshot ou com noindex entra no sitemap.
6. Toda rota core atual permanece presente.
7. XML passa em parser; sitemap index funciona quando os limites forem excedidos.
8. npm run smoke:seo-indexability cobre as URLs dinâmicas por fixture/manifest, além das rotas core.
9. npm run smoke:seo-global e npm run smoke:seo-generator-global continuam verdes.
10. Build de produção contém build/sitemap.xml final e robots.txt continua apontando para ele.

### 5.5 Métricas após publicação

- URLs enviadas no sitemap por tipo.
- URLs válidas/descobertas/indexadas no relatório de Sitemaps e Indexação de páginas do Search Console.
- Impressões, cliques e CTR para páginas de evento, produção, artista e artigo.
- Sessões orgânicas que chegam a páginas de evento.
- Cliques de evento → início de checkout, quando a atribuição existir.

Não interpretar “URL enviada” como “URL indexada”; sitemap é uma indicação de descoberta, não garantia de rastreamento ou indexação.

## 6. Canal, CTA e conversão

**Canal:** Google Search → páginas públicas de eventos, produções, artistas e artigos → descoberta de eventos → página do evento.

**CTA de participante:** Ver evento e ingressos, conforme disponibilidade real mostrada na página.

**CTA de produtor:** Conhecer a Cutinapp para produtores / Cadastrar minha produção, somente quando o runtime e a landing receberem GO.

**Métrica principal:** cliques orgânicos para páginas de evento a partir de impressões de URLs dinâmicas.

**Métrica de negócio:** sessões orgânicas que iniciam checkout e, quando a atribuição estiver disponível, compras concluídas.

**Baseline:** N/D; Search Console não consultado nesta execução.

## 7. Referências

- Gerador: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/generate-seo-snapshots.mjs
- Sitemap: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/public/sitemap.xml
- Validador: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/check-seo-indexability.mjs
- Handoff W2 de páginas temporais vazias (07/11): https://github.com/petertecnetdev/ecosystem-coordination/blob/main/messages/20261107-1054-AUX03-W2-to-W09-empty-city-period-indexability.md
- Especificação W2 de agendas públicas (08/11): https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261108-W2-public-production-agenda-discovery-seo.md
- Google Search Central — sitemaps: https://developers.google.com/search/docs/crawling-indexing/sitemaps/overview
- Google Search Central — criação/submissão: https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap
- Google Search Central — canonical: https://developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls
- Google Search Central — sitemap index e limites: https://developers.google.com/search/docs/crawling-indexing/sitemaps/large-sitemaps

## 8. Próxima ação

1. W09 revisar e aceitar/recusar formalmente a geração de sitemap dinâmico no gerador compartilhado.
2. Se aceito, W09 implementar no mesmo fluxo dos snapshots e ampliar o smoke de indexabilidade.
3. W00 coordenar a dependência com os handoffs de agendas e páginas temporais vazias, sem duplicar implementação.
4. Conta principal/operador com acesso ao Search Console submeter o sitemap após o runtime receber GO e registrar o relatório inicial.
5. AUX-03 comparar URLs enviadas, descobertas e indexadas e medir cliques orgânicos → evento.

## 9. Limites desta execução

- Diagnóstico e especificação concluídos.
- Nenhum código do produto alterado.
- Nenhuma branch ou PR de produto criada.
- Nenhum merge, build, deploy ou acesso à VPS.
- Nenhuma publicação editorial/social.
- Nenhuma consulta ao Search Console.

**Precisa da conta principal:** SIM — coordenar W09, autorizar a integração e disponibilizar Search Console para a validação pós-publicação.

**Estado final:** DYNAMIC_SITEMAP_GAP_CONFIRMED — SPEC_READY — HANDOFF_W09_W00 — NO_PRODUCT_CODE_CHANGED — NOT_BUILT — NOT_DEPLOYED — NOT_INDEXED_VERIFIED.
