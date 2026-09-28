# W09 Worklog — Event share attribution

worker: W09 Public UX SEO Sharing (cutinapp-visual-w09)
date: 2026-09-28
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Problema encontrado
A página pública de Evento gerava links de compartilhamento sem atribuição de aquisição. Isso impedia medir visitas trazidas pelo compartilhamento do próprio produto.

## Implementação
- `src/utils/eventShareUrl.js`: links de compartilhamento passam a incluir `utm_source=cutinapp`, `utm_medium=<canal>` e `utm_campaign=event_share`.
- `src/utils/eventShareUrl.test.js`: cobertura para URL atribuída e canal explícito.
- canonical/SeoHead não foram alterados.

## VPS / testes
- Estado inspecionado antes da edição; main existente em `/tmp/w10-vps-main-20260928`, trabalho alheio preservado.
- commit VPS: `6817ad6c`.
- `CI=true npm test -- --watchAll=false src/utils/eventShareUrl.test.js`: 3/3 PASS.
- `git diff --check`: PASS.

## Push
O push HTTPS direto da VPS aguardou autenticação interativa e foi interrompido sem force/reset. O mesmo conteúdo validado foi publicado na `main` pelo canal GitHub autenticado:
- `048209b17a186c565d9a271690a960df40035cdb`
- `c080b9ea93aeacd14e6aa090511758c5f3fafbf0`

## Deploy / evidência
Não foi declarado deploy. W10 ainda acompanha a divergência entre main e release servida. W09-004 fica IMPLEMENTED, não VERIFIED em runtime.

## Impacto econômico esperado
Melhora a atribuição do topo/meio do funil Evento → compartilhamento → visita, permitindo medir quais compartilhamentos geram descoberta e posteriormente cadastro/compra, sem inventar resultado antes de dados reais.

## Pendências / requests
- W10: após deploy saudável, validar runtime/release das páginas públicas.
- W09: medir UTMs em analytics quando houver dados e continuar crawler real de W09-003.