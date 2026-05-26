---
name: fetchcatch-evaluate
description: >-
  Integrate FetchCatch flows at runtime via the Evaluate API or .NET SDK.
  Use when calling POST /v1/evaluate, resuming paused runs, wiring API keys,
  generating client code, or explaining how apps consume decision flow output.
---

# FetchCatch Evaluate API

Published flows run at `POST /v1/evaluate/{flowSlug}`. Auth uses **tenant API keys** (`Authorization: Bearer fc_live_...`), not console session tokens.

Base URL: `https://api.fetchcatch.com`

## When to use

- Integrating rules into an application (checkout, fraud, approvals, routing)
- Testing a published flow with sample input
- Handling paused runs (`wait_for_event`) and resume
- Choosing between REST and the .NET SDK
- Explaining input/output contracts from flow `inputSchema` and response types

## Start a run

```
POST /v1/evaluate/{flowSlug}
Authorization: Bearer {apiKey}
Content-Type: application/json
```

Prefer flat JSON matching the start node's `inputSchema`:

```json
{
  "userId": "u-123",
  "amount": 499.99
}
```

Optional envelope keys: `correlationKey`, `dryRun`, legacy `input` wrapper.

Response includes run result or paused state with `runId` for resume.

## Resume a paused run

```
POST /v1/runs/{runId}/resume
Authorization: Bearer {apiKey}
Content-Type: application/json
```

```json
{
  "event": "user_confirmed",
  "payload": { "confirmed": true }
}
```

Event name must match the `wait_for_event` node's `eventName`.

## .NET SDK

```bash
dotnet add package FetchCatch.Client
# or FetchCatch.AspNetCore for DI: services.AddFetchCatch(...)
```

```csharp
var result = await client.EvaluateAsync<MyInput, MyDecision>(
    "checkout-flow",
    new MyInput { UserId = "u-123", Amount = 499.99m },
    cancellationToken);
```

Typed evaluate/resume, structured exceptions, retries, OpenTelemetry.

## Other runtime endpoints

| Endpoint | Purpose |
|----------|---------|
| `GET /v1/runs` | List runs |
| `GET /v1/runs/{id}` | Run detail + step trace |
| `GET /v1/runs/stats` | Dashboard KPIs |

## Prerequisites checklist

1. Flow is **published** (not draft-only) — run `fcc publish`, publish from the console, or (legacy) set `"publish": true` on apply.
2. API key created in console or synced to `.fetchcatch/api-keys/`.
3. HTTP nodes' backing APIs reachable from FetchCatch runtime.
4. Input matches start node `inputSchema`; output matches bound response type.

## Documentation

| Topic | URL |
|-------|-----|
| Evaluate API | https://fetchcatch.com/docs/v0.1/evaluate-api.md |
| .NET SDK | https://fetchcatch.com/docs/v0.1/dotnet-sdk.md |
| Core concepts | https://fetchcatch.com/docs/concepts |
