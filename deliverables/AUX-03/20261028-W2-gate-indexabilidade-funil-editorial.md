# AUX-03-W2 — Gate P1 de descoberta orgânica antes da publicação editorial (28/10/2026)

**Owner:** AUX-03-W2  
**Status:** DIAGNOSTIC_ACTIONABLE — PUBLICATION_BLOCKED_PENDING_RUNTIME_PROOF  
**Área:** SEO editorial, páginas públicas e aquisição de produtores  
**Canal:** Google → artigo → landing de produtores → cadastro → primeiro evento  
**Prioridade:** P1 para prova de indexabilidade/CTA; P2 para expandir novos artigos.

## Decisão desta execução

**Não produzir mais um artigo sem verificar se os quatro ativos preparados chegam ao leitor e ao crawler.** Há conteúdos preparados em 25, 26 e 27/10, mas nenhum teve publicação no CMS ou indexação comprovada. O PR #722 (links editoriais) e o #724 (copy comercial) continuam sendo gates de revisão/integração; o #725 pertence ao W3. O SEO técnico/crawler-visible é escopo do W09; este documento fornece um critério de aceite editorial e handoff, não toma a implementação do W09.

## Confirmado em 28/10/2026

1. A abertura da home pública pela ferramenta web retornou apenas o texto **“Ative o JavaScript para usar a Cutinapp.”** (fonte: https://cutinapp.petertecnet.com.br/). Isso prova apenas a visão obtida por esse cliente sem renderização JavaScript, **não prova que o Google não renderiza nem que a página está desindexada**.
2. As tentativas de abrir `/blog`, `/for-producers`, `/sitemap.xml` e `/robots.txt` pela mesma ferramenta falharam com erro de acesso. Isso **não comprova** HTTP 404/5xx no navegador real; o status HTTP final e o HTML inicial permanecem **não verificados**.
3. Na `main` consultada do frontend, `public/index.html` contém title, description, canonical e OG genéricos **da home**, inclusive `canonical=https://cutinapp.petertecnet.com.br/`. A página `src/pages/blog/BlogArticlePage.js` busca artigo via cliente e define title/description/canonical no `document.head` após obter `entry`. Portanto, **é necessário demonstrar** que o HTML efetivamente servido para cada artigo apresenta metadados próprios e conteúdo útil a um crawler sem depender de interação. Não assumir que a `main` é a versão em produção.
4. A `main` consultada de `src/pages/ProducerLandingPage.js` ainda anuncia trial/assinatura de 30 dias. A correção pertence ao PR #724/W3 e não deve ser contornada por copy editorial com alegações comerciais não verificadas.
5. Inventário real do CMS, Search Console, URLs de artigos publicadas, sessões, cliques e primeiras publicações **não verificados**. Nenhum evento, preço ou cidade foi inventado.

**Evidências de código:**  
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/public/index.html  
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/blog/BlogArticlePage.js  
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/ProducerLandingPage.js  
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722  
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724  

## Ação concreta P1 — matriz de aceite de publicação (responsáveis W09 + conta principal)

| URL | Intenção | Requisito de HTML inicial / publicação | Responsável |
| --- | --- | --- | --- |
| `/` | marca e descoberta | 200, canonical da home, identidade oficial, links de navegação reais | W09/QA |
| `/for-producers` | aquisição de produtores | 200, title/description/canonical **da landing**, H1 e CTA coerentes com modelo comercial; nenhuma promessa de trial sem lastro | W3 + W09 |
| `/blog` | navegação editorial | 200, cards de artigos **publicados** com `<a href>` navegáveis e títulos próprios; não listar rascunhos | W09 + editor |
| `/blog/como-divulgar-evento-no-instagram` | artigo de alta intenção | **somente após publicação real:** 200, canonical autorreferente, title, description, um H1, texto principal legível e links para destinos 200 | W09 + AUX-03-W2 |

**Critério de rejeição:** se o HTML inicial da URL de artigo contiver apenas shell JS ou canonical da home, marcar **P1 BLOCKED / CRAWLER_VISIBILITY_UNPROVEN**, encaminhar a W09 com request/response e **não declarar artigo indexável nem divulgar como aquisição Google**. É aceitável renderização posterior para experiência, mas deve existir evidência de que o conteúdo e metadata da URL são acessíveis ao mecanismo de busca. A indexação final só pode ser confirmada com ferramentas de inspeção do mecanismo de busca.

### Comandos de evidência para executar em ambiente com rede (não executados nesta entrega)

```bash
for path in / /for-producers /blog; do
  echo "=== $path ==="
  curl -sS -L --max-time 20 -D /tmp/cutinapp-headers.txt \
    "https://cutinapp.petertecnet.com.br$path" \
    -o /tmp/cutinapp-page.html
  head -n 12 /tmp/cutinapp-headers.txt
  grep -Eio '<title>[^<]*</title>|<link[^>]*rel="canonical"[^>]*>|<meta[^>]*name="description"[^>]*>' \
    /tmp/cutinapp-page.html | head -n 8
  grep -Eio '<h1[^>]*>[^<]*|Ative o JavaScript para usar a Cutinapp' \
    /tmp/cutinapp-page.html | head -n 4
done
```

Executar a mesma coleta para o slug do artigo **apenas depois de verificar sua publicação real**. Salvar cabeçalhos, trecho do HTML, data, commit servido, captura mobile 320/360/390/430 e resultado de URL Inspection. Não registrar cookies/tokens ou dados pessoais no worklog.

## Copy de landing pronta para revisão de W3 (não implementada)

- **SEO title sugerido:** Plataforma para produtores de eventos | Cutinapp
- **Description sugerida:** Organize e publique eventos, gerencie ingressos e acompanhe a operação em uma página conectada à sua produção. Conheça a Cutinapp para produtores.
- **H1 atual na main:** Publique, venda e opere seu evento em um fluxo só.
- **Canonical esperado:** `https://cutinapp.petertecnet.com.br/for-producers` (validar URL final real).
- **OG:** usar título e descrição coerentes com a landing servida; imagem aprovada da identidade oficial, sem improvisar logo ou flyer.
- **CTA comercial condicionado:** **Cadastrar minha produção** → fluxo real de cadastro/produção, após #724/#725 validados. Evitar alegações de trial, assinatura, preços, taxas ou gratuidade até confirmação.

## Ordem de execução e owner

1. **Conta principal / W00:** revisar #722 e #724; solicitar evidência de QA/CI/mobile e integrar se aprovados. W3 é dono de #724/#725.
2. **W09:** validar URL por URL no HTML servido (title, description, canonical, OG, Schema.org, texto e links), sitemap/robots e Search Console. Resolver a camada de crawler sem criar páginas vazias de cidade/categoria.
3. **AUX-03-W2 + editor:** consultar inventário CMS por slug/intenção; publicar primeiro o artigo Instagram já pronto (25/10) **apenas quando gates estiverem satisfeitos**. Inserir link interno somente para URLs reais com 200.
4. **AUX-03-W2:** capturar baseline após publicação e acompanhar aquisição; não declarar uplift sem dados.

## Hipótese, CTA e métricas

**Hipótese:** corrigir o percurso público e disponibilizar conteúdo próprio da URL a crawlers e leitores é pré-condição para converter artigos em aquisição orgânica; o efeito sobre rankings e cadastros permanece não medido.

**CTA:** Cadastrar minha produção → `/for-producers` e fluxo de cadastro validado.

**Métricas:** (1) número de artigos com URL 200 e metadata/corpo verificáveis no HTML servido; (2) sessões orgânicas por URL; (3) CTR de clique único artigo→landing = visitantes únicos que clicaram / sessões do artigo na mesma janela, com deduplicação explícita; (4) produtores atribuídos que publicam primeiro evento em até 30 dias. **Baseline atual: indisponível.**

**Conta principal necessária:** SIM — aprovação/merge, CMS, QA e evidência Search Console.  
**NEXT_ACTION:** W09/conta principal produzir prova por URL de HTML crawler-visible + oferta corrigida; AUX-03 publicar primeiro artigo validado e medir.
