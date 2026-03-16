# TX Signer Architecture (V1)

## Goal
Keep private keys outside tx sandbox. Sandbox requests signatures; host signer performs signing.

## Boundary
- tx sandbox: **no key material**
- host signer daemon: key custody + signing
- communication: Unix socket (`/tmp/tx-signer.sock`), local-only

## Components
1. `tx-signer` daemon (host)
2. `tx-signer-policy.json` (testnet-first controls)
3. `tx-signer-client.py` (sandbox/client helper)

## Current policy
- mode: testnet
- EVM chain allowlist: Base Sepolia (84532)
- Solana cluster: devnet
- mainnet disabled until manual policy change

## Security controls
- key file never mounted into tx sandbox
- socket permissions 600
- explicit mode gate (`testnet`)
- audit logging path reserved in signer logs

## Next hardening (V2)
- encrypted key at rest + unlock step
- amount/recipient allowlist enforcement in signer
- structured signed-request schema + nonce/replay checks
- hardware-backed signer option (TPM/HW wallet)
