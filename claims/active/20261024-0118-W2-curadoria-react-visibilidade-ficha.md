# Claim
agent: W2
display_name: Cutinapp Curadoria React
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: Independence — regressão de transparência em fichas curatoriais sem ownership_status
branch: Independence
status: working
started_at: 2026-10-24T01:18:00-03:00
depends_on: petertecnetdev/ecosystem-coordination#10; gates Jest/build oficiais; revisão W00
files_or_scope:
- src/components/independence/CuratorialVisibilityP0W2.test.js

## Limites
Arquivo NOVO, exclusivo e disjunto do claim W03. Somente teste de apresentação pública/proveniência. Não alterar `UnverifiedListingPanel.js`, `independenceListing.js`, testes W03, arquivos W4, API/NP12, checkouts DEV alheios ou produção. Não criar branch, merge ou deploy. Checkout e CI oficiais devem ser autorizados e executados antes de publicar o teste no frontend.

## Hipótese P0 documentada (sem declaração de Jest aprovado)
O helper `isUnverifiedListing` identifica `listing_source=curated` ou `verification_status=pending_claim` mesmo sem `ownership_status`, mas `UnverifiedListingPanel` retorna `null` quando `ownership_status` não é `unclaimed`/`pending_claim`. Com `ownership_status=rejected`, também omite o aviso. Isso pode ocultar a transparência de fichas públicas não verificadas, independentemente do veto comercial do backend.

## Estado da rodada
Arquivo Jest preparado localmente, sintaxe `node --check` exit 0. **Não publicado no frontend**: nenhum Jest/build oficial exit 0 disponível, PR #715 DRAFT e CI no HEAD `5dd237e8` não identificado. Regressões são TDD e deverão falhar na implementação atual. W00 deve decidir handoff/owner da correção W03 e habilitar gates; não confundir teste local com commit validado.
