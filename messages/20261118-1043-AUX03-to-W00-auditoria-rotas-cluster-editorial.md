# Handoff AUX-03-W2 → W00 — auditoria de rotas do cluster editorial

**Data:** 18/11/2026 10:43 BRT  
**Origem:** AUX-03-W2 — SEO, Blog & Public Discovery  
**Destino:** W00 / conta principal

## Resultado
Revisei os quatro guias editoriais existentes e comparei seus destinos internos com as rotas declaradas na main da Cutinapp.

Corrigi duas referências residuais a `/events` no guia de ingresso digital. O corpo do artigo já havia sido corrigido em 17/11; o bloco de mensuração e a nota de gate ainda estavam desatualizados. Ambos agora apontam para `/eventos`.

**Commit editorial:** `aa7e1493c8295bbffb4fe0abba46ff4bf726675d`  
**Arquivo atualizado:** https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261110-W2-guia-ingresso-digital-qr-code.md

## Confirmado
- src/App.js main declara /search, /for-producers, /artists, /artist/:slug, /cidades e /eventos.
- /events não está declarado; /eventos é a rota de descoberta pública.
- Os destinos dos guias de 11, 13 e 14/11 correspondem às rotas revisadas.
- O cluster não tem publicação ou indexação comprovadas.
- #643 permanece OPEN; #722 OPEN/NOT MERGED; #724 OPEN/NOT MERGED; #727 OPEN/DRAFT/NOT MERGED.
- CURRENT_STATE.md está consolidado em 30/10 e BLOCKERS.md não espelha a issue pública #643.

## Solicitações
1. W00: atualizar BLOCKERS.md para refletir #643 e coordenar o gate público.
2. Conta principal/Infra: resolver a divergência de release e comprovar o mesmo SHA no filesystem, HTTP local do Nginx e HTTPS.
3. W00/owner de #722: atualizar a branch atrás da main, repetir CI e integrar o renderizador de links editoriais após revisão.
4. Operador editorial autorizado: refletir /eventos no rascunho do CMS e devolver ID/URL efetivo.
5. AUX-03: executar QA mobile e medir artigo → evento → checkout somente após GO.

Nenhuma alteração de código de produto, merge, build, deploy ou acesso à VPS foi realizada.
