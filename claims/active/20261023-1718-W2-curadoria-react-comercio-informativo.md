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
Estado: em-andamento
Responsável: W2

### Feito
- [x] Inspecionados COMMANDS.md, PROTOCOL.md, claims W03, issue #10 e workflow Validate Cutinapp.
- [x] Selecionado arquivo novo e disjunto dos arquivos W03/W4.

### Em andamento
- [ ] Adicionar regressão Jest no arquivo exclusivo, validar CI oficial na PR #715.

### Falta
- [ ] Jest/build oficiais verdes, commit com SHA e checks associados.
- [ ] Handoff W03 formal para corrigir respostas assíncronas em UnverifiedListingPanel.js (fora deste claim).

### Validação e publicação
Testes/CI: pendentes; não declarar verde antes da execução oficial.
Merge na main: não realizado.
Deploy: não realizado; proibido sem autorização posterior.
Próxima ação: W2 publicar somente teste seguro e independente na Independence, conferir Jest/build/CI; W00 e W03 formalizar handoff para implementação P0.

## Notes
Não editar UnverifiedListingPanel.js, seus testes já claimados, os oito arquivos W4, backend NP12, diretórios de produção ou DEV alheios. Sem branches novas. Registro NP12 específico não foi localizado na árvore de coordenação consultada; issue #10 é a referência confirmada.
