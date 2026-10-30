# AUX-03-W2 — Distribuição orgânica do primeiro artigo (30/10/2026)

owner: AUX-03-W2
date: 2026-10-30 America/Sao_Paulo
priority: P1 (gates de aquisição) / P2 (distribuição)
status: DELIVERABLE_COMMITTED_VERIFIED — NOT_POSTED — NOT_PUBLISHED — CONVERSION_NOT_MEASURED
area: SEO editorial, blog, Instagram, aquisição de produtores
channel: Reels/Carrossel/Stories/WhatsApp autorizado → artigo → /for-producers → primeiro evento

## Objetivo
Transformar o artigo já escrito e formatado para CMS em um pacote de distribuição orgânica pronto para publicação após os gates, sem criar outro artigo não publicado nem duplicar trabalho técnico de W09 ou landing de W3.

## Coordenação e evidências consultadas
- `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `orchestration/STATE.md`, `orchestration/assignments/AUX-03/W2.md`, `claims/active/20261008-1600-AUX-03-W2-seo-public-discovery.md`.
- Worklog de 29/10 e kit editorial de 26/10, diagnóstico de 28/10, artigo original de 25/10 e JSON CMS de 29/10.
- PR #722, #724 e #725 consultados em 30/10: OPEN, NOT_MERGED, mergeable=true. #722 é W2; #724/#725 são W3.
- Tentativa de consulta pública `/blog` via web em 30/10 não acessível; não permite afirmar que o site está indisponível ou que o artigo está indexado.

## Confirmado — trabalho realizado
- Produzido kit de distribuição com roteiro completo de Reel (20–25s), carrossel de 6 cards, 3 Stories, mensagem opcional de WhatsApp com consentimento, legendas prontas, CTAs e parâmetros UTM propostos.
- Especificadas restrições de identidade visual oficial, acessibilidade mobile, ausência de fatos/eventos inventados, não enviar mensagens sem consentimento, canonical sem UTM e medição D+7/D+30.
- O kit contém placeholders obrigatórios para URL real: **nenhum link ou post foi publicado**.
- Entregável gravado no GitHub e recuperado para validação de integridade (seções A/B/C/D, gates, métricas, placeholders).

## Entregável e commit
`deliverables/AUX-03/20261030-W2-distribuicao-organica-artigo-instagram.md`
commit: `021a618c3b47c60f12892e651f99a25e944ac115`
url: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261030-W2-distribuicao-organica-artigo-instagram.md

## Oportunidade, hipótese e recomendação
**Oportunidade:** o artigo Instagram já está em payload CMS, mas sem prova de publicação. Em vez de aumentar o estoque de artigos não publicados, preparar distribuição concreta que começa no dia em que a URL estiver verificada.
**Hipótese:** Reel/carrossel/Stories educativos levam produtores ao guia e aumentam avanço para a landing, mas sem dados ainda.
**Recomendação:** priorizar aprovação e publicação do artigo existente; não divulgar URLs propostas ou landing com oferta desatualizada.

## CTA e métrica
- CTA social: **Leia o guia completo** → URL real do artigo, somente após HTTP 200/QA.
- CTA comercial no artigo: **Conheça a Cutinapp para produtores** → `/for-producers`, condicionado ao PR #724 validado.
- Métrica intermediária: cliques únicos artigo→landing / sessões do artigo, com deduplicação e período definidos.
- Métrica de negócio: produtores atribuídos ao artigo que publicaram primeiro evento em até 30 dias.
- Baseline: NÃO MEDIDO. Conteúdo publicado: 0 confirmado. Posts publicados: 0.

## Evidências e próximos responsáveis
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261029-W2-instagram-article-cms-draft.json

**NEXT_ACTION:** conta principal/W00 revisar e integrar #722/#724 após CI e QA; W3 resolver #725; editor validar inventário CMS, cadastrar/publicar o artigo e obter URL real; W09 verificar crawler-visible; AUX-03-W2 substituir placeholders, distribuir peças aprovadas e medir.
**Conta principal necessária:** SIM — integração, aprovação editorial/visual, acesso CMS e autorização de postagem.
**VPS:** nenhuma alteração.
