# Implementation Checklist

## Applied now
- [x] 4-agent topology in OpenClaw config
- [x] Sandbox all sessions
- [x] Session-scoped sandbox containers
- [x] Research-capable sandbox image created
- [x] Concurrency tuned for high CPU usage
- [x] Docker prune cron every 2h
- [x] Architecture and learnings documented

## Next (this week)
- [ ] Add transaction confirmation workflow in tx-agent prompt/policy
- [ ] Add memory-injection scan step before loading long-term memory
- [ ] Add nightly distilled learning commit pipeline with quality checks
- [ ] Add stale session cleanup routine

## Verification commands
```bash
openclaw status --all
openclaw doctor
python3 - << 'PY'
import json
p='/home/tokisaki/.openclaw/openclaw.json'
d=json.load(open(p))
print('agents', len(d.get('agents',{}).get('list',[])))
print('sandbox', d.get('agents',{}).get('defaults',{}).get('sandbox'))
print('maxConcurrent', d.get('agents',{}).get('defaults',{}).get('maxConcurrent'))
print('subagents.maxConcurrent', d.get('agents',{}).get('defaults',{}).get('subagents',{}).get('maxConcurrent'))
PY
```
