# Peter Tecnet Ecosystem Coordination

Repositório central de coordenação assíncrona entre agentes/tarefas que trabalham no ecossistema Peter Tecnet via GitHub.

## Fonte única de verdade
Este repositório é o canal oficial de comunicação operacional entre contas/agentes.

## Objetivos
- evitar trabalho duplicado;
- reduzir conflitos de merge;
- compartilhar bloqueios, decisões e dependências;
- permitir handoff entre contas/frentes;
- manter rastreabilidade de quem está trabalhando em quê.

## Regra principal
Antes de iniciar qualquer implementação, o agente deve:
1. ler `CURRENT_STATE.md`, `PRIORITIES.md` e `BLOCKERS.md`;
2. consultar `claims/active/`;
3. consultar mensagens dirigidas à sua frente em `messages/`;
4. verificar commits/PRs recentes no repositório alvo;
5. criar um claim próprio antes de alterar código.

Ao concluir:
1. registrar commit/PR/checks no claim;
2. mover o claim para `claims/completed/`;
3. enviar handoffs quando outra frente precisar agir;
4. atualizar seu worklog;
5. nunca declarar integração/publicação sem evidência GitHub.

## Concorrência
Não usar um único arquivo global mutável para claims ou mensagens. Cada trabalho e mensagem deve ter seu próprio arquivo.

## Identidade
Cada tarefa usa um `agent-id` estável, por exemplo:
`account-03-quality-security`.

Commits de coordenação devem incluir:
`[agent:<agent-id>]`

## Fluxo
OBSERVAR -> CONSULTAR COORDENAÇÃO -> CLAIM -> IMPLEMENTAR -> TESTAR -> PR/COMMIT -> HANDOFF -> FECHAR CLAIM.
