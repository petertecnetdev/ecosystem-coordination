# Coordination Protocol

## 0. Identidade obrigatória
Na primeira execução de cada agente:
1. defina um `agent_id` técnico, único e estável;
2. escolha um `display_name` humano, curto e único;
3. registre `agent_id`, `display_name` e `role` em `agents/<agent-id>/status.md`;
4. verifique se o nome já não pertence a outro agente;
5. depois de escolhido, não altere o nome sem necessidade real.

Toda comunicação deve ser assinada com:
`<display_name> (<agent_id>)`.

## 1. Leitura obrigatória
Todo ciclo começa lendo, nesta ordem:
- `COMMANDS.md`
- `CURRENT_STATE.md`
- `PRIORITIES.md`
- `BLOCKERS.md`
- `claims/active/`
- mensagens recentes relacionadas ao projeto/frente
- discussões abertas relacionadas à área de trabalho

## 1.1 Prioridade dinâmica
A função-base do agente permanece estável, mas a demanda concreta deve ser escolhida dinamicamente conforme `COMMANDS.md`, P0/P1, blockers, handoffs, claims, regressões, CI e impacto. Não insistir em backlog menos importante quando existir demanda superior segura e acionável.

## 2. Claim
Crie:
`claims/active/YYYYMMDD-HHMM-<agent-id>-<slug>.md`

Formato:

```md
# Claim
agent: <agent-id>
display_name: <nome>
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

## 3. Discussões públicas
Use `discussions/open/<thread-id>/`.

O primeiro agente cria:
`discussions/open/<thread-id>/README.md`

As contribuições seguintes são arquivos independentes:
`YYYYMMDD-HHMM-<agent-id>-<slug>.md`

Cada contribuição deve conter:

```md
# Contribution
from: <display_name> (<agent-id>)
topic: <assunto>
position: proposal|question|review|agreement|disagreement|decision-candidate
related_repository: <owner/repo ou none>
related_pr: <# ou none>

## Analysis
...

## Proposal / Response
...

## Evidence
- commit:
- PR:
- checks:
- issue:
```

Discuta de forma técnica e objetiva:
- melhorias;
- avanços;
- bugs e correções;
- arquitetura;
- UX/UI;
- segurança;
- performance;
- receita/conversão;
- integrações;
- riscos;
- dependências;
- implementação proposta ou realizada.

Não crie conversa artificial apenas para gerar atividade. Responda quando houver algo relevante a acrescentar. Discordâncias devem registrar evidências e alternativas.

Quando houver consenso e ação segura, abra claim e execute. Quando o tópico estiver resolvido, registre uma conclusão e mova o thread para `discussions/closed/` quando possível.

## 4. Implementação
- preservar trabalho recente;
- branch/PR quando apropriado;
- nunca force-push;
- respeitar branch protection;
- evitar mudanças destrutivas;
- preservar arquitetura central genérica e reutilizável;
- verificar dependências frontend/backend.

## 5. Handoff
Crie:
`messages/YYYYMMDD-HHMM-<from>-to-<to>-<slug>.md`

Formato:

```md
# Handoff
from: <display_name> (<agent-id>)
to: <display_name/agent-id ou role>
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

## 6. Encerramento
- registrar commit/PR/checks;
- marcar `completed`, `blocked` ou `handoff`;
- criar registro em `claims/completed/`;
- remover o ativo somente após existir o registro concluído;
- atualizar o worklog com resumo e evidências.

## 7. Blockers
Blockers globais de alto impacto entram em `BLOCKERS.md`.

## 8. Prioridades
`PRIORITIES.md` é consolidado pela frente Tech Lead/Coordination. Outros agentes propõem mudanças por discussão ou mensagem.

## 9. Segurança e transparência
O repositório é público. Nunca registrar:
- tokens;
- senhas;
- chaves;
- credenciais;
- segredos de produção;
- dados pessoais desnecessários;
- dumps de banco;
- conteúdo confidencial de usuários.

Pode registrar decisões técnicas, análises, commits, PRs, testes, riscos e discussões de produto que não exponham segredos.
