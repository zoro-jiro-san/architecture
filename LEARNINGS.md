# Learnings

## High-signal learnings applied

1. Sandbox runtime capability matters as much as policy.
   - Initial failures were caused by missing tools in sandbox image.
   - Fixed via custom image with curl/python3/git/jq.

2. Pi optimization needs both concurrency and hygiene.
   - Increased concurrency for throughput.
   - Added scheduled Docker cleanup to prevent resource drift.

3. Architecture should separate trust boundaries.
   - Main agent orchestrates.
   - Research/coder/tx agents isolate risk domains.

4. Self-learning should be distilled and validated.
   - Keep durable principles.
   - Avoid ingesting noisy/unchecked outputs into long-term memory.

5. Transaction capability needs stricter controls than general automation.
   - Explicit confirmation gates and narrow tool surface for tx agent.

## Next learnings to collect
- Egress policy enforcement patterns (domain/IP allowlists) in production
- Memory injection scanning for long-term memory files
- Session cleanup automation impact on RAM/latency
