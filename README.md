# Zoro Architecture (Public)

Security-first, sandbox-native multi-agent architecture for OpenClaw on Raspberry Pi.

## Visual Summary

```mermaid
flowchart TB
    U[User: Sarthi] --> M[main agent\nOrchestrator]

    M --> R[research agent\nExternal research/API]
    M --> C[coder agent\nCode/test tasks]
    M --> T[tx agent\nFuture payments/transactions]

    subgraph Sandbox Layer (session-scoped)
      R --> SR[(sandbox session)]
      C --> SC[(sandbox session)]
      T --> ST[(sandbox session)]
    end

    SR --> EXT[External APIs / Web]
    SC --> REPO[Code repos / toolchains]
    ST --> PAY[Payment rails (future)]

    SECRETS[(~/.openclaw/secrets\nchmod 600)] --> R
    SECRETS --> C
    SECRETS --> T

    LOGS[Redacted Logs] --> M
    LEARN[learnings.md / principles] --> M

    style T fill:#ffe6e6,stroke:#b30000,stroke-width:2px
    style Sandbox Layer fill:#eef7ff,stroke:#1f6feb,stroke-width:1px
```

## Current Runtime Profile
- Sandbox mode: `all`
- Scope: `session`
- Workspace access: `rw`
- Sandbox image: `openclaw-sandbox-common:bookworm-slim`
- Concurrency: `maxConcurrent=6`, `subagents.maxConcurrent=12`

## Repos and Artifacts
- Implementation docs in this repo:
  - `ARCHITECTURE.md`
  - `LEARNINGS.md`
  - `IMPLEMENTATION_CHECKLIST.md`

