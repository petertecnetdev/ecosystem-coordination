# AUX-03-W2 — Worklog 2026-11-18 — auditoria de rotas do cluster editorial

## Objetivo
Verificar os destinos internos dos quatro guias editoriais existentes e eliminar referências residuais à rota inexistente `/events`, sem criar conteúdo duplicado.

## Área
SEO editorial, links internos, descoberta pública, aquisição de participantes e conversão de produtores.

## Oportunidade
Em 17/11, o corpo do guia de ingresso digital já havia sido corrigido para `/eventos`, mas o bloco de mensuração e a nota de validação ainda mencionavam `/events`. A inconsistência poderia reaparecer no CMS ou em instruções de publicação.

## Coordenação consultada
- CURRENT_STATE.md, PRIORITIES.md e BLOCKERS.md.
- orchestration/STATE.md, WORKER_REGISTRY.md e assignments/AUX-03/W2.md.
- Claim ativo W2 sobre metadados da landing de produtores; preservado, pois seu escopo é #727/#724.
- Worklogs e entregáveis de 10–17/11.
- Campanha W1 de checklist de pré-venda de 17/11; não duplicada.
- Issue #643 e PRs #722, #724 e #727 consultados diretamente.
- CURRENT_STATE.md está consolidado em 30/10; BLOCKERS.md não espelha #643. Handoff enviado a W00, sem editar arquivos de sua propriedade.

## Confirmado
- src/App.js na main, blob 6db85d5f80c14acd2ed185ebf9e4afa535e14288, declara /search, /for-producers, /artists, /artist/:slug, /cidades e /eventos.
- /events não está declarado no roteador revisado; /eventos é o destino público de descoberta.
- Guia de ingresso digital: corpo já apontava para /eventos; CTA de mensuração e nota de gate ainda continham /events.
- Guia de descoberta (11/11): /search, /cidades e /eventos correspondem a rotas declaradas.
- Guia de check-in (13/11): /for-producers corresponde a rota declarada.
- Guia de line-up (14/11): /for-producers, /artists e /artist/:slug correspondem a rotas declaradas.
- #643 permanece OPEN; #722 OPEN/NOT MERGED; #724 OPEN/NOT MERGED; #727 OPEN/DRAFT/NOT MERGED.
- O cluster segue sem publicação/indexação comprovadas. Não foram encontrados exemplos de eventos públicos verificáveis nesta consulta.

## Hipótese
Eliminar referências residuais à rota inexistente reduz o risco de o operador editorial copiar um CTA errado para o CMS. Não há dados de clique ou conversão para quantificar o efeito.

## Trabalho realizado
1. Revisei os quatro ativos editoriais já existentes.
2. Comparei cada destino com as declarações de rota em src/App.js.
3. Corrigi duas referências no guia de ingresso digital: CTA de mensuração e nota de validação, ambas de /events para /eventos.
4. Consultei novamente o arquivo; o conteúdo atualizado não contém mais a referência /events.
5. Não criei artigo, branch ou PR; não alterei código do produto, merge, build, deploy ou VPS.

## Entregável
deliverables/AUX-03/20261118-1043-AUX-03-auditoria-rotas-cluster-editorial.md

Arquivo editorial atualizado:
https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261110-W2-guia-ingresso-digital-qr-code.md

Commit editorial:
aa7e1493c8295bbffb4fe0abba46ff4bf726675d

## Canal
Google Search → guia de ingresso digital → /eventos → página de evento → checkout.

## CTA
Explore os eventos publicados na Cutinapp → /eventos.

## Métrica
Cliques no CTA por sessão do artigo; visitas a páginas individuais de evento; inícios de checkout atribuídos ao guia. Baseline N/D.

## Evidências
- Roteador: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/App.js
- Guia corrigido: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261110-W2-guia-ingresso-digital-qr-code.md
- PR #722: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727

## Próxima ação
W00/conta principal coordenar #722 e #643 e atualizar BLOCKERS.md; operador editorial refletir /eventos no CMS; AUX-03 validar os links em mobile após GO público.

## Precisa da conta principal
SIM — integração de #722, resolução de #643, publicação/CMS e QA público.
