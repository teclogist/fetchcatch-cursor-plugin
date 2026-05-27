---
name: fcc-run
description: Fetch a flow run by ID with step trace (for debugging and AI review)
---

# fcc run

Fetch an evaluate run by id — status, step trace, outputs, and loose-end hints
(paused waits, step errors).

```bash
fcc run <runId> --json
```

Use after `POST /v1/evaluate/{slug}` returns a `runId`, or when investigating a
run from the console Runs dashboard.

| Flag | Purpose |
|------|---------|
| `--json` | Machine-readable payload (same shape as `GET /v1/runs/{id}`) — prefer this for agents |
| (none) | Human-readable summary with loose-end callouts |

Requires `fcc login` or `FETCHCATCH_TOKEN`. Does not require a local `.fetchcatch/`
project unless you need `--env` workspace switching.

If the run is **waiting**, the output includes the expected event name and resume URL.
If **failed**, inspect step errors in the trace before changing flow JSON.
