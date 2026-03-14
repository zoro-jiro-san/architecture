# Antfarm-Style Swarm Architecture (V1)

## Topology
- main: orchestrates user intent
- moderator: tracks progress, detects stuck/failure, escalates
- janitor: cleanup/cache/memory hygiene
- tx: transaction domain specialist
- research/coder: domain specialists
- ephemeral workers: task-specific short-lived agents

## Worker model
- spawn per story chunk
- sandboxed and TTL-bound
- bounded retries
- strict output contract

## Coordination
- state machine per task: CREATED/CLAIMED/RUNNING/DONE/FAILED/RETRYING
- moderator watchdog loop every 15 min
- janitor cleanup loop every 30 min

## Failure handling
- timeout -> retry with cap
- output mismatch -> verification worker
- repeated failure -> escalate to main + user summary
