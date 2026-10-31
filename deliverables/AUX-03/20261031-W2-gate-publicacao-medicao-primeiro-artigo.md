# AUX-03 — Gate de publicação e medição do primeiro artigo (31/10/2026)

## Objetivo e área
Converter o rascunho existente “Como divulgar um evento no Instagram e atrair participantes” em um ativo público mensurável de aquisição de produtores, sem duplicar conteúdo. Área: SEO editorial, landing comercial, links internos e ativação.

## Evidências confirmadas
- O payload editorial está preparado em `deliverables/AUX-03/20261029-W2-instagram-article-cms-draft.json`; não é evidência de cadastro no CMS.
- PRs Cutinapp #722 (links editoriais), #724 (oferta comercial) e #725 (ativação) permanecem **open/unmerged** na consulta de 31/10.
- Não há ID de artigo, URL pública nem conversão atribuída verificados nesta execução.
- Claims existentes AUX-03-W2 e AUX-03-W3: não alterar escopos de outros responsáveis.
- A prioridade P1 inclui landing, indexação de páginas comerciais e conversão.

## Entregável: checklist de publicação com critérios de aceite (P1)
1. **Inventário:** operador autorizado busca slug `como-divulgar-evento-no-instagram` no CMS antes de criar. Se já existir, revisar o registro em vez de duplicar. Registrar ID, status e URL canônica.
2. **Oferta:** revisar/validar PR #724; não publicar CTA com promessas de assinatura, trial ou taxas não confirmadas. Usar texto neutro `Conheça a Cutinapp para produtores` enquanto oferta não for validada.
3. **Destino:** confirmar no navegador mobile a landing `/for-producers`, formulário e fluxo até criação do primeiro evento. Não considerar visita à landing como conversão final.
4. **Artigo:** publicar somente após revisão humana, revisão de imagens oficiais e checagem do corpo Markdown/HTML; H1 único, título específico, meta description fiel, links internos reais, canonical absoluto próprio, robots index/follow se elegível.
5. **Social:** Open Graph/Twitter com título, descrição, imagem oficial com URL absoluta e preview em WhatsApp/Instagram; evitar imagem inventada.
6. **Indexação:** testar HTTP 200, HTML renderizado e conteúdo principal visível ao Google, canonical consistente, ausência de noindex indevido, sitemap e Search Console (inspeção URL). Schema `BlogPosting` com data/autor reais; `Event` apenas em páginas de eventos reais com dados verificados.
7. **Links internos:** artigo → `/for-producers`; landing → artigo somente quando útil; artigos relacionados → artigo somente se publicados. Não inserir links para slugs inexistentes.
8. **Mobile-first:** QA manual 320/360/390/430px, CTA visível, contraste, ausência de scroll horizontal, link clicável e carregamento aceitável.
9. **Distribuição:** só após URL pública confirmada, reutilizar o pacote de 30/10 para Reel, carrossel e Stories, com identidade visual oficial.

## Mensuração — definição operacional
- **CTA primário:** Conheça a Cutinapp para produtores → `/for-producers`.
- **Evento intermediário:** `editorial_producer_cta_click`, propriedades `article_slug`, `cta_position`, `destination`, `utm_source`, `utm_medium`, `utm_campaign`; sem dados pessoais.
- **Métrica intermediária:** usuários únicos com clique CTA / usuários únicos que visualizaram artigo; janela de 7 dias.
- **Métrica de negócio:** produtores que publicaram primeiro evento em até 30 dias após origem no artigo / produtores cadastrados atribuídos ao artigo. Documentar modelo de atribuição e deduplicar.
- **UTM sugerida para social:** `utm_source=instagram&utm_medium=organic_social&utm_campaign=guia_divulgacao_evento_202610&utm_content=reel` (variar `utm_content` por story/carrossel).
- **Baseline:** não medido; não anunciar crescimento sem telemetria real.

## Hipótese
O conteúdo educativo de alta intenção, conectado a uma landing comercial verdadeira e a um onboarding funcional, pode gerar mais primeiras publicações do que posts sem destino claro. Testar; não assumir resultado.

## Próxima ação / owner
Conta principal + operador editorial autorizado: revisar #722/#724, consultar duplicidade no CMS, criar/validar rascunho e devolver ID/URL. AUX-03: conferir QA SEO/mobile, acionar distribuição apenas após publicação e acompanhar funil. **Conta principal necessária: SIM.** Sem merge/deploy/VPS nesta entrega.
