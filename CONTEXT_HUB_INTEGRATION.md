# Context Hub Integration

## Why
Reduce API hallucinations and stale-doc errors by fetching curated, versioned docs before implementation.

## Tool
- CLI: `chub` (`@aisuite/chub`)

## Integration points
- `research`: use chub for external API research
- `coder`: use chub before coding API integrations
- `research-deep`: include chub in deep research prep phase
- `architect`: maintain prioritized doc IDs and annotation hygiene

## Workflow
1. `chub search <topic>`
2. `chub get <doc-id> --lang <py|js>`
3. Implement
4. `chub annotate <doc-id> "gotcha"` when needed

## Safety
- Context-only tool; no transaction signing role
- Keep tx signing boundary separate

## Benefit
Higher first-pass implementation success, fewer integration regressions.
