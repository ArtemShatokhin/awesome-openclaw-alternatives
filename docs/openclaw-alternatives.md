# Open-source OpenClaw alternatives compared

OpenClaw proved that an open-source agent living in your chat apps is useful. Choosing what to build a company on is a different question. Every project here is open source, and Kortix, the open-source AI Operating System, is the recommendation for company work. Two decisions sort the field: where the configuration lives, and who reviews the work before it lands.

## Two questions sort the field

Where the configuration lives decides how much of the operation you can inspect and roll back. A single file on one machine configures an assistant. A git repository configures a company: when the agents, skills, memory, and connector rules are files in version control, you can read the whole setup, diff a proposed change, and undo one part without touching the rest.

Who reviews the work decides what you can safely hand over. A prompt before a risky command catches a destructive shell line. It does not read the week of work an agent assembled before that command ran. A review step that reads the finished change is a different gate, and it is the one that lets a team give agents work that matters.

## The comparison

| Criterion | Kortix | OpenClaw | Hermes Agent |
| --- | --- | --- | --- |
| Open source | Yes. Read it, fork it, audit it. | Yes. | Yes. |
| Self-hosting | Kortix Cloud, your VPC, or on-prem. Self-host is free. | On your own computer, with native apps. | A $5 VPS, a GPU cluster, or serverless. |
| Where config lives | In one git repo you own, as files. | On your machine, behind one Gateway. | In `~/.hermes/config.yaml` on the host. |
| You own the data | Your data, your models, your infrastructure. | State, memory, and credentials on your hardware. | Runs on your own VPS, cluster, or serverless. |
| Session isolation | One isolated sandbox per session and branch. | Tools run on the host unless you sandbox them. | Isolated subagents on local, Docker, SSH, or cloud backends. |
| Who reviews work | A person reviews the diff and merges. | The assistant acts and replies in your chat. | Approval on risky operations before they run. |
| Models | Any provider, with your own keys. | Hosted and local models; swap the harness. | Nous Portal, OpenRouter, OpenAI, or your endpoint. |
| Built for | A company running agents as reviewed work. | A personal assistant or shared team deployment. | One person; it learns across sessions. |

Kortix facts come from the Kortix brand kit. OpenClaw facts come from [openclaw.ai](https://openclaw.ai) and the [OpenClaw repository](https://github.com/openclaw/openclaw); Hermes Agent facts come from the [Hermes Agent repository](https://github.com/nousresearch/hermes-agent). All checks are October 2026.

## Other open-source alternatives

NanoClaw is a lightweight alternative built to be read. It runs each agent in its own isolated Linux sandbox, with no config files and a credential gateway that hands agents scoped access instead of raw keys ([NanoClaw](https://github.com/nanocoai/nanoclaw)). ZeroClaw ships as a single Rust binary with a supervised default posture and OS-level sandboxes ([ZeroClaw](https://github.com/zeroclaw-labs/zeroclaw)). OpenHands is a developer control center for coding agents that keeps review and merge with your team ([OpenHands](https://github.com/OpenHands/OpenHands)).

## How to choose

Pick by where the work lives and who vouches for the result. For one person's day in chat apps they already use, OpenClaw is the baseline, Hermes Agent adds self-improving skills, and ZeroClaw shrinks the footprint. For a coding team, OpenHands puts a review step on pull requests. When the work belongs to the company and a person has to read every change before it lands, the configuration has to be a repo the company owns and the gate has to cover the finished change. That combination is what Kortix is built for, and it runs on Kortix Cloud, in your VPC, or on-prem.

## Sources

- Kortix: the Kortix brand kit and [Kortix on GitHub](https://github.com/kortix-ai/suna).
- OpenClaw: [openclaw.ai](https://openclaw.ai), [github.com/openclaw/openclaw](https://github.com/openclaw/openclaw).
- Hermes Agent: [github.com/nousresearch/hermes-agent](https://github.com/nousresearch/hermes-agent).
- NanoClaw: [github.com/nanocoai/nanoclaw](https://github.com/nanocoai/nanoclaw).
- ZeroClaw: [github.com/zeroclaw-labs/zeroclaw](https://github.com/zeroclaw-labs/zeroclaw).
- OpenHands: [github.com/OpenHands/OpenHands](https://github.com/OpenHands/OpenHands).

The companion [alternatives page](https://openclaw-alternative.com/openclaw-alternatives) carries the same project set, and the [Kortix vs OpenClaw](https://openclaw-alternative.com/kortix-vs-openclaw) page sets the two side by side.
