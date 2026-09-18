# Coordination Protocol

## 1. Leitura obrigatória
Todo ciclo começa lendo:
- `CURRENT_STATE.md`
- `PRIORITIES.md`
- `BLOCKERS.md`
- `claims/active/`
- mensagens recentes relacionadas ao projeto/frente

## 2. Claim
Crie:
`claims/active/YYYYMMDD-HHMM-<agent-id>-<slug>.md`

Formato:

```md
# Claim
agent: <agent-id>
repository: <owner/repo>
area: <área funcional>
task: <objetivo>
branch: <branch ou TBD>
status: working
started_at: <ISO-8601>
depends_on: <PR/claim/none>
files_or_scope:
- <caminho/área>

## Notes
<contexto curto>
```

Não iniciar o mesmo escopo de outro claim ativo sem handoff explícito.

## 3. Implementação
- preservar trabalho recente;
- branch/PR quando apropriado;
- nunca force-push;
- respeitar branch protection;
- evitar mudanças destrutivas;
- preservar arquitetura central genérica e reutilizável;
- verificar dependências frontend/backend.

## 4. Handoff
Crie:
`messages/YYYYMMDD-HHMM-<from>-to-<to>-<slug>.md`

Formato:

```md
# Handoff
from: <agent-id>
to: <agent-id ou role>
repository: <owner/repo>
related_pr: <# ou none>
priority: P0|P1|P2|P3
status: action-required|informational

## Context
...

## Requested action
...

## Evidence
- commit:
- PR:
- checks:
```

## 5. Encerramento
- registrar commit/PR/checks;
- marcar `completed`, `blocked` ou `handoff`;
- criar registro em `claims/completed/`;
- remover o ativo somente após existir o registro concluído.

## 6. Blockers
Blockers globais de alto impacto entram em `BLOCKERS.md`.

## 7. Prioridades
`PRIORITIES.md` é consolidado pela frente Tech Lead/Coordination. Outros agentes propõem mudanças via mensagem.

## 8. Segurança
Nunca registrar tokens, senhas, chaves, credenciais, segredos de produção ou dados pessoais desnecessários.
