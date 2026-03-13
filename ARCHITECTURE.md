# Architecture Blueprint (Applied)

## 1) Agent Topology

### main (default)
- Role: orchestration, user interaction, policy enforcement
- Strategy: delegate external/research/code/tx tasks to specialist agents

### research
- Role: web/API research and knowledge synthesis
- Security: sandboxed, session-isolated, disposable runtime

### coder
- Role: implementation/testing/patching in isolated environment
- Security: sandboxed with controlled filesystem scope

### tx
- Role: future payment/transaction operations
- Security: strict tool restrictions, explicit human confirmation policy

## 2) Sandbox Policy
- `sandbox.mode = all`
- `sandbox.scope = session`
- `workspaceAccess = rw`
- Docker image: `openclaw-sandbox-common:bookworm-slim`
- Network: `bridge` (needed for research jobs)

### Research sandbox image includes
- curl
- python3
- git
- jq

## 3) Security Controls
- Elevated actions restricted to allowlisted Telegram sender
- Secrets stored in `~/.openclaw/secrets/*.env` with `chmod 600`
- Log redaction enabled
- mDNS minimized
- Post-Docker cleanup policy enforced

## 4) Self-learning Loop (from Hermes/OpenClaw-compatible patterns)
- Nightly learning window: 00:00–06:00
- Distill results to durable principles and operational learnings
- Keep validation pass before committing learned conclusions
- Avoid GPU/RL-heavy pipelines on Pi (not resource fit)

## 5) Performance Profile (Pi)
- `agents.defaults.maxConcurrent = 6`
- `agents.defaults.subagents.maxConcurrent = 12`
- Docker prune every 2 hours
- Keep heavy jobs in sandbox workers, not main loop

## 6) External Research Insights Applied

### OpenSandbox
- Adopted principle: network-aware sandboxing (egress controls concept)
- Practical application now: sandbox-first + disposable sessions + strict secrets

### agency-agents
- Adopted principle: role-specific agents and installable OpenClaw workspaces
- Practical application now: explicit 4-agent topology

### autoresearch
- Adopted principle: autonomous research loops and artifact distillation
- Rejected for Pi runtime: CUDA/GPU-heavy dependency path

### MiroFish / thinking-context
- Adopted principle: structured planning/checklists/validation passes
- Policy: no raw private reasoning exposure; use auditable summaries

