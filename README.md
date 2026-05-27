# FetchCatch Cursor Plugin

Official Cursor plugin for [FetchCatch](https://fetchcatch.com) — the multi-tenant rules engine for version-controlled decision flows.

## What it does

This plugin helps developers author, sync, and integrate FetchCatch rules from Cursor:

| Component | Purpose |
|-----------|---------|
| **Skills** | Agent knowledge for workspace editing, JSONata, and Evaluate API integration |
| **Rules** | Guardrails when editing `.fetchcatch/**/*.json` |
| **Commands** | Quick `fcc plan`, `fcc status`, and `fcc run` workflows |

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

## Plugin contents

```
cursor-plugin/
├── .cursor-plugin/plugin.json
├── skills/
│   ├── fetchcatch-workspace/   # Flow authoring + fcc sync
│   ├── fetchcatch-jsonata/     # Expression patterns
│   └── fetchcatch-evaluate/    # Runtime API + .NET SDK
├── rules/
│   └── fetchcatch-workspace-guardrails.mdc
├── commands/
│   ├── fcc-plan.md
│   ├── fcc-status.md
│   └── fcc-run.md
└── assets/logo.svg
```

## Local testing

Before publishing, load the plugin locally:

1. Copy `cursor-plugin/` to `~/.cursor/plugins/local/fetchcatch/`
2. Ensure `.cursor-plugin/plugin.json` is at the plugin root
3. Restart Cursor or run **Developer: Reload Window**
4. Open a repo with `.fetchcatch/` and verify skills/rules appear

On Windows:

```powershell
Copy-Item -Recurse -Force cursor-plugin "$env:USERPROFILE\.cursor\plugins\local\fetchcatch"
```

## Documentation

- [FetchCatch docs](https://fetchcatch.com/docs)
- [AI agent guide](https://fetchcatch.com/docs/v0.1/ai-agent-guide.md)
- [CLI reference](https://fetchcatch.com/docs/v0.1/cli-reference.md)
- [LLM discovery](https://fetchcatch.com/llms.txt)

## Public marketplace repo

Cursor Marketplace submission uses the **public** repository:

**https://github.com/teclogist/fetchcatch-cursor-plugin**

This folder is a development copy inside the private monorepo. After changes here, sync to the public repo (see `SYNC.md` in the public repo).

## License

MIT — see [LICENSE](./LICENSE).
