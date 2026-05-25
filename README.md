# FetchCatch Cursor Plugin

Official Cursor plugin for [FetchCatch](https://fetchcatch.com) — the multi-tenant rules engine for version-controlled decision flows.

**Submit to Cursor Marketplace:** [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish) with this repository URL.

## What it does

| Component | Purpose |
|-----------|---------|
| **Skills** | Agent knowledge for workspace editing, JSONata, and Evaluate API integration |
| **Rules** | Guardrails when editing `.fetchcatch/**/*.json` |
| **Commands** | Quick `fcc plan` and `fcc status` workflows |

## Prerequisites

1. A [FetchCatch account](https://fetchcatch.com) and workspace
2. The [`fcc` CLI](https://fetchcatch.com/downloads) installed
3. A repo with `.fetchcatch/` (create with `fcc init --workspace YOUR-SLUG`)

## Getting started

```bash
# In your application repo
fcc init --workspace my-workspace
fcc login
fcc pull
```

Install this plugin from the Cursor Marketplace, then ask the agent:

- "Add a fraud-check branch to `checkout-flow`"
- "Run fcc plan and summarize pending changes"
- "Show me how to call this flow from my .NET app"

## Repository layout

```
.
├── .cursor-plugin/plugin.json
├── skills/
│   ├── fetchcatch-workspace/
│   ├── fetchcatch-jsonata/
│   └── fetchcatch-evaluate/
├── rules/
├── commands/
├── assets/logo.svg
├── README.md
├── CHANGELOG.md
└── LICENSE
```

## Local testing

1. Copy this repo to `~/.cursor/plugins/local/fetchcatch/`
2. Restart Cursor or run **Developer: Reload Window**
3. Open a repo with `.fetchcatch/` and verify skills/rules load

```powershell
Copy-Item -Recurse -Force . "$env:USERPROFILE\.cursor\plugins\local\fetchcatch"
```

## Documentation

- [FetchCatch docs](https://fetchcatch.com/docs)
- [AI agent guide](https://fetchcatch.com/docs/v0.1/ai-agent-guide.md)
- [CLI reference](https://fetchcatch.com/docs/v0.1/cli-reference.md)
- [LLM discovery](https://fetchcatch.com/llms.txt)

## License

MIT — see [LICENSE](./LICENSE).
