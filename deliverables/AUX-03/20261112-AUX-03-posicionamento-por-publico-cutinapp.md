# AUX-03 — Posicionamento por público na página pública da Cutinapp

**Data:** 12/11/2026 10:09 BRT  
**Prioridade:** P2 de conteúdo/UX; publicação condicionada ao gate P0 público  
**Estado:** COPY_READY — IMPLEMENTATION_PENDING_W3 — PUBLIC_RUNTIME_NO_GO

## Objetivo

Aumentar a clareza da página de produto da Cutinapp no site Peter Tecnet, deixando explícito que a plataforma atende quatro públicos — participantes, produtores, artistas e organizadores — sem criar outro artigo nem duplicar a infraestrutura SEO já existente.

## Área

Aquisição orgânica de marca, página institucional de produto, posicionamento, intenção de busca, conversão por público e distribuição.

## Confirmado — pesquisa e evidências

### 1. O domínio público da Cutinapp continua sem validação

- Em 12/11/2026, a consulta direta a `https://cutinapp.petertecnet.com.br/` retornou HTTP 530 nesta ferramenta.
- A issue P0 [#643](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643) continua aberta. Ela documenta divergência entre o SHA do release no filesystem da VPS e o SHA servido pelo Nginx/HTTPS.
- A consulta de busca `site:cutinapp.petertecnet.com.br` não retornou resultados nesta rodada. A busca exata por “Cutinapp” + “Peter Tecnet” retornou o perfil GitHub da organização, mas não uma página do domínio Cutinapp. Isso é um sinal de visibilidade insuficiente nesta consulta, não prova conclusiva de desindexação; não houve acesso ao Google Search Console.

### 2. A página de produto da Peter Tecnet já possui base SEO

No repositório `petertecnetdev/petertecnet.com.br`, confirmei:

- `src/seoEntities.js` já define title, description, headline, benefícios, intenções e FAQ da Cutinapp.
- Title atual: `Cutinapp | Eventos, ingressos, vendas e check-in por QR Code | Peter Tecnet`.
- Description atual explica publicação de eventos, venda de ingressos e itens, organização de participantes/promoters e check-in por QR Code.
- `scripts/generate-seo-pages.mjs` gera HTML estático para `/plataformas/cutinapp`, canonical, description, Open Graph, Twitter Cards e JSON-LD.
- `platformSchema()` já emite `SoftwareApplication`/`WebApplication`, `WebPage`, `BreadcrumbList` e `Product`, vinculando a aplicação à organização Peter Tecnet.
- O gerador inclui a página no sitemap.
- `platformBody()` usa atualmente o nome “Cutinapp” como H1 e exibe headline/description, benefícios, FAQ e CTAs genéricos “Acessar Cutinapp” e “Falar com a Peter Tecnet”. Não há seção explícita que separe a proposta para participantes, produtores, artistas e organizadores.

A rota pública `https://petertecnet.com.br/plataformas/cutinapp` abriu nesta consulta e expôs o título correto, mas a extração retornou apenas uma linha/imagem; não foi possível validar visualmente o conteúdo completo ou o mobile.

### 3. Google Business Profile — elegibilidade ainda não confirmada

A marca Metricool `cutinapp` (ID 7119630) apresenta apenas `gbpData` em `networksData`; não apresenta `instagramData`.

Para 13/10/2026–12/11/2026, a consulta Metricool retornou:
- métricas disponíveis de avaliações, visualizações de fotos/posts e cliques/ações: valores 0;
- nenhuma linha de palavras-chave;
- nenhuma linha de publicações do perfil.

Esses são dados retornados pelo conector, não uma verificação independente no painel do Google. Não há publicação agendada no Metricool consultado.

A política oficial do Google exige contato presencial com clientes durante o horário informado e lista marcas e negócios exclusivamente online entre os exemplos de perfis inelegíveis. Como não foi confirmado se a Peter Tecnet/Cutinapp recebe clientes presencialmente em uma unidade real ou presta atendimento presencial dentro das regras, não recomendo publicar ou otimizar o GBP até validar a elegibilidade.

Fonte oficial: https://support.google.com/business/answer/13763036?hl=pt-BR

## Hipótese

Uma seção explícita por público pode melhorar a compreensão imediata da oferta e aumentar a proporção de visitantes que escolhem o próximo passo correto. Não há teste A/B ou dados de conversão que comprovem uplift.

## Entregável — bloco editorial pronto para a página /plataformas/cutinapp

### Hero proposto

**Eyebrow:** PLATAFORMA DE EVENTOS PETER TECNET

**H1:** Descubra eventos. Compre ingressos. Viva experiências.

**Texto de apoio:**

A Cutinapp conecta participantes, produtores, artistas e organizadores em uma plataforma para descobrir eventos, divulgar produções, apresentar perfis artísticos e organizar a jornada do ingresso ao check-in.

**CTA primário:** Explorar eventos  
**Destino proposto:** `https://cutinapp.petertecnet.com.br/events`  
**Regra:** só ativar depois do GO público e da validação mobile.

**CTA secundário:** Cadastrar minha produção  
**Destino proposto:** `https://cutinapp.petertecnet.com.br/for-producers`  
**Regra:** só ativar depois do GO público e da integração/QA do fluxo de produtores. O texto coincide com o CTA previsto no PR #724, que permanece aberto/não integrado na consulta.

### Seção: Uma plataforma para quem participa e para quem movimenta eventos

**Participantes**  
Encontre eventos, consulte as informações da produção e acesse seus ingressos digitais em uma jornada conectada.

**Produtores**  
Apresente sua produção, publique eventos e organize ingressos, participantes e operação de entrada.

**Artistas**  
Tenha um perfil público para apresentar seu trabalho, compartilhar sua presença artística e conectar seu perfil às produções e eventos publicados.

**Organizadores**  
Organize a divulgação e a programação da produção, compartilhe páginas públicas e facilite o acesso do público às informações do evento.

### Fechamento

**Título:** Da descoberta ao check-in, uma experiência conectada.

**Texto:** A Cutinapp reúne páginas de eventos, ingressos digitais, participantes, perfis artísticos e validação de entrada por QR Code em uma plataforma da Peter Tecnet.

**CTA:** Conhecer a Cutinapp

### Direção de implementação

- Preservar o title, description, canonical, Open Graph, Twitter e JSON-LD existentes; eles já cobrem a entidade e a intenção principal.
- Substituir o H1 genérico “Cutinapp” pelo H1 proposto somente após revisão do owner W3.
- Inserir a seção de quatro públicos após os benefícios e antes do FAQ.
- Preservar o visual oficial e o layout mobile-first; cards empilhados em telas estreitas, sem carrossel horizontal obrigatório.
- Manter os CTAs externos desativados/sem destino público ativo até o gate de runtime.
- Não adicionar preço, trial, assinatura, gratuidade, taxa ou promessa comercial que não esteja validada contra a configuração vigente.
- Não duplicar FAQ, Schema.org, sitemap, página de confiança ou artigo comercial já existente.

## Canal

Busca de marca/termos comerciais → página de produto Peter Tecnet → rota pública Cutinapp → exploração de eventos ou cadastro de produção.

## CTA

- Participantes: **Explorar eventos**.
- Produtores: **Cadastrar minha produção**.
- Marca/empresa: **Conhecer a Cutinapp**.

Todos os destinos da Cutinapp dependem de GO público.

## Métricas

1. Impressões e cliques orgânicos para consultas de marca (“Cutinapp”, “Cutinapp Peter Tecnet”, “plataforma de eventos Cutinapp”) no Search Console.
2. Cliques da página Peter Tecnet para o domínio Cutinapp.
3. Cliques por CTA (participante vs. produtor).
4. Cadastros de produtores originados na página.
5. Primeiro evento publicado em até 7 dias após o cadastro.
6. Sessões de participantes que chegam à página de evento e iniciam checkout.

**Baseline:** N/D. Não houve acesso ao Search Console nem telemetria de CTA nesta execução.

## Próxima ação

1. Conta principal/infra resolver a issue P0 #643 e comprovar o mesmo SHA no filesystem, HTTP local do Nginx e HTTPS público.
2. W00 reconciliar a issue #643 em `BLOCKERS.md`; o arquivo consultado lista FIN-P0-001, mas não espelha este gate público P0.
3. W3 revisar e aplicar o bloco editorial em `src/seoEntities.js`/gerador, respeitando seu ownership e fluxo Git autorizado.
4. Conta principal validar a elegibilidade do Google Business Profile: existe unidade real que recebe clientes durante horários informados ou atendimento presencial recorrente que se enquadre nas regras? Se não, não usar GBP como canal da plataforma online.
5. Após GO, testar página Peter Tecnet e destinos Cutinapp em 320/360/390/430 px, verificar CTAs e medir os eventos de conversão.

## Precisa da conta principal?

**SIM** — para resolver o gate público, autorizar a revisão/integração W3 e confirmar a condição operacional que determina a elegibilidade do GBP.

## Limites desta entrega

Nenhum código foi alterado. Nenhuma publicação foi criada no GBP/Instagram. Nenhum post foi agendado. Nenhum artigo anterior foi duplicado. Nenhuma branch, PR, merge, build, deploy ou acesso à VPS foi realizado.
