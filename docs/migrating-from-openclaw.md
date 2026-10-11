# Migrating from OpenClaw

You do not have to choose between OpenClaw and Kortix. Keep OpenClaw for a personal assistant on your own machine, and move the company work to Kortix, the open-source AI Operating System. Both tools keep your work as plain files, and they put those files in different places, so the move comes down to what to copy, in what order, and what to leave behind.

## Run them side by side first

OpenClaw and Kortix keep separate state, so each uses its own keys and channels. There is no cutover date: connect Kortix, move one workflow, and confirm it before you move the next. OpenClaw keeps its work as files on one machine, and Kortix keeps the same kinds of files in one git repo you own.

## What maps to what

| In OpenClaw | In Kortix | What you do |
| --- | --- | --- |
| Skills, a `SKILL.md` per folder | `skills/<name>/SKILL.md` | Copy the folder in; allow it to an agent. |
| Persona or system prompt | `agents/<name>.md` | Move the prompt in; declare its reach. |
| `MEMORY.md`, `USER.md`, daily notes | `memory/` | Copy durable facts; prune stale daily notes. |
| Channel plugins | connectors in `kortix.yaml` | Reconnect each service as a connector account. |
| Model and harness plugins | any model, your keys | Add provider keys or the ChatGPT plan you pay for. |
| Scheduled tasks | cron or webhook triggers | Recreate each task with `kortix triggers add`. |
| One local Gateway | one isolated sandbox per session | Nothing to move; each session isolates itself. |
| Local config files | `kortix.yaml` at the repo root | Recreate the settings as manifest entries. |

## The order to do it in

Install the CLI and scaffold the repo first, so there is somewhere for everything else to land.

```
curl -fsSL https://kortix.com/install | bash
kortix login
kortix init my-company
cd my-company
kortix ship
```

Move skills next, because they carry the least state. An OpenClaw skill is a folder with a `SKILL.md`, and a Kortix skill is the same shape under `skills/<name>/SKILL.md`, so the folders copy across. You then allow each agent the skills it may load through the agent's block in `kortix.yaml`.

Move the persona and system prompts after the skills. An OpenClaw persona becomes `agents/<name>.md`, an OpenCode agent file whose frontmatter sets the model and mode and whose body is the system prompt. The governance is the agent's block in `kortix.yaml`.

Move memory once the agents exist. Kortix keeps `MEMORY.md`, `USER.md`, and dated notes in a `memory/` directory in the repo. Copy the durable facts and the notes that still matter, and leave the stale daily notes behind.

Reconnect channels as connectors, not as files. Each channel plugin becomes a connector account, and connector credentials are brokered server-side and never enter the machine. Slack and Microsoft Teams are live; email is experimental, per project.

Point the models at your own keys, then recreate the scheduled tasks. Each OpenClaw scheduled task becomes a cron or webhook trigger in `kortix.yaml`, and the CLI writes the entry for you.

```
kortix triggers add daily-digest --type cron --cron "0 0 9 * * 1-5" --timezone America/Los_Angeles --prompt "Summarize yesterday's activity and save it as a daily note."
kortix ship
kortix triggers ls
```

Start a session and review the first change request last, so you see the whole loop end to end.

```
kortix sessions new --prompt "Summarize this week's support tickets" --wait
kortix cr ls
kortix cr diff 1
kortix cr merge 1
```

## What changes when you move

The runtime changes shape. Instead of one Gateway serving every conversation, each Kortix session gets its own isolated sandbox on its own branch. In OpenClaw, tools run on the host for the main session unless you configure sandboxing, so a change can take effect directly. Kortix inserts a gate: every session works on its own branch, and when the agent finishes it opens a change request. Session work reaches main through a change request, merge is default-deny for agents, and a session can never merge a change request it opened itself.

## What to leave behind

Leave machine-specific paths, secrets you no longer use, and daily notes that no longer describe anything true. Nothing that stays in OpenClaw needs to move, since the two tools run side by side with separate state.

## Sources

Kortix facts come from the Kortix brand kit. OpenClaw facts come from [openclaw.ai](https://openclaw.ai) and the [OpenClaw repository](https://github.com/openclaw/openclaw). The companion [migration guide](https://openclaw-alternative.com/migrate-from-openclaw) and the [Kortix vs OpenClaw](https://openclaw-alternative.com/kortix-vs-openclaw) page cover the same move in more depth.
