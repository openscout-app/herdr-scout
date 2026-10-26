# Scout for herdr

This repository is the herdr plugin for Scout. It is public. It adds three
herdr actions: ask an agent, ask about the selection, and open the Scout feed.

## Where work goes

- Every action calls the `scout` CLI. The plugin carries no runtime code.
- Behavior that every harness needs goes to the core repository,
  `openscout-app/scout`. Land it there first, then use it here.
- Behavior specific to herdr goes here: the actions, the panes, and the
  manifest.

| Path | Holds |
| --- | --- |
| `herdr-plugin.toml` | The plugin manifest: actions and panes |
| `scout-herdr.ts` | The action and pane entry points |
| `scout-herdr.test.ts` | Tests |

## Rules

- The plugin is one Bun script without dependencies. Keep it that way.
- `SCOUT_BIN` overrides the `scout` binary. Use the `HERDR_*` variables that
  herdr sets. Do not hard-code herdr or state paths.
- When you add or rename an action or a pane, update the manifest and the
  README in the same change.
- Raise `min_herdr_version` when you use a newer herdr plugin API.
- Scout is for high-trust local developer use. Do not claim enterprise,
  compliance, or multi-tenant readiness.
- This repository is public. Do not commit local paths, host names,
  credentials, or private source.

## Checks

- `bun test`

## Commits and pull requests

- Commit subjects use gitmoji: `✨ Add a reply action to the feed`.
- Do not add AI co-author trailers or "Generated with" lines.
- Push a branch to `openscout-app/herdr-scout` and open a pull request into
  `main`.

<!-- scout:begin -->
## Scout

- Work for another agent, or on another machine, goes through Scout: `scout ask` (MCP `ask`).
- Another machine: `scout ask --on <host> --project <path on that host> --harness <claude|codex>`; `scout hosts` lists machines and their projects. Don't ssh in to launch agents.
- Syntax: `scout ask --help`, `scout help --detail`. Added by `scout setup agents-md`; `scout setup agents-md --remove` takes it out.
<!-- scout:end -->
