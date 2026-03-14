# Tech Stack Extensions (Integrated)

## External Inputs Reviewed
- Apify Crawlee Python
- Mastra observational memory pattern
- Helius core-ai skills
- Layr-Labs skill (EigenCloud / ecloud)
- Solana Dev Skill
- Snarktank Antfarm

## Adoption Decisions

### Adopt now
1. **Crawlee-Python (light mode)** for research crawling
   - Use HTTP + parser mode (Pi friendly)
   - Avoid browser-first crawling by default

2. **Observer/Reflector memory loop (conceptual from Mastra)**
   - Daily observer summary from recent activity
   - Weekly reflector distillation into durable principles

3. **Antfarm-inspired orchestration controls**
   - role-tier separation
   - bounded loops and retries
   - state machine for long tasks
   - watchdog/health-check pattern

4. **Chain skill packs (phased)**
   - Phase 1: reference-only imports (safe)
   - Phase 2: read-only chain analysis tools
   - Phase 3: tx write actions only behind strict confirmation

### Avoid / defer
- Heavy cloud GraphRAG and social simulation stacks on Pi
- GPU-oriented training loops
- Any unconstrained autonomous tx execution

## Agent Impact
- `research`: gains structured crawling + decomposition pipeline
- `tx`: gains chain-skill references, strict risk tiering
- `main`: gains orchestration state machine and watchdog model
- `janitor`: gains log rotation + periodic hygiene enforcement

## Guardrails
- Sandbox-first for external interaction agents
- Host-mode only for janitor maintenance duties
- Secrets never logged or echoed
- Explicit human confirmation for any irreversible tx action
