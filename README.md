# agents

[![version](https://raw.githubusercontent.com/psyb0t/agents/badges/version.svg)](https://github.com/psyb0t/agents/releases)
[![license](https://raw.githubusercontent.com/psyb0t/agents/badges/license.svg)](LICENSE)

60 Codex plugins and 59 Claude plugins. One `marketplace add`. Then go ahead and tell your agent to place a
trade on MetaTrader, rip the stems out of a track, transmit FM off a Raspberry
Pi Zero, read your unread mail, post to Telegram from a real userbot account,
forecast a time series, watch for military aircraft overhead, or drive a browser
that anti-bot stacks can't smell. Every one of them runs on your own metal.

No SaaS in the middle. No per-seat bill. No API key to some company that reads
everything you pipe through it and loses it in a breach next quarter. Just:
"here's a tool I already run" → "now my agent knows how to drive it."

Each entry is a skill: markdown that teaches an agent the endpoints, the
arguments, and the shit that will bite you, plus an MCP bridge where the tool
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
  - [API clients](#api-clients)
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
`codex plugin install` isn't a thing. It'll tell you so. Registering the
catalog installs nothing on its own; it just points the client here.

Every plugin below works in both clients with those exact commands. Swap in the
name and go. The one exception is `loop`, which is Codex-only because it's a
Codex CLI plugin and there's nothing for Claude Code to install.

Restart the session after installing or the skill won't be loaded.

## Plugins

### Development

Coding agents, frameworks, and the tools you point them at.

- **[`claudebox`](https://github.com/psyb0t/docker-claudebox)**: Runs Claude Code in a Docker container, drivable via CLI, HTTP REST API, an OpenAI-compatible endpoint, MCP, Telegram, or cron.
- **[`codexbox`](https://github.com/psyb0t/docker-codexbox)**: OpenAI Codex CLI in a Docker container, exposed via REST API, an OpenAI-compatible endpoint, MCP, a Telegram bot, and a cron scheduler.
- **[`decidealot`](https://github.com/psyb0t/decidealot)**: Self-hosted local Laya and Von decision models over TypeSafe-compatible REST and MCP.
- **[`gen-asyncapi`](https://github.com/psyb0t/gen-asyncapi)**: Generates Go or TypeScript types, strict validation, message dispatch and a WebSocket client from AsyncAPI 3 specs, run from go generate.
- **[`gitrakz`](https://github.com/psyb0t/gitrakz)**: Drive a self-hosted gitrakz instance: sync a GitHub user's activity into local SQLite, query the timeline and derived work sessions, and run deterministic programmatic templates that export to CSV/PDF/JSON, over its /api/v1 REST API.
- **[`go-asyncapi`](https://github.com/psyb0t/go-asyncapi)**: Go library that loads AsyncAPI 3 documents into servers, channels, operations and messages, with $refs followed across files and traits merged.
- **[`goenv`](https://github.com/psyb0t/goenv)**: Go library that reads the ENV environment variable and returns whether a process is running in prod or dev, defaulting to prod.
- **[`loop`](https://github.com/psyb0t/codex-plugin-loop)**: Codex CLI plugin that repeats instructions at a fixed interval in the active TUI session, holding one turn open and waiting on the input-interruptible clock.sleep tool between iterations. *(Codex only)*
- **[`peen`](https://github.com/psyb0t/peen)**: Durable coding-agent backend: configure providers and Docker workspaces, send work over WebSocket, add harness layers, and inspect or control SQLite-backed sessions.
- **[`pibox`](https://github.com/psyb0t/docker-pibox)**: pi-coding-agent running in a container, exposed over HTTP REST, an OpenAI-compatible endpoint, MCP, a Telegram bot, and a cron scheduler.
- **[`servicepack`](https://github.com/psyb0t/servicepack)**: Clone-and-own Go service framework: concurrent service manager with retry, dependency ordering, readiness gating, and CLI scaffolding.
- **[`stealthy-auto-browse`](https://github.com/psyb0t/docker-stealthy-auto-browse)**: Stealth browser automation in Docker: Camoufox, OS-level input, HTTP API and MCP server for authorized anti-bot QA and security testing.
- **[`vibecheck`](https://github.com/psyb0t/vibecheck)**: Self-hosted typed classification, scoring, and policy decisions over REST and MCP.

### Infrastructure

Storage, tunnels, mounts, proxies: the plumbing.

- **[`aigate`](https://github.com/psyb0t/aigate)**: Self-hosted AI platform combining inference routing, MCP tools, browser automation, and media generation behind one OpenAI-compatible endpoint.
- **[`hybrids3`](https://github.com/psyb0t/docker-hybrids3)**: Self-hosted lightweight object storage over S3, plain HTTP, and MCP, with SQLite metadata, per-bucket keys, a master key, and presigned URLs.
- **[`persistent-sshfs`](https://github.com/psyb0t/persistent-sshfs)**: Bash tool that brings up SSHFS mounts, retrying key-based SSH auth until connected, then mounts with sshfs -o reconnect.
- **[`proxq`](https://github.com/psyb0t/docker-proxq)**: Redis-backed async HTTP proxy: submit any request, get a job ID instantly, poll for status, fetch the replayed upstream response.
- **[`pr0xteus`](https://github.com/psyb0t/pr0xteus)**: WireGuard-backed SOCKS5 tunnel pools for trusted services that need a configured country exit without exposing an open proxy.
- **[`ssh-tunnel-swarm`](https://github.com/psyb0t/ssh-tunnel-swarm)**: Bash tool that manages many concurrent SSH forward and reverse tunnels from a single rules file, with auto-reconnect and per-host keys.
- **[`supervisor-config-gen`](https://github.com/psyb0t/supervisor-config-gen)**: Bash script that generates a Supervisor (supervisord) program config file from the current directory, with zero CLI flags.

### Media

Audio, video, speech. Generate it, mangle it, transcribe it.

- **[`audiolla`](https://github.com/psyb0t/docker-audiolla)**: Self-hosted audio-production API for stem separation, mastering, MIR analysis, DSP chains, MIDI, and AI restoration via REST and MCP.
- **[`flickies`](https://github.com/psyb0t/docker-flickies)**: Self-hosted video toolkit for lipsync, face restoration, and ffmpeg operations, exposed over REST and MCP.
- **[`mediaproc`](https://github.com/psyb0t/docker-mediaproc)**: Media processing over SSH: ffmpeg, sox, and ImageMagick for video/audio transcoding and image manipulation in a locked-down container.
- **[`qwenspeak`](https://github.com/psyb0t/docker-qwenspeak)**: Self-hosted text-to-speech via Qwen3-TTS models over SSH, with preset voices, voice cloning, and voice design.
- **[`talkies`](https://github.com/psyb0t/docker-talkies)**: Self-hosted OpenAI-compatible speech API: ASR transcription (7 backends) and TTS synthesis (Kokoro, Qwen3-TTS voice cloning) over HTTP and MCP.

### Finance

Market data and order entry, self-hosted.

- **[`ibkr-httpapi`](https://github.com/psyb0t/ibkr-httpapi)**: HTTP+JSON bridge to Interactive Brokers via ib_async: market data, options/futures, account/positions, order entry, and server-side TA over REST and MCP.
- **[`mt5-httpapi`](https://github.com/psyb0t/mt5-httpapi)**: MetaTrader 5 trading via REST: market data, orders, positions, history, and server-side technical analysis.
- **[`mql-compiler`](https://github.com/psyb0t/docker-mql-compiler)**: Compile MQL4 and MQL5 sources to .ex4/.ex5 on Linux with MetaEditor under Wine in Docker, and read the compiler's errors.
- **[`wickworks`](https://github.com/psyb0t/docker-wickworks)**: Self-hosted OHLC service computing technical indicators and Smart-Money-Concepts primitives from candlestick bars via REST and MCP.

### Communication

Mail and messaging as an API your agent can drive.

- **[`mailbox`](https://github.com/psyb0t/docker-mailbox)**: Multi-mailbox IMAP/SMTP control plane exposed as a REST API and MCP server on a single port for reading, searching, sending, and deleting mail.
- **[`telethon-plus`](https://github.com/psyb0t/docker-telethon-plus)**: HTTP + MCP control plane over a real Telegram MTProto userbot account: messages, dialogs, media, chat admin, polls, and an incoming-message webhook.

### Data

Feeds and forecasts.

- **[`planesnitch`](https://github.com/psyb0t/docker-planesnitch)**: Self-hosted aircraft monitor that alerts on military, government, or custom-watchlist planes near your locations via Telegram or webhook, using free public ADS-B data.
- **[`predictalot`](https://github.com/psyb0t/docker-predictalot)**: Self-hosted forecasting API: zero-shot time-series forecasting and supervised tabular ML over REST and MCP.
- **[`rankrat`](https://github.com/psyb0t/rankrat)**: Self-hosted MCP server over Google Search Console, Bing Webmaster Tools, GA4, and PageSpeed Insights: search analytics, indexing and crawl diagnostics, ranking and opportunity reports. Read-only by default, scoped to the properties you configure.

### API clients

Typed Go clients for other people's APIs, generated from the specs they publish.

- **[`go-cerebras`](https://github.com/psyb0t/go-cerebras)**: Unofficial Go client for the Cerebras Inference API, generated with oapi-codegen: typed methods for chat completions, completions and model listing.
- **[`go-contextual-ai`](https://github.com/psyb0t/go-contextual-ai)**: Unofficial Go client for the Contextual AI API: typed methods for agents, queries, datastores, documents, generate, rerank, parse and LMUnit, generated from Contextual AI's OpenAPI spec.
- **[`go-elevenlabs`](https://github.com/psyb0t/go-elevenlabs)**: Unofficial Go client for the ElevenLabs REST API, generated with oapi-codegen, with one typed method per endpoint.
- **[`go-etoro`](https://github.com/psyb0t/go-etoro)**: Unofficial Go clients for the eToro public API: a typed REST client and a WebSocket client for rates, candles, market status and order updates, generated from the specs eToro publishes.
- **[`go-exa`](https://github.com/psyb0t/go-exa)**: Unofficial Go client for the Exa search API: search, find similar, page contents, cited answers and research tasks, generated from the spec Exa publishes.
- **[`go-fireworks`](https://github.com/psyb0t/go-fireworks)**: Unofficial Go client for the Fireworks AI REST API, generated with oapi-codegen: typed methods for chat completions, models, deployments, datasets and fine-tuning jobs.
- **[`go-hubspot`](https://github.com/psyb0t/go-hubspot)**: Unofficial Go client for the HubSpot API, generated from HubSpot's unified OpenAPI spec: CRM objects, associations, properties, marketing, CMS, automation and more, with Bearer token auth.
- **[`go-ibkr`](https://github.com/psyb0t/go-ibkr)**: Unofficial Go client for the Interactive Brokers Web API (Client Portal API v1): accounts, positions, contracts, market data and orders, generated from the spec Interactive Brokers publishes.
- **[`go-jina`](https://github.com/psyb0t/go-jina)**: Unofficial Go client for the Jina AI APIs: embeddings, reranking, models, chat completions, batch embedding jobs and the Reader API, generated from Jina AI's OpenAPI documents.
- **[`go-julep`](https://github.com/psyb0t/go-julep)**: Unofficial Go client for the Julep API: typed methods for agents, tools, tasks, executions, sessions and chat, users, docs, files and secrets, generated from Julep's OpenAPI spec.
- **[`go-kalshi`](https://github.com/psyb0t/go-kalshi)**: Unofficial Go client for Kalshi: a typed Trade REST client, market data and perps WebSocket clients, and a request signer, generated from the specs Kalshi publishes.
- **[`go-llama-api`](https://github.com/psyb0t/go-llama-api)**: Unofficial Go client for the Meta Llama API: chat completions, models, moderations and uploads, generated from Meta's OpenAPI spec.
- **[`go-mistral`](https://github.com/psyb0t/go-mistral)**: Unofficial Go client for the Mistral AI REST API, generated with oapi-codegen, with one typed method per endpoint.
- **[`go-perplexity`](https://github.com/psyb0t/go-perplexity)**: Unofficial Go client for the Perplexity REST API, generated with oapi-codegen: Sonar chat completions, search, embeddings, agents, skills and models.
- **[`go-render-api`](https://github.com/psyb0t/go-render-api)**: Unofficial Go client for the Render public REST API, generated with oapi-codegen, with one typed method per endpoint.
- **[`go-revolut-business`](https://github.com/psyb0t/go-revolut-business)**: Unofficial Go client for the Revolut Business REST API, generated with oapi-codegen, with one typed method per endpoint.
- **[`go-runway`](https://github.com/psyb0t/go-runway)**: Unofficial Go client for the Runway API: typed methods for image, video and audio generation, task polling, voices, avatars, workflows and organization usage.
- **[`go-supabase-management`](https://github.com/psyb0t/go-supabase-management)**: Unofficial Go client for the Supabase Management API: typed methods for organizations, projects, branches, database and auth config, edge functions, secrets and more.
- **[`go-tinker`](https://github.com/psyb0t/go-tinker)**: Unofficial Go client for the Thinking Machines Tinker API: typed methods for model creation, forward and backward passes, optimizer steps, sampling, weights and futures.
- **[`go-togetherai`](https://github.com/psyb0t/go-togetherai)**: Unofficial Go client for the Together AI REST API, generated with oapi-codegen, with one typed method per endpoint.
- **[`go-trading212`](https://github.com/psyb0t/go-trading212)**: Unofficial Go client for the Trading 212 Public API: account, positions, orders, history, instruments and pies, generated from the spec Trading 212 publishes.
- **[`go-valtown`](https://github.com/psyb0t/go-valtown)**: Unofficial Go client for the Val Town API: vals, branches, files, environment variables, blobs, SQLite, email, telemetry and users, generated from Val Town's OpenAPI document.
- **[`go-vercel`](https://github.com/psyb0t/go-vercel)**: Unofficial Go client for the Vercel REST API, generated from Vercel's OpenAPI spec, with a typed method for every endpoint.
- **[`go-weave`](https://github.com/psyb0t/go-weave)**: Unofficial Go client for the W&B Weave trace server API: typed methods to log and query calls, objects, tables, feedback, costs and evaluations.
- **[`go-writer-ai`](https://github.com/psyb0t/go-writer-ai)**: Unofficial Go client for the Writer (writer.com) API: chat, completions, files, Knowledge Graphs, no-code applications and tools, generated from Writer's OpenAPI spec.
- **[`go-xai`](https://github.com/psyb0t/go-xai)**: Unofficial Go client for the xAI (Grok) REST API, generated with oapi-codegen: chat completions, responses, messages, embeddings, image and video generation, files, skills and models.

## Calling them

In Codex a skill is `$<plugin>:<skill>`: `$loop:loop`, `$mailbox:mailbox`.

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
`loop` is the odd one: its repo root *is* the plugin, so it uses a `url`
source with no path. Don't reach for `git-subdir` there: it demands a `path`,
and Codex throws out root-equivalent junk like `"."`, so the plugin just
silently never exists.

Everything lives in this one catalog instead of every repo shipping its own,
because a marketplace registers under its `name`, and a second one claiming a
name that's already taken either clobbers the first (Claude Code) or gets
rejected flat out (Codex).

## License

[WTFPL](LICENSE).
