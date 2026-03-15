# Toolset Policy by Agent

## main
- Purpose: orchestration and policy gate
- Default: delegate execution to specialists
- Avoid: high-risk direct execution when specialist exists

## research (sandbox)
- Allowed: web/API discovery, parsing, synthesis
- Forbidden: irreversible state-changing actions

## coder (sandbox)
- Allowed: code/test/build, patching
- Required: bounded loops and verifiable outputs

## tx (dedicated sandbox)
- Allowed: preflight, simulation, settlement planning
- State-changing actions: explicit human confirmation required
- Never: unlimited approvals, unverified contracts

## moderator (host)
- Allowed: progress monitoring, budget checks, status reporting
- Forbidden: direct task routing to external systems

## janitor (host)
- Allowed: cleanup/hygiene and maintenance
- Trigger: main requests + scheduled jobs

## architect (host)
- Allowed: architecture planning, release/research review, upgrade proposals
- Output: phased plan with risk + rollback
