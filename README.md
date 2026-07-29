# agents

[![version](https://raw.githubusercontent.com/psyb0t/agents/badges/version.svg)](https://github.com/psyb0t/agents/releases)
[![license](https://raw.githubusercontent.com/psyb0t/agents/badges/license.svg)](LICENSE)

25 plugins. One `marketplace add`. Then go ahead and tell your agent to place a
trade on MetaTrader, rip the stems out of a track, transmit FM off a Raspberry
Pi Zero, read your unread mail, post to Telegram from a real userbot account,
forecast a time series, watch for military aircraft overhead, or drive a browser
that anti-bot stacks can't smell. Every one of them runs on your own metal.

No SaaS in the middle. No per-seat bill. No API key to some company that reads
everything you pipe through it and loses it in a breach next quarter. Just:
"here's a tool I already run" → "now my agent knows how to drive it."

Each entry is a skill — markdown that teaches an agent the endpoints, the
arguments, and the shit that will bite you — plus an MCP bridge where the tool
speaks MCP. The catalog holds no copies of anything: every entry points at the
source repo, so you always get whatever that project last shipped.

## Contents

- [Install](#install)
- [Plugins](#plugins)
  - [Development](#development)
  - [Infrastructure](#infrastructure)
  - [Media](#media)
  - [Finance](#finance)
  - [Communication](#communication)
  - [Data](#data)
- [Calling them](#calling-them)
- [Adding your own](#adding-your-own)
- [License](#license)

## Install

Register the catalog once:

```bash
claude plugin marketplace add psyb0t/agents
codex plugin marketplace add psyb0t/agents
```

Take what you want:

```bash
claude plugin install <plugin>@psyb0t
codex plugin add <plugin>@psyb0t
```

Yes, the verbs are different. Claude Code says `install`, Codex says `add`, and
`codex plugin install` isn't a thing — it'll tell you so. Registering the
catalog installs nothing on its own; it just points the client here.

Every plugin below works in both clients with those exact commands — swap in the
name and go. The one exception is `loop`, which is Codex-only because it's a
Codex CLI plugin and there's nothing for Claude Code to install.

Restart the session after installing or the skill won't be loaded.

## Plugins

### Development

Coding agents, frameworks, and the tools you point them at.

- **[`claudebox`](https://github.com/psyb0t/docker-claudebox)** — Runs Claude Code in a Docker container, drivable via CLI, HTTP REST API, an OpenAI-compatible endpoint, MCP, Telegram, or cron.
- **[`codexbox`](https://github.com/psyb0t/docker-codexbox)** — OpenAI Codex CLI in a Docker container, exposed via REST API, an OpenAI-compatible endpoint, MCP, a Telegram bot, and a cron scheduler.
- **[`goenv`](https://github.com/psyb0t/goenv)** — Go library that reads the ENV environment variable and returns whether a process is running in prod or dev, defaulting to prod.
- **[`loop`](https://github.com/psyb0t/codex-plugin-loop)** — Codex CLI plugin that repeats instructions at a fixed interval in the active TUI session, using Goal mode plus a session-owned background timer. *(Codex only)*
- **[`pibox`](https://github.com/psyb0t/docker-pibox)** — pi-coding-agent running in a container, exposed over HTTP REST, an OpenAI-compatible endpoint, MCP, a Telegram bot, and a cron scheduler.
- **[`servicepack`](https://github.com/psyb0t/servicepack)** — Clone-and-own Go service framework: concurrent service manager with retry, dependency ordering, readiness gating, and CLI scaffolding.
- **[`stealthy-auto-browse`](https://github.com/psyb0t/docker-stealthy-auto-browse)** — Stealth browser automation in Docker — Camoufox, OS-level input, HTTP API and MCP server for authorized anti-bot QA and security testing.

### Infrastructure

Storage, tunnels, mounts, proxies — the plumbing.

- **[`aigate`](https://github.com/psyb0t/aigate)** — Self-hosted AI platform combining inference routing, MCP tools, browser automation, and media generation behind one OpenAI-compatible endpoint.
- **[`hybrids3`](https://github.com/psyb0t/docker-hybrids3)** — Self-hosted lightweight object storage over S3, plain HTTP, and MCP, with SQLite metadata, per-bucket keys, a master key, and presigned URLs.
- **[`persistent-sshfs`](https://github.com/psyb0t/persistent-sshfs)** — Bash tool that brings up SSHFS mounts, retrying key-based SSH auth until connected, then mounts with sshfs -o reconnect.
- **[`proxq`](https://github.com/psyb0t/docker-proxq)** — Redis-backed async HTTP proxy: submit any request, get a job ID instantly, poll for status, fetch the replayed upstream response.
- **[`ssh-tunnel-swarm`](https://github.com/psyb0t/ssh-tunnel-swarm)** — Bash tool that manages many concurrent SSH forward and reverse tunnels from a single rules file, with auto-reconnect and per-host keys.
- **[`supervisor-config-gen`](https://github.com/psyb0t/supervisor-config-gen)** — Bash script that generates a Supervisor (supervisord) program config file from the current directory, with zero CLI flags.

### Media

Audio, video, speech. Generate it, mangle it, transcribe it.

- **[`audiolla`](https://github.com/psyb0t/docker-audiolla)** — Self-hosted audio-production API for stem separation, mastering, MIR analysis, DSP chains, MIDI, and AI restoration via REST and MCP.
- **[`flickies`](https://github.com/psyb0t/docker-flickies)** — Self-hosted video toolkit for lipsync, face restoration, and ffmpeg operations, exposed over REST and MCP.
- **[`mediaproc`](https://github.com/psyb0t/docker-mediaproc)** — Media processing over SSH — ffmpeg, sox, and ImageMagick for video/audio transcoding and image manipulation in a locked-down container.
- **[`qwenspeak`](https://github.com/psyb0t/docker-qwenspeak)** — Self-hosted text-to-speech via Qwen3-TTS models over SSH, with preset voices, voice cloning, and voice design.
- **[`talkies`](https://github.com/psyb0t/docker-talkies)** — Self-hosted OpenAI-compatible speech API — ASR transcription (7 backends) and TTS synthesis (Kokoro, Qwen3-TTS voice cloning) over HTTP and MCP.

### Finance

Market data and order entry, self-hosted.

- **[`ibkr-httpapi`](https://github.com/psyb0t/ibkr-httpapi)** — HTTP+JSON bridge to Interactive Brokers via ib_async — market data, options/futures, account/positions, order entry, and server-side TA over REST and MCP.
- **[`mt5-httpapi`](https://github.com/psyb0t/mt5-httpapi)** — MetaTrader 5 trading via REST — market data, orders, positions, history, and server-side technical analysis.
- **[`wickworks`](https://github.com/psyb0t/docker-wickworks)** — Self-hosted OHLC service computing technical indicators and Smart-Money-Concepts primitives from candlestick bars via REST and MCP.

### Communication

Mail and messaging as an API your agent can drive.

- **[`mailbox`](https://github.com/psyb0t/docker-mailbox)** — Multi-mailbox IMAP/SMTP control plane exposed as a REST API and MCP server on a single port for reading, searching, sending, and deleting mail.
- **[`telethon-plus`](https://github.com/psyb0t/docker-telethon-plus)** — HTTP + MCP control plane over a real Telegram MTProto userbot account — messages, dialogs, media, chat admin, polls, and an incoming-message webhook.

### Data

Feeds and forecasts.

- **[`planesnitch`](https://github.com/psyb0t/docker-planesnitch)** — Self-hosted aircraft monitor that alerts on military, government, or custom-watchlist planes near your locations via Telegram or webhook, using free public ADS-B data.
- **[`predictalot`](https://github.com/psyb0t/docker-predictalot)** — Self-hosted forecasting API — zero-shot time-series forecasting and supervised tabular ML over REST and MCP.

## Calling them

In Codex a skill is `$<plugin>:<skill>` — `$loop:loop`, `$mailbox:mailbox`.

Working inside one of the tool repos? Codex finds the skill on its own, no
install needed, and it's plain `$<skill>`.

## Adding your own

Two catalog files, because the two clients read different schemas from
different paths:

| Client | File |
|---|---|
| Claude Code | `.claude-plugin/marketplace.json` |
| Codex | `.agents/plugins/marketplace.json` |

Most entries use a `git-subdir` source aimed at the repo's `.agents/` dir.
`loop` is the odd one — its repo root *is* the plugin, so it uses a `url`
source with no path. Don't reach for `git-subdir` there: it demands a `path`,
and Codex throws out root-equivalent junk like `"."`, so the plugin just
silently never exists.

Everything lives in this one catalog instead of every repo shipping its own,
because a marketplace registers under its `name` — and a second one claiming a
name that's already taken either clobbers the first (Claude Code) or gets
rejected flat out (Codex).

## License

[WTFPL](LICENSE).
