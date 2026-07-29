# Changelog

All notable changes per release. Versions follow [semver](https://semver.org).

## v1.1.1 — 2026-07-29

- Rewrote the README. It opened by explaining that entries are metadata-only
  plugins rooted at each repository's `.agents/` directory — internal plumbing
  nobody installing a plugin needs to know — and got three paragraphs in without
  saying what the catalog actually gives you. It now leads with the range:
  trading terminals, audio and video pipelines, RF on a Raspberry Pi, mail, a
  Telegram account, object storage, stealth browsing, coding agents in
  containers.
- All source-layout detail moved under "Adding an entry", where it belongs, and
  a "How a skill gets invoked" section covers the `$<plugin>:<skill>` form and
  the plain `$<skill>` form Codex uses inside a tool's own repository.
- Fixed a claim that survived v1.1.0: "How it is wired" still said every entry
  used a `git-subdir` source, which stopped being true when `loop` landed with a
  `url` source.

## v1.1.0 — 2026-07-29

- Added `loop` to the Codex marketplace — a Codex CLI plugin that repeats
  instructions at a fixed interval in the active TUI session, using Goal mode
  plus a session-owned background timer.
- `loop` is the first entry using `source: "url"` rather than `git-subdir`. Its
  plugin lives at the repository root instead of under `.agents/`, and
  `git-subdir` cannot express that: it requires a `path`, and Codex rejects
  root-equivalent values such as `"."` or `"./"`, silently skipping the plugin
  so `codex plugin add` reports it as not found. Omitting `path` on a `url`
  source makes the whole repository the plugin.
- `loop` is Codex-only — it ships no Claude manifest, so it is absent from
  `.claude-plugin/marketplace.json` and its README row gives
  `codex plugin add loop@psyb0t` instead of the `claude plugin install` form
  used by every other entry.
- Corrected the README intro, which claimed every entry is rooted at its
  repository's `.agents/` directory. That stopped being true with `loop`.
- Added `.github/workflows/pipeline.yml` rendering the version and license
  badges on tag pushes, and the badge block at the top of the README.

## v1.0.2 — 2026-07-27

- Added the Codex install command to the README. The Install section listed
  `claude plugin install <plugin>@psyb0t` but nothing equivalent for Codex, so a
  Codex user was told to register the marketplace and left with no way to install
  from it. The command is `codex plugin add <plugin>@psyb0t` — the verb is `add`,
  and `codex plugin install` does not exist.
- Noted that registering a marketplace installs nothing by itself, and that an
  installed plugin's skill is invoked in Codex as `$<plugin>:<skill>` while a
  skill discovered from a repository's own `.agents/skills/` invokes as
  `$<skill>`.

## v1.0.1 — 2026-07-27

- Renamed the `docker-mailbox` entry to `mailbox` in both marketplace files and the
  README index, so it installs as `mailbox@psyb0t`. It was the only plugin named after
  its repository rather than the tool, and the new name matches the MCP-bridge plugin
  shipped at `docker-mailbox/.agents/plugins/mailbox`. Published in
  [docker-mailbox v0.4.8](https://github.com/psyb0t/docker-mailbox/releases/tag/v0.4.8);
  the ClawHub skill is unaffected and remains `@psyb0t/docker-mailbox`.

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
