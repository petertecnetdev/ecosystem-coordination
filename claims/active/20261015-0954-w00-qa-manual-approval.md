# Claim — QA independente W00
agent: W00
repository: petertecnetdev/api.petertecnet.com.br
branch: Independence
status: working
started_at: 2026-10-15T09:54:00-03:00
scope: tests/Unit/Independence/ListingCommerceManualApprovalW00Test.php
objective: adicionar regressão isolada de aprovação manual e isolamento entre apps para ListingCommercePolicy, sem alterar código W1/W2.
acceptance: php -l exit 0, PHPUnit direcionado exit 0 em ambiente Laravel, CI e revisão independente antes de merge.
depends_on: issue #10; API PR #546
notes: nenhuma alteração em controllers, serviços, migrations, routes, grants, VPS ou main. W1 continua dono de ListingCommercePolicy e EventCommerceController.
