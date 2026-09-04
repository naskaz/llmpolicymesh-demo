# LLMPolicyMesh OpenRouter Integration Tests

Live integration tests that verify LLMPolicyMesh with OpenRouter.

## Set your OpenRouter API key

Open PowerShell and run:

```powershell
$env:OPENROUTER_API_KEY = Read-Host "Enter your OpenRouter API key" -MaskInput
```

## Run the tests

```powershell
dotnet run --project .\LLMPolicyMesh.OpenRouterIntegrationTests.csproj -c Release --no-launch-profile
```

## Tests

| Test                 | What it verifies                                                                     |
| -------------------- | ------------------------------------------------------------------------------------ |
| `LIVE-001`           | Completes a real OpenRouter model request through LLMPolicyMesh.                     |
| `LIVE-PII-001`       | Removes PII before sending the request to OpenRouter.                                |
| `LIVE-INJECTION-001` | Blocks prompt injection before any OpenRouter request is made.                       |
| `LIVE-TOOL-001`      | Sends an allowed tool declaration through the real model path.                       |
| `LIVE-COMPOSE-001`   | Combines PII protection, tool policy, auditing, and tracing on a real model request. |
| `LIVE-USAGE-001`     | Reads actual OpenRouter token usage through the provider usage contract.             |
