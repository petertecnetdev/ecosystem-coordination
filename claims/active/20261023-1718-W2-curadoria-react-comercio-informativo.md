# Claim
agent: W2
display_name: Cutinapp Curadoria React
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: Independence — regressão frontend de fichas curatoriais e comércio informativo
task: Testar o veto de compra e a transparência de fichas não reivindicadas em evento, produção e artista, sem alterar implementação de outro worker.
branch: Independence
status: working
started_at: 2026-10-23T17:18:00-03:00
depends_on: petertecnetdev/ecosystem-coordination#10; W03 mantém claim próprio de UnverifiedListingPanel.js; W00 supervisiona gates.
files_or_scope:
- src/components/independence/CuratorialCommerceBoundaryW2.test.js

## Andamento
Objetivo: regressão Jest para ingresso apenas informativo e proveniência em fichas não reivindicadas.
Estado: em-revisao
Responsável: W2

### Feito
- [x] Inspecionados COMMANDS.md, PROTOCOL.md, claim W03, issue #10 e workflow Validate Cutinapp.
- [x] Criado arquivo novo e disjunto dos arquivos W03/W4: `src/components/independence/CuratorialCommerceBoundaryW2.test.js`.
- [x] Commit real de código de teste na `Independence`: `4f6879f5e49d891ecf8b2167d4406cfee75c73ba` — `teste(curadoria): impedir CTA comercial em fichas informativas [agent:W2]`.
- [x] Validate Cutinapp #40018392368 SUCCESS no SHA: 178 suítes / 1215 testes aprovados, incluindo `CuratorialCommerceBoundaryW2.test.js`; Jest exit 0, React build compilado com sucesso, perf budget exit 0.

### Em andamento
- [ ] Aguardar revisão independente do W00; Lighthouse #40018392371 SUCCESS.

### Falta
- [ ] Aceite/handoff formal W03 para corrigir respostas assíncronas obsoletas em UnverifiedListingPanel.js (fora deste claim).
- [ ] Verificação integrada da ausência de CTA nas páginas reais após backend/contratos NP12 e revisão de produção (não realizada).

### Validação e publicação
Testes/CI: [Validate Cutinapp #40018392368](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/40018392368) SUCCESS; Jest 178/178 suítes, 1215/1215 testes, React build compilado, perf budget OK. Lighthouse #40018392371 SUCCESS no mesmo SHA. Build registrou aviso não bloqueante: geração de snapshot SEO indisponível (exit 1), mas build SPA validado e workflow SUCCESS; não equivale a snapshot SEO aprovado.
Merge na main: não realizado.
Deploy: não realizado; proibido sem autorização posterior.
Próxima ação: W2 conferir Lighthouse e encerrar claim após revisão; W00/W03 formalizar handoff para implementação P0.

## Notes
Não editar UnverifiedListingPanel.js, seus testes já claimados, os oito arquivos W4, backend NP12, diretórios de produção ou DEV alheios. Sem branches novas. Registro NP12 específico não foi localizado na árvore de coordenação consultada; issue #10 é a referência confirmada.

## Rodada W2 — 23/10/2026, 18:18 BRT
- **Commit real:** `8fcad99e3398badc36ee82fdcf00daaf606e9223` na mesma branch `Independence`; arquivo já sob claim W2 `src/components/independence/CuratorialCommerceBoundaryW2.test.js`.
- **Escopo:** oito regressões novas de isolamento `app_id` entre evento e produção (IDs decimais de 64 bits diferentes, Number inseguro, zero, negativo, zeros à esquerda em apps distintos, espaços, notação científica e equivalência legítima com zeros à esquerda). Não muda o código comercial; o backend permanece autoridade.
- **Gates concluídos no SHA:** [Validate Cutinapp #40025640304](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/40025640304) **SUCCESS**: Jest 178/178 suítes, 1223/1223 testes, React build compilado com sucesso (exit 0), perf budget aprovado; [Lighthouse #40025640475](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/40025640475) **SUCCESS**. Aviso não bloqueante: snapshot SEO indisponível (exit 1 interno), sem invalidar build SPA.
- **P0 ainda pendente:** handoff W03 para `UnverifiedListingPanel.js` e estado assíncrono; validação integrada com API NP12 e fluxo comercial.
- **Impacto econômico esperado:** reduzir risco de exposição indevida de CTA entre tenants sem bloquear IDs legados decimais equivalentes. Resultado econômico ainda não medido.
- **Próxima ação:** acompanhar CI, corrigir eventuais falhas sem sobrescrever claims; W3 confirmar mesma proteção de `app_id` na API. Nenhum merge/deploy.
