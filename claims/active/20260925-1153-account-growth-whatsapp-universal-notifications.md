# CLAIM — Universal WhatsApp Notifications

- status: IMPLEMENTING
- owner: account-growth
- started_at: 2026-09-25T11:53:00-03:00
- scope: `petertecnetdev/api.petertecnet.com.br`
- goal: consolidate Peter Tecnet WhatsApp Cloud API as a reusable notification channel with queue, audit persistence, webhook status processing, template mapping, preferences and tests.
- exclusions: Admin Center UI is not modified while active Admin Center claims exist; integration will expose backend data/endpoints suitable for that UI.
- coordination: preserve existing WhatsApp onboarding/authentication, email, in-app notifications, and app/establishment isolation.
- implementation_branch: `feat/universal-whatsapp-notifications`
- implementation_commit: `a311d818d42c0d7558612d5a534c8a2e37d4c426`
- pull_request: `petertecnetdev/api.petertecnet.com.br#526`
- validation: PR mergeable with no conflicts; repository exposed no GitHub Actions/status checks for the commit. Container PHP 8.4 is available, but direct repository clone is blocked by network isolation, so automated PHPUnit execution remains unproven in this run.
- external_gate: production end-to-end requires Meta WABA/Phone Number ID/permanent System User token/App Secret/webhook verify token and approved physical templates in the production `.env`/Meta Business configuration. No secret is requested or stored in Git.
