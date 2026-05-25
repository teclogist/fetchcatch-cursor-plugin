---
name: fcc-plan
description: Preview FetchCatch sync changes with fcc plan --json
---

# fcc plan

Run a dry-run preview of what would be pushed or pulled.

```bash
fcc plan --json
```

Interpret exit codes:

| Code | Meaning |
|------|---------|
| 0 | In sync |
| 1 | Error |
| 2 | Pending changes — summarize push/pull lists from JSON |
| 3 | Conflicts — list conflicted paths; recommend `fcc diff` |

If `.fetchcatch/` is missing, suggest `fcc init --workspace SLUG` and `fcc login` first.
