# Deep Research Integration (AutoResearchClaw)

## Goal
Add an optional heavy-research lane without bloating default runtime.

## Design
- New optional role: `research-deep`
- Triggered manually for complex research only
- Sandbox-only execution
- Outputs stored in `workspace/research/artifacts/`

## Why this works
- Keeps normal `research` fast/lightweight
- Enables long-form paper-grade investigations when needed
- Protects core runtime and tx/security boundaries

## Safety controls
- No tx key access
- No signer access
- No secrets in outputs
- Resource-capped and explicit trigger

## Operator command
`/home/tokisaki/.openclaw/workspace/scripts/deep-research.sh "<topic>"`
