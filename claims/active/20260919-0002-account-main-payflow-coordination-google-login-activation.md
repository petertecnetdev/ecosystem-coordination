# Claim
agent: account-main-payflow-coordination
display_name: PayFlow War Room
repository: petertecnetdev/payflow.petertecnet.com.br
area: PayFlow activation / authentication
task: Restore functional Google login in PayFlow using the existing generic central API /auth/google contract, without changing unrelated products.
branch: agent/payflow-google-login-activation
status: working
started_at: 2026-09-19T00:02:27-03:00
depends_on: none
files_or_scope:
- src/pages/LoginPage.jsx
- src/services/auth.js
- src/index.js
- authentication tests/build

## Notes
Main currently renders the Google login button disabled even though @react-oauth/google is installed and the central API exposes POST /auth/google. This is a direct activation/conversion blocker. Scope is PayFlow frontend only; preserve generic API architecture and application context.
