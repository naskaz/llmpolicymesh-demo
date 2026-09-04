# LLMPolicyMesh Capability and Integration Tests

Tests that verify LLMPolicyMesh capabilities using deterministic, simulated transports.

## Run the tests

```powershell
dotnet run --project .\LLMPolicyMesh.CapabilityAndIntegrationTests.csproj -c Release
```

## Tests

| Test                   | What it verifies                                                                    |
| ---------------------- | ----------------------------------------------------------------------------------- |
| `RETRY-001`            | Retries a transient HTTP failure and succeeds.                                      |
| `FALLBACK-001`         | Routes to a fallback endpoint after the primary endpoint fails.                     |
| `BUDGET-001`           | Rejects a request exceeding its cost ceiling before transport.                      |
| `PII-001`              | Redacts PII from both HTTP requests and responses.                                  |
| `INJECTION-001`        | Blocks deterministic prompt injection before model transport.                       |
| `STREAM-001`           | Redacts sensitive data split across streaming chunks.                               |
| `CIRCUIT-001`          | Opens the circuit after repeated endpoint failures.                                 |
| `BUDGET-002`           | Enforces cumulative tenant budget reservations.                                     |
| `TOOL-SEC-001`         | Rejects an unauthorized tool declaration before transport.                          |
| `RAG-001`              | Sanitizes unsafe retrieval content before transport.                                |
| `AUDIT-001`            | Emits sanitized audit events without sensitive payload data.                        |
| `TRACE-001`            | Emits `ActivitySource` telemetry for gateway execution.                             |
| `METRIC-001`           | Emits `Meter` telemetry for gateway execution.                                      |
| `TIMEOUT-001`          | Enforces the configured per-attempt timeout.                                        |
| `RETRYAFTER-001`       | Honors `Retry-After` before retrying a throttled request.                           |
| `FALLBACK-EXHAUST-001` | Fails safely after primary and fallback routes are exhausted.                       |
| `RAG-SCORE-001`        | Removes retrieval chunks below the configured relevance threshold.                  |
| `POLICY-ORDER-001`     | Executes custom policy rules in configured order.                                   |
| `USAGE-SETTLE-001`     | Settles budget reservations from provider usage before later requests.              |
| `CIRCUIT-002`          | Recovers after the configured circuit-break duration.                               |
| `FALLBACK-002`         | Preserves configured ordering across multiple fallback routes.                      |
| `BUDGET-003`           | Keeps failed-request budget accounting conservative when provider usage is unknown. |
| `BUDGET-004`           | Maintains atomic tenant limits under concurrent request pressure.                   |
| `TOOL-ARG-001`         | Rejects unsafe tool URL arguments before transport.                                 |
| `TOOL-LIMIT-001`       | Rejects responses exceeding the configured tool-call limit.                         |
| `RAG-LIMIT-001`        | Enforces the maximum retrieval chunk count.                                         |
| `STREAM-LIMIT-001`     | Rejects streams exceeding the maximum buffered-byte limit.                          |
| `AUDIT-002`            | Detects modification of a tamper-evident audit ledger.                              |
| `TELEMETRY-PII-001`    | Prevents prompt PII from appearing in tracing or metric tags.                       |
| `COMPOSE-001`          | Combines PII protection, injection defense, tool policy, budgeting, and auditing.   |
| `COMPOSE-002`          | Combines retries, fallback routing, circuit breaking, and budget accounting.        |
| `CONCURRENCY-001`      | Keeps a 100-request tenant budget burst atomic.                                     |
| `CONCURRENCY-002`      | Keeps concurrent tenant budgets isolated from each other.                           |
| `STREAM-ADV-001`       | Redacts PII split into single-character streaming chunks.                           |
| `FAILURE-001`          | Preserves budget state across timeout-to-fallback execution.                        |
| `AUDIT-ADV-001`        | Maintains a valid tamper-evident audit chain under concurrent writes.               |
