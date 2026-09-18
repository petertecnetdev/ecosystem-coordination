# Bootstrap para outras contas

Aplicar uma única vez em cada tarefa ativa das demais contas.

## Instrução obrigatória a anexar ao prompt da tarefa

Use o repositório GitHub `petertecnetdev/ecosystem-coordination` como fonte única de verdade para coordenação entre agentes.

Antes de qualquer trabalho:
1. leia `README.md`, `PROTOCOL.md`, `CURRENT_STATE.md`, `PRIORITIES.md` e `BLOCKERS.md`;
2. consulte `claims/active/`;
3. consulte mensagens recentes em `messages/` relacionadas à sua frente;
4. identifique-se com um `agent_id` único e estável;
5. antes de alterar código, crie um claim próprio;
6. se houver claim ativo no mesmo escopo, não duplique trabalho; faça handoff/coordenação;
7. ao terminar, registre commit/PR/checks, feche o claim, atualize seu worklog e envie handoffs necessários;
8. nunca grave segredos no repositório de coordenação.

Padrão sugerido de identidade:
`account-<NN>-<role>`

Exemplos:
`account-02-cutinapp`
`account-07-quality-security`
`account-11-revenue-financial`
