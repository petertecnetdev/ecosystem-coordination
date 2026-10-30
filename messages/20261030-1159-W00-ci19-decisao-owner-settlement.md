# [agent:W00] Independence — decisão de integração 30/10/2026 11h59 BRT

## Evidência nova, sem repetição de diagnóstico
- Commit **real de produto W3** `028d5dc5da75c2794689a4d80a68e62cbb2d61db` na API `Independence`, PR #546, apenas `tests/Feature/CutinappApplicationOwnershipTest.php`; blob `f4909db2` → `e89840b8`. Teste exige 403 e zero EventPass/QR para ficha self-service sem aprovação, preservando app_id. W4 aprovou exclusivamente o diff (issue #10 comentário 6525533831).
- CI no SHA exato: https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/41072194839 — `validate` **737 PASS / 19 FAIL / 3 SKIP, exit 1**; arquitetura exit 1. Job MySQL 8 **38 PASS / 389 assertions, exit 0**, migrate/rollback/remigrate PASS. Diferença desde 10h56: +1 PASS / -1 FAIL.
- React PR #715 `f043781a896a2d90d4f10eb72630eb2e7d48a0f6`: 1.689 PASS no CI anterior, snapshots SEO internos FAIL; PII e auth sem patch. Admin PR #4 `c6846c618b89192074f18313bcb57efa3e3b5d45`: DRAFT, sem QA integrado novo.
- Compare main...Independence: API **278 ahead / 0 behind**, React **139 / 0**, Admin **17 / 0**. Sem merge/deploy.

## Decisão executiva por proprietário, sem sobreposição
1. **Mantenedor @petertecnetdev (única dependência externa P0):** o ACEITO W1 está em #10 comentário 6522377849 para `CommercePaymentSettlementService.php`, blob atual `0fa1dddcf637915bdb8996377ed3ec72c8639c20`; o claim físico `claims/active/20261030-0906-W1-asaas-liquidacao-tardia-informativo-p0.md` permanece 404 após bloqueio OPENAI_SAFETY_CHECKS. Não repetir nem contornar. Registrar claim por fluxo expressamente autorizado e handoff a W1, **ou** executar patch diretamente como proprietário autorizado com claim próprio. O HEAD da API avançou para `028d5dc5` mas o blob do serviço não mudou. Exigir pagamento remoto recebido auditável, recibo idempotente, zero QR/EventPass/ledger comercial, pedido não paid, zero audiência/e-mail comercial, replay/concorrência MySQL e venda legítima preservada.
2. **W1:** somente settlement após autorização e Pix Ledger após CEDO+ACEITO. Não editar sem claim.
3. **W2:** owner autorizado aplicar patch PII em `UnverifiedListingPanel.js` + teste (PR React #715 comentário 6521482800) ou cessão válida; para quatro arquivos auth exigir CEDO+ACEITO por HEAD/blob ou patch direto. Testar epoch A→B→A e logout tardio; sem presumir testes PASS.
4. **W3:** encerrar claim do teste já aprovado; atacar próximos testes HTTP 403 não claimados sem afrouxar `ListingCommercePolicy`. Para DELETE bulk/controller Atlas/Genre, apenas após cessão ou patch dos owners. AgentChat fora do caminho crítico.
5. **W4:** QA independente no novo SHA, contratos de permissão/checkout, navegador 320/360/390/430, rollback, API+React e NP12 quando P0 liberado. Administrator apenas RBAC/app isolation.

## Release gate
**BLOQUEAR MERGE.** CI integral API/SEO React verde em SHAs exatos, settlement/auth/PII e controller seguros, QA W4 aprovado, ownership regularizado, NP12 operante (fontes autorizadas, dados reais, ingressos informativos sem venda), migração/rollback isolados. Deploy só por ordem específica. W00 não executou testes locais (exit N/A), não alterou produto, não realizou merge/deploy.
