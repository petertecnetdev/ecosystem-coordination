# AUX-03 — Revisão de SEO da landing de produtores

**Data:** 23/11/2026 10:11 BRT  
**Objetivo:** melhorar a correspondência entre a landing `/for-producers` e buscas comerciais por plataforma de eventos e ingressos, sem introduzir promessas comerciais ou funcionalidades não confirmadas.  
**Área:** aquisição de produtores, SEO on-page, landing page e conversão.  
**Estado:** SEO_REVIEW_POSTED_TO_PR727 — WAITING_REVIEW — NOT_MERGED — NOT_PUBLISHED.

## 1. Confirmado

### Estado do trabalho existente
Consultei `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, os worklogs e os registros recentes de AUX-03. A consolidação de CURRENT_STATE/PRIORITIES continua datada de 30/10/2026; BLOCKERS.md contém FIN-P0-001, mas não espelha a issue #643 da Cutinapp. Não alterei arquivos de ownership do W00.

Verifiquei diretamente os PRs do frontend:
- **#724** — copy visível da landing alinhada ao modelo por transação; aberto.
- **#727** — title, meta description e JSON-LD da landing; aberto.
- **#722** — links editoriais clicáveis; aberto.
- **#726** — CTA prioritário no onboarding; aberto.

O PR #727 depende do #724 ou do mesmo release para evitar que metadados e copy visível comuniquem ofertas diferentes.

### Busca pública
Em 23/11/2026, consultei resultados para:
- `site:cutinapp.petertecnet.com.br`
- `Cutinapp eventos ingressos`
- `Cutinapp Peter Tecnet`

A consulta não retornou páginas da Cutinapp entre os resultados apresentados. Isso é um sinal de visibilidade fraca nesta consulta, **não prova de desindexação**.

A abertura direta de `https://cutinapp.petertecnet.com.br/` retornou HTTP 530 pela ferramenta de consulta. A rota `/for-producers` também não pôde ser aberta. Isso impede validar o snippet/runtime público nesta execução e não comprova indisponibilidade universal.

### Referências de SERP
As páginas abaixo usam explicitamente linguagem de plataforma de ingressos/venda de ingressos para produtores:
- https://appticket.com.br/
- https://tikat.com.br/
- https://www.tiketa.com.br/produtores

Foram usadas apenas para observar a linguagem de busca e o enquadramento da oferta; não foram copiadas alegações, preços ou funcionalidades.

## 2. Oportunidade

O title proposto no PR #727 — “Plataforma para produtores de eventos | Cutinapp” — descreve o público, mas não explicita a intenção de consideração “plataforma de eventos e ingressos”.

A landing pode manter o foco em produtores e, ao mesmo tempo, cobrir a expressão comercial usada por quem compara soluções de venda de ingressos.

## 3. Recomendação editorial

### Title proposto — 60 caracteres
`Plataforma de eventos e ingressos para produtores | Cutinapp`

### Meta description proposta — 144 caracteres
`Crie sua produção, publique eventos, venda ingressos e organize participantes. Sem assinatura obrigatória; taxas por transação podem se aplicar.`

### Regras de consistência
- Manter o CTA visível “Cadastrar minha produção”, conforme PR #724.
- Manter no texto visível a ressalva de taxas por transação e do meio de pagamento.
- Não inserir preços, percentuais, prazos de repasse, garantias de venda ou meios de pagamento sem confirmação comercial atual.
- Manter title, description, conteúdo visível e JSON-LD coerentes.
- Confirmar canonical e URL final no runtime; não assumir que o caminho do CMS ou a URL canônica proposta estão publicados.
- Não adicionar FAQPage ou outros dados estruturados sem conteúdo correspondente visível e elegível.

## 4. Trabalho realizado

- Revisei os estados e dependências dos PRs #722, #724, #727 e #726.
- Comparei o title atual do PR #727 com a linguagem observada em resultados de busca do segmento.
- Redigi uma alternativa específica de title e meta description, mantendo a oferta comercial confirmada no PR.
- Publiquei comentário editorial no PR #727 para revisão do owner, sem alterar código, branch ou PR.
- Registrei a dependência de release com o PR #724.
- Não criei novo artigo, para não aumentar o backlog editorial enquanto os conteúdos existentes aguardam publicação.
- Não publiquei, agendei, contatei produtores, fiz merge, build, deploy ou acesso à VPS.

## 5. Entregável e evidência

- **Comentário no PR #727:** https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727#issuecomment-7102233714
- **PR #727:** https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- **PR #724:** https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- **Issue #643:** https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643

## 6. Hipótese

Um title que inclua “eventos e ingressos” pode corresponder melhor às buscas de consideração por plataforma de venda de ingressos e tornar o resultado mais claro para produtores. Não há dados de Search Console que comprovem uplift de posição, impressões ou CTR.

## 7. Canal, CTA e métrica

- **Canal:** Google Search → landing pública de produtores.
- **CTA:** “Cadastrar minha produção” (definido no PR #724; ainda não validado publicamente).
- **Métrica primária:** primeiros eventos publicados por produtores originados da busca orgânica na landing.
- **Métricas intermediárias:** impressões, CTR, sessões orgânicas na landing, cliques no CTA e cadastros iniciados.
- **Baseline:** N/D. Search Console e Analytics não foram consultados nesta execução.

## 8. Próxima ação

1. Owner do PR #727 avaliar a sugestão de title/description.
2. Integrar #724 e #727 no mesmo release ou em sequência coordenada.
3. Resolver a issue #643 e validar que o runtime público serve o release esperado.
4. Conferir title, description, canonical, JSON-LD e CTA em mobile.
5. Após publicação, consultar Search Console e registrar baseline de impressões/CTR; não declarar ganho antes dos dados.

## 9. Precisa da conta principal

**SIM** — revisão/aceite da copy comercial, coordenação do release e validação pública após resolver #643.

## 10. Estado operacional

- Pesquisa e revisão editorial: concluídas.
- Comentário no PR: publicado.
- Código/branch: sem alterações.
- Merge/build/deploy: não realizados.
- VPS: não acessada.
- Publicação/indexação: não comprovadas.

`SEO_REVIEW_POSTED_TO_PR727 — WAITING_OWNER_REVIEW — PR724_DEPENDENCY — ISSUE643_OPEN — NOT_MERGED — NOT_PUBLISHED`.
