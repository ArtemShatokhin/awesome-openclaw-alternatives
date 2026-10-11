# What is OpenClaw?

OpenClaw is an open-source AI assistant that runs on your own computer and meets you in the messaging channels you already use. Its own site describes it plainly: it organizes your inbox, sends email, manages your calendar, and does it from WhatsApp, Telegram, or any chat app you already use, with no subscription, no hosted tier, and no token ([openclaw.ai](https://openclaw.ai)). A company that runs agents as reviewed work needs different answers to three questions, and Kortix, the open-source AI Operating System, is the platform built around those answers.

## OpenClaw in one paragraph

OpenClaw is an open-source AI assistant that runs on your own computer, meets you in the channels you already use, and keeps its state on your hardware. It is stewarded by the OpenClaw Foundation, an independent 501(c)(3), and has no paid tier, hosted service, or token. It is an agent harness and message router rather than a hosted product: you install it on a machine you control, connect your own model, and talk to it from chat.

## Who OpenClaw is for

OpenClaw suits one person who wants an always-available assistant on their own computer, and it scales to a shared team deployment. Its own repository says one Gateway can run it as a personal assistant on a laptop or as a shared team deployment, with configuration the only difference. It also suits people who want their agent to live where they already talk: Discord, iMessage, Slack, Teams, Telegram, WhatsApp, and 20+ more, plus native apps for macOS, iOS, Android, Windows, and Linux.

## How OpenClaw works

OpenClaw runs a local Gateway as the control plane for sessions, tools, events, and channel connections. The Control UI, the CLI, and the terminal UI all connect to that Gateway, and channels bring the assistant to each messaging service. Models and agent harnesses are plugins you can swap without changing anything else, and state, memory, and credentials live on your hardware. By default its tools run on the host for the main session unless you configure sandboxing, and DM-capable channels pair unknown senders before they can reach the assistant ([OpenClaw repository](https://github.com/openclaw/openclaw)).

## Where a company agent platform differs

A company agent platform answers three questions differently: where the configuration lives, where each unit of work runs, and who reviews the result. Kortix is the open-source AI Operating System, and its answers are a git repo you own, one isolated sandbox per session, and a change request a person approves.

| Question | OpenClaw | Kortix |
| --- | --- | --- |
| Where the configuration lives | On your machine, behind one Gateway. | In one git repo you own, as files. |
| Where the agent runs | On your own computer. | One isolated sandbox per session and branch. |
| Who reviews the work | The assistant acts and replies in chat. | A person reviews the diff and merges. |
| Built for | A personal assistant, or a shared team deployment. | A company running agents as reviewed work. |

Because Kortix keeps agents, skills, memory, and connectors as files in one repo, you can read the whole setup, diff a proposed change, and undo one part without touching the rest. Each session runs on its own isolated sandbox, and thousands of agents run in parallel on one config, each on its own cloud computer. Session work reaches main through a change request, and merge is default-deny for agents.

## Sources

OpenClaw facts come from [openclaw.ai](https://openclaw.ai) and the [OpenClaw repository](https://github.com/openclaw/openclaw). Kortix facts come from the Kortix brand kit. Checked October 2026. The [alternatives page](https://openclaw-alternative.com/openclaw-alternatives) compares the wider field, and the [Kortix vs OpenClaw](https://openclaw-alternative.com/kortix-vs-openclaw) page sets the two side by side.
