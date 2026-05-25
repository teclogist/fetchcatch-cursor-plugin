# Syncing from the private FetchCatch monorepo

The product codebase lives in a private repository. This public repo contains **only** the Cursor marketplace plugin.

When updating the plugin from the monorepo (`fetchcatch/cursor-plugin/`):

```powershell
$src = "C:\dev\fetchcatch\cursor-plugin"
$dest = "C:\dev\fetchcatch-cursor-plugin"

Copy-Item -Force "$src\.cursor-plugin\plugin.json" "$dest\.cursor-plugin\plugin.json"
Copy-Item -Recurse -Force "$src\skills\*" "$dest\skills\"
Copy-Item -Recurse -Force "$src\rules\*" "$dest\rules\"
Copy-Item -Recurse -Force "$src\commands\*" "$dest\commands\"
Copy-Item -Force "$src\assets\logo.svg" "$dest\assets\logo.svg"
Copy-Item -Force "$src\CHANGELOG.md" "$dest\CHANGELOG.md"
```

Then in this repo:

1. Restore `repository` in `.cursor-plugin/plugin.json` to `https://github.com/teclogist/fetchcatch-cursor-plugin`
2. Bump `version` in `plugin.json` and `CHANGELOG.md`
3. Commit, push, and resubmit to Cursor if required for updates

Do **not** copy monorepo-only files (`marketplace.json`, internal paths, or private docs).
