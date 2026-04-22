# Contributing to Mad House Agents

This is the canonical agent library for the Mad House org. When you add or update an agent here, it rolls out to every Mad House repo that syncs from this one.

That means the bar is real. An agent that ships here runs everywhere.

---

## How to contribute

### Adding a new agent

1. Fork the repo and create a branch: `feature/agent-name-agent`
2. Create `agents/<name>.agent.md` using the structure below
3. Add the agent to the table in `README.md`
4. Bump the badge count in `README.md`
5. Open a PR against `main`

The Librarian runs a unification pass before any agent PR merges. The Reviewer checks that the agent is well-scoped and doesn't overlap with an existing one.

### Updating an existing agent

1. Branch: `fix/agent-name-description` or `docs/agent-name-description`
2. Make the change
3. Open a PR with a clear description of what changed and why

Mad House defaults to branch-first, PR-first development. Agents can prepare the branch and open the PR, but a human should merge. The org-wide workflow lives here:

https://github.com/madebymadhouse/bot-dev-playbook/blob/main/AGENTIC_GIT_WORKFLOW.md

### Agent file structure

Every `.agent.md` file must have valid YAML frontmatter:

```markdown
---
name: Agent Name
description: One sentence. This is what shows in agent pickers and registries. Make it specific.
tools: [read, search, execute, edit, todo]
user-invocable: true
argument-hint: What to say when invoking this agent. Give a real example prompt.
---

Agent body here.
```

**Frontmatter fields:**

| Field | Required | Notes |
|---|---|---|
| `name` | Yes | Title case, no "Agent" suffix |
| `description` | Yes | One sentence. Specific. What it does, not what it is. |
| `tools` | Yes | Use the minimal portable alias set this agent actually needs: `read`, `search`, `execute`, `edit`, `web`, `todo`, `agent` |
| `user-invocable` | Yes | Always `true` for agents in this repo |
| `argument-hint` | Yes | A real example prompt — not a vague description |

**Body:** Write it for the agent, not for a human reading it. Use clear section headers. Be explicit about what the agent should and shouldn't do. The more concrete, the better the behavior.

Avoid giant explicit tool inventories in frontmatter unless a specific extension tool is required. The portable alias vocabulary keeps the same agent spec usable across Copilot, Claude, Gemini, Codex, OpenClaw, and other runners that can map common capabilities.

---

## Commit format

All commits must follow [Conventional Commits](https://www.conventionalcommits.org/):

```
feat(agents): add <name> agent
fix(agents): correct <name> routing logic
docs(readme): update agent table
ci: add pr-check workflow
```

The `commitlint` check in the PR workflow will reject non-conforming commits. See `@git-keeper` in `.github/agents/` for the full commit guide.

---

## PR standards

Use the PR template. Fill in all sections. The PR description gate will fail if the body is under 50 characters.

A good PR for a new agent includes:
- What the agent does (and what it intentionally does not do)
- Why this agent rather than extending an existing one
- How you tested it — what prompts you tried, what the behavior was
- Any agents it coordinates with or hands off to

---

## What gets rejected

- Agents that duplicate an existing agent's scope without a clear reason
- Agents with vague `description` or `argument-hint` fields
- Commits that bundle multiple unrelated agent changes
- PRs that touch agents and README in the same commit (separate concerns)
- Breaking changes to existing agent behavior without a discussion issue first

---

## Syncing to other repos

Once an agent merges here, sync it to all Mad House repos:

```bash
for repo in \
  /home/samhcharles/repos/bot-dev-playbook \
  /home/samhcharles/repos/vps-maintenance-playbook \
  /home/samhcharles/srv/bots/chopsticks-lean; do
  cp agents/<name>.agent.md "$repo/.github/agents/<name>.agent.md"
  cd "$repo"
  git add .github/agents/<name>.agent.md
  git commit -m "feat(agents): sync <name> agent from madebymadhouse/agents"
  cd -
done
```

Each repo gets its own commit. No batching.
