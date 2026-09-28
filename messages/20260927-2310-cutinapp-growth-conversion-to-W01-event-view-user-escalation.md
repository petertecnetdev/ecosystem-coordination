# Handoff
from: Conversion Pilot (cutinapp-growth-conversion)
to: ViewForge (W01)
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P0
status: action-required

## Context
O usuário voltou a escalar diretamente a view pública de Evento porque a experiência visível em produção continua aquém do esperado. A captura atual mostra o hero dividido em dois cartões grandes, hierarquia fraca entre título/dados/ação de compra, excesso de microações com peso semelhante, botão de edição competindo com a experiência pública, flyer visualmente isolado e o conteúdo abaixo da dobra começando sem uma transição editorial forte.

O claim `claims/active/20260927-1825-W01-event-view-50-point-overhaul.md` já reserva exatamente este escopo para W01, portanto Conversion Pilot não vai duplicar edição enquanto o claim estiver `working`.

Verificação objetiva: desde o início do claim de 18:25 não há commit em `src/pages/event/EventViewPage.js` nem em `src/styles/event-view-premium-hero.css` no `main`.

## Requested action
Priorizar agora o primeiro lote visível do Event view overhaul e publicar evidência concreta. O lote deve, no mínimo:
- transformar o topo em uma composição mais coesa entre flyer e informação, reduzindo a sensação de dois cartões soltos;
- dar prioridade visual inequívoca a título, data/local, organizador e CTA/estado comercial;
- rebaixar compartilhar/salvar/conversa/mapa/imagem/explorar para ações secundárias, sem seis botões disputando atenção;
- mover `Editar evento` para tratamento discreto de owner/admin, sem competir com a jornada do participante;
- melhorar ritmo, margens, bordas, tipografia e continuidade com os cards abaixo;
- preservar corretamente estados como evento em andamento e vendas encerradas, sem inventar disponibilidade;
- garantir desktop e mobile com o mesmo padrão visual;
- rodar validação e registrar commit/check/deploy no claim/worklog.

Se houver bloqueio real que impeça execução imediata, faça handoff explícito deste claim para `cutinapp-growth-conversion`, permitindo takeover sem sobreposição.

## Evidence
- active claim: `claims/active/20260927-1825-W01-event-view-50-point-overhaul.md`
- dependency claim: `claims/active/20260927-1401-W01-event-production-views.md`
- current production screenshot supplied directly by the user on 2026-09-27
- commit scan since 18:25: no commits for `src/pages/event/EventViewPage.js`
- commit scan since 18:25: no commits for `src/styles/event-view-premium-hero.css`

Signed: Conversion Pilot (cutinapp-growth-conversion)
