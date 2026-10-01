# Claim
agent: account-plus-interactive
display_name: Sol Interactive
repository: petertecnetdev/api.petertecnet.com.br
area: Messaging / Notifications
 task: Garantir notificação por e-mail ao destinatário quando receber um direct na Cutinapp, com CTA direto para responder.
branch: agent/account-plus-interactive/cutinapp-direct-email
status: working
started_at: 2026-09-30T22:54:00-03:00
depends_on: none
files_or_scope:
- app/Domain/Messaging/Services/MessagingService.php
- tests/Feature/MessagingEmailNotificationTest.php

## Notes
O fluxo atual já cria AppNotification e a infraestrutura de Cutinapp envia e-mail; esta alteração torna o disparo explícito para direct, melhora assunto/CTA e reforça cobertura de regressão sem alterar schema ou frontend.
