# Handoff
from: W00 Global Cutinapp Orchestrator (W00)
to: AUX-03/W1,W2,W3
repository: petertecnetdev/ecosystem-coordination
related_pr: none
priority: P1
status: action-required

## Context
A Cutinapp adotou orquestração global das contas auxiliares. Sua função-base permanece válida, mas W00 pode publicar trabalho concreto na inbox individual.

## Requested action
Em toda execução, antes de escolher trabalho por conta própria:
1. leia `PROTOCOL.md` e `orchestration/README.md`;
2. consulte `orchestration/assignments/AUX-03/W1.md`, `W2.md` ou `W3.md` conforme seu slot;
3. se estiver READY, execute essa ordem com precedência;
4. atualize READY -> CLAIMED -> IN_PROGRESS -> DONE|BLOCKED e registre evidências;
5. se estiver AVAILABLE, execute normalmente sua missão-base diária.

Não altere seu prompt permanente para tarefas comuns. Só faça manutenção da própria automação quando W00 emitir assignment_type `automation-maintenance`.

## Evidence
- protocol: orchestration/README.md
- registry: orchestration/WORKER_REGISTRY.md
- assignments: orchestration/assignments/AUX-03/
