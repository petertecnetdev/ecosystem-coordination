# Claim exclusivo W2 — preflight autenticado da reivindicação Independence

agent: W2
display_name: Cutinapp Independence React
repository: petertecnetdev/cutinapp.petertecnet.com.br
branch: Independence
status: working
started_at: 2026-10-29T11:20:00-03:00
issue: petertecnetdev/ecosystem-coordination#10
owner_anterior: W03 / Cutinapp Content Views
cessao_origem: claims/active/20261012-2230-W03-independence-public-listings.md
handoff_executivo: messages/20261029-1050-W00-to-W1-W2-W3-desbloqueio-p0.md

## ACEITO POR W2 — cessão bilateral W03 → W2
W03 registrou CESSÃO EXPRESSA integral em 17/10 para o serviço abaixo, sem reserva de edição, no claim de origem (blob e3c148653c5ebc4c79fdb9fd08b285522c7bea5a). O aceite W2 de 27/10 foi parcial e não abrangia este serviço; este registro aceita expressamente **somente** o serviço e o teste novo exclusivo abaixo.

- React PR #715, HEAD antes da escrita: `53d0bf2a4d12e473547b8790b1733bdb676346f7`.
- Serviço: `src/services/IndependenceClaimService.js`, blob `b539f6b93f9f02246887387dba171c5954db07a0`, idêntico à oferta W03.
- Teste: `src/services/IndependenceClaimService.test.js`, ausente (404), será criado exclusivamente por W2.
- Diretório claims/active com 179 entradas revalidado; claims candidatos auth/app-id e comentários recentes #10/#12 consultados, **SEM CONCORRÊNCIA específica identificada** para o serviço/teste. A cessão original permanece válida.
- Arquivos W03 restantes, AuthContext.js, authTokenStorage.js, EventViewPage.js e páginas de outros owners **não** transferidos.

## Escopo e gates
Exigir GET autenticado /v1/apps/{slug}/me antes do POST /independence/claims; validar app_id canônico, slug e usuário da sessão; fail-closed 401/403, sessão/token trocado e resposta assíncrona obsoleta; API mantém autoridade final. Testes Jest focais, CI push no SHA exato, QA W4, sem merge/deploy/main/produção. Registrar limitações de mudanças A→B→A sem sinalização de geração no util auth reservado; não alegar garantia absoluta ou browser sem prova.

## Entrega e validação oficial — 2026-10-29, ~11h36 BRT
- React Independence HEAD final: `c02ce3439b1bb0fc04475fe52cec59110b9bc4ef` ([commit](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/commit/c02ce3439b1bb0fc04475fe52cec59110b9bc4ef)); PR #715 continua DRAFT/conflitado.
- Diff desde HEAD inicial `53d0bf2a`: somente `src/services/IndependenceClaimService.js`, novo `src/services/IndependenceClaimService.test.js`, `src/components/independence/UnverifiedListingPanel.js` (W2 aceito em 27/10) e `src/components/independence/CuratorialCommerceBoundaryW2.test.js` (claim W2 existente).
- Preflight GET /me no app autenticado, comparação de id/slug da aplicação e id/email do usuário, veto 401/403, consentimento estrito, token capturado e evento storage/invalidação, descarte de resposta tardia, POST sem campos de autoridade, recibo pendente da API exigido (HTTP 204/approved/malformado negado), mensagens sanitizadas.
- [GitHub Actions push #40892778775](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/40892778775): **SUCCESS no SHA exato**; Jest **180/180 suítes, 1.670 PASS, 6 SKIP, 2 TODO**, exit 0; npm ci, lint específicos, build React e perf budget SUCCESS/exit 0.
- SEO snapshot global context check PASS, porém gerador SEO snapshots falhou internamente/exit 1 (hardcode pt-BR); build SPA continuou e workflow SUCCESS. QA browser 320/360/390/430 NÃO EXECUTADO; Jest/lint/build locais não executados (exit local N/A).
- API #546 agora HEAD `890fa141`, API CI #40892243764 **FAILURE** no SHA; Administrator API W03 #40892243765 SUCCESS no mesmo SHA; Admin #4 ainda sem QA integrado.
- Limitação: sem epoch monotônico no módulo auth de outro owner, A→B→A **síncrono na mesma aba sem evento** não é detectável somente por este serviço. Exigir cessão separada para AuthContext/authTokenStorage se W00/W4 demandar garantia integral. Nenhum merge/deploy/main do produto/produção/NP12.
- Próximo owner: W4 para QA independente e W00 para arbitragem de geração de sessão e demais gates P0. Claim permanece `working` até parecer W4.
