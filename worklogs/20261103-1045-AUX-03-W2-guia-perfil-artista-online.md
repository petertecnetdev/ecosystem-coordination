# AUX-03 W2 — Worklog 2026-11-03 10:45 BRT

## Objetivo
Criar um ativo editorial novo para aquisição orgânica de artistas e formações, levando buscas sobre perfil artístico online a uma ação de ativação verificável na Cutinapp.

## Área
SEO editorial, blog, descoberta pública de artistas, aquisição e ativação de artistas.

## Oportunidade
Os materiais AUX-03 imediatamente anteriores cobrem aquisição de produtores (Reel sobre primeiro evento e pesquisa por Stories), organização de participantes e segurança na compra de ingressos. Não encontrei artigo AUX-03 recente dedicado à identidade pública de artistas. O código da main já oferece perfis artísticos públicos, compartilhamento, links oficiais, agenda de eventos e fluxo de ativação/reivindicação. Isso permite um conteúdo novo baseado em capacidades existentes, sem inventar eventos ou provas sociais.

## Coordenação consultada
- Consultei CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims/README.md, claims/active/, claims/completed/, worklogs recentes, deliverables/AUX-03, orchestration/STATE.md, WORKER_REGISTRY.md e assignments/AUX-03/W1-W3.
- CURRENT_STATE.md ainda tem última consolidação global em 30/10; complementei com worklogs recentes de 01–03/11 e leitura direta dos PRs.
- AUX-03 W2 estava AVAILABLE, sem assignment W00 ativo. O claim AUX-03-W2 de 02/11 continua pendente de Lighthouse e integração do PR #724; este novo conteúdo tem escopo distinto: aquisição de artistas, não alteração da landing de produtores.
- PRs #722, #724, #725 e #726 permanecem abertos e sem merge na consulta de 03/11. PR #727 permanece aberto em draft. Não alterei nenhum desses PRs.
- A homepage pública foi aberta pelo crawler apenas com o shell “Ative o JavaScript para usar a Cutinapp”; /for-producers não pôde ser aberta pela ferramenta de pesquisa. Isso não prova indisponibilidade geral nem ausência de indexação. Não usei eventos específicos porque não havia inventário público verificável nesta execução.

## Confirmado — evidências funcionais na main consultada
- App.js declara /artists e /artist/:slug como rotas públicas e /artist/onboarding como rota protegida.
- ArtistViewPage.js exibe nome artístico, tipo, bio, gêneros, cidade, métricas, eventos futuros confirmados, histórico, links oficiais (site, YouTube, Instagram, Spotify), botão de seguir e compartilhamento nativo/cópia de link.
- ArtistOnboardingPage.js permite pesquisar perfil existente e solicitar reivindicação com evidência; para perfil novo, a ativação inicial solicita nome artístico, gênero/categoria e apresentação curta.
- ArtistOnboardingPage.js informa que a identidade artística não depende de uma produção e que verificação é um estado separado.
- ArtistViewPage.js mantém convites pendentes separados; a própria interface informa que só entram no line-up público depois da confirmação.
- ArtistManagePage.js contém campos para tipo de artista, bio, cidade/UF, gêneros, Instagram, YouTube, Spotify, site, foto e capa.
- protectedRoute em App.js exige usuário autenticado e e-mail verificado para /artist/onboarding; LoginFormComponent preserva o destino e oferece link para criar conta.

## Trabalho realizado
- Mapeei o fluxo real de ativação, reivindicação, edição, visualização pública e compartilhamento.
- Escolhi intenção de busca nova: “perfil artístico online”, com variações “perfil de artista”, “perfil de banda” e “divulgar agenda de shows”. Volume e dificuldade de busca não foram medidos; a prioridade é uma hipótese editorial baseada na aderência à funcionalidade.
- Produzi artigo completo, title, meta description, slug, canonical proposto, categoria, resumo, headings, recomendações de BlogPosting, links internos e gate de publicação.
- Incluí carrossel de seis cards, legenda e três Stories para distribuição do mesmo tema, sem repetir a pesquisa de produtores ou os Reels anteriores.
- Expliquei a diferença entre ativação, reivindicação, vínculo e verificação. Não prometi que toda formação pode ser criada livremente por qualquer usuário: criação de formações pode depender de curadoria.
- Não criei branch nem alterei código de produto, CMS, Instagram ou VPS.

## Entregável
- Artigo + pacote social: deliverables/AUX-03/20261103-W2-guia-perfil-artista-online.md
- Commit: b387b13bd9a1c313e30eb633136c816a14d8a53d

## Canal e CTA
- **Canal:** Google/blog → /artists → /artist/onboarding → perfil público → compartilhamento em Instagram, WhatsApp e portfólio.
- **CTA:** “Ativar meu perfil artístico”.
- **Destino:** /artist/onboarding.
- **Condição:** login e e-mail verificado; usuário sem conta pode seguir pelo fluxo de criação oferecido na tela de login.

## Métricas
- Intermediária: cliques únicos no CTA / sessões do artigo.
- Ativação: perfis artísticos ativados / cliques qualificados no CTA.
- Qualidade: perfis com bio, gênero, foto/capa e pelo menos um link oficial / perfis ativados.
- Distribuição: compartilhamentos do perfil / perfis ativos.
- Resultado: participações confirmadas em eventos / perfis artísticos ativos.
- Baseline: N/D. Os eventos analíticos específicos e a atribuição UTM após login não foram validados; não declarar conversões medidas.

## Evidências
- App routes: src/App.js, main SHA 6db85d5f80c14acd2ed185ebf9e4afa535e14288.
- Public artist profile: src/pages/artist/ArtistViewPage.js, main SHA 0b1f2d82f7d8b9120c2df8c3c6660d0ade642864.
- Artist onboarding: src/pages/artist/ArtistOnboardingPage.js, main SHA bb2d108316393668e745e1dd532971db53a6a785.
- Artist profile editor: src/pages/artist/ArtistManagePage.js, main SHA retornado pelo fetch da execução.
- SEO routes: src/components/SeoManager.js, main SHA 14216dcf98e6fb27cb02a52ba33b46230fae4eb4.
- Recent coordination: worklogs/20261103-1007-AUX-03-W1-story-pesquisa-produtores.md; deliverables/AUX-03/20261103-W1-story-pesquisa-produtores.md.
- Pull request states read directly on 03/11: #722 OPEN, #724 OPEN, #725 OPEN, #726 OPEN, #727 OPEN/DRAFT; all NOT_MERGED.
- Deliverable commit: b387b13bd9a1c313e30eb633136c816a14d8a53d.

## Próxima ação
1. Conta principal/editorial: conferir se o CMS já contém artigo equivalente; cadastrar este material como draft se não houver duplicidade.
2. Definir URL final e imagem Open Graph original com identidade oficial; preencher datas e publisher apenas com valores reais do CMS.
3. Validar o CTA em smartphone: login → criar conta, se necessário → verificar e-mail → retornar a /artist/onboarding → ativar perfil.
4. Publicar somente após confirmar conteúdo, canonical, metadados e crawler-visible no URL final.
5. Depois da publicação, medir sessões, cliques, ativações e perfis completados. Se a indexação de perfis de artista continuar dependente de renderização client-side, encaminhar melhoria de metadados/crawler ao owner W09, sem editar sua área.

## Precisa da conta principal?
SIM — acesso ao CMS para verificar duplicidade/cadastrar draft e aprovação/publicação; QA do fluxo real de cadastro/verificação e da URL pública.

## Estado final
ARTICLE_READY — SOCIAL_COPY_READY — COMMITTED_TO_COORDINATION — NOT_IN_CMS — NOT_PUBLISHED — NOT_INDEXED — CONVERSION_NOT_MEASURED — NO_PRODUCT_CODE_CHANGED — NO_VPS_CHANGE.
