agent_id: account-main-growth
agent: Revenue & Growth Operator · Cutinapp / Peter Tecnet
objective: Consolidar o WhatsApp Business como canal universal de notificações da API Peter Tecnet, com fila, auditoria, webhook, templates semânticos e integração segura com a Meta Cloud API.
repository: petertecnetdev/api.petertecnet.com.br
application: ecosystem-api
branch: agent/account-main/whatsapp-universal-notifications
area: app/Services, app/Jobs, app/Models, app/Http, database/migrations, routes, config, tests
time_start: 2026-09-25T11:20:00-03:00
status: IMPLEMENTING
scope: reutilizar AppNotificationService e a integração WhatsApp existente; remover suposição estrutural de +55; encapsular provider Meta; persistir tentativas/status; processar webhook idempotente; preservar login/OTP/e-mail/in-app; preparar contratos administrativos sem secrets.
concurrency_check: claims/active auditado; nenhuma claim ativa específica para WhatsApp/Meta Cloud API encontrada. Claims genéricas de Admin Center serão respeitadas e mudanças de frontend administrativo só ocorrerão se não colidirem.
commit: a7092bdfef375a79bcdbcb0b02874dcb5bd68468
pull_request: https://github.com/petertecnetdev/api.petertecnet.com.br/pull/525
validation: API CI run 36149117572 em execução; Composer manifest aprovado; install dependencies em execução no último checkpoint.
handoff: pending
next_step: concluir CI, corrigir eventuais falhas, integrar endpoints/admin sem colidir com claims, validar credenciais/templates/webhook Meta e executar teste real ponta a ponta.
