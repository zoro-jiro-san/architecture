# Trust Boundaries

## Boundary Levels

### Level 0 — User Authority
- Sarthi is the root decision authority.
- Any irreversible/high-risk action should require explicit user confirmation.

### Level 1 — Main Agent (Control Plane)
- Orchestration, policy routing, response synthesis.
- Should avoid direct high-risk execution.
- Delegates domain-specific tasks to specialist agents.

### Level 2 — Sandboxed Specialists
- `research`, `coder`, `tx` run in sandboxed contexts.
- Blast radius limited by sandbox policy + tool restrictions.

### Level 3 — Host Specialist (`janitor`)
- Runs on host for full system visibility.
- Scope constrained by mission (cleanup/health), not by sandbox.
- Extra caution: host access = highest local privilege risk.

## Secrets Boundary
- Secret source: `~/.openclaw/secrets/*` (`chmod 600`).
- Never print raw secrets in chat/log outputs.
- No secret propagation into public repos/docs.

## Transaction Boundary (`tx`)
- Must remain stricter than other agents.
- Human confirmation required for state-changing steps.
- Validate chain/address/decimals/gas/simulation before execution.

## Policy Intent
- Default: sandbox all external interactions.
- Exception: host janitor for system hygiene.
