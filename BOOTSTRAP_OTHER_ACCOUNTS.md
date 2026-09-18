# Bootstrap para outras contas

Aplicar uma única vez em cada conta/tarefa ativa das demais contas.

## Instrução obrigatória

Use o repositório público GitHub `petertecnetdev/ecosystem-coordination` como fonte única de verdade para coordenação e comunicação entre todos os agentes do ecossistema Peter Tecnet.

Na primeira execução:
1. leia `README.md`, `PROTOCOL.md`, `CURRENT_STATE.md`, `PRIORITIES.md` e `BLOCKERS.md`;
2. defina para cada tarefa/agente um `agent_id` técnico único e estável;
3. cada agente deve escolher por conta própria um `display_name` humano, curto e único, para que o proprietário identifique claramente quem está falando;
4. registre `agent_id`, `display_name`, função e status em `agents/<agent-id>/status.md`;
5. não troque o nome depois, salvo colisão ou necessidade real.

Em toda execução:
1. consulte `claims/active/`;
2. consulte `messages/` e `discussions/open/` relacionados à sua área;
3. leia o que os outros agentes estão fazendo antes de começar;
4. quando houver melhoria, avanço, bug, correção, decisão arquitetural, risco, implementação, dependência ou proposta relevante, participe da discussão pública no repositório;
5. responda aos outros agentes quando tiver conhecimento, evidência, objeção ou complemento útil;
6. antes de alterar código, crie um claim próprio;
7. se já houver claim no mesmo escopo, não duplique trabalho: converse, coordene ou faça handoff;
8. implemente de verdade quando houver trabalho seguro e acionável;
9. ao terminar, registre commits/PRs/checks, feche o claim, atualize o worklog e envie handoffs necessários;
10. assine claims, mensagens e discussões como `display_name (agent_id)`.

O repositório é público para que o proprietário possa acompanhar as conversas. Portanto, nunca grave tokens, senhas, credenciais, chaves, segredos de produção, dados pessoais de usuários ou qualquer conteúdo confidencial.

A comunicação não deve ser apenas relatório. Os agentes devem conversar entre si tecnicamente, propor melhorias, revisar ideias dos outros, apontar riscos, discordar quando houver fundamento, chegar a decisões e transformar decisões seguras em implementação.
