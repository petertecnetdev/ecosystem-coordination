# [agent:W00] Independence — decisão de liquidação tardia e gate de integração (30/10/2026 07h54 BRT)

**Estado: BLOQUEADO PARA MERGE.** Não realizar merge, deploy, alteração da main de produto, nova branch ou automação. Preservar OPENAI_SAFETY_CHECKS, claims e revisão independente.

## Evidências verificadas nesta rodada

- Lido `ecosystem-coordination/main/COMMANDS.md` blob `3f3e61ba797331cdf8833e0262aaeb1076ef2311`, issues #10/#12 e comentários, `claims/active` (182 entradas incluindo .gitkeep; 181 claims), `handoffs` (4 entradas), PRs API #546, React #715 e Admin #4. Sem CEDO+ACEITO novo comprovado para Ledger, controller Atlas/Genre e os quatro arquivos de autenticação.
- API PR #546 OPEN, branch `Independence` HEAD **`689c4bec63cac7e3e88a66df93c1f9f56046245b`**, main `d960738b8428443a269074d2f2338529178159e6`, ahead 276 / behind 0, **4 branches**. CI oficial [#41038109186](https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/41038109186) no SHA exato: job `validate` **FAIL**, PHPUnit **734 PASS / 22 FAIL / 3 SKIP**, exit 1; arquitetura exit 1. Job MySQL 8 efêmero **SUCCESS**, 38 testes/389 asserções, exit 0; migrações/rollback/remigração PASS. Outros dois workflows focados do mesmo SHA concluíram SUCCESS; isso não torna o gate geral verde.
- W1 publicou **três commits reais**: `19ac8a98`, `7400c0d6`, `689c4bec`, nos arquivos sob seu claim `CommerceOrderPaymentRetryService.php` (blob `92a08ee4`) e `CutinappCommerceProductionSafetyTest.php` (blob `51b32880`). Retry Pix agora nega HTTP 403 se ticket foi reclassificado como informativo; W4 aprovou **esse teste dirigido**. Não reexecutar trabalho concluído.
- React PR #715 OPEN/DRAFT, HEAD `f043781a896a2d90d4f10eb72630eb2e7d48a0f6`, ahead 139 / behind 0, **9 branches**. Validate 1.689 PASS/exit 0, mas SEO snapshot interno falha; PII fail-closed e epoch A→B→A/logout tardio não corrigidos.
- Admin PR #4 OPEN/DRAFT, HEAD `c6846c618b89192074f18313bcb57efa3e3b5d45`, ahead 17 / behind 0, **2 branches**. Apenas RBAC por app indispensável à Independence; QA integrado pendente.
- **W00 nesta rodada:** sem commit próprio de produto, testes locais não executados (exit N/A), sem merge/deploy. Os cinco agendamentos W00–W4 foram consultados e estão habilitados nos horários originais.

## NOVO P0 — webhook pago após reclassificação do ingresso

**Achado W4, revisão estática, exploração NÃO reproduzida.** O commit W1 bloqueia a retomada de um Pix quando o ingresso se torna informativo, porém um Pix emitido anteriormente ainda pode ser pago remotamente. O webhook Asaas encaminha a confirmação a `CommercePaymentSettlementService::confirm()`, que no blob **`0fa1dddcf637915bdb8996377ed3ec72c8639c20`** emite `EventPass` sem revalidar a classificação atual do ticket. `AsaasCommerceWebhookService.php` blob `9a0d08a7` aciona a liquidação. **Risco: QR indevido após conversão para ficha informativa e pagamento já recebido**; não há prova de exploração nem de venda efetiva.

**Owner executivo: W1, condicionado a ownership exclusivo confirmado para os arquivos de liquidação e teste.** W1 deve verificar claim atual/owner antes de editar; caso haja claim de terceiro, solicitar `CEDO | agent_id | claim | HEAD | blob | SEM CONCORRÊNCIA` e registrar `ACEITO POR W1`, ou exigir patch direto do proprietário. W00 solicita ao mantenedor @petertecnetdev designação expressa do owner do serviço de liquidação, sem presumir autorização de escrita.

**Critérios de aceite obrigatórios do patch**:
1. Revalidar em transação e sob lock o estado comercial do ticket/produção/evento imediatamente antes da emissão, usando a política compartilhada sem relaxar a autorização; nenhum `EventPass` ou QR para ticket que se tornou `curatorial_information_only`.
2. Não descartar confirmação de dinheiro realmente recebido: preservar rastreabilidade do pagamento e criar estado/fluxo auditável de exceção para reconciliação ou estorno, com idempotência do webhook e replay, sem falsificar venda ou lançar crédito de produtor indevido. Verificar contratos de status/ledger antes de codificar; não simplesmente lançar exceção e perder o webhook.
3. Teste integrado em MySQL isolado: compra inicialmente legítima → Pix emitido → ticket reclassificado → webhook `PAYMENT_RECEIVED` → zero QR, zero emissão indevida, tratamento financeiro seguro e único sob replay e concorrência. Preservar caso positivo de venda legítima. Mock do provedor é suficiente para gate de código, sem alegar integração real Asaas.
4. Commit de produto com SHA, blobs, testes/exit code, CI no HEAD exato e revisão independente W4. Se sem ownership, entregar patch/teste executável ao owner e registrar bloqueio, sem contorno.

## Outros gates — não duplicar trabalho

- **W2:** patch PII em `UnverifiedListingPanel.js` blob `71e041d7` e teste `03943466` segue sem escrita autorizada; solicitar aplicação por owner. Auth `AuthContext.js` `78917a5a`, `authTokenStorage.js` `25bbc63d`, `authSessionSync.js` `79b446dc`, `AuthService.js` `a188c9fa` sem CEDO+ACEITO. Testar epoch monotônico A→B→A e logout tardio.
- **W3:** patch e teste HTTP exatos publicados no [PR #546](https://github.com/petertecnetdev/api.petertecnet.com.br/pull/546#issuecomment-6520605051), claim `20261030-0531-W3-organization-selfservice-provenance.md` blob `8e565a59`, `OrganizationService.php` blob `139ba544`, escrita bloqueada por safety. Mantenedor deve aplicar por fluxo permitido, sem ampliar `$fillable` nem dar autorização comercial. Controller `EventManagementController.php` blob `9c6eeac0` continua reservado Atlas/Genre; obter cessões ou patch dos owners. CI geral mantém 22 falhas (11 HTTP 403, 5 lifecycle, 3 arquitetura, 1 Pix payout, 2 periféricas), sem reduzir segurança para satisfazer asserções. AgentChat fora do caminho crítico.
- **W4:** auditoria independente dos novos SHAs, browser 320/360/390/430, auth, claims, RBAC cross-app, duplicação, checkout e webhook tardio; veto ao merge até todos gates aprovados.
- **Ledger:** teste `FinancialPayoutSecurityTest.php` blob `fa7d6d84`, claim `3607278d`; cessão W1 ou correção direta, mantendo HTTP 422 e zero destinos.
- **NP12:** após P0, validar operação real de descoberta por fontes autorizadas, deduplicação, vínculos, dados verificáveis, ingressos informativos sem venda, logs e monitoramento antes de declarar entrega integral.

**Próximo passo executivo único:** @petertecnetdev designar owner/claim exclusivo do `CommercePaymentSettlementService.php` no HEAD `689c4bec` e autorizar implementação segura do cenário `PAYMENT_RECEIVED` tardio por W1 ou proprietário atual. W4 revisará. **MERGE VETADO** até CI geral verde, QA e NP12; deploy somente mediante ordem específica.
