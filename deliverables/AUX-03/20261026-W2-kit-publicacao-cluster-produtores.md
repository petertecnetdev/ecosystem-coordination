# AUX-03-W2 — Kit de publicação e links internos: cluster de aquisição de produtores

Data: 2026-10-26
Owner: AUX-03-W2
Status: EDITORIAL_PACKAGE_READY — NOT_PUBLISHED — NOT_DEPLOYED
Prioridade: P1 (desbloqueio de conversão) / P2 (expansão editorial)
Canal: blog público, busca orgânica, navegação interna e landing /for-producers
Objetivo: transformar três artigos já preparados em um percurso editorial mensurável até a primeira publicação de evento, sem criar outro rascunho redundante.

## Evidência e limites
- Fonte de verdade consultada: CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, orchestration/assignments/AUX-03/W2.md, claims/active/20261008-1600-AUX-03-W2-seo-public-discovery.md e worklogs recentes.
- Artigo completo de Instagram de 25/10 disponível em deliverables/AUX-03/20261025-W2-artigo-divulgar-evento-instagram.md. Os artigos de 11/10 e 12/10 são conhecidos por worklogs; seus corpos completos não foram recuperados nesta execução.
- PR #722 (links Markdown): OPEN, ready for review, mergeable=true, NOT_MERGED (consulta 26/10).
- PR #724 (copy comercial landing): OPEN, ready for review, mergeable=true, NOT_MERGED (consulta 26/10).
- PR #725 (retorno do cadastro produtor autenticado): OPEN, DRAFT, mergeable=true, NOT_MERGED (consulta 26/10); pertence ao W3.
- Na main consultada, src/pages/blog/BlogArticlePage.js ainda exibe links Markdown como texto; metadata title/description/canonical/BlogPosting é criada no navegador depois do carregamento do artigo. Não há evidência de indexação crawler-visible ou de runtime atualizado.
- A main consultada de src/pages/ProducerLandingPage.js ainda anuncia trial e assinatura. NÃO publicar CTAs de campanha para a landing até integrar e verificar a correção #724.
- O site público e o inventário do CMS não foram acessíveis; nenhuma URL de artigo é declarada publicada. Não existem dados de tráfego/conversão verificados.
- Escopo de implementação de prerender/sitemap/Schema.org permanece com W09; este kit é editorial e de publicação, sem reivindicar alterações técnicas de W09.

## Cluster editorial reutilizando ativos existentes

| Papel | Consulta / intenção | Slug proposto (não publicado) | Origem | Próxima ação |
|---|---|---|---|---|
| Decisão | como escolher plataforma para vender ingressos online | /blog/como-escolher-plataforma-vender-ingressos-online | worklog 11/10 | localizar corpo completo, checar CMS e revisão |
| Planejamento | como calcular preço de ingresso de evento | /blog/como-calcular-preco-ingresso-evento | worklog 12/10 | localizar corpo completo, validar fórmulas e checar CMS |
| Distribuição | como divulgar evento no Instagram | /blog/como-divulgar-evento-no-instagram | deliverable 25/10 | pronto para revisão CMS/OG/mobile |
| Conversão | produtor quer publicar primeiro evento | /for-producers | landing existente; PR #724 | validar copy comercial e CTA |

Nenhuma estimativa de volume de busca foi medida. Não criar páginas de cidade sem inventário real suficiente.

## Entrega 1 — inserções editoriais prontas (ativar SOMENTE após URLs publicadas)

### No artigo Instagram, inserir depois de “Meça ações, não apenas visualizações”
> Se o seu evento tem ingressos pagos, a divulgação também precisa levar a uma oferta clara. Antes de anunciar, [revise como calcular o preço do ingresso](/blog/como-calcular-preco-ingresso-evento) e confira se custos, taxas e lotes estão explicados ao participante.

Condição: publicar somente quando o artigo de preço existir e retornar 200 com canonical correto. Caso contrário, omitir o parágrafo.

### No artigo de precificação, inserir próximo ao checklist final
> Definir o valor é uma etapa; escolher como publicar e vender também faz diferença. Compare os critérios de [uma plataforma para vender ingressos online](/blog/como-escolher-plataforma-vender-ingressos-online) antes de abrir as vendas.

Condição: usar somente depois de validar a publicação do artigo de escolha de plataforma.

### No artigo de escolha de plataforma, inserir na seção sobre divulgação/alcance
> Depois de publicar a página do evento, organize a distribuição. Veja um [roteiro prático para divulgar o evento no Instagram](/blog/como-divulgar-evento-no-instagram), com Reels, Stories e um destino claro para o interessado.

Condição: usar somente depois de validar a publicação do artigo Instagram.

### CTA comercial uniforme para os três artigos
> Vai organizar seu próximo evento? [Conheça a Cutinapp para produtores](/for-producers) e veja como começar pela sua produção.

Condição obrigatória: PR #724 integrado e oferta comercial validada em runtime. Não mencionar trial, assinatura, gratuidade, taxas específicas ou promessas de resultado sem confirmação.

## Entrega 2 — pacote CMS pronto para o artigo Instagram

- H1: Como divulgar um evento no Instagram e atrair participantes
- Slug: como-divulgar-evento-no-instagram
- SEO title: Como divulgar um evento no Instagram | Cutinapp
- Meta description: Aprenda a divulgar seu evento no Instagram com Reels, Stories, link claro e uma rotina simples para transformar interesse em participantes.
- Excerpt/listagem: Um guia prático para planejar Reels e Stories, organizar informações e levar interessados até a página do evento.
- Categoria: Divulgação de eventos
- Tags propostas: divulgação de eventos; Instagram; Reels; Stories; produtores de eventos
- Canonical PROPOSTO: https://cutinapp.petertecnet.com.br/blog/como-divulgar-evento-no-instagram
- OG: type=article; title e description acima; url=canonical; imagem 1200x630 somente depois de asset original aprovado com logo oficial; não reutilizar logo improvisada.
- Schema.org: BlogPosting; headline/description/author ou publisher válidos, datePublished e dateModified REAIS, imagem real quando disponível. Evitar FAQPage artificial.
- H1 é fornecido pelo campo título da página; não duplicar H1 no corpo.
- Corpo editorial: deliverables/AUX-03/20261025-W2-artigo-divulgar-evento-instagram.md (seção entre delimitadores). Não copiar metadata e checklist para dentro do conteúdo do CMS.

## Entrega 3 — navegação e descoberta pública

- /blog: quando o CMS tiver os três artigos publicados, usar cartões com títulos claros e excerpt específico, sem prometer artigos inexistentes.
- Link de /blog para /for-producers: apenas quando a oferta #724 estiver correta e o CTA for testado no celular.
- Em artigos: 1 CTA comercial contextual + até 2 links editoriais relevantes. Não inserir links para slugs ainda não publicados.
- Produções, artistas e eventos reais: somente vincular quando houver entidade pública verificada e autorização; não inventar evento, preço, data, endereço, depoimento ou avaliação.
- Categorias e cidades: somente abrir página indexável se houver conjunto real de conteúdo e intenção de busca distinta; evitar páginas vazias/duplicadas.

## Gate operacional de publicação (sequência)

1. Revisão principal dos PRs #722 e #724; integrar conforme QA/CI. PR #725 continua sob W3, sem interferência deste worker.
2. Confirmar versão realmente servida da landing, ausência de promessa indevida de trial/assinatura e CTA funcionando em 320/360/390/430 px.
3. Conferir inventário de artigos no CMS (slug/título/intenção) antes de cadastrar. Se existir artigo equivalente, atualizar o existente em vez de duplicar.
4. Publicar primeiro o artigo Instagram (conteúdo completo disponível), com imagem OG oficial e data real. Confirmar resposta 200, canonical autorreferente, title, description, um H1, headings e links clicáveis.
5. Verificar HTML inicial/crawler: title, description, canonical, OG, BlogPosting e corpo relevante devem ser observáveis por crawler no ambiente servido. Se apenas client-side, encaminhar evidência ao owner W09; não declarar indexado.
6. Publicar os dois artigos complementares somente depois de recuperar/revisar seus corpos e verificar CMS. Inserir os três links cruzados apenas após 200/QA.
7. Submeter URL final ao mecanismo de indexação/Search Console quando houver acesso; registrar data de publicação, URL final e primeiro baseline real. Não interpretar ausência de resultado em pesquisa site: como prova de não indexação.

## Métrica, CTA e teste de hipótese

- CTA: Conheça a Cutinapp para produtores → /for-producers.
- Métrica de entrada: sessões orgânicas por URL de artigo, segmentadas por source/medium quando instrumentadas.
- Métrica intermediária: CTR artigo→landing = cliques únicos no CTA / sessões do artigo (definir janela e deduplicação).
- Métrica de ativação: produtores com primeiro evento publicado atribuível ao artigo / produtores cadastrados atribuíveis ao artigo, em 30 dias (somente com consentimento/atribuição válida).
- Métrica de negócio: primeiros eventos publicados atribuídos ao cluster; não confundir cadastro com ativação.
- Eventos analíticos PROPOSTOS (não confirmados): blog_article_view, blog_producer_cta_click, producer_signup_completed, producer_first_event_published. Reutilizar eventos existentes antes de criar novos.
- Hipótese: links editoriais contextualizados + CTA comercial coerente reduzem abandono entre leitura e ativação. Sem uplift medido.

## Próxima ação / dono

AUX-03-W2: acompanhar revisão do PR #722, preparar publicação editorial após gates, registrar URLs e primeiras métricas reais.
AUX-03-W3: owner da landing #724 e jornada #725.
W09: owner de SEO técnico/crawler-visible.
Conta principal: SIM — revisar/integrar PRs, liberar CMS, aprovar imagem/identidade e validar publicação.
Estado final: PACKAGE_COMMITTED quando confirmado no GitHub; ARTICLE_NOT_PUBLISHED; PRS_NOT_MERGED; RUNTIME_NOT_VERIFIED.
