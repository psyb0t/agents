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

- **[`claudebox`](https://github.com/psyb0t/docker-claudebox)**: Claude Code running in an isolated Docker container, driven via interactive shell, one-shot exec, an HTTP REST API, an OpenAI-compatible chat/completions adapter, an MCP server, a Telegram bot, and a YAML cron scheduler.
- **[`codexbox`](https://github.com/psyb0t/docker-codexbox)**: OpenAI Codex CLI running in a Docker container, put on the network: a REST API, an OpenAI-compatible chat-completions endpoint, an MCP server, a Telegram bot, and a cron scheduler.
- **[`decidealot`](https://github.com/psyb0t/decidealot)**: Run local Laya, Von, and CLM or hosted Jev decisions through Decidealot REST or MCP.
- **[`gen-asyncapi`](https://github.com/psyb0t/gen-asyncapi)**: Generates Go or TypeScript types, strict validation, message dispatch and a WebSocket client from AsyncAPI 3 specs, run from go generate.
- **[`gitrakz`](https://github.com/psyb0t/gitrakz)**: Drive a self-hosted gitrakz instance: sync a GitHub user's activity into local SQLite, query the filterable timeline and derived work sessions, and run deterministic programmatic templates that export to CSV/PDF/JSON: over its bearer-protected /api/v1 REST API.
- **[`go-asyncapi`](https://github.com/psyb0t/go-asyncapi)**: Go library that loads AsyncAPI 3 documents into servers, channels, operations and messages, with $refs followed across files and traits merged.
- **[`goenv`](https://github.com/psyb0t/goenv)**: Go library that reads the ENV environment variable and reports whether the process is running in prod or dev, defaulting to prod when ENV is unset or anything other than the literal "dev".
- **[`loop`](https://github.com/psyb0t/codex-plugin-loop)**: Codex CLI plugin that repeats instructions at a fixed interval in the active TUI session, holding one turn open and waiting on the input-interruptible clock.sleep tool between iterations. *(Codex only)*
- **[`peen`](https://github.com/psyb0t/peen)**: Durable coding-agent backend: configure providers and Docker workspaces, send work over WebSocket, add harness layers, and inspect or control SQLite-backed sessions.
- **[`pibox`](https://github.com/psyb0t/docker-pibox)**: pi-coding-agent running in a container: interactive shell, one-shot exec, an HTTP REST API, an OpenAI-compatible chat endpoint, an MCP server, a Telegram bot, and a cron scheduler, all on one image.
- **[`servicepack`](https://github.com/psyb0t/servicepack)**: Clone-and-own Go service framework: debug related services together locally, then ship one binary or split them into microservices with lifecycle, retry, readiness, and CLI scaffolding.
- **[`stealthy-auto-browse`](https://github.com/psyb0t/docker-stealthy-auto-browse)**: Headless-detection-resistant browser automation in Docker: Camoufox stealth browser, human-like OS-level input via PyAutoGUI, HTTP API and MCP server, for authorized QA and defensive security testing.
- **[`vibecheck`](https://github.com/psyb0t/vibecheck)**: Use Vibecheck for typed classification, scoring, and policy decisions over REST or MCP.

### Infrastructure

Storage, tunnels, mounts, proxies: the plumbing.

- **[`aigate`](https://github.com/psyb0t/aigate)**: Self-hosted AI platform behind one OpenAI-compatible endpoint: inference routing across cloud and local providers, MCP tool use, browser automation, image/speech/transcription, object storage, agentic code execution, web search, email and Telegram gateways, and a web UI.
- **[`hybrids3`](https://github.com/psyb0t/docker-hybrids3)**: Self-hosted lightweight object storage speaking S3 (boto3/AWS SDK, Sig V4), plain HTTP (curl + Bearer auth), and MCP (Streamable HTTP tools) from one container: SQLite metadata, flat-file storage, config-defined buckets, per-bucket keys, a cross-bucket master key, and presigned GET/PUT URLs.
- **[`persistent-sshfs`](https://github.com/psyb0t/persistent-sshfs)**: Bash tool that brings up SSHFS mounts and retries the initial connection until key-based SSH auth succeeds, then mounts with sshfs -o reconnect.
- **[`proxq`](https://github.com/psyb0t/docker-proxq)**: Redis-backed async HTTP proxy queue built on asynq: submit any request, get a job ID back instantly, poll for status, and fetch the replayed upstream response.
- **[`pr0xteus`](https://github.com/psyb0t/pr0xteus)**: WireGuard-backed SOCKS5 and HTTP proxy pools for trusted services that need a configured country exit without exposing an open proxy.
- **[`ssh-tunnel-swarm`](https://github.com/psyb0t/ssh-tunnel-swarm)**: Bash tool that spins up and supervises many concurrent SSH forward and reverse tunnels from a plain-text rules file, with auto-reconnect.
- **[`supervisor-config-gen`](https://github.com/psyb0t/supervisor-config-gen)**: Bash script that generates a Supervisor (supervisord) [program:*] config file from the current directory with zero CLI flags, args, or env vars.

### Media

Audio, video, speech. Generate it, mangle it, transcribe it.

- **[`audiolla`](https://github.com/psyb0t/docker-audiolla)**: Self-hosted audio-production API: stem separation, mastering, MIR analysis, DSP chains, MIDI, and AI restoration over REST and MCP.
- **[`flickies`](https://github.com/psyb0t/docker-flickies)**: Self-hosted video toolkit: lipsync, face restore, and ffmpeg ops (trim, concat, transcode, scale) via REST and MCP.
- **[`mediaproc`](https://github.com/psyb0t/docker-mediaproc)**: Media processing over SSH: ffmpeg, sox, and ImageMagick for video/audio transcoding and image manipulation inside a locked-down lockbox container.
- **[`qwenspeak`](https://github.com/psyb0t/docker-qwenspeak)**: Self-hosted text-to-speech via Qwen3-TTS models over SSH: preset voices, voice cloning, and voice design.
- **[`talkies`](https://github.com/psyb0t/docker-talkies)**: Self-hosted OpenAI-compatible speech API: ASR and TTS over HTTP, live ASR over WebSocket, and ASR plus file staging over MCP.

### Finance

Market data and order entry, self-hosted.

- **[`ibkr-httpapi`](https://github.com/psyb0t/ibkr-httpapi)**: HTTP+JSON bridge to Interactive Brokers via ib_async and a local IB Gateway container: market data, option chains with Greeks, account/positions, order entry, and server-side technical analysis over REST and MCP.
- **[`mt5-httpapi`](https://github.com/psyb0t/mt5-httpapi)**: MetaTrader 5 trading via REST: market data, orders, positions, history, and server-side technical analysis.
- **[`mql-compiler`](https://github.com/psyb0t/docker-mql-compiler)**: Compile MQL4 and MQL5 sources to .ex4/.ex5 on Linux with MetaEditor under Wine in Docker, and read the compiler's errors.
- **[`wickworks`](https://github.com/psyb0t/docker-wickworks)**: Stateless OHLC primitives service: candlestick bars in, technical indicators and Smart-Money-Concepts objects out, over REST and MCP.

### Communication

Mail and messaging as an API your agent can drive.

- **[`mailbox`](https://github.com/psyb0t/docker-mailbox)**: Multi-mailbox IMAP/SMTP control plane exposed as a REST API and MCP server on a single port: read, search, send, mark-seen, and delete mail across multiple inboxes.
- **[`telethon-plus`](https://github.com/psyb0t/docker-telethon-plus)**: HTTP + MCP control plane over a real Telegram MTProto userbot (Telethon): send/read/edit/delete/forward messages, dialogs, entities, media, chat admin, and polls, plus an incoming-message webhook.

### Data

Feeds and forecasts.

- **[`planesnitch`](https://github.com/psyb0t/docker-planesnitch)**: Self-hosted aircraft monitor: alerts on military/government/police aircraft, emergency squawks, and custom ICAO watchlists near your locations via Telegram and webhooks, no SDR or hardware required.
- **[`predictalot`](https://github.com/psyb0t/docker-predictalot)**: Self-hosted forecasting service: zero-shot time-series forecasting (chronos-2, timesfm-2.5, moirai-2, toto-1, sundial-base-128m) across univariate, multivariate, covariate, and sample-path types, plus supervised tabular ML (9 backends, 3 meta-learners) with train+persist and weighted ensembles. Unified REST + MCP (Streamable-HTTP at /mcp).
- **[`rankrat`](https://github.com/psyb0t/rankrat)**: Self-hosted SEO intelligence over Google Search Console, Bing Webmaster Tools, GA4, PageSpeed, CrUX, Cloudflare, IndexNow, and optional local Lighthouse: persistent monitoring, internal-link and content opportunities, ownership, remediation, onboarding, and multi-provider backlinks. Writable by default with one read-only switch. MCP over stdio and Streamable HTTP, plus REST.

### Hardware

Talking to physical machines over USB and serial.

- **[`marlinfw-tools`](https://github.com/psyb0t/marlinfw-tools)**: Inspect and carefully control a USB-connected Marlin 3D printer (Ender 3 and similar) from a locked-down Docker container: firmware and settings reports, telemetry, SD listings, supervised homing, single audited calibration writes and a supervised first-layer test.

### API clients

Typed Go clients for other people's APIs, generated from the specs they publish.

- **[`go-bfl`](https://github.com/psyb0t/go-bfl)**: Unofficial Go client for the Black Forest Labs FLUX API, generated from its public OpenAPI specification.
- **[`go-browser-use`](https://github.com/psyb0t/go-browser-use)**: Unofficial Go client for the Browser Use Cloud API v4: agent runs, sessions, workspaces, browsers, profiles, files and integrations.
- **[`go-btse`](https://github.com/psyb0t/go-btse)**: Unofficial Go client for BTSE: spot, futures, market data, wallets, earn and OTC, generated from the public API specifications.
- **[`go-bunnynet`](https://github.com/psyb0t/go-bunnynet)**: Unofficial Go client for the Bunny.net core API: CDN, DNS, storage and video library configuration, statistics, load balancers and billing.
- **[`go-calcom`](https://github.com/psyb0t/go-calcom)**: Unofficial Go client for Cal.com API v2: bookings, event types, availability, schedules, calendars, teams and profile, generated from the public OpenAPI spec.
- **[`go-cerebras`](https://github.com/psyb0t/go-cerebras)**: Unofficial Go client for the Cerebras Inference API, generated with oapi-codegen: typed methods for chat completions, completions and model listing.
- **[`go-contextual-ai`](https://github.com/psyb0t/go-contextual-ai)**: Unofficial Go client for the Contextual AI API: typed methods for agents, queries, datastores, documents, generate, rerank, parse and LMUnit, generated from Contextual AI's OpenAPI spec.
- **[`go-coolify`](https://github.com/psyb0t/go-coolify)**: Unofficial Go client for the Coolify API: applications, deployments, databases, services, projects, servers and teams, generated from the spec Coolify publishes.
- **[`go-deribit`](https://github.com/psyb0t/go-deribit)**: Unofficial Go client for Deribit crypto options and futures: REST account, orders, instruments and market data, plus generated WebSocket subscriptions.
- **[`go-dydx-indexer`](https://github.com/psyb0t/go-dydx-indexer)**: Unofficial Go client for the dYdX v4 Indexer API: typed methods for markets, orderbooks, candles, trades, funding, subaccounts, positions, orders, fills, transfers and PnL, generated from the indexer's OpenAPI spec.
- **[`go-elevenlabs`](https://github.com/psyb0t/go-elevenlabs)**: Unofficial Go client for the ElevenLabs REST API, generated with oapi-codegen, with one typed method per endpoint.
- **[`go-etoro`](https://github.com/psyb0t/go-etoro)**: Unofficial Go clients for the eToro public API: a typed REST client and a WebSocket client for rates, candles, market status and order updates, generated from the specs eToro publishes.
- **[`go-exa`](https://github.com/psyb0t/go-exa)**: Unofficial Go client for the Exa search API: search, find similar, page contents, cited answers and research tasks, generated from the spec Exa publishes.
- **[`go-fireworks`](https://github.com/psyb0t/go-fireworks)**: Unofficial Go client for the Fireworks AI REST API, generated with oapi-codegen: typed methods for chat completions, models, deployments, datasets and fine-tuning jobs.
- **[`go-hubspot`](https://github.com/psyb0t/go-hubspot)**: Unofficial Go client for the HubSpot API, generated from HubSpot's unified OpenAPI spec: CRM objects, associations, properties, marketing, CMS, automation and more, with Bearer token auth.
- **[`go-ibkr`](https://github.com/psyb0t/go-ibkr)**: Unofficial Go client for the Interactive Brokers Web API (Client Portal API v1): accounts, positions, contracts, market data and orders, generated from the spec Interactive Brokers publishes.
- **[`go-intercom`](https://github.com/psyb0t/go-intercom)**: Unofficial Go client for the Intercom REST API: contacts, companies, conversations, messages, articles, tickets and workspace data, generated from the published spec.
- **[`go-jina`](https://github.com/psyb0t/go-jina)**: Unofficial Go client for the Jina AI APIs: embeddings, reranking, models, chat completions, batch embedding jobs and the Reader API, generated from Jina AI's OpenAPI documents.
- **[`go-julep`](https://github.com/psyb0t/go-julep)**: Unofficial Go client for the Julep API: typed methods for agents, tools, tasks, executions, sessions and chat, users, docs, files and secrets, generated from Julep's OpenAPI spec.
- **[`go-kalshi`](https://github.com/psyb0t/go-kalshi)**: Unofficial Go client for Kalshi: a typed Trade REST client, market data and perps WebSocket clients, and a request signer, generated from the specs Kalshi publishes.
- **[`go-klavis`](https://github.com/psyb0t/go-klavis)**: Unofficial Go client for the Klavis AI API: MCP servers, tool calls, Strata, user integrations, OAuth and sandboxes, generated from the spec Klavis AI publishes.
- **[`go-label-studio`](https://github.com/psyb0t/go-label-studio)**: Unofficial Go client for the Label Studio API: projects, tasks, annotations, predictions, imports, exports, storage and administration, generated from HumanSignal's public spec.
- **[`go-latitude-llm`](https://github.com/psyb0t/go-latitude-llm)**: Unofficial Go client for the Latitude LLM API: projects, traces, scores, annotations, saved searches, issues, API keys and organization management, generated from the public OpenAPI spec.
- **[`go-llama-api`](https://github.com/psyb0t/go-llama-api)**: Unofficial Go client for the Meta Llama API: chat completions, models, moderations and uploads, generated from Meta's OpenAPI spec.
- **[`go-lovable`](https://github.com/psyb0t/go-lovable)**: Unofficial Go client for the Lovable API: projects, publishing, analytics, security scans, workspaces, groups and members, generated from the public OpenAPI spec.
- **[`go-mem0`](https://github.com/psyb0t/go-mem0)**: Unofficial Go client for the Mem0 Platform API: memories, entities, organizations, projects, webhooks, profiles and Dream operations, generated from the spec Mem0 publishes.
- **[`go-mistral`](https://github.com/psyb0t/go-mistral)**: Unofficial Go client for the Mistral AI REST API, generated with oapi-codegen, with one typed method per endpoint.
- **[`go-morphik`](https://github.com/psyb0t/go-morphik)**: Unofficial Go client for the Morphik API: ingestion, documents, retrieval, queries, models, cloud apps and connectors, generated from Morphik's published spec.
- **[`go-opik`](https://github.com/psyb0t/go-opik)**: Unofficial Go client for the Opik REST API: projects, traces, spans, datasets, experiments and prompts, generated from the specification Comet publishes.
- **[`go-perplexity`](https://github.com/psyb0t/go-perplexity)**: Unofficial Go client for the Perplexity REST API, generated with oapi-codegen: Sonar chat completions, search, embeddings, agents, skills and models.
- **[`go-polar`](https://github.com/psyb0t/go-polar)**: Unofficial Go client for the Polar API: products, customers, subscriptions, checkouts, orders, benefits and usage billing, generated from the public OpenAPI spec.
- **[`go-postgrid`](https://github.com/psyb0t/go-postgrid)**: Unofficial Go client for PostGrid print and mail and address verification, generated from the published OpenAPI document.
- **[`go-render-api`](https://github.com/psyb0t/go-render-api)**: Unofficial Go client for the Render public REST API, generated with oapi-codegen, with one typed method per endpoint.
- **[`go-revolut-business`](https://github.com/psyb0t/go-revolut-business)**: Unofficial Go client for the Revolut Business REST API, generated with oapi-codegen, with one typed method per endpoint.
- **[`go-roark`](https://github.com/psyb0t/go-roark)**: Unofficial Go client for the Roark API: voice AI agents, calls, chats, simulations, metrics and monitoring, generated from the spec Roark publishes.
- **[`go-runway`](https://github.com/psyb0t/go-runway)**: Unofficial Go client for the Runway API: typed methods for image, video and audio generation, task polling, voices, avatars, workflows and organization usage.
- **[`go-skyvern`](https://github.com/psyb0t/go-skyvern)**: Unofficial Go client for the Skyvern API: tasks, agents, runs, browser sessions, credentials and schedules, generated from the spec Skyvern publishes.
- **[`go-solana-tracker`](https://github.com/psyb0t/go-solana-tracker)**: Unofficial Go client for the Solana Tracker Data API and Datastream: token, price, pool, wallet, trade and chart data, generated from the public OpenAPI and AsyncAPI specs.
- **[`go-supabase-management`](https://github.com/psyb0t/go-supabase-management)**: Unofficial Go client for the Supabase Management API: typed methods for organizations, projects, branches, database and auth config, edge functions, secrets and more.
- **[`go-surge`](https://github.com/psyb0t/go-surge)**: Unofficial Go client for the Surge SMS API: accounts, messages, contacts, campaigns, phone numbers, recordings, users and verifications, generated from Surge's public OpenAPI spec.
- **[`go-tinker`](https://github.com/psyb0t/go-tinker)**: Unofficial Go client for the Thinking Machines Tinker API: typed methods for model creation, forward and backward passes, optimizer steps, sampling, weights and futures.
- **[`go-togetherai`](https://github.com/psyb0t/go-togetherai)**: Unofficial Go client for the Together AI REST API, generated with oapi-codegen, with one typed method per endpoint.
- **[`go-trading212`](https://github.com/psyb0t/go-trading212)**: Unofficial Go client for the Trading 212 Public API: account, positions, orders, history, instruments and pies, generated from the spec Trading 212 publishes.
- **[`go-twelvedata`](https://github.com/psyb0t/go-twelvedata)**: Unofficial Go client for the Twelve Data market data API: prices, time series, technical indicators, fundamentals and reference data, generated from the public OpenAPI spec.
- **[`go-unstructured`](https://github.com/psyb0t/go-unstructured)**: Unofficial Go client for the Unstructured Platform and Partition APIs: connectors, workflows, jobs, notifications and document partitioning.
- **[`go-valtown`](https://github.com/psyb0t/go-valtown)**: Unofficial Go client for the Val Town API: vals, branches, files, environment variables, blobs, SQLite, email, telemetry and users, generated from Val Town's OpenAPI document.
- **[`go-vectara`](https://github.com/psyb0t/go-vectara)**: Unofficial Go client for the Vectara API v2: corpora, documents, search, generation, chats and API keys, generated from the spec Vectara publishes.
- **[`go-vercel`](https://github.com/psyb0t/go-vercel)**: Unofficial Go client for the Vercel REST API, generated from Vercel's OpenAPI spec, with a typed method for every endpoint.
- **[`go-weave`](https://github.com/psyb0t/go-weave)**: Unofficial Go client for the W&B Weave trace server API: typed methods to log and query calls, objects, tables, feedback, costs and evaluations.
- **[`go-writer-ai`](https://github.com/psyb0t/go-writer-ai)**: Unofficial Go client for the Writer (writer.com) API: chat, completions, files, Knowledge Graphs, no-code applications and tools, generated from Writer's OpenAPI spec.
- **[`go-xai`](https://github.com/psyb0t/go-xai)**: Unofficial Go client for the xAI (Grok) REST API, generated with oapi-codegen: chat completions, responses, messages, embeddings, image and video generation, files, skills and models.
- **[`go-zeroentropy`](https://github.com/psyb0t/go-zeroentropy)**: Unofficial Go client for the ZeroEntropy API: collections, documents, retrieval queries, reranking and status, generated from the public OpenAPI spec.
- **[`go-zulip`](https://github.com/psyb0t/go-zulip)**: Unofficial Go client for the Zulip REST API: messages, users, channels, subscriptions, events and administration, generated from the spec Zulip publishes.

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
