# Runbooks

## 1) High Memory Usage
1. Check current memory: `free -h`
2. Check OpenClaw process RSS
3. Restart gateway if sustained high usage
4. Verify compaction mode (`safeguard`)
5. Review session count and stale history

## 2) Sandbox Research Failure
1. Validate tooling in sandbox (`curl/python3/git/jq`)
2. Validate sandbox image config
3. Retry task in fresh session
4. Capture failure class (tool missing/network/policy)

## 3) Docker Pressure
1. `docker system df`
2. `docker ps -a`
3. `docker system prune -f`
4. For heavy cleanup: `docker system prune -af`

## 4) TX Safety Incident
1. Stop further tx actions
2. Capture exact request + preflight state
3. Verify whether any state-changing tx was sent
4. Notify user with concise incident summary
5. Patch policy/checklist gap before resuming tx operations

## 5) Janitor Actions
- Runs every 30 minutes
- Logs to workspace-janitor/janitor.log
- Performs resource checks + safe cleanup
