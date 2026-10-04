# W08 — API physical cleanup batch E

Data: 2026-10-03 21:31–21:32 America/Sao_Paulo

## Resultado

- API_BRANCH_COUNT_BEFORE: 499
- DELETED_VERIFIED_THIS_RUN: 32
- API_BRANCH_COUNT_AFTER: 467
- NET_REDUCTION: 32
- HIGH_RISK_SECOND_REVIEWS: 8
- DELETE_READY_REMAINING: 0 (no shard W08 auditado nesta rodada)
- UNIQUE_USEFUL: 0
- NEW_BRANCHES_CREATED: 0

## Execução

- Commit do workflow: `4a69bea43f7e83fd8e62f7fe25f3c22b419887d6`
- Run: https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/37165172557
- Job: https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/37165172557/job/111326492850
- Conclusão: `success`
- Sumário do log: `deleted=32 already_absent=0 changed=0 failures=0`
- Verificação posterior: todas as 32 referências ausentes; contagem live 467.

## Admin Center

- ADMINCENTER_COUNT: 2 (`main`, `feat/media-library-admin`)
- PR #2: merged; source branch ausente.
- PR #1: KEEP; aberto e dependente do API PR #534, que permanece aberto/não mergeável.
- Lacuna de governança observada: API de branches reporta `protected=false` para `main`; W08 não possui permissão administrativa para corrigir proteção.

## Exclusões verificadas

- `feature/event-items-bulk-selection` @ `2e5194fb7bb803273bcae738c0ff601a20e9d20f`
- `feature/event-list-weekly-agenda-strategy-20260910` @ `5c7677ef14d00f740f7480068313cf50ecc142e4`
- `feature/event-producer-notifications-v2` @ `0b78dc98f37466d5c02ce10e5be8be676def4925`
- `feature/financial-ledger-reconciliation-20260903` @ `6c2d9e167b6f6ad8dd8b1a6e3ae9c1bef73c1678`
- `feature/generic-catalog-production-20260902` @ `7f5349fc32a96edfb87afc2cbef1c9b5ede8f0e4`
- `feature/generic-fulfillment-qr-privacy-20260902` @ `e78c8f93cd16f8bd79f91b24848e1b41d90b57c1`
- `feature/generic-social-messaging` @ `7c607f646c70a33d2f924aad1e6a7ff5b54b025f`
- `feature/generic-social-messaging-copy` @ `1c8746ad3fd34e1be7616c30ac9916953037411c`
- `feature/laora-production` @ `e5fb3b79734fb1c2b25c2b40c306b10c6a5bf335`
- `feature/laora-production-hardening` @ `0e258a47a283db641d6e5885827560e8d6bc5843`
- `feature/leasing-contextual-roles` @ `b92a19f17a0439a8294bd934a32f64bf0e172c52`
- `feature/peter-account-ecosystem-v2` @ `57bf8d1a942edf8063637cd121f6f654e4408ba2`
- `feature/producer-media-library` @ `beb2ab3523f2f0cdf340a7fc7f9d1e8a16cb45f5`
- `feature/producer-media-library-clean` @ `beb2ab3523f2f0cdf340a7fc7f9d1e8a16cb45f5`
- `feature/producer-media-library-final` @ `beb2ab3523f2f0cdf340a7fc7f9d1e8a16cb45f5`
- `feature/producer-media-library-final2` @ `beb2ab3523f2f0cdf340a7fc7f9d1e8a16cb45f5`
- `feature/producer-media-library-pr` @ `beb2ab3523f2f0cdf340a7fc7f9d1e8a16cb45f5`
- `feature/producer-media-library-ready` @ `2edcbd8da0c11affa966dbd916593ea837530b8f`
- `feature/producer-media-library-release` @ `beb2ab3523f2f0cdf340a7fc7f9d1e8a16cb45f5`
- `feature/producer-media-library-v2` @ `beb2ab3523f2f0cdf340a7fc7f9d1e8a16cb45f5`
- `feature/producer-media-library-v3` @ `beb2ab3523f2f0cdf340a7fc7f9d1e8a16cb45f5`
- `feature/public-nexus-services-by-cnpj` @ `2a1382af8454809e06d349291a513ad39875466b`
- `feature/rasoio-operations-dashboard` @ `cf6a3f43476b4917fd64f667b788f662d8edb2ae`
- `feature/recovery-channel-attribution-20260908` @ `1bd4875c0e5f702d6f6b18f21fc6c0918ceb85ff`
- `feature/cutinapp-artist-groups` @ `e0ac2fc5e93fa65e81649bee886adfe8b8356b05`
- `feature/ecosystem-impersonation-v2` @ `91a2701914200682a0c6ff562832e64cfd8d4813`
- `feat/social-feed-facebook-main` @ `1b29ec632a45f6f6ba57b4908168b0cde8d2dae8`
- `feature/admin-command-center-v2` @ `4690a8660942ddc5ea9b0fbb784b289c88c3d1ed`
- `feature/cutinapp-domain-2026` @ `5339b50f242403dc726310a478353e7455a224bd`
- `feature/cutinapp-mercadopago-auto-split-20260918` @ `9e906c7b8bc04f55b73f78056df1de75cbc15701`
- `feature/cutinapp-participant-social` @ `84badb935bc90ad8a22d95954d6dd9e9b0f3e6cb`
- `feature/ecosystem-impersonation` @ `c1759df7b87c65d982e0ee83cff06b4e5c898b96`

## Segunda revisão high-risk

- `feature/financial-ledger-reconciliation-20260903`: 24 arquivo(s) sensível(is); decisão preservada por integração/PR merged ou supersessão auditada.
- `feature/generic-catalog-production-20260902`: 4 arquivo(s) sensível(is); decisão preservada por integração/PR merged ou supersessão auditada.
- `feature/generic-fulfillment-qr-privacy-20260902`: 4 arquivo(s) sensível(is); decisão preservada por integração/PR merged ou supersessão auditada.
- `feature/recovery-channel-attribution-20260908`: 1 arquivo(s) sensível(is); decisão preservada por integração/PR merged ou supersessão auditada.
- `feature/ecosystem-impersonation-v2`: 5 arquivo(s) sensível(is); decisão preservada por integração/PR merged ou supersessão auditada.
- `feature/admin-command-center-v2`: 1 arquivo(s) sensível(is); decisão preservada por integração/PR merged ou supersessão auditada.
- `feature/cutinapp-mercadopago-auto-split-20260918`: 3 arquivo(s) sensível(is); decisão preservada por integração/PR merged ou supersessão auditada.
- `feature/ecosystem-impersonation`: 5 arquivo(s) sensível(is); decisão preservada por integração/PR merged ou supersessão auditada.

## Segurança

- Heads revalidados imediatamente antes do disparo e travados por SHA.
- Nenhuma referência do shard W07 foi incluída.
- Nenhum código de aplicação, deploy manual, force-push, reset ou `update_ref` de exclusão.

