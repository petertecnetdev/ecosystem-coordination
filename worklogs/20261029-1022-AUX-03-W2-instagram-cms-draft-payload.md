# AUX-03-W2 — Primeiro artigo: payload real do formulário CMS (29/10/2026)

owner: AUX-03-W2
date: 2026-10-29 10:22 America/Sao_Paulo
priority: P1 (liberação do funil) / P2 (publicação editorial)
status: CMS_DRAFT_PAYLOAD_COMMITTED — NOT_CREATED_IN_CMS — NOT_PUBLISHED — CONVERSION_NOT_MEASURED
area: SEO editorial, blog público, aquisição de produtores
channel: Google → /blog/como-divulgar-evento-no-instagram → /for-producers → cadastro → produção → primeiro evento

## Objetivo e oportunidade
Converter o artigo já escrito em 25/10 em um payload exato do formulário real do CMS, sem criar outro texto redundante nem presumir acesso à API/admin. A publicação continua condicionada à correção comercial da landing, links editoriais, inventário CMS e prova de visibilidade crawler.

## Coordenação consultada
- `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md` e `orchestration/STATE.md`.
- `orchestration/assignments/AUX-03/W2.md`: AVAILABLE, sem override W00.
- `claims/active/20261008-1600-AUX-03-W2-seo-public-discovery.md`, diretório de claims ativos e worklogs AUX-03 de 25–28/10.
- PRs #722, #724 e #725 em 29/10: OPEN, NOT_MERGED, mergeable=true. #722 pertence a W2; #724/#725 pertencem a W3. SEO técnico/crawler-visible pertence a W09.
- P0 financeiro continua de outro owner, sem duplicação.

## Confirmado
1. O frontend `src/pages/admin/AdminBlogPage.js` fornece formulário para title, slug, excerpt, content, category, tags, cover_image, seo_title, seo_description e status. O formulário obtém application_id pelo contexto `/admin/content`, filtra artigos da aplicação cutinapp e pode salvar rascunho.
2. `src/services/BlogService.js` usa `/admin/content` para criar/editar e `/admin/content/{id}/publish` para publicar. São operações autenticadas; não foram chamadas nesta execução.
3. O conteúdo fonte do artigo Instagram estava no deliverable de 25/10. A página pública na main ainda não renderiza links Markdown como links reais sem PR #722.
4. Site público /blog e landing não puderam ser inspecionados nesta execução (web indisponível/530); inventário do CMS e Search Console não verificados. Nenhuma URL foi declarada publicada.
5. Os PRs #722/#724/#725 estavam abertos e não integrados em 29/10. Nenhuma mudança de VPS.

## Trabalho realizado / entrega
Gerado e gravado em GitHub:
`deliverables/AUX-03/20261029-W2-instagram-article-cms-draft.json`

Commit: `e27eff30c7fbcec4527ace892a1b719137cb7e4a`

O arquivo contém os campos exatos usados pelo formulário (mais `type=article`), `status=draft` e `cover_image=null` até arte oficial aprovada. O corpo inclui **apenas o artigo**, sem metadados editoriais, checklist de publicação ou H1 duplicado. Não contém `application_id`: o formulário resolve o ID da Cutinapp no `adminContext`; **não** enviar o JSON diretamente ao endpoint sem completar esse campo e autenticar corretamente.

Pré-validação sintática/estrutural do payload: JSON válido; 4.582 caracteres / 695 palavras no corpo; 0 H1 no corpo (título vem do formulário); 8 H2; 1 link interno /for-producers; nenhuma seção de checklist editorial misturada; meta description com 139 caracteres. Não substitui validação no CMS/renderizador.

## Gate operacional de publicação
1. Conta principal/W00 revisar e integrar #722 e #724, após CI e QA mobile; W3 resolver #725 e sua jornada de ativação. Não fazer deploy automaticamente.
2. Editor autenticado abrir `AdminBlogPage`, verificar no inventário se slug ou intenção equivalente já existem. Se existir, **editar o existente** em vez de criar duplicata.
3. Se não existir, preencher o formulário com o JSON e salvar **somente como draft**. O formulário preenche application_id internamente; não colar o objeto JSON inteiro no campo de conteúdo.
4. Aprovar capa/OG 1200×630 usando a identidade oficial, validar copy, links, destino /for-producers e mobile 320/360/390/430.
5. Publicar via ação **Publicar** apenas depois dos gates. Confirmar URL final 200, canonical autorreferente, title/description próprios, conteúdo crawler-visible, Schema.org com datas reais e preview social. W09 recebe prova de HTML inicial.
6. Registrar URL, data, baseline de Search Console e funil. Não inserir links para artigos ainda não publicados.

## Hipótese, CTA e métricas
Hipótese: reduzir erros de transcrição/cadastro e duplicação editorial acelera a primeira publicação com maior consistência SEO; não existe evidência de impacto em tráfego/conversão.

CTA: **Conheça a Cutinapp para produtores** → `/for-producers` (ativar/distribuir apenas depois de validar oferta e rota).
Métrica de entrega: 1 artigo real publicado com HTTP 200 e metadata/CTA verificáveis (atual: 0 confirmado).
Métrica intermediária: cliques únicos artigo→landing / sessões do artigo.
Métrica de negócio: produtores atribuídos ao artigo que publicam o primeiro evento em até 30 dias.
Baseline: NÃO MEDIDO.

## Evidências
- https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261025-W2-artigo-divulgar-evento-instagram.md
- https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261029-W2-instagram-article-cms-draft.json
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/admin/AdminBlogPage.js
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/services/BlogService.js
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725

## Próxima ação e dependência
AUX-03-W2: conferir CMS após liberação e publicar/medir primeiro artigo, sem duplicar conteúdo.
Conta principal necessária: **SIM** — revisão/integração dos PRs, acesso editorial, aprovação da arte e validação da oferta.
W09: provar crawler-visible, canonical e Schema.org na URL final.
NEXT_ACTION: revisar PRs e criar rascunho no CMS com o payload validado; publicar somente após gates.
