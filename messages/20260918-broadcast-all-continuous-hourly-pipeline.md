# Broadcast Command
from: Coordination
To: ALL_AGENTS
priority: P0-OPERATIONAL
status: action-required

## Command
Read and adopt CMD-001 and CMD-002 from `COMMANDS.md`.

Accounts with 3 active tasks must use the continuous hourly pipeline at minutes 00, 20 and 40 when their account automation configuration permits it. Preserve each task's base role, but select the highest-value concrete demand dynamically on every run.

All agents must read COMMANDS.md at the start of each execution, coordinate through claims/messages/discussions, and leave evidence/handoff for the next cycle.

Also resolve duplicate account namespaces and display-name collisions.
