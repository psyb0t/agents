# agents

[![version](https://raw.githubusercontent.com/psyb0t/agents/badges/version.svg)](https://github.com/psyb0t/agents/releases)
[![license](https://raw.githubusercontent.com/psyb0t/agents/badges/license.svg)](LICENSE)

Agent skills and plugins from psyb0t projects — one marketplace for all of them.

Almost every entry is a metadata-only plugin rooted at its own repository's
`.agents/` directory: a skill (markdown that teaches an agent to drive the tool)
and, where the tool speaks MCP, a bridge plugin. Nothing here declares hooks,
executables, or MCP servers of its own.

The exception is `loop`, whose repository root *is* the plugin. It is referenced
with `source: "url"` and no `path` rather than `git-subdir`, because `git-subdir`
requires a `path` and Codex rejects root-equivalent values like `"."` — the
plugin would simply never be found.

## Table of contents

- [Install](#install)
- [Plugins](#plugins)
- [How it is wired](#how-it-is-wired)
- [License](#license)

## Install

Add the marketplace once:

```bash
claude plugin marketplace add psyb0t/agents
codex plugin marketplace add psyb0t/agents
```

Then install whatever you need:

```bash
claude plugin install <plugin>@psyb0t
codex plugin add <plugin>@psyb0t
```

The install verb differs between the two clients: Claude Code uses
`plugin install`, Codex uses `plugin add`. There is no `codex plugin install`.

Adding the marketplace on its own installs nothing — it registers the catalog so
individual plugins can be installed from it. Once installed, a plugin's skill is
invoked in Codex as `$<plugin>:<skill>`.

Codex additionally discovers any of these skills automatically in a checkout of
the tool's own repository, since it scans `.agents/skills/` natively. No install
is involved there, and the skill invokes as plain `$<skill>`.

## Plugins

| Plugin | What it does | Install | Repo |
|---|---|---|---|
| `aigate` | Self-hosted AI platform combining inference routing, MCP tools, browser automation, and media generation behind one OpenAI-compatible endpoint. | `claude plugin install aigate@psyb0t` | [aigate](https://github.com/psyb0t/aigate) |
| `audiolla` | Self-hosted audio-production API for stem separation, mastering, MIR analysis, DSP chains, MIDI, and AI restoration via REST and MCP. | `claude plugin install audiolla@psyb0t` | [docker-audiolla](https://github.com/psyb0t/docker-audiolla) |
| `claudebox` | Runs Claude Code in a Docker container, drivable via CLI, HTTP REST API, an OpenAI-compatible endpoint, MCP, Telegram, or cron. | `claude plugin install claudebox@psyb0t` | [docker-claudebox](https://github.com/psyb0t/docker-claudebox) |
| `codexbox` | OpenAI Codex CLI in a Docker container, exposed via REST API, an OpenAI-compatible endpoint, MCP, a Telegram bot, and a cron scheduler. | `claude plugin install codexbox@psyb0t` | [docker-codexbox](https://github.com/psyb0t/docker-codexbox) |
| `flickies` | Self-hosted video toolkit for lipsync, face restoration, and ffmpeg operations, exposed over REST and MCP. | `claude plugin install flickies@psyb0t` | [docker-flickies](https://github.com/psyb0t/docker-flickies) |
| `goenv` | Go library that reads the ENV environment variable and returns whether a process is running in prod or dev, defaulting to prod. | `claude plugin install goenv@psyb0t` | [goenv](https://github.com/psyb0t/goenv) |
| `hybrids3` | Self-hosted lightweight object storage over S3, plain HTTP, and MCP, with SQLite metadata, per-bucket keys, a master key, and presigned URLs. | `claude plugin install hybrids3@psyb0t` | [docker-hybrids3](https://github.com/psyb0t/docker-hybrids3) |
| `ibkr-httpapi` | HTTP+JSON bridge to Interactive Brokers via ib_async — market data, options/futures, account/positions, order entry, and server-side TA over REST and MCP. | `claude plugin install ibkr-httpapi@psyb0t` | [ibkr-httpapi](https://github.com/psyb0t/ibkr-httpapi) |
| `loop` | Codex CLI plugin that repeats instructions at a fixed interval in the active TUI session, using Goal mode plus a session-owned background timer. **Codex only.** | `codex plugin add loop@psyb0t` | [codex-plugin-loop](https://github.com/psyb0t/codex-plugin-loop) |
| `mailbox` | Multi-mailbox IMAP/SMTP control plane exposed as a REST API and MCP server on a single port for reading, searching, sending, and deleting mail. | `claude plugin install mailbox@psyb0t` | [docker-mailbox](https://github.com/psyb0t/docker-mailbox) |
| `mediaproc` | Media processing over SSH — ffmpeg, sox, and ImageMagick for video/audio transcoding and image manipulation in a locked-down container. | `claude plugin install mediaproc@psyb0t` | [docker-mediaproc](https://github.com/psyb0t/docker-mediaproc) |
| `mt5-httpapi` | MetaTrader 5 trading via REST — market data, orders, positions, history, and server-side technical analysis. | `claude plugin install mt5-httpapi@psyb0t` | [mt5-httpapi](https://github.com/psyb0t/mt5-httpapi) |
| `persistent-sshfs` | Bash tool that brings up SSHFS mounts, retrying key-based SSH auth until connected, then mounts with sshfs -o reconnect. | `claude plugin install persistent-sshfs@psyb0t` | [persistent-sshfs](https://github.com/psyb0t/persistent-sshfs) |
| `pibox` | pi-coding-agent running in a container, exposed over HTTP REST, an OpenAI-compatible endpoint, MCP, a Telegram bot, and a cron scheduler. | `claude plugin install pibox@psyb0t` | [docker-pibox](https://github.com/psyb0t/docker-pibox) |
| `planesnitch` | Self-hosted aircraft monitor that alerts on military, government, or custom-watchlist planes near your locations via Telegram or webhook, using free public ADS-B data. | `claude plugin install planesnitch@psyb0t` | [docker-planesnitch](https://github.com/psyb0t/docker-planesnitch) |
| `predictalot` | Self-hosted forecasting API — zero-shot time-series forecasting and supervised tabular ML over REST and MCP. | `claude plugin install predictalot@psyb0t` | [docker-predictalot](https://github.com/psyb0t/docker-predictalot) |
| `proxq` | Redis-backed async HTTP proxy: submit any request, get a job ID instantly, poll for status, fetch the replayed upstream response. | `claude plugin install proxq@psyb0t` | [docker-proxq](https://github.com/psyb0t/docker-proxq) |
| `qwenspeak` | Self-hosted text-to-speech via Qwen3-TTS models over SSH, with preset voices, voice cloning, and voice design. | `claude plugin install qwenspeak@psyb0t` | [docker-qwenspeak](https://github.com/psyb0t/docker-qwenspeak) |
| `servicepack` | Clone-and-own Go service framework: concurrent service manager with retry, dependency ordering, readiness gating, and CLI scaffolding. | `claude plugin install servicepack@psyb0t` | [servicepack](https://github.com/psyb0t/servicepack) |
| `ssh-tunnel-swarm` | Bash tool that manages many concurrent SSH forward and reverse tunnels from a single rules file, with auto-reconnect and per-host keys. | `claude plugin install ssh-tunnel-swarm@psyb0t` | [ssh-tunnel-swarm](https://github.com/psyb0t/ssh-tunnel-swarm) |
| `stealthy-auto-browse` | Stealth browser automation in Docker — Camoufox, OS-level input, HTTP API and MCP server for authorized anti-bot QA and security testing. | `claude plugin install stealthy-auto-browse@psyb0t` | [docker-stealthy-auto-browse](https://github.com/psyb0t/docker-stealthy-auto-browse) |
| `supervisor-config-gen` | Bash script that generates a Supervisor (supervisord) program config file from the current directory, with zero CLI flags. | `claude plugin install supervisor-config-gen@psyb0t` | [supervisor-config-gen](https://github.com/psyb0t/supervisor-config-gen) |
| `talkies` | Self-hosted OpenAI-compatible speech API — ASR transcription (7 backends) and TTS synthesis (Kokoro, Qwen3-TTS voice cloning) over HTTP and MCP. | `claude plugin install talkies@psyb0t` | [docker-talkies](https://github.com/psyb0t/docker-talkies) |
| `telethon-plus` | HTTP + MCP control plane over a real Telegram MTProto userbot account — messages, dialogs, media, chat admin, polls, and an incoming-message webhook. | `claude plugin install telethon-plus@psyb0t` | [docker-telethon-plus](https://github.com/psyb0t/docker-telethon-plus) |
| `wickworks` | Self-hosted OHLC service computing technical indicators and Smart-Money-Concepts primitives from candlestick bars via REST and MCP. | `claude plugin install wickworks@psyb0t` | [docker-wickworks](https://github.com/psyb0t/docker-wickworks) |

## How it is wired

Each entry points at its source repository with a `git-subdir` source targeting
that repo's `.agents/` directory, so the plugin is always whatever that
repository last released — this catalog carries no copies.

Two marketplace files live here because the two clients read different schemas
and different paths:

| Client | File |
|---|---|
| Claude Code | `.claude-plugin/marketplace.json` |
| Codex | `.agents/plugins/marketplace.json` |

A marketplace registers under its `name`, and a second marketplace claiming a
registered name either replaces the first (Claude Code) or is rejected outright
(Codex). That is why every plugin is listed here rather than each repository
publishing its own marketplace.

## License

[WTFPL](LICENSE).
