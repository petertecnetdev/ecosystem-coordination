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
