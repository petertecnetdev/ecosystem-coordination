# Claim
agent: account-plus-interactive
display_name: Sol Interactive
repository: petertecnetdev/api.petertecnet.com.br
area: Messaging / Notifications
task: Garantir notificação por e-mail ao destinatário quando receber um direct na Cutinapp, com CTA direto para responder.
branch: agent/account-plus-interactive/cutinapp-direct-email
status: review
started_at: 2026-09-30T22:54:00-03:00
depends_on: runtime queue/scheduler availability
files_or_scope:
- app/Domain/Messaging/Services/MessagingService.php (audit only; no behavior change required)
- app/Domain/Messaging/Services/MessageEngagementService.php (audit only; existing owner of direct email delivery)
- tests/Feature/MessagingEmailNotificationTest.php (validated locally)
- tests/Feature/MessageEngagementDirectEmailTest.php (new regression coverage)

## Notes
A auditoria confirmou que o e-mail de Direct já é implementado por MessageEngagementService/MessageEngagementMail, com preferência email_new_messages, agrupamento, cooldown, lembretes e link /messages?conversation=<id>. AppNotificationService mantém send_email=false de propósito para evitar duplicidade.

PR: https://github.com/petertecnetdev/api.petertecnet.com.br/pull/537
commit: 765ff24c3197913e8ae549877d68485833cd6878
validation: 3 cenários, 10 assertions, exit code 0 no worktree da VPS; API CI em execução.

Operational blocker: na VPS inspecionada não há processos queue:work nem schedule:work ativos; /etc/supervisor/conf.d/petertecnet-queue.conf e petertecnet-scheduler.conf estão com autostart=false. O envio efetivo depende da fila Redis e do comando messaging:dispatch-engagement agendado a cada minuto. Não houve alteração da VPS porque este trabalho não recebeu autorização explícita de deploy/produção.
