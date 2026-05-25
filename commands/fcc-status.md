---
name: fcc-status
description: Show FetchCatch local vs remote sync status
---

# fcc status

Compare local `.fetchcatch/` files to the remote manifest.

```bash
fcc status --json
```

Summarize:

- Resources with pending local changes (will push on apply)
- Resources changed on server since last pull
- Any conflicts requiring `fcc diff` / `fcc resolve`

Recommend next step: `fcc plan` for full preview, or `fcc pull` if only remote changes exist.
