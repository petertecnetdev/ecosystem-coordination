# Global Commands

Este arquivo contém ordens operacionais globais para os agentes do ecossistema Peter Tecnet.

Todos os agentes devem lê-lo no início de cada execução, antes de selecionar trabalho.

## CMD-001 — Continuous hourly pipeline
status: ACTIVE
target: ALL_ACCOUNTS
priority: P0-OPERATIONAL

### Schedule standard
Para contas com 3 tarefas ativas:
- Task A: hourly at minute 00
- Task B: hourly at minute 20
- Task C: hourly at minute 40

Cada tarefa continua com frequência máxima de 1 execução por hora, mas a conta inicia um novo ciclo a cada 20 minutos.

Para contas com 5 tarefas, manter escalonamento equivalente de 12 minutos quando já configurado.

### Dynamic demand assignment
A responsabilidade-base de cada agente permanece, porém a prioridade concreta de cada execução é dinâmica.

No início de cada ciclo, escolher trabalho nesta ordem:
1. P0 aberto em BLOCKERS.md;
2. comando global ACTIVE aplicável;
3. handoff action-required dirigido ao agente/role;
4. regressão crítica ou falha de CI relacionada ao seu domínio;
5. claim/handoff que precise de revisão para destravar integração;
6. P1 de maior impacto;
7. oportunidade segura de maior impacto em receita, conversão, estabilidade, segurança ou arquitetura;
8. backlog P2/P3 apenas quando não houver trabalho mais importante.

Se a demanda mais importante estiver fora da especialidade principal do agente, ele pode assumir somente quando tiver capacidade clara e o trabalho não estiver claimado. Caso contrário, deve encaminhar ao agente apropriado e escolher a próxima prioridade.

### Continuity
Ao finalizar:
- registrar evidências;
- atualizar worklog;
- fechar claim;
- criar handoff para o próximo agente quando houver continuidade;
- deixar explícito o próximo ponto recomendado.

O agente seguinte deve ler esse estado e continuar, revisar ou escolher outro trabalho de maior prioridade.

### No artificial idling
Se não houver blocker, handoff ou claim pendente, o agente deve buscar trabalho seguro e útil dentro de sua função. Não criar atividade artificial nem duplicar trabalho.

## CMD-002 — Identity cleanup
status: ACTIVE
target: ALL_AGENTS
priority: P1-COORDINATION

Regularizar agent_id/display_name duplicados ou namespaces de conta conflitantes. Cada conta deve possuir namespace exclusivo e cada agente deve possuir display_name único e estável.

Quando concluído, registrar no status do agente e no worklog.
