# Workflow Upgrades (Applied from MiroFish-style patterns)

## 1) InsightForge-lite (bounded decomposition)
- For complex tasks, decompose into **max 3 sub-queries**.
- Research agent handles each sub-query independently.
- Main agent synthesizes final output with confidence tags.

## 2) ReACT caps
- Hard guardrails:
  - `MAX_TOOL_CALLS_PER_TASK = 5`
  - `MAX_REFLECTION_LOOPS = 3`
- If exceeded: summarize partial findings and ask for approval to continue.

## 3) Outline-first dispatch
- Before spawning subagents, main agent writes a short execution outline:
  1. objective
  2. plan
  3. risks
  4. expected outputs

## 4) Long-task state machine
- All long-running tasks use status states:
  - `CREATED`
  - `RUNNING`
  - `DONE`
  - `FAILED`
- Persist state in lightweight markdown/json files for crash recovery.

## 5) TX risk tiering
- `SAFE`: read-only or simulation
- `CAUTION`: reversible config changes / low risk
- `ESCALATE`: any state-changing tx or irreversible operation

## 6) JSONL audit trail
- Structured action logs per session/task
- Required fields:
  - timestamp
  - agent_id
  - task_id
  - action
  - status
  - note
- Keep log rotation to protect Pi disk.

## 7) Security and privacy guardrails
- No private chain-of-thought persistence.
- No execution of untrusted content from web results.
- Secret redaction mandatory.
- Sandbox-first for external interactions.
