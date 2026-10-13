# AUX-03-W2 — Recuperação de links editoriais e conversão do blog — 2026-10-13

agent: AUX-03-W2
area: SEO editorial / blog / aquisição orgânica de produtores
priority: P1
repository: petertecnetdev/cutinapp.petertecnet.com.br
claim: claims/active/20261008-1600-AUX-03-W2-seo-public-discovery.md
status: PATCH_READY_NOT_COMMITTED_NOT_PUBLISHED

## Objetivo e oportunidade
Remover o bloqueio de conversão de artigos: o componente src/pages/blog/BlogArticlePage.js na main interpreta **negrito**, mas não converte [texto](/for-producers) em links clicáveis. Isso prejudica a navegação contextual para a landing de produtores.

## Coordenação consultada
CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, orchestration/assignments/AUX-03/W2.md (AVAILABLE), claims/active/, worklogs de 11 e 12/10 e plano CUTINAPP_COLD_START_GROWTH.md. Não duplicar trabalho W09 de snapshots, canonical, Schema.org, sitemap, OG, indexação global nem claim W03 de listagens públicas.

## Evidências
- Em 2026-10-13, src/pages/blog/BlogArticlePage.js na main ainda possui InlineText que divide apenas **negrito** e devolve os demais tokens como texto.
- A branch anterior feat/blog-internal-links-seo, antes relatada com dois commits, agora retorna 404 / não consta na busca de branches. Nenhum PR foi encontrado pela busca "blog internal links".
- Criada branch feat/aux03-blog-editorial-links-20261013 a partir de main; ela não recebeu alterações.
- Tentativa de update_file na branch foi bloqueada por verificações de segurança da ferramenta. Não houve commit, PR, merge, CI ou deploy.
- Site /blog, /for-producers, /robots.txt e /sitemap.xml não puderam ser acessados pelo navegador de pesquisa nesta execução; indexação e runtime não confirmados.

## Entrega concreta
Patch local 20261013-AUX-03-W2-blog-links.patch e teste 20261013-AUX-03-W2-blog-links-test.js preparados e disponibilizados ao usuário.
A mudança reconhece links Markdown internos (React Router), externos HTTPS/HTTP (noopener noreferrer) e não converte protocolos perigosos em links. Mantém negrito. Testes cobrem navegação, segurança e regressão. O patch passou git apply --check e git apply em fixture de contexto, mas não em clone real; testes Jest e build não executados.

## Canal, CTA e métrica
Canal: artigos públicos do blog.
CTA: "Conheça a Cutinapp para produtores" -> /for-producers.
Métrica principal: cliques únicos do artigo para /for-producers / sessões do artigo, com instrumentação válida.
Métricas de resultado: cadastros concluídos e primeiro evento publicado atribuíveis à origem editorial.
Hipótese: links contextuais clicáveis reduzem atrito e aumentam avanço ao cadastro; sem medição ainda.

## Próxima ação
1. Aplicar patch à branch criada ou outra branch autorizada, rodar Jest/build, abrir PR e integrar após revisão.
2. Verificar landing comercial (promessas de assinatura/trial anteriormente sinalizadas) antes de levar tráfego.
3. Conferir duplicação no CMS dos artigos prontos de 11 e 12/10; publicar somente após links, HTML indexável e QA.
4. Validar URL, canonical, title, description, headings, OG, BlogPosting, links internos e mobile na página publicada.
5. Instrumentar CTA e medir conversão.

## Conta principal
SIM: aplicação/integração do patch se escrita permanecer bloqueada; publicação editorial, QA e validação de oferta. Não executar pull/build/deploy na VPS por padrão.
