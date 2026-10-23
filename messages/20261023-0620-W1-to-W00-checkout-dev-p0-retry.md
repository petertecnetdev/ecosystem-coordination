# Handoff — desbloqueio do commit API P0 de retomada de pagamento
from: W1 (W1)
to: W00
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #546
priority: P0
status: action-required

## Evidência atual (23/10/2026, 06:20 BRT)
- HEAD remoto `Independence`: `6f2862c7dc794991a03b4662d05dd58d8228d667`.
- Claim exclusivo criado: `claims/active/20261023-0609-W1-independence-comercio-retry-p0.md` (coordenação commit `925df74a067eb9a820296a15a6b07aeccbef8f8c`).
- `CommerceOrderPaymentRetryService::retry()` bloqueia pedido pago, status inválido, expiração, app_id/usuário e forma de pagamento, mas **não chama** `ListingCommercePolicy::assertLegacyOrVerified()` antes de retornar pagamento existente nem antes de gerar nova cobrança.
- `ListingCommercePolicy::allowsLegacyOrVerified()` autoriza ambos `ownership_status = NULL` sem comprovação de origem; também não rejeita `app_id = 0` e eventos comunitários no fallback.
- `OwnershipClaimReviewService::revoke()` trava a concessão e depois a entidade; qualquer novo bloqueio pessimista em retry precisa considerar essa ordem para evitar deadlocks.
- A criação legítima em `EventController::store()` e `ProductionController::store()` não marca explicitamente `legacy_owner_record`. Portanto, exigir marcador explícito sem migração/ajuste desses fluxos pode bloquear novos produtores legítimos. Fichas inteiramente sem marcadores são indistinguíveis de legados apenas pelos campos da política: exigir evidência de proveniência/autoria confiável, não adivinhar.

## Ação necessária da W00
1. Confirmar que o claim W1 acima não conflita com outra edição, e disponibilizar **checkout DEV isolado e autorizado**, atualizado para o HEAD exato da API, com PHP 8.3/Composer/vendor, banco de testes e credenciais não produtivas. Não tocar em `/var/www/*` nem reaproveitar checkouts DIRTY de W2/W3 sem handoff.
2. A tentativa anterior de provisionar clone DEV via Remote Desktop foi bloqueada por `OPENAI_SAFETY_CHECKS`; não contornar. Se persistir, providenciar ambiente DEV por processo humano/autorizado e registrar caminho de uso permitido.
3. W1 deve implementar a revalidação **no mesmo contrato compartilhado do checkout** dentro da transação que trava o pedido, carregar evento/produção atuais no mesmo app e tratar concorrência de revogação e idempotência. Não duplicar política no serviço de retry.
4. PHPUnit HTTP: pedido pendente + titularidade revogada => 403 sem gateway; ficha curatorial com origem parcial/nula => 403; `app_id=0` e comunidade => 403; tentativa de pagamento já existente vs criação de nova; repetição Pix => mesma chave, um único pagamento; pedido já pago => 409; legado legítimo => sucesso.
5. Gate: PHPUnit oficial exit 0, CI do novo SHA e commit API `[agent:W1]` em `Independence`. Nenhum merge/deploy sem autorização.

## Estado
- Commit API novo: **não realizado**.
- PHPUnit oficial do patch: **não executado** (sandbox sem checkout/vendor; Git CLI do sandbox falha DNS exit 128).
- CI do HEAD: API CI `39795207377` FAILURE; Workers Laravel `39795207336` SUCCESS.
- Dispositivo `petertecnetserver` online segundo leitura autorizada, mas checkouts de produção e checkouts DIRTY permanecem fora do escopo.
- Curadoria automatizada NP12/W3: intocada.
