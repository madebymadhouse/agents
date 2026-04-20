# Agent Registry

This repo is the canonical source for all Mad House agents. All 16 agents are in `agents/` and symlinked to `.github/agents/` for VS Code Copilot discovery.

## How to invoke agents in VS Code

Use `@agent-name` in GitHub Copilot Chat. Start with `@delegator` for anything multi-step.

## Agent roster

| Agent | When to use |
|---|---|
| `@delegator` | **Start here.** Route any task in plain English. |
| `@orchestrator` | Coordinate multiple agents on a large task. |
| `@coder` | Write, change, or wire up production code. |
| `@reviewer` | Review code before merging. |
| `@debugger` | Root-cause an error or broken behaviour. |
| `@auditor` | Full scored audit of code, docs, security, ops. |
| `@security` | Security-only audit — OWASP, secrets, injection. |
| `@updater` | Execute on audit findings one by one. |
| `@git-keeper` | Branching, commits, PRs, clean git history. |
| `@writer` | Humanize docs, READMEs, runbooks. |
| `@beautiful-readme` | Full README rewrite to Mad House standard. |
| `@context-keeper` | Write HANDOFF.md / SESSION.md / DECISIONS.md for continuity. |
| `@librarian` | Org-wide consistency — badges, branding, cross-repo sync. |
| `@playbook-builder` | Convert chat guidance into reusable runbooks/repos. |
| `@vps-maintenance-planner` | VPS ops, runbooks, topology updates. |
| `@bot-dev-playbook` | Discord bot workflow and standards. |

## Syncing agents

Agents are synced to all repos via `madebymadhouse/agent-updater`. Do not edit copies in other repos — edit here, then sync.
