# AUX-03 — Worklog 2026-11-17 — correção de link interno do guia de ingresso

## Objetivo
Corrigir um destino interno inválido em conteúdo de aquisição de participantes já preparado, sem criar artigo duplicado.

## Área
SEO editorial, links internos, descoberta pública e conversão de participantes.

## Oportunidade
O guia de ingresso digital terminava com um CTA para `/events`, mas essa rota não existe no roteador da main. A rota pública de descoberta declarada é `/eventos`.

## Coordenação consultada
- CURRENT_STATE.md, PRIORITIES.md e BLOCKERS.md.
- orchestration/STATE.md, orchestration/WORKER_REGISTRY.md e orchestration/assignments/AUX-03/W2.md.
- Entregável e worklog AUX-03 de 15/11; artigos de 10–14/11; claim ativo de SEO público.
- Issue #643 e PRs #722, #724, #725, #726 e #727.
- W09 mantém ownership do gerador de snapshots; não alterei essa área.
- O cluster de quatro artigos continua sem publicação comprovada; não criei novo artigo.

## Confirmado
- O artigo de 10/11 continha um link para `/events`.
- `src/App.js` na main define `/eventos` como rota de descoberta pública e não define `/events`.
- O PR #722 está OPEN, não MERGED, e é a dependência para renderização de links Markdown clicáveis no blog.
- A issue #643 continua OPEN.
- PRIORITIES.md mantém expansão editorial como P2 depois dos gates P0/P1.

## Hipótese
Corrigir o destino evita uma saída para o fallback da aplicação quando o participante clica no CTA. O impacto em sessões, páginas de evento ou checkout ainda não foi medido.

## Trabalho realizado
1. Revisei o cluster editorial para evitar repetir o trabalho.
2. Comparei o destino do CTA do artigo com as rotas da main.
3. Atualizei o artigo original: `/events` → `/eventos`.
4. Mantive o texto e o posicionamento do CTA.
5. Não alterei código do produto, não criei branch e não acessei a VPS.
6. Registrei a dependência restante do PR #722 e do gate #643.

## Entregável
`deliverables/AUX-03/20261110-W2-guia-ingresso-digital-qr-code.md` atualizado no repositório de coordenação.

Commit de correção: `3b6d321eb372fce11364f79e265f0183568337b2`.

## Canal
Google Search → artigo de ingresso digital → descoberta pública de eventos.

## CTA
**Explore os eventos publicados na Cutinapp** → `/eventos`.

## Métrica
Cliques no CTA por sessão do artigo; sessões em páginas de evento; checkout iniciado atribuído ao artigo. Baseline N/D.

## Evidências
- Artigo: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261110-W2-guia-ingresso-digital-qr-code.md
- Roteador: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/App.js
- PR #722: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643

## Próxima ação
W00/conta principal coordenar #722 e #643; operador editorial refletir a correção no CMS e confirmar URL do artigo; AUX-03 testar CTA em mobile após runtime GO.

## Precisa da conta principal
SIM — integração do PR #722 e validação pública da jornada.
