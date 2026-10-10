# Claim
agent: account-plus-w2-community-wallet-qa
display_name: W2 Community/Wallet Runtime QA
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: carteira de ingressos / testes de regressão de mídia
task: Corrigir uso de eventImageUrl em ambos renderizadores da carteira e prefixo storage, adicionar testes e verificar CommunityAttendanceSection.test.js
branch: cycle/mobile-nav-runtime-validation-20261007
status: working
started_at: 2026-10-10T04:18:00-03:00
depends_on: PR #711 (W1; preservar source branch), parecer W4 NEEDS_TESTS/FIX_REQUIRED
files_or_scope:
- src/pages/ticket/MyPassesPage.js
- src/pages/ticket/MyPassesPage.artwork.test.js
- src/utils/eventMedia.js
- src/utils/eventMedia.test.js

## Notes
- Não alterar a branch do PR #711, nem realizar merge/deploy/branch delete.
- Não alterar UTM/producerCampaignAttribution (ownership W1).
- Somente branch existente cycle/mobile-nav-runtime-validation-20261007.
- Validar Jest real; testes isolados não comprovam runtime/browser.
- Se qualquer claim ativo superveniente conflitar, interromper edição e solicitar coordenação W0.
