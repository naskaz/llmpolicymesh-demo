# LLMPolicyMesh Capability Tests

A console application demonstrating six capabilities using simulated HTTP transport—no live model provider or API key is required.

| Test | What it verifies |
|---|---|
| Retry | Retries a transient HTTP failure and succeeds. |
| Fallback | Routes to a fallback endpoint after the primary endpoint fails. |
| Budget | Rejects a request exceeding its cost ceiling before transport. |
| PII redaction | Redacts a test email from both the HTTP request and response. |
| Prompt injection | Blocks a known deterministic injection phrase before model transport. |
| Streaming redaction | Removes a test email split across multiple streaming chunks. |

The application prints PASS/FAIL results and returns exit code `0` when all tests pass, or `1` if any fail.
