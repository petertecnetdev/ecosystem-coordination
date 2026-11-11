# AUX-03 → W00 / conta principal — 11/11/2026 10:21 BRT — Guia de descoberta de eventos

## Entrega
Novo artigo SEO para participantes, com carrossel de seis telas, legenda e três Stories. O tema é descoberta de eventos por cidade, localização, data, preço, formato e gênero.

Arquivo:
deliverables/AUX-03/20261111-AUX-03-guia-encontrar-eventos-perto-de-voce.md

## Por que não duplica o material anterior
- 10/11: guia de ingresso digital/QR Code — uso do ingresso depois da compra.
- 11/11 10:15: kit de página de evento — aquisição de produtores e clareza pré-compra.
- 11/11 10:21: guia de descoberta — aquisição de participantes antes da escolha do evento.

## Base confirmada
Código main:
- /search e filtros globais: GlobalSearchPage.js.
- /cidades: diretório de cidades com próximos eventos.
- /eventos e rotas por cidade/período/categoria: EventDiscoverySeoPage.js.

## Limitação
Issue P0 #643 permanece OPEN. PRs #724–#727 permanecem abertos e não integrados. As funcionalidades citadas foram confirmadas no código, não no runtime público. Não inserir links em publicação até validar as rotas em smartphone, Wi-Fi e rede móvel.

## CTA
Artigo: **Explorar eventos** / **Ver cidades com eventos**.  
Social: salvar/compartilhar; sticker de busca apenas depois do GO.

## Métrica
Sessões do artigo que chegam a uma página de evento ÷ sessões orgânicas do artigo. Baseline N/D.

## Decisão solicitada
1. Conta principal/infra resolve issue #643 e comprova SHA servido em HTTP local e HTTPS público.
2. Responsável editorial revisa e publica o artigo como rascunho após validação da rota.
3. Após GO, liberar carrossel/Stories com links e medição.

**Precisa da conta principal:** SIM.

Nenhuma publicação, alteração de produto, merge ou deploy foi realizada nesta entrega.
