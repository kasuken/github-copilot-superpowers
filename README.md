
# GitHub Copilot SuperPowers

Opinionated, repo-local configuration for **GitHub Copilot (Chat + Agent mode)**: instruction hierarchy, reusable prompt files, custom agent profiles, and MCP server config.

<img width="1536" height="1024" alt="GitHub Copilot SuperPowers" src="https://github.com/user-attachments/assets/3414f8d4-5180-4926-8850-18378710a930" />

[Quickstart](#quickstart) • [What’s inside](#whats-inside) • [MCP servers](#mcp-servers) • [Repo layout](#repo-layout)

> [!NOTE]
> This repository is intentionally small and **highly opinionated**. It’s designed to be copied into other repos and adapted.

## Why this exists

GitHub Copilot gets significantly more useful when you make its “defaults” explicit: what quality bars to follow, when to stop and investigate, and how to keep edits scoped.
This repo packages those defaults in a form that’s easy to version, review, and reuse.

## What’s inside

- **Instruction system** under `.github/instructions/` (rules, workflow, quality gates)
- **Reusable prompts** under `.github/prompts/` (ex: generate a README, generate `AGENTS.md`, repo story time)
- **Custom agents** under `.github/agents/` (ex: Critical Thinking, Mentor, Janitor)
- **Agent “skills” playbooks** under `.github/skills/` (investigation mode, root-cause tracing, verification gates, etc.)
- **VS Code workspace settings** under `.vscode/settings.json` (enables Copilot agent features used by this repo)
- **MCP configuration** under `.vscode/mcp.json` (Sequential Thinking, Context7, Memory, Serena)

## Quickstart

### Use this repo as a template

1. Copy these folders into your target repository:

   - `.github/`
   - `.vscode/`

2. Review and tailor the instruction files:

   - Start with `.github/copilot-instructions.md`
   - Then adjust rules in `.github/instructions/` to match your team’s tolerance for “guard rails”.

> [!IMPORTANT]
> The instruction set in `.github/instructions/` is designed to reduce flakiness and “agent drift”, but it can also feel strict.
> If you don’t want delegation-heavy workflows or you’re not using subagents, loosen or remove those constraints.

### Use it in VS Code

- Open the repository (or your repo that copied these files) in VS Code.
- Ensure GitHub Copilot is enabled.
- Keep `.vscode/settings.json` checked in so the workspace defaults travel with the repo.

## MCP servers

This repo includes a ready-to-use MCP configuration at `.vscode/mcp.json`.

Configured servers:

- **Sequential Thinking** (structured reasoning)
- **Context7** (library documentation lookup)
- **Memory** (lightweight knowledge graph)
- **Serena** (project-aware code intelligence)

> [!TIP]
> If MCP servers fail to start, verify prerequisites:
> - `npx`-based servers require Node.js.
> - The Serena server in this repo is launched via `uvx` (from the `uv` Python tooling).

## Working with the prompt and agent files

- Prompt files live in `.github/prompts/` and are meant to be used from Copilot Chat when you want repeatable, higher-quality outputs.
- Agent profiles live in `.github/agents/` and define specialized “modes” (for example: a devil’s-advocate reviewer, a mentor, or a cleanup-focused janitor).
- Skills in `.github/skills/` are short playbooks that the agent can load on-demand (for example: switch to investigation mode after repeated failures).

## Repo layout

```
.
├─ .github/
│  ├─ copilot-instructions.md
│  ├─ agents/
│  ├─ instructions/
│  ├─ prompts/
│  └─ skills/
└─ .vscode/
   ├─ mcp.json
   └─ settings.json
```

## Notes

> [!CAUTION]
> GitHub-flavored admonitions (like the blocks in this README) don’t render everywhere and are intentionally limited in where they can be nested. If you copy/paste sections into places like `<details>` or nested lists, you may need to rewrite them as plain blockquotes.

