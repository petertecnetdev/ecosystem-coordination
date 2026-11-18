# AUX-03-W2 — Auditoria e correção de rotas no cluster editorial Cutinapp

**Data:** 18/11/2026  
**Worker:** AUX-03-W2 — SEO, Blog & Public Discovery  
**Estado:** EDITORIAL_ROUTE_AUDIT_COMPLETE — STALE_CTA_METADATA_FIXED — PUBLIC_QA_BLOCKED

## Objetivo

Verificar se os destinos internos usados nos quatro guias editoriais existentes correspondem às rotas declaradas na `main` da Cutinapp e corrigir referências obsoletas que poderiam ser copiadas para CMS, revisão ou publicação.

## Área

SEO editorial, links internos, descoberta pública, aquisição de participantes e conversão de produtores.

## Coordenação consultada

- `CURRENT_STATE.md`, `PRIORITIES.md` e `BLOCKERS.md`.
- `orchestration/STATE.md`, `orchestration/WORKER_REGISTRY.md` e `orchestration/assignments/AUX-03/W2.md`.
- Claim ativo de W2 para SEO da landing de produtores; mantido intacto porque seu escopo de produto é PR #727 e depende de #724.
- Entregáveis e worklogs AUX-03 de 10 a 17/11.
- Campanha W1 de pré-venda publicada em 17/11: não foi duplicada; esta execução é uma revisão de rotas nos guias editoriais.
- Estados atuais de issue #643 e PRs #722, #724 e #727 consultados diretamente no GitHub.

**Limitação de coordenação:** `CURRENT_STATE.md` ainda está consolidado em 30/10. `BLOCKERS.md` lista FIN-P0-001, mas não reflete a issue P0 #643. A divergência foi encaminhada a W00, sem editar arquivos de ownership do orquestrador.

## Confirmado — rotas na main

Arquivo consultado: `src/App.js`, blob `6db85d5f80c14acd2ed185ebf9e4afa535e14288`.

Rotas públicas declaradas:
- `/search`
- `/for-producers`
- `/artists`
- `/artist/:slug`
- `/cidades`
- `/eventos` e variações por cidade/categoria/período

A rota `/events` não está declarada no roteador revisado. Para descoberta pública, o destino declarado é `/eventos`.

## Confirmado — auditoria dos quatro guias existentes

| Guia | Destinos editoriais verificados | Resultado |
|---|---|---|
| Ingresso digital e QR Code (10/11) | `/eventos` | Corpo já estava correto; metadados ainda citavam `/events` |
| Encontrar eventos perto de você (11/11) | `/search`, `/cidades`, `/eventos) | Rotas declaradas |
| Check-in com QR Code para produtores (13/11) | `/for-producers` | Rota declarada; CTA aguarda GO comercial e público |
| Organizar e divulgar line-up (14/11) | `/for-producers`, `/artists`, `/artist/:slug` | Rotas declaradas; perfis reais devem ser usados somente após verificação |

Não foram criados novos artigos, páginas de cidade ou exemplos de eventos/artistas. Nenhum evento real publicado foi encontrado com evidência suficiente nesta consulta para ser usado como exemplo; isso não prova inexistência de eventos.

## Oportunidade

O guia de ingresso digital já havia recebido a correção do link no corpo do artigo em 17/11, mas o bloco de mensuração e a nota de gate ainda conservavam `/events`. Essa inconsistência editorial poderia reintroduzir o destino incorreto em um rascunho do CMS, checklist de publicação ou handoff.

## Trabalho realizado

1. Revisei os quatro guias existentes e seus destinos internos.
2. Comparei os destinos com as rotas declaradas em `src/App.js`.
3. Confirmei que os destinos dos guias de 11, 13 e 14/11 correspondem às rotas revisadas.
4. Corrigi as duas referências residuais a `/events` no guia de ingresso digital:
   - CTA de mensuração: `/events` → `/eventos`;
   - nota de validação pública: `/events` → `/eventos`.
5. Consultei novamente o arquivo após a gravação; o blob novo não contém mais a referência antiga.
6. Não alterei código do produto, não criei branch ou PR, não fiz merge/build/deploy e não acessei a VPS.

## Entregável

- [Guia de ingresso digital corrigido](https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261110-W2-guia-ingresso-digital-qr-code.md)
- Commit da correção editorial: `aa7e1493c8295bbffb4fe0abba46ff4bf726675d`
- Novo blob verificado: `2b03097734b00bc33cf8b55f8fb96afd2331e7c0`
- Roteador consultado: [src/App.js](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/App.js)

## Canal e CTA

**Canal:** Google Search → guia de ingresso digital → descoberta pública → página de evento → ingresso/checkout.

**CTA:** **Explore os eventos publicados na Cutinapp** → `/eventos`.

O CTA só deve ser considerado funcional no blog após a integração e QA do PR #722 e a liberação do runtime público.

## Métrica

- Cliques únicos no CTA `/eventos) por sessão do guia.
- Sessões do guia que chegam a páginas individuais de eventos.
- Inícios de checkout atribuídos ao artigo.

**Baseline:** N/D. Não foram consultados Analytics ou Search Console; nenhum clique, indexação ou conversão foi presumido.

## Bloqueios confirmados

- Issue [#643](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643): OPEN. A issue descreve divergência entre o release validado no filesystem e o SHA servido pelo Nginx/HTTPS.
- PR [#722](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722): OPEN, NOT MERGED; branch ainda declara HEAD `d717ef3` e está atrás da main. É a dependência para transformar links Markdown do blog em links clicáveis.
- PR [#724](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724): OPEN, NOT MERGED; copy da landing de produtores.
- PR [#727](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727): OPEN, DRAFT, NOT MERGED; metadados SEO da landing, dependente de #724.

## Hipótese

A consistência entre link no corpo, CTA de mensuração e nota de publicação reduz erros de configuração editorial e evita que o operador recopie uma rota obsoleta. O impacto em cliques e conversões ainda precisa ser medido.

## Próxima ação

1. W00/conta principal: coordenar #722 e #643 e atualizar `BLOCKERS.md` com a issue pública P0.
2. Conta principal/Infra: comprovar o mesmo SHA no filesystem, HTTP local do Nginx e HTTPS público antes de declarar GO.
3. Operador editorial autorizado: ao criar o rascunho, copiar o destino corrigido `/eventos` e retornar ID/URL do CMS.
4. AUX-03-W2: depois do GO, validar todos os links em mobile e acompanhar artigo → evento → checkout.
5. W09: manter a revisão de snapshots/HTML inicial e canonical dentro do ownership existente.

## Precisa da conta principal

**SIM** — para integrar #722, resolver #643, liberar o runtime público e autorizar o QA do CMS/produção.
