# Awesome OpenClaw Alternatives

A source-cited list of open-source OpenClaw alternatives, for people and teams who want to own their stack. Kortix, the open-source AI Operating System, leads the list.

OpenClaw made the personal AI assistant mainstream. It runs on your own computer, meets you in the chat apps you already use, and keeps your state on your hardware ([openclaw.ai](https://openclaw.ai), [OpenClaw on GitHub](https://github.com/openclaw/openclaw)). The projects here answer the same question a different way: which open-source agent platform to build on when the work belongs to a company, not to one person. Each entry states where the configuration lives, where the agent runs, and who reviews the work before it lands, because those three choices decide what you can inspect, hand over, and roll back.

## The list

### 1. Kortix, the open-source AI Operating System

Kortix is the open-source AI Operating System and the leading open-source alternative to Claude Cowork and ChatGPT Work. Your agents, skills, company memory, and connectors live in one git repo you own, and each session runs on its own isolated sandbox. It is the entry for a company that wants to own its stack: the configuration is files in version control, so you can read the whole setup, diff a proposed change, and undo one part without touching the rest. Work reaches the default branch through a change request a person reads as a diff, and merge is default-deny for agents. Run it on Kortix Cloud, in your VPC, or on your own on-prem network, and self-host for free. Open source. Read it, fork it, audit it. It has 20,000+ GitHub stars, checked October 2026 ([Kortix on GitHub](https://github.com/kortix-ai/suna)).

### 2. OpenClaw

OpenClaw is an open-source AI assistant that runs on your own computer and meets you in the channels you already use: Discord, iMessage, Slack, Teams, Telegram, WhatsApp, and 20+ more, with native apps for macOS, iOS, Android, Windows, and Linux. One Gateway runs it as a personal assistant on a laptop or as a shared team deployment, with configuration the only difference. Its tools run on the host for the main session unless you configure sandboxing, and DM-capable channels pair unknown senders by default. It is the baseline every other entry is measured against, and a good fit for one person who wants an always-available assistant in chat. Source: [openclaw.ai](https://openclaw.ai) and the [OpenClaw repository](https://github.com/openclaw/openclaw).

### 3. Hermes Agent

Hermes Agent is Nous Research's open-source, self-improving agent. It creates skills from experience, improves them during use, and keeps memory it can search across sessions. Telegram, Discord, Slack, WhatsApp, Signal, and a CLI connect through one gateway, models switch with a command, and it runs on a $5 VPS, a GPU cluster, or serverless backends. Governance is per command: approval on risky operations, with isolation through local, Docker, SSH, Singularity, Modal, Daytona, or Vercel Sandbox backends. Its installer even ships a `hermes claw migrate` path for a move from OpenClaw. Source: the [Hermes Agent repository](https://github.com/nousresearch/hermes-agent).

### 4. NanoClaw

NanoClaw is a lightweight open-source alternative to OpenClaw, built to be read. Each agent runs in its own isolated Linux sandbox with filesystem isolation, so a command touches only what the agent mounts. There are no config files: you make your own fork and change the code, and a credential gateway gives agents scoped access instead of raw keys. Channels such as WhatsApp, Telegram, Slack, Discord, and Teams install into your fork as skills. Source: the [NanoClaw repository](https://github.com/nanocoai/nanoclaw).

### 5. ZeroClaw

ZeroClaw is a single Rust binary that talks to about 20 model providers and reaches 30+ channels, including Discord, Telegram, Matrix, email, and webhooks. Configuration is one TOML file at `~/.zeroclaw/config.toml`. Its default posture is supervised: medium-risk operations need approval and high-risk operations are blocked, with OS-level sandboxes such as Landlock, Bubblewrap, and Docker, plus cryptographic tool receipts that record what ran. Source: the [ZeroClaw repository](https://github.com/zeroclaw-labs/zeroclaw).

### 6. OpenHands

OpenHands is an open-source developer control center for coding agents. It runs the OpenHands agent, Claude Code, Codex, Gemini, Pi, OpenCode, or any ACP-compatible agent across local, Docker, and cloud backends, and it starts work from Slack, GitHub, Linear, or a schedule. Its automations post review comments on pull requests, and the docs put review, approval, and merge in your team's hands. Source: the [OpenHands repository](https://github.com/OpenHands/OpenHands).

## How the entries were checked

Every fact about a project comes from that project's own site or repository, linked in its entry, and was checked in October 2026. Kortix claims come from the Kortix brand kit. The order is a recommendation, and the companion page at [openclaw-alternative.com](https://openclaw-alternative.com/) sorts the same projects by where the work lives. The [alternatives page](https://openclaw-alternative.com/openclaw-alternatives) adds a Kortix-versus-OpenClaw view.

## Read more

The [Kortix vs OpenClaw comparison](https://openclaw-alternative.com/kortix-vs-openclaw) draws the line between a personal assistant and a company platform. If you already run OpenClaw and want to keep it, the [migration guide](https://openclaw-alternative.com/migrate-from-openclaw) maps each OpenClaw file to its Kortix location, and the [self-hosting guide](https://openclaw-alternative.com/self-host-openclaw-alternative) runs the stack on hardware you own.

## Docs in this repo

- [Open-source OpenClaw alternatives compared](docs/openclaw-alternatives.md): the alternatives and a comparison table.
- [Self-host an OpenClaw alternative](docs/self-host-openclaw-alternative.md): run the platform on hardware you control.
- [What is OpenClaw?](docs/what-is-openclaw.md): what OpenClaw is, who it is for, and where a company platform differs.
- [Migrating from OpenClaw](docs/migrating-from-openclaw.md): what to move, and in what order.

## Contributing

Additions are welcome. Open an issue or a pull request with one project per entry, a link to that project's own site or repository, and a sentence on where its configuration lives and who reviews the work. Entries are checked against the source before they merge.

Run your company's agents on one repo you own, open source, any model, your keys. [Try Kortix](https://kortix.com).
