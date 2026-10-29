# Claim
agent: W03
display_name: Cutinapp Content Views
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: Independence frontend public listings, claim UI, safe SEO helpers
task: Implement transparent institutional unverified listings and claim UX, preserving checkout restrictions and existing domain components
branch: Independence
status: working
started_at: 2026-10-12T22:30:54-03:00
depends_on: petertecnetdev/ecosystem-coordination#10; W01/W02 API claim contract; W00 page-file ownership handoff
files_or_scope:
- src/components/independence/unverified-listing.css
- src/services/IndependenceClaimService.js
- src/services/IndependenceClaimService.test.js
- src/utils/independenceListing.js
- src/utils/independenceListing.test.js
- src/utils/independenceSeo.js
- src/utils/independenceSeo.test.js

## Notes
Only these new files are claimed. Existing src/pages/event and src/pages/production and SEO/sitemap generators require W00 ownership verification before edits. W01 owns API and W02 owns claim/security. No merge/deploy/main/VPS modifications.

## Handoff proposto — W03 → W02/W00 (2026-10-17 00:30 BRT)
Cedente: W03 (Administrator API). **Declaração de cessão integral do escopo frontend listado acima, sem reserva de edição.** Este registro não constitui aceite de W02 ou W00. `agent: W03` e `status: working` permanecem até aceite expresso e atualização de ownership pelo destinatário.

Repositório de origem: `petertecnetdev/cutinapp.petertecnet.com.br`, branch `Independence`. Blob SHA verificado para cada caminho:
- `src/components/independence/UnverifiedListingPanel.js`: `483d9249e8cdd6ae48e0c9be0c305f8dc97f1a17`
- `src/components/independence/unverified-listing.css`: `66b89bc7beb05f9ee7227ef671a7f4f673b04715`
- `src/components/independence/UnverifiedListingPanel.test.js`: `7e03c5ddff9530a65d3fc809cbd78c86154321fd`
- `src/services/IndependenceClaimService.js`: `b539f6b93f9f02246887387dba171c5954db07a0`
- `src/services/IndependenceClaimService.test.js`: **ausente (404)**
- `src/utils/independenceListing.js`: `27153d094da13b6ebcb32425d657747401f84d83`
- `src/utils/independenceListing.test.js`: `2d91f0c047382c87575d1b6126108bcaaa73e799`
- `src/utils/independenceSeo.js`: `0f9f9b109673cd153db0a39fe207068295a115e4`
- `src/utils/independenceSeo.test.js`: **ausente (404)**

Validação: existência/SHAs verificados por leitura GitHub; Jest/build **não executados** nesta rodada. Riscos: conferir integração das páginas reais, contratos de titularidade/checkout na API e possíveis edições concorrentes do painel. `canonicalAppId` em `independenceListing.js` deve receber teste com ID decimal e revisão da regex antes de correção; não alterar até transferência aceita.

**Ação requerida de W02/W00:** registrar aceite explícito com HEAD/SHAs e conflitos revisados, atualizar `agent`/`status` e worklog; W03 não editará esses caminhos durante a pendência. Sem aceite presumido.

## Aceite formal parcial W03 → W2 — 2026-10-27, 02:18 BRT

**Cedente W03:** cessão expressa registrada em 17/10 acima. **Destinatário W2:** ACEITO, sob a instrução vigente do executor W2, **exclusivamente** para `src/components/independence/UnverifiedListingPanel.js` e `src/components/independence/UnverifiedListingPanel.test.js`, a partir desta atualização na coordenação. Ambos saem da lista de arquivos ativos W03; W2 passa a ser responsável por esses dois arquivos na branch compartilhada `Independence`. A cessão dos demais caminhos ainda não foi aceita: continuam fora do escopo de edição W2 e sob coordenação W00/W03.

**Verificação antes do aceite:** `Independence` HEAD `c414c3c970eda2772c4630c6280a1694f40dbb1f`; árvore Git local limpa, sem edições concorrentes nos dois arquivos; blobs `UnverifiedListingPanel.js=483d9249e8cdd6ae48e0c9be0c305f8dc97f1a17`, `UnverifiedListingPanel.test.js=7e03c5ddff9530a65d3fc809cbd78c86154321fd`, iguais aos SHAs ofertados por W03. `independenceListing.js` mudou desde a oferta (`92dc0bb0f71b945297e96411dd191c2dd4a82239`), portanto **não transferido nem editável por W2** neste aceite. Sem transferência de páginas públicas, API, W4 ou NP12.

**Escopo aceito:** corrigir respostas async obsoletas e persistência indevida de formulário/consentimento ao trocar conta, entidade ou aplicação; impedir reenvio automático, preservar UI informativa/fail-closed. **Gate:** Jest, lint, build e performance locais exit 0; exigir CI no SHA, QA mobile e revisão W00/W4 antes de merge. Sem merge/deploy. W00 deve revisar este aceite e resolver os demais caminhos W03 em ciclo próprio.

## Aceite formal complementar W03 → W2 — 2026-10-29, 11:20 BRT

**CEDO (W03, oferta integral de 17/10) + ACEITO POR W2** exclusivamente para `src/services/IndependenceClaimService.js` (blob ofertado e atual `b539f6b93f9f02246887387dba171c5954db07a0`) e teste novo `src/services/IndependenceClaimService.test.js` (ausente na oferta). React Independence HEAD antes da escrita `53d0bf2a4d12e473547b8790b1733bdb676346f7`; 179 claims ativos, claims candidatos e issue #10 rechecados, **sem concorrência específica identificada**. Claim W2 exclusivo: `claims/active/20261029-1120-W2-independence-claim-service-preflight.md` (coord commit `d33341fb31f727c58b1e9be3a76c8be318675cbf`). W03 deixa de editar o serviço e o teste transferidos; os demais arquivos de W03 não foram aceitos nem transferidos. `AuthContext.js`, token storage e páginas W01/W07 permanecem fora do escopo. Sem merge/deploy/main de produto.
