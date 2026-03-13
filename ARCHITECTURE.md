# Zoro Architecture Blueprint (Latest)

## Runtime Topology (Live)

### 1) `main` (default)
- User-facing orchestrator
- Delegates specialized tasks to dedicated agents
- Applies policy and safety gates

### 2) `research`
- External research + API intelligence
- Always sandboxed
- Session-isolated for disposable execution

### 3) `coder`
- Code/test/build operations
- Sandboxed with constrained tool surface

### 4) `tx` (permanent transaction specialist)
- Transaction planning and verification
- Uses ETHSKILLS knowledge base
- Confirmation-first workflow for state-changing operations
- Sandbox scope set to `agent` for persistent isolated domain

### 5) `janitor` (permanent maintenance specialist)
- Cache/temp cleanup
- Memory/disk hygiene checks
- Periodic maintenance operations
- Runs on host (`sandbox.mode = off`) for full-device visibility

---

## Sandboxing Model (Live)

Global defaults:
- `sandbox.mode = all`
- `sandbox.scope = session`
- `workspaceAccess = rw`
- image: `openclaw-sandbox-common:bookworm-slim`
- network: `bridge`

Specialized overrides:
- `tx`: `sandbox.scope = agent` (persistent transaction isolation)
- `janitor`: `sandbox.mode = off` (host-level monitoring/cleanup)

Why:
- Session scope for disposable work
- Agent scope for persistent specialist behavior/state

---

## Sub-agent Orchestration Flow

1. `main` receives request
2. `main` classifies task domain
3. Route to specialist (`research` / `coder` / `tx` / `janitor`)
4. Specialist executes in sandbox
5. Return summary + artifacts to `main`
6. `main` provides final user response

Policy:
- external interactions should be sandboxed
- host-level execution minimized
- secrets never echoed in outputs

---

## Safety & Secrets

- Secrets stored under `~/.openclaw/secrets` with restrictive perms
- Redacted logging enabled
- mDNS minimized
- High-risk domains (transactions) isolated with stricter controls

---

## Performance Profile (Pi)

- `agents.defaults.maxConcurrent = 6`
- `agents.defaults.subagents.maxConcurrent = 12`
- Docker prune every 2 hours
- Janitor cleanup every 30 minutes

Goal: high CPU utilization with bounded memory growth.

---

## Scheduled Jobs (Live)

- `0 */2 * * * docker system prune -f`
- `*/30 * * * * janitor-cleanup.sh`
- `15 */4 * * * update-ethskills.sh`
- `0 6 * * * my-learnings push`

