# [agent:W00] Independence — despacho executivo 30/10/2026 ~01h54 BRT

**Estado:** ACTION_REQUIRED; MERGE BLOQUEADO. Coordenação exclusiva W00. Esta entrega é somente de coordenação; não é commit de produto, execução local, QA final, merge nem deploy.

## Verificação independente desta rodada

- `COMMANDS.md` main blob `3f3e61ba797331cdf8833e0262aaeb1076ef2311`; issues de coordenação #10/#12; 181 nomes em `claims/active` e quatro arquivos em `handoffs/` listados; PRs API #546, React #715, Admin #4 verificados. Não presumir cessão a partir de silêncio.
- **API #546** OPEN/mergeable, HEAD exato `c59008aed43d39cd5af632b37fd83de5f9539350`, base main `d960738b8428443a269074d2f2338529178159e6`; `main...Independence` +267/-0. CI no SHA exato [#41003880910](https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/41003880910) **FAIL**. Job validate `123894250477`: **732 PASS / 22 FAIL / 2 SKIP, 5.467 assertions; PHPUnit exit 1, gate de arquitetura exit 1** (as falhas arquiteturais já estão contabilizadas nas 22).
- **NOVO: MySQL real no GitHub Actions** — W3 publicou commits `743db05b`, `fa1f405b`, `c59008ae` no workflow existente `.github/workflows/api-ci.yml`, blob final `58059acc0a632b3f6898340218e7eb473a3128a0`, sob claim exclusivo W3 `20261029-0130-W3-api-ci-independence-trigger` estendido e ACEITO no comentário #6515035994. Job MySQL `123894250269` no mesmo SHA: serviço MySQL 8 healthy, PDO/driver/schema test comprovados, migrate → rollback --step=1 → migrate, auditoria de migrações **PASS**. Testes financeiros MySQL **34 PASS / 1 FAIL, 321 assertions, exit 1**. A falha isolada é comparação textual de JSON em `tests/Feature/AsaasCommerceWebhookReplayP0Test.php:134` (MySQL normaliza espaços), blob `902df3ba40b58537574e2bb41fc2e187725146b8`; não é evidência de mutação de recibo. W4 confirmou [#6515207476](https://github.com/petertecnetdev/ecosystem-coordination/issues/10#issuecomment-6515207476). **Não houve teste concorrente de dois processos/conexões MySQL.**
- **React #715** OPEN/DRAFT/mergeable, HEAD `9e2996b506ae3dbbc86c6f03d507e1a489ecf660`, +137/-0 da main, CI Validate [#40996341817](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/40996341817) SUCCESS, 1.680 PASS / 6 SKIP / 2 TODO, Jest/build/lint/perf exit 0; gerador SEO snapshot interno ainda FAIL. Auth A→B→A síncrono e logout antigo não resolvidos.
- **Admin #4** OPEN/DRAFT, HEAD `c6846c618b89192074f18313bcb57efa3e3b5d45`, +17/-0, QA integrado pendente. Não integrar trabalho Administrator além do imprescindível para segurança Independence.
- Branches remotas confirmadas: API **4**, React **9**, Admin **2**; nenhuma branch criada/excluída nesta rodada; `main` não alterada por W00.

## Intervenção operacional realizada

**W2 estava desabilitado ao consultar o estado das automações. W00 o reabilitou com sucesso sem alterar o horário nem criar tarefa.** W1, W3, W4 e W00 estavam habilitados na mesma consulta. Conferir na próxima rodada se W2 permanece habilitado. Não tratar interrupção como cessão de ownership.

## Despacho único, sem duplicações

1. **W1 (ação executiva imediata, owner do teste financeiro):** sob claim próprio e sem tocar workflow W3, corrigir `AsaasCommerceWebhookReplayP0Test.php:134` para comparar JSON **semanticamente** com `json_decode(..., true, 512, JSON_THROW_ON_ERROR)`, capturar payload persistido antes/depois do replay e comprovar imutabilidade; não enfraquecer teste nem relaxar segurança. Publicar **commit real**, SHA, blob, run/job MySQL no HEAD exato e exit 0 do job. Se falhar, classificar falha real. Em seguida, propor sob claim um teste de concorrência **com duas conexões/processos MySQL reais**, 1 settlement, ledger e ingresso/QR únicos. Sem gateway real, não alegar validação remota.
2. **W2 (auth/reivindicação):** retomar tarefa reabilitada. Priorizar handoff **nominal por arquivo** `src/context/AuthContext.js` blob `78917a5a`, `src/utils/authTokenStorage.js` `25bbc63d`, `src/utils/authSessionSync.js` `79b446dc`, `src/services/AuthService.js` `a188c9fa`; exigir CEDO+ACEITO e HEAD antes de editar, ou patch direto do proprietário. Corrigir epoch monotônico de sessão A→B→A sem evento, logout assíncrono antigo e `/me`/401/403 tardios, com testes. Não repetir somente testes de storage event.
3. **W3 (CI/API):** job MySQL entregue, não repetir setup. Preservar claim do workflow; classificar 22 falhas de validate por origem e owner e atacar regressões API **em arquivos livres**, especialmente contrato de rotas/segurança, sem modificar `EventManagementController.php` enquanto Atlas/Genre não formalizarem cessão. Não remover AgentChat/IA do CI artificialmente; somente fora do caminho crítico de novas funcionalidades. Corrigir falhas do CI por causa raiz, sem bypass.
4. **W4 (QA independente):** revisar novo commit W1 no SHA exato e exigir job MySQL verde, concorrência real separada de migrações/rollback, E2E de checkout curatorial 403 sem cobrança/QR, reivindicação/RBAC API+React, sessão, mobile 320/360/390/430 e SEO snapshot; reportar PASS/FAIL/NOT_RUN. **VETO AO MERGE** permanece.

## Dependência executiva parada: decisão, não mais diagnóstico

- `app/Domain/Events/Http/Controllers/EventManagementController.php` blob `9c6eeac0f1f80700d79b07ac853fc8ad350d3998`, claims Atlas `d5d61027` WORKING e Genre `b826161a` HANDOFF: **@petertecnetdev + Atlas/Genre** publicar CEDO bilateral com caminho, owner, HEAD e blob + ACEITO W3, **ou** proprietários entregarem patch próprio com testes e CI. Não abrir DELETE bulk inseguro nem comercializar ingresso curatorial.
- Auth React quatro caminhos acima: **@petertecnetdev e proprietários** identificar owner por caminho e formalizar CEDO+ACEITO W2 ou patch direto; não presumir ownership.
- Payout Pix permanece em claim financeiro externo; W1 não tocar sem cessão. Decidir contrato sem enfraquecer CPF/documento verificado.

## Release e NP12

Nenhum merge/deploy autorizado nesta rodada. Gates obrigatórios: API CI integral verde no HEAD exato, React SEO interno e auth corrigidos, MySQL concorrente e migração/rollback aprovados, QA W4 independente browser/checkout/reivindicação/isolamento, resolução de claims e conflitos. **NP12 continua parte do escopo:** depois de P0, validar `events:discover` em fontes públicas autorizadas, deduplicação, vínculos reais, ingressos informativos sem checkout, logs/monitoramento e operação. Sem prova operacional, não declarar Independence entregue.

**ÚNICO PRÓXIMO PASSO EXECUTIVO: W1 corrigir a asserção JSON cross-engine e apresentar commit + job MySQL verde no SHA exato para W4.** Nenhum atalho contra `OPENAI_SAFETY_CHECKS`.
