# Handoff AUX-03-W2 → W00 — liberar publicação do cluster editorial

**Data:** 15/11/2026 09:50 BRT  
**Prioridade:** P1 editorial, bloqueada por P0 runtime  
**Status:** ACTION_REQUIRED

## Entrega concluída por W2
O plano de publicação e interlinking dos quatro artigos AUX-03 já preparados está em:
`deliverables/AUX-03/20261115-AUX-03-publicacao-cluster-conteudo-cutinapp.md`.

Ordem recomendada:
1. Check-in QR para produtores.
2. Line-up para produtores/artistas.
3. Descoberta de eventos para participantes.
4. Ingresso digital QR para participantes.

Não criar artigos duplicados; converter os existentes em rascunhos/publicações com IDs e URLs verificáveis.

## Bloqueios confirmados
1. **Issue #643 OPEN:** Nginx/HTTPS serve SHA diferente do release no filesystem. Não liberar tráfego nem declarar runtime GO até comprovação de SHA público.
2. **PR #722 OPEN:** links Markdown continuam não clicáveis na main. O PR contém parser seguro, mas sua branch está atrás da main. Últimos runs registrados no PR passaram; atualizar a branch e repetir checks antes de integrar.
3. **PR #724 OPEN + PR #727 OPEN:** alinhar copy visível e metadados da landing de produtores na mesma liberação. Os jobs Validate e Lighthouse de #727 (41459268768 e 41459268813) foram reconsultados e estão SUCCESS; isso não equivale a merge.
4. **CMS:** nenhum ID de rascunho/publicação foi verificado para os quatro artigos.
5. **Search Console:** sem acesso nesta execução; indexação não comprovada.

## Ações solicitadas
- W00/conta principal: resolver #643 e coordenar revisão/integração de #722, #724 e #727.
- W09: validar snapshots/HTML inicial do blog, canonical, OG e BlogPosting.
- Operador editorial autorizado: criar rascunhos, retornar ID/URL de cada artigo e confirmar slug/canonical antes de publicar.
- AUX-03-W2: executar QA editorial/SEO após GO.

## CTA e métrica
Produtor: “Cadastrar minha produção” em `/for-producers`, após GO.
Participante: “Explorar eventos” em `/eventos`, após GO.
Métrica principal: produtores originados pelo conteúdo que publicam o primeiro evento em até 7 dias. Baseline N/D.

## Limites
Nenhum código de produto, branch, merge, build, deploy, VPS, CMS ou post social foi alterado por este handoff.
