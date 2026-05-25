# Cursor Marketplace submission

Use this checklist at **[cursor.com/marketplace/publish](https://cursor.com/marketplace/publish)**.

## Repository link

```
https://github.com/teclogist/fetchcatch-cursor-plugin
```

## Logotype URL

```
https://fetchcatch.com/favicon.svg
```

Or after this commit is on `main`:

```
https://raw.githubusercontent.com/teclogist/fetchcatch-cursor-plugin/main/assets/logo.svg
```

## Short description

```
Cursor plugin for FetchCatch rules-engine workspaces — flow authoring in .fetchcatch/, fcc sync, JSONata help, and Evaluate API integration.
```

## Full description

```
FetchCatch is a multi-tenant rules engine for teams who want business logic as version-controlled decision flows instead of scattered if/else code.

This plugin helps Cursor developers:

• Author flows and response types in .fetchcatch/flows/ and .fetchcatch/response-types/
• Write JSONata expressions for conditions, transforms, and HTTP input mappings
• Sync safely with the fcc CLI (plan → apply, conflict resolution, CI)
• Integrate published flows via POST /v1/evaluate/{slug} or the .NET SDK

Includes agent skills for workspace editing, JSONata, and runtime integration; guardrail rules for .fetchcatch JSON; and commands for fcc plan and fcc status.

Prerequisites: FetchCatch account, fcc CLI, and a repo initialized with fcc init.
Docs: https://fetchcatch.com/docs
```

## Keywords

```
fetchcatch, rules-engine, decision-flows, jsonata, business-rules, fcc, workflow, openapi
```

## Pre-submission checklist

- [x] Public GitHub repository
- [x] Valid `.cursor-plugin/plugin.json` at repo root
- [x] MIT `LICENSE`
- [x] `README.md` with usage instructions
- [x] Skills, rules, and commands with YAML frontmatter
- [x] Logo committed at `assets/logo.svg`
- [ ] Tested locally in `~/.cursor/plugins/local/fetchcatch/`
- [ ] Submitted at cursor.com/marketplace/publish

## After approval

1. Announce on [fetchcatch.com/docs](https://fetchcatch.com/docs) (optional)
2. Bump `version` in `.cursor-plugin/plugin.json` and `CHANGELOG.md` for updates
3. Re-submit or follow Cursor’s update process for new versions

## Review timeline

Cursor manually reviews all plugins and updates. Expect a wait; watch the email tied to your Cursor account.
