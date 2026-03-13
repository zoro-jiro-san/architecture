# Zoro Architecture (Public)

Security-first, sandbox-native multi-agent architecture for OpenClaw on Raspberry Pi.

## Visual Architecture

![Zoro Architecture Diagram](./diagrams/architecture.svg)

- Mermaid source: [`diagrams/architecture.mmd`](./diagrams/architecture.mmd)
- SVG diagram: [`diagrams/architecture.svg`](./diagrams/architecture.svg)

## Current Runtime Profile
- Sandbox mode: `all`
- Scope: `session`
- Workspace access: `rw`
- Sandbox image: `openclaw-sandbox-common:bookworm-slim`
- Concurrency: `maxConcurrent=6`, `subagents.maxConcurrent=12`

## Key Components
- **main agent**: orchestration and policy gate
- **research agent**: external API/web research in sandbox
- **coder agent**: implementation/test tasks in sandbox
- **tx agent**: transaction/payment domain (strict controls)
- **secrets store**: `~/.openclaw/secrets` with restrictive perms
- **memory layer**: learnings/principles with validation before persistence

## Docs
- `ARCHITECTURE.md`
- `LEARNINGS.md`
- `IMPLEMENTATION_CHECKLIST.md`
