# Self-host an OpenClaw alternative

Running an agent on your own hardware is why many people left hosted assistants in the first place. Kortix, the open-source AI Operating System, is the self-hostable option in this list: run it on Kortix Cloud, in your VPC, or on your own on-prem network, and self-host for free. Self-hosting takes a machine you control, a model account, and a handful of commands to bring the platform up and review the first change that lands.

## What you are hosting

Kortix is the open-source AI Operating System. Your agents, skills, company memory, and connectors live in one git repo you own, and each session runs on its own isolated sandbox. What you host is the platform that starts those sessions and the review gate in front of them, so every session works on its own branch and lands as a change request. On the machine you control, the stack has no Redis and no separate worker, which keeps the footprint small.

## Before you start

You need a machine you control with Docker installed, a git repo for the project, and a model account. Kortix is model-agnostic: any model provider with your own keys, or the ChatGPT plan you already pay for, or sign-in with your OpenCode Console account for OpenCode Zen and Go. Nothing else is required to start.

## Install the CLI

The CLI runs on macOS and Linux, or on Windows through WSL. It downloads a prebuilt binary and opens a browser to sign you in.

```
curl -fsSL https://kortix.com/install | bash
kortix login
```

## Scaffold the project repo

`kortix init` turns a directory into a project with a `kortix.yaml` manifest and starter agent and skill folders. `kortix ship` checks the configuration, asks for any missing secret, pushes the repo, and runs it.

```
kortix init my-company
cd my-company
kortix ship
```

To bind a repo folder you already have to a project you created, run `kortix projects link <project-id>`.

## Start the stack on your own hardware

`kortix self-host start` brings up the platform on your machine. The first run asks six things and no model key. GitHub connects in the dashboard under Settings → Git, and models are BYOK in the app. Pipedream is optional. The [Docs](https://kortix.com/docs/host) cover the deployment and the host options in full.

## Connect a channel

Slack and Microsoft Teams are live; email is experimental, per project. Connect the app from the project dashboard, invite the bot, and mention it with a task. A Slack mention starts a session on its own machine and the agent replies in the same thread.

## Add a trigger

A trigger starts a session with no person present. A cron schedule fires it on the clock, and a signed webhook fires it on an event. Add one, push it, and confirm it is live.

```
kortix triggers add daily-digest --type cron --cron "0 0 9 * * 1-5" --timezone America/Los_Angeles --prompt "Summarize yesterday's activity and save it as a daily note."
kortix ship
kortix triggers ls
```

Approval gates are off until you set them, so decide where the work needs a person before you leave a trigger unattended.

## Start a session and review the change

```
kortix sessions new --prompt "Summarize this week's support tickets" --wait
kortix cr ls
kortix cr diff 1
kortix cr merge 1
```

Session work reaches main through a change request. Merge is default-deny for agents, and a session can never merge a change request it opened itself, so what lands is a diff you read and approved.

## Where Kortix fits beside OpenClaw

OpenClaw is a personal assistant on your own computer, run as one Gateway, and its tools run on the host unless you configure sandboxing ([OpenClaw repository](https://github.com/openclaw/openclaw)). That suits one person with a laptop. Kortix suits a company: one git repo you own, one isolated sandbox per session, and a review gate before work lands. Many teams keep OpenClaw for personal work and self-host Kortix for the company, with separate state and separate keys. The [migration guide](https://openclaw-alternative.com/migrate-from-openclaw) covers running both.

## Sources

Kortix facts come from the Kortix brand kit. OpenClaw facts come from [openclaw.ai](https://openclaw.ai) and its repository. The companion [self-hosting page](https://openclaw-alternative.com/self-host-openclaw-alternative) and the [alternatives page](https://openclaw-alternative.com/openclaw-alternatives) cover the wider field.
