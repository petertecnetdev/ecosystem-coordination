# AUX-03-W2 — SEO editorial de intenção comercial — 2026-10-11

agent: AUX-03-W2
display_name: AUX-03 SEO & Public Discovery
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO editorial / aquisição de produtores
status: DRAFT_READY_NOT_PUBLISHED
claim: claims/active/20261008-1600-AUX-03-W2-seo-public-discovery.md

## Objetivo
Atrair produtores pesquisando como escolher uma plataforma para vender ingressos online, conectando o artigo à landing /for-producers.

## Coordenação e evidências
- Consultados COMMANDS.md, CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims/active/ e inbox AUX-03/W2.md (AVAILABLE).
- Branch existente feat/blog-internal-links-seo comparada com main: ahead 2, behind 0, arquivos BlogArticlePage.js e BlogArticlePage.test.js.
- Tentativa de PR draft para a branch existente bloqueada por verificações de segurança da ferramenta. Nenhum merge/deploy realizado.
- Página src/pages/ProducerLandingPage.js em main ainda anuncia trial de 30 dias e assinatura; evitar reproduzir essa promessa em conteúdo novo. Correção anterior em branch separada aguarda integração.

## Entregável
Rascunho original em Markdown: 'Como escolher uma plataforma para vender ingressos online', slug 'como-escolher-plataforma-vender-ingressos-online', 878 palavras, foco em taxas, checkout mobile, emissão, check-in, página pública e recorrência. Conteúdo preparado no artefato da execução; não cadastrado no Admin Blog nem publicado. Links internos planejados: /for-producers, /event e /productions. Antes da publicação, confirmar inventário editorial e regras comerciais atuais.

## CTA e métricas
CTA: 'Conheça a Cutinapp para produtores' → /for-producers.
Métrica primária: cliques qualificados do artigo para /for-producers.
Secundárias: cadastro concluído e primeiro evento publicado (dependem de atribuição válida).
Hipótese: artigo de comparação com critérios verificáveis gera tráfego mais próximo de decisão do que conteúdo puramente institucional; sem resultado medido.

## Próxima ação
1. Revisar artigo para evitar duplicação no CMS e validar informações comerciais.
2. Destravar PR de links Markdown e rodar CI antes de merge.
3. Publicar só depois de conferir HTML inicial indexável e destino do CTA; W09 mantém ownership de snapshots SEO.
4. Instrumentar clique editorial→landing e medir conversão.

## Conta principal
Necessária para revisar/integrar branch e validar publicação. Sem gasto, sem deploy VPS, sem afirmação de resultado.
