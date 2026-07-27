# Changelog

All notable changes per release. Versions follow [semver](https://semver.org).

## v1.0.0 — 2026-07-27

First release — the marketplace catalog for every psyb0t agent skill and plugin.

- Added `.claude-plugin/marketplace.json` (Claude Code) and
  `.agents/plugins/marketplace.json` (Codex), each listing the same 24 plugins.
  Both are metadata only; no entry ships hooks, executables, or MCP servers.
- Every entry resolves through a `git-subdir` source pointing at the `.agents/`
  directory of the tool's own repository, so a plugin is always whatever that
  repository last released and nothing is duplicated here.
- Added a README index: the shared `marketplace add` commands, a table of all 24
  plugins with their install line and source repo, and the reason a single
  catalog exists — a marketplace registers under its `name`, so a second one
  claiming a registered name replaces the first in Claude Code and is rejected
  outright by Codex.
