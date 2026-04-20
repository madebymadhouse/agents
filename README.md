<div align="center">

# Mad House Agents

**Every AI agent built by Mad House — in one place.**

![License](https://img.shields.io/github/license/madebymadhouse/agents)
![Last Commit](https://img.shields.io/github/last-commit/madebymadhouse/agents)

</div>

---

This repo is the canonical home for all Mad House AI agents. Each agent is a `.agent.md` file with a YAML frontmatter block and a behavior specification that any VS Code Copilot agent, OpenClaw sub-agent, or compatible AI runtime can pick up.

> [!NOTE]
> Agents here are **definitions**, not deployments. Copy the `.agent.md` file into the `.github/agents/` directory of any repo where you want to use it.

---

## Agents

### Workflow Agents

| Agent | What it does |
|---|---|
| [auditor.agent.md](./agents/auditor.agent.md) | Deep structured audit of any repo, service, docs, or environment. Produces scored findings with exact fixes. |
| [updater.agent.md](./agents/updater.agent.md) | Acts on audit findings. Executes changes systematically, one finding at a time, with verification. |
| [playbook-builder.agent.md](./agents/playbook-builder.agent.md) | Turns repeated chat guidance into a real repo, playbook, or runbook set. |

### Documentation Agents

| Agent | What it does |
|---|---|
| [beautiful-readme.agent.md](./agents/beautiful-readme.agent.md) | Writes or rewrites GitHub READMEs to the Mad House beautiful-README standard. |

### Bot Development Agents

| Agent | What it does |
|---|---|
| [bot-dev-playbook.agent.md](./agents/bot-dev-playbook.agent.md) | Mad House bot development workflow — standards, handoffs, and coordination. |

### Infrastructure Agents

| Agent | What it does |
|---|---|
| [vps-maintenance-planner.agent.md](./agents/vps-maintenance-planner.agent.md) | VPS maintenance, runtime inspection, topology updates, and safe change planning. |

---

## How to Use an Agent

**In VS Code Copilot:**

Copy the `.agent.md` file into your repo's `.github/agents/` directory. VS Code will pick it up automatically.

```bash
# Example: add the auditor to your repo
cp agents/auditor.agent.md /your/repo/.github/agents/auditor.agent.md
```

**Invoke by name in chat:**
```
@auditor audit this repo, scope: docs + structure
@updater apply the HIGH and CRITICAL findings from this audit
@beautiful-readme rewrite the README for this repo
```

---

## Agent Format

Every agent in this repo follows the same format:

```markdown
---
name: Agent Name
description: One sentence — when to use this agent and what it does.
tools: [read, search, execute, edit, todo, agent]
user-invocable: true
argument-hint: What the user should tell this agent when invoking it.
---

[Agent behavior specification — required reads, goals, constraints, process, output format]
```

---

## Adding a New Agent

1. Create a new file in `agents/` named `your-agent-name.agent.md`
2. Use the format above
3. Add a row to the table in this README
4. Open a PR

> [!TIP]
> If you're not sure what an agent needs, use the `playbook-builder.agent.md` to design it first.

---

## Related Repos

| Repo | What it is |
|---|---|
| [madebymadhouse/bot-dev-playbook](https://github.com/madebymadhouse/bot-dev-playbook) | Shared workflow and standards for Discord bot development |
| [madebymadhouse/vps-maintenance-playbook](https://github.com/madebymadhouse/vps-maintenance-playbook) | VPS maintenance notebook for the live Mad House server |
| [samhcharles/chopsticks-lean](https://github.com/samhcharles/chopsticks-lean) | The live Mad House Discord bot |

---

## License

[MIT](./LICENSE)
