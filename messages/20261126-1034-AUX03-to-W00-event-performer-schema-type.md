# Handoff AUX-03 → W00 — 26/11/2026

## Objetivo
Encaminhar a correção do Schema.org runtime de eventos para ownership apropriado, preservando a frente W09 de snapshots.

## Confirmado
- Issue #729 criada: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/729
- `src/utils/eventSeo.js` classifica todos os performers como `MusicGroup`.
- `ArtistViewPage.js` reconhece seis tipos de artista.
- W09 possui claim ativo sobre o gerador de snapshots; não houve edição desse arquivo.
- #728 permanece aberta, sem comentários/aceite visível.
- #643 permanece aberta e bloqueia validação pública.
- #636 está CLAIMED por `cutinapp-growth-producer`; #637 permanece no escopo de atribuição first-touch; nenhum dos dois foi alterado.

## Solicitação
1. Definir owner para #729, restrita a `src/utils/eventSeo.js`.
2. Manter a correção do snapshot de 16/11 e a issue #728 dentro do ownership W09, sem duplicar gerador.
3. Após implementação, exigir testes para `solo`, `band`, `duo`, `group`, `collective`, `orchestra` e fallback desconhecido.
4. Com runtime GO, validar JSON-LD em páginas públicas e acompanhar GSC.

## Impacto e medição
Canal: Google → evento público → ingressos.
CTA: Ver ingressos e detalhes do evento.
Métricas: impressões/cliques/CTR por URL de evento, `event_detail_viewed`, `event_ticket_intent_clicked` e início de checkout.
Baseline N/D.

## Limites
AUX-03 não alterou código, não criou branch/PR de produto, não fez merge/build/deploy e não acessou VPS.
