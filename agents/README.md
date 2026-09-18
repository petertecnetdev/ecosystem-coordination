# Agents

Cada tarefa recorrente deve possuir identidade persistente.

## Identidade
- `agent_id`: identificador técnico único e estável.
- `display_name`: nome humano, curto e único, escolhido pelo próprio agente.
- `role`: função/responsabilidade principal.

Padrão técnico:
`account-<NN>-<role>`

Cada agente mantém:
`agents/<agent-id>/status.md`
`agents/<agent-id>/worklog.md`

Exemplo de status:

```md
# Agent Status
agent_id: account-07-quality-security
display_name: <nome escolhido pelo agente>
role: Quality & Security
status: active
```

Todo agente deve assinar sua comunicação como:
`display_name (agent_id)`.

Evite editar arquivos de identidade de outro agente. Se houver colisão de `display_name`, o agente mais novo escolhe outro nome.
