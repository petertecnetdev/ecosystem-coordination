# Handoff
from: Sol Interactive (account-plus-interactive)
to: Infra / Deploy / Tech Lead
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #537
priority: P1
status: action-required

## Context
A auditoria do envio de e-mail de Direct confirmou que a aplicação já possui o fluxo correto via MessageEngagementService/MessageEngagementMail. O fluxo respeita email_new_messages, mute/notification_level, agrupamento, cooldown e lembretes; o AppNotificationService não envia um segundo e-mail para evitar duplicidade.

Na VPS petertecnetserver, a inspeção mostrou ausência de processos `php artisan queue:work` e `php artisan schedule:work`. Os arquivos `/etc/supervisor/conf.d/petertecnet-queue.conf` e `/etc/supervisor/conf.d/petertecnet-scheduler.conf` existem, mas ambos estão com `autostart=false`.

O envio depende de `ProcessMessageEngagement` na fila Redis e de `messaging:dispatch-engagement`, agendado a cada minuto. Com worker/scheduler parados, o código não consegue entregar os e-mails de Direct em produção.

## Requested action
No próximo ciclo explicitamente autorizado de deploy/VPS, reconciliar a configuração Supervisor com a configuração versionada, iniciar/validar queue worker e scheduler, e executar um teste runtime de Direct com confirmação de entrega de e-mail. Não criar um segundo mecanismo síncrono de e-mail, pois isso duplicaria o fluxo existente.

## Evidence
- commit: 765ff24c3197913e8ae549877d68485833cd6878
- PR: https://github.com/petertecnetdev/api.petertecnet.com.br/pull/537
- checks: local `php artisan test tests/Feature/MessagingEmailNotificationTest.php tests/Feature/MessageEngagementDirectEmailTest.php` => 3 cenários, 10 assertions, exit code 0
- runtime inspection: nenhum processo artisan de queue/scheduler visível; configs Supervisor com autostart=false
