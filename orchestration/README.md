# Cutinapp Global Worker Orchestration

Esta pasta é o control plane assíncrono do W00 para workers auxiliares executados em outras contas ChatGPT.

## Autoridade
- `W00` é o orquestrador global da Cutinapp.
- W00 coordena W1-W4 da conta principal diretamente.
- W00 coordena AUX-01..AUX-11 indiretamente por estas filas GitHub.
- Workers AUX não precisam alterar a própria automação para receber trabalho novo.
- A função-base de cada worker permanece estável; a assignment atual pode sobrescrever temporariamente essa função.

## Precedência
1. P0 explícito do W00.
2. Assignment `READY` dirigida ao worker.
3. Handoff/action-required dirigido ao worker.
4. Função-base permanente do worker.

## Estado da assignment
- `AVAILABLE`: sem ordem específica; executar função-base.
- `READY`: ordem emitida por W00 e ainda não iniciada.
- `CLAIMED`: worker aceitou a ordem e está preparando execução.
- `IN_PROGRESS`: trabalho em andamento.
- `BLOCKED`: depende de ação externa.
- `DONE`: concluída com evidência.
- `CANCELLED`: cancelada por W00 antes de execução ou por emergência documentada.

W00 não deve substituir `CLAIMED` ou `IN_PROGRESS`, exceto por P0. Nesse caso deve registrar o cancelamento/handoff e preservar evidências.

## Ciclo do worker AUX
1. Ler `COMMANDS.md`, `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`.
2. Ler sua inbox em `orchestration/assignments/AUX-XX/WN.md`.
3. Ler claims e handoffs relevantes.
4. Se assignment estiver `READY`, executá-la antes da função-base.
5. Criar claim antes de alterar código.
6. Atualizar assignment para `CLAIMED`/`IN_PROGRESS`.
7. Executar e validar.
8. Registrar worklog/commit/PR/evidências.
9. Marcar `DONE` ou `BLOCKED`.
10. Se estiver `AVAILABLE`, executar a função-base diária normal.

## Regra de produtividade
Nenhum AUX deve ficar ocioso por ausência de assignment. `AVAILABLE` significa: execute a especialidade-base e entregue um resultado concreto.

## Comunicação
Resultados devem ser registrados nos mecanismos já existentes do repositório:
- `claims/`
- `messages/`
- `handoffs/`
- `worklogs/`
- `discussions/`

`orchestration/` serve para comando, alocação e visibilidade de capacidade; não substitui evidência de execução.
