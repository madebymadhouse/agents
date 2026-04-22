# Agent Portability Contract

This repo is the portable core for the Mad House agent fleet.

The rule is simple: keep the agent body stable, keep the tool vocabulary small, and let each platform map the same agent into its own runtime.

That is how one agent spec stays usable across Copilot, Claude, Gemini, Codex, OpenClaw, and anything urchin sits over later.

---

## Portable Tool Vocabulary

Every agent should prefer these frontmatter aliases:

| Alias | Meaning |
|---|---|
| `read` | Read files or nearby context |
| `search` | Search code, docs, or symbols |
| `execute` | Run safe shell or runtime checks |
| `edit` | Create or modify files |
| `web` | Fetch URLs or external docs |
| `todo` | Track ordered work |
| `agent` | Invoke another agent |

If a platform supports these aliases directly, use them as-is.

If it does not, map them to the closest native capability. Do not fork the agent prompt just because the runtime names tools differently.

---

## Platform Mapping

| Platform | How to treat these agent files |
|---|---|
| Copilot | Native `.agent.md` support. Consume aliases directly. |
| Claude-style runners | Load the body as the system prompt and map aliases to available tools. |
| Gemini-style runners | Use the same prompt body and translate aliases into function/tool declarations. |
| Codex-style runners | Use the same prompt body and map aliases to read/search/edit/exec primitives. |
| OpenClaw | Keep the same body and map aliases into sandboxed worker capabilities. |
| Urchin | Treat agent outputs, handoffs, and memory files as durable sync artifacts rather than platform-specific transcripts. |

---

## What Must Stay Stable

These parts of an agent are the shared contract and should not drift by platform:

1. Name
2. Description
3. Argument hint
4. Scope boundaries
5. Required process
6. Output format
7. Hard rules

Tool names may be mapped.

Behavior should not be.

---

## Machine-to-Machine Contracts

When one agent delegates to another runner or worker, prefer a neutral contract shape:

```text
GOAL:
[exact task]

INPUTS:
[files, data, context]

CONSTRAINTS:
[execution limits, allowed tools, forbidden actions]

SUCCESS CRITERIA:
[how the caller will verify the result]

DELIVERABLES:
[patches, notes, logs, artifacts]
```

Avoid naming one platform in the contract unless the task truly depends on that platform.

---

## Memory and Sync

For urchin and similar sync systems, the important thing is not which model produced the work. The important thing is that the work resolves into stable artifacts a human can reuse.

Prefer durable outputs like:

| Artifact | Why it matters |
|---|---|
| handoff files | Carry active state between sessions and agents |
| decision logs | Preserve why a choice was made |
| task logs | Show what changed and what remains |
| audit reports | Turn broad inspection into ranked actions |
| runbooks | Convert repeated chat guidance into reusable procedure |

Urchin can bridge the gap between agent workflows and human memory by syncing these stable artifacts into the user's note system instead of treating any one chat log as the source of truth.

---

## Hard Rules

1. Prefer portable aliases over platform-specific tool IDs.
2. Do not fork agent bodies per platform unless behavior truly differs.
3. Put platform-specific details in adapters, loaders, or docs.
4. Keep machine contracts neutral and verification-first.
5. Optimize for durable artifacts that a human and a sync system can both understand.