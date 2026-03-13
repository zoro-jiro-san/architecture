# TX Guardrails (Operational)

## Objective
Prevent irreversible mistakes in onchain/payment operations.

## Mandatory Preflight
1. Confirm chain/network
2. Verify target address (checksum + source)
3. Verify token decimals
4. Verify amount units
5. Estimate gas and max fee constraints
6. Simulate transaction path
7. Evaluate slippage and MEV exposure
8. Record rollback/recovery plan
9. Require human approval statement

## Execution States
- `ANALYZE` (read-only)
- `PREPARE` (build exact action plan)
- `CONFIRM` (human sign-off)
- `EXECUTE` (only after sign-off)
- `VERIFY` (post-tx validation)

## Never Events
- Never execute on ambiguous chain/address
- Never assume 18 decimals by default
- Never proceed without explicit user confirmation
- Never expose private keys/secrets in output

## Required Artifacts
- `TX_PREFLIGHT_VALIDATOR.md`
- `TX_CONFIRMATION_TEMPLATE.md`
- Structured tx summary before execution
