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

## Atualização W1 — 27/10/2026, 10h06 BRT (somente leitura; action-required)

- **HEAD/CI conferidos:** API `Independence` = `658589374d4b400318bae19798fb3397f51275b2`; PR #546 OPEN, `mergeable=false`. Actions por `head_sha`: somente W03 #40450375321, `failure` no passo **Executar PHPUnit oficial W03**; a etapa isolada W03 passou. `combined statuses=[]`. Não existe execução PHPUnit W1 para um patch nem SHA W1 novo.
- **DEV reavaliado:** Desktop Commander `petertecnetserver` OFFLINE (último contato ~5h); `srv1900287` OFFLINE (~970h). Checkout DEV W1 exclusivo/autorizado, `vendor` e banco de testes continuam não comprovados. Não acessar `/var/www` ou diretórios de outros workers; não contornar `OPENAI_SAFETY_CHECKS`.
- **Claim verificado:** `claims/active/20261023-0609-W1-independence-comercio-retry-p0.md` lista apenas `CommerceOrderPaymentRetryService.php`, `ListingCommercePolicy.php`, `CutinappCommerceProductionSafetyTest.php` e `ListingCommerceCompatibilityTest.php`. **Não inclui** `AsaasPaymentService.php`, `OwnershipClaimReviewService.php` nem persistência de intenções; exigir handoff/claim exclusivo antes de alterar esses contratos compartilhados.

### Achados adicionais confirmados no código do HEAD

1. `CommerceOrderPaymentRetryService::retry()` faz `lockForUpdate()` do pedido, mas carrega `event`/`production` por relacionamento e **não** trava grants/entidades da revogação. A transação termina antes de `accounts->readiness()` e da chamada externa; duas tentativas podem atravessar essa janela e a revogação pode ocorrer depois da leitura. O caminho `existingPayload()` também retorna cobrança anterior sem revalidação de `ListingCommercePolicy`.
2. Em `AsaasPaymentService::createOrRecoverPayment()`, a busca GET `firstPayment()` retorna `null` tanto quando não há cobrança quanto quando ocorre `RuntimeException|ConnectionException`. Após resultado GET inconclusivo, a execução faz POST. Na recuperação de POST com `ConnectionException`, nova consulta inconclusiva também é tratada como ausência. **Necessário estado explícito desconhecido/reconciliação; nunca converter indisponibilidade do provedor em autorização para novo POST.**
3. `firstPayment()` devolve a primeira cobrança não deletada, sem conferir no objeto recebido `externalReference`, `customer`, `billingType` e `value` esperados. `retryAsaas()` usa sempre `order.public_id` como referência remota, enquanto a chave local `commerce-order-...-retry-N` varia por tentativa. Assim, um retry posterior pode recuperar cobrança terminal antiga ou, sob concorrência e GET vazio, disparar POSTs simultâneos. A correção deve distinguir **recuperação da mesma tentativa** de **nova tentativa autorizada**, mantendo histórico e unicidade por intenção.
4. `ListingCommercePolicy::allowsLegacyOrVerified()` retorna `true` quando os dois `ownership_status` são `null`, sem exigir `app_id>0`, rejeitar comunidade ou comprovar origem legada. Atenção à compatibilidade: cadastros legítimos novos ainda não recebem necessariamente marcador `legacy_owner_record`; não aplicar fail-closed sem migração/critério de proveniência que preserve produtores reais.

### Providência requerida de W00 e aceite W1

- Disponibilizar DEV W1 exclusivo **com autorização formal**, dependências e banco isolado, no HEAD acima (ou novo HEAD registrado); publicar caminho permitido e teste de acesso.
- Coordenar handoff exclusivo para Asaas, revogação e persistência de intenção/reconciliação; definir serialização de retry/revoke, ordem global de locks e barreira de revogação sem manter transação aberta durante chamada de rede.
- Depois, W1 implementa e executa PHPUnit HTTP oficial (revogado, não reivindicado, outro `app_id`, concorrência, GET inconclusivo sem POST, retry idempotente, legado legítimo), **exit 0**, e publica commit **de produto** `[agent:W1]` com SHA e CI desse SHA. Sem merge/deploy.

**Estado desta atualização:** somente coordenação; 0 arquivos de aplicação alterados, 0 commits de produto W1, PHPUnit W1 não executado. Automação W1 permanece ativa às :06.
