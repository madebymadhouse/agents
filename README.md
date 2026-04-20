<div align="center">

# Mad House Agents

**Every AI agent built by Mad House — in one place.**

![License](https://img.shields.io/github/license/madebymadhouse/agents)
![Last Commit](https://img.shields.io/github/last-commit/madebymadhouse/agents)

</div>

---

All the Mad House agents live here. Each one is a `.agent.md` file — a YAML frontmatter block plus a behavior spec that VS Code Copilot, OpenClaw, or any compatible AI runtime can pick up and run.

You don't run agents from this repo directly. You copy the file you want into your repo's `.github/agents/` folder and it shows up in your context automatically.

> [!TIP]
> Not sure which agent to use? The `argument-hint` field in each file's frontmatter tells you exactly what to pass when invoking it.

---

## Don't Feel Like Reading?

Drop this repo into any AI assistant — Claude, ChatGPT, Copilot, whatever you use — and ask it to explain any agent, help you pick the right one, or walk you through adding agents to your repo. Everything it needs is already here.

---

## Agents

### Unification & Oversight

| Agent | What it does |
|---|---|
| [librarian.agent.md](./agents/librarian.agent.md) | Keeps the whole Mad House repo ecosystem in order. Unified branding, consistent wording, cross-repo ref sync, org-wide health reports. Coordinates all other agents. Librarians don't play. |

### Workflow

| Agent | What it does |
|---|---|
| [auditor.agent.md](./agents/auditor.agent.md) | Audits any repo, service, docs, or environment. Produces scored findings — CRITICAL to LOW — with exact fixes, not vague recommendations. |
| [updater.agent.md](./agents/updater.agent.md) | Acts on audit findings. Works through them one at a time, verifies each change, and keeps a log of what was done. |
| [security.agent.md](./agents/security.agent.md) | Security-focused audit. OWASP Top 10, secrets in code, auth gaps, injection surfaces, vulnerable deps, infra exposure. Exact findings, exact fixes. |
| [playbook-builder.agent.md](./agents/playbook-builder.agent.md) | Turns repeated chat guidance into a real repo, runbook set, or playbook. Use when something keeps getting re-explained in conversation. |

### Writing & Documentation

| Agent | What it does |
|---|---|
| [writer.agent.md](./agents/writer.agent.md) | Rewrites any doc, README, or prose to sound like a person wrote it. Applies the Mad House humanized writing standard — no jargon, no filler, no corporate voice. |
| [beautiful-readme.agent.md](./agents/beautiful-readme.agent.md) | Writes GitHub READMEs with centered heroes, real badges, callout blocks, mermaid diagrams, and feature grids. No bullet wallpaper. |

### Bot Development

| Agent | What it does |
|---|---|
| [bot-dev-playbook.agent.md](./agents/bot-dev-playbook.agent.md) | Mad House Discord bot development workflow — standards, handoffs, and coordination across bot repos. |

### Infrastructure

| Agent | What it does |
|---|---|
| [vps-maintenance-planner.agent.md](./agents/vps-maintenance-planner.agent.md) | VPS maintenance planning — runtime inspection, topology updates, runbooks, and safe change sequences. |

---

## How to Use an Agent

Drop the `.agent.md` file into your repo's `.github/agents/` directory. VS Code picks it up automatically.

```bash
# Add the auditor to any repo
cp agents/auditor.agent.md your-repo/.github/agents/auditor.agent.md
```

Then invoke by name in chat:

```
@auditor audit this repo, scope: docs + security
@updater fix all HIGH and CRITICAL findings from that audit
@writer rewrite the README for this project — readers are developers, direct tone
@beautiful-readme rewrite the README for madebymadhouse/chopsticks-lean
```

---

## Agent Format

Every agent follows this format:

```markdown
---
name: Agent Name
description: One sentence. When to reach for this agent and what it does.
tools: [read, search, execute, edit, todo, agent]
user-invocable: true
argument-hint: What to tell the agent when invoking it.
---

[Behavior specification — required reads, goals, constraints, process, output format]
```

---

## Adding a New Agent

1. Create `agents/your-agent-name.agent.md`
2. Use the format above
3. Add a row to the right table in this README
4. Open a PR

> [!TIP]
> Use `playbook-builder.agent.md` to design a new agent before writing it from scratch. It'll help you define scope, constraints, and output format before you're committed to a shape.

---

## Mad House Repos

| Repo | What it is |
|---|---|
| [madebymadhouse/agents](https://github.com/madebymadhouse/agents) | This repo — all agents |
| [madebymadhouse/bot-dev-playbook](https://github.com/madebymadhouse/bot-dev-playbook) | Shared workflow and standards for Discord bot development |
| [madebymadhouse/vps-maintenance-playbook](https://github.com/madebymadhouse/vps-maintenance-playbook) | VPS maintenance notebook for the live server |
| [madebymadhouse/chopsticks-lean](https://github.com/madebymadhouse/chopsticks-lean) | The live Mad House Discord bot |

---

## License

[MIT](./LICENSE)
