# Architecture Deep Dive

## System Goals
1. Security-first automation
2. High throughput on Raspberry Pi without memory runaway
3. Explicit trust boundaries between agent roles
4. Reliable long-term learning and architecture evolution

## Agent Responsibility Matrix

| Agent | Primary Purpose | Sandbox Mode | Scope | Risk Level | Notes |
|------|------------------|--------------|-------|-----------|-------|
| main | orchestration + policy | all | session | Medium | user-facing control plane |
| research | external intel/API | all | session | Medium | disposable execution |
| coder | code/test/build | all | session | Medium | constrained tools |
| tx | transaction domain | all | agent | High | strict preflight + confirmation |
| janitor | host hygiene | off | host | High | system maintenance only |

## Data Flow
1. User request enters `main`
2. `main` classifies domain
3. Task routed to specialist
4. Specialist returns structured results
5. `main` synthesizes user-safe response
6. Learnings distilled into durable docs

## Learning Architecture
- Operational notes: `learnings.md`
- Durable principles: architecture docs + policy docs
- Distillation gate: do not persist noisy/unverified claims

## Performance Strategy
- Concurrency tuned for CPU utilization
- Periodic prune and janitor cycle to prevent drift
- Keep heavy external interactions in isolated workers

## Migration Direction: Docker -> OpenSandbox
Phase 1: stable Docker sandbox baseline (current)
Phase 2: side-by-side OpenSandbox path for research/tx
Phase 3: cut over default external-task sandboxing to OpenSandbox
Phase 4: keep Docker fallback for resilience


## Operational Intelligence Upgrades (New)
- InsightForge-lite decomposition (max 3 sub-queries)
- ReACT caps (`MAX_TOOL_CALLS=5`, `MAX_REFLECTION=3`)
- Outline-first task dispatch before subagent spawn
- Persistent task state machine (`CREATED/RUNNING/DONE/FAILED`)
- TX risk tier system (`SAFE/CAUTION/ESCALATE`)
- JSONL audit logs with rotation
