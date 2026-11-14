# Handoff AUX-03 → W00 / W09 — Guia SEO de line-up e revisão de performer

**Data:** 14/11/2026 10:23 BRT  
**Origem:** AUX-03 — SEO, Blog & Public Discovery  
**Destino:** W00 (coordenação) e W09 (SEO compartilhado)

## Entrega editorial
Novo artigo evergreen pronto para revisão:
`deliverables/AUX-03/20261114-AUX-03-guia-lineup-artistas-divulgacao.md`

Tema: **Como organizar e divulgar o line-up de um evento**.

O material inclui title, meta description, slug, canonical proposto, headings, artigo completo, mapa de links internos, carrossel, Reel, Stories, CTA e métrica.

Não duplica os artigos anteriores sobre página de evento, check-in QR, ingresso digital, busca por eventos ou divulgação no Instagram. Também não repete a prospecção Funclube/Noite Infame de 13–14/11.

## Ação solicitada a W09 — SEO de evento
Na main, `src/utils/eventSeo.js` já cria `performer` no JSON-LD, mas a função `eventPerformers` serializa todos os artistas como `MusicGroup`.

A main também distingue tipos de perfil em `src/pages/artist/ArtistViewPage.js`: `solo`, `band`, `duo`, `group`, `collective`, `orchestra`.

**Revisão recomendada:**
1. Mapear artista `solo` como `Person`.
2. Mapear banda/duo/grupo/coletivo/orquestra para tipo de grupo apropriado.
3. Confirmar que apenas artistas publicamente confirmados entram no JSON-LD.
4. Confirmar consistência entre `response.event.artists` usado no SEO e o endpoint público `/events/public/:slug/artists` que alimenta a seção visual.
5. Validar JSON-LD e Rich Results Test depois de o runtime estar acessível.

Referência oficial Google: https://developers.google.com/search/docs/appearance/structured-data/event — `performer` aceita `Person` ou `PerformingGroup`; a página de evento deve ter URL própria e focar em um evento.

AUX-03 não alterou `eventSeo.js`, não criou branch e não assumiu ownership de W09.

## Ação solicitada a W00 / conta principal
- Resolver issue P0 #643 e comprovar a mesma release por HTTP e HTTPS.
- Coordenar revisão/integração do PR #722 e dos PRs #724–#727.
- Confirmar operador editorial para cadastrar o artigo como rascunho.
- Aprovar publicação social e garantir resposta ao Direct se a palavra LINE-UP for usada.

## Gates
- O artigo está pronto, mas **não publicado**.
- Não inserir CTA clicável para `/for-producers` antes do GO do runtime e integração da oferta.
- Não afirmar que eventos reais estão disponíveis: nenhum evento público da própria Cutinapp foi validado nesta execução.
- Metricool: marca Cutinapp tem GBP, sem `instagramData`; agenda de 14 a 21/11 vazia.
- Sem código de produto, branch, PR, merge, build, deploy ou VPS.

## Métrica e continuidade
Métrica principal: produtores qualificados originados pelo artigo que publicam o primeiro evento em até 30 dias / produtores qualificados originados pelo artigo.

Após GO:
1. cadastrar rascunho;
2. validar links, canonical, OG e schema;
3. publicar;
4. distribuir carrossel/Reel/Stories;
5. medir sessões orgânicas → CTA → produtor qualificado → primeiro evento publicado.

**Precisa da conta principal:** SIM.
