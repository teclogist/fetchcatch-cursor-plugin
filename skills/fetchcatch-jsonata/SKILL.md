---
name: fetchcatch-jsonata
description: >-
  Write and review JSONata expressions in FetchCatch decision flows.
  Use when editing expression fields on condition, transform, wait_for_event,
  http input mappings, or decision responseValues nodes in .fetchcatch/flows/.
---

# FetchCatch JSONata

FetchCatch evaluates [JSONata](https://jsonata.org/) in condition, transform, wait_for_event, HTTP `inputs`, and decision `responseValues`.

## When to use

- Editing `"expression"` on condition, transform, or wait_for_event nodes
- Mapping HTTP parameters in `"inputs": { "param": "jsonata here" }`
- Dynamic decision values with `"="` prefix in `responseValues`
- Debugging expression errors or wrong branch outcomes

## Run state bindings

| Binding | Description |
|---------|-------------|
| `input` | Caller payload from `/v1/evaluate` |
| `nodes.{nodeId}` | That node's output state |
| `context` | Optional legacy evaluate envelope |

After an HTTP node:

```
nodes.http_fetch_user.status
nodes.http_fetch_user.body.fieldName
```

## Common patterns

### Condition

```json
"expression": "nodes.http_fetch_user.body.balance >= input.amount"
```

### HTTP input mapping

```json
"inputs": {
  "userId": "input.userId",
  "filter": "\"active\""
}
```

### Transform

```json
"expression": "{ \"fullName\": nodes.http_1.body.firstName & ' ' & nodes.http_1.body.lastName }"
```

### Decision with dynamic value

Prefix with `=` to evaluate as JSONata:

```json
"responseValues": {
  "approved": true,
  "reason": "=nodes.cond_1.expression ? 'auto-approved' : 'manual review'"
}
```

## Tips

1. Expressions live inside JSON strings — escape quotes correctly.
2. Prefer referencing `nodes.{id}.body` for HTTP responses, not guessing shapes.
3. After HTTP nodes, inspect actual response structure before writing conditions.
4. Keep expressions readable; use transform nodes to compute intermediate values.
5. Condition edges must use `"when": "true"` and `"when": "false"`.

## Full reference

https://fetchcatch.com/docs/v0.1/expressions-jsonata.md
