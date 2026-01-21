
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

- **Instruction system** under `.github/instructions/` (rules, workflow, quality gates, execution protocol)
- **Reusable prompts** under `.github/prompts/` (ex: generate a README, generate `AGENTS.md`, repo story time, create release notes)
- **Custom agents** under `.github/agents/` (ex: Critical Thinking, Mentor, Janitor)
- **Agent "skills" playbooks** under `.github/skills/` (investigation mode, root-cause tracing, verification gates, uncertainty verification, minimalist development, task direction approval)
- **VS Code workspace settings** under `.vscode/settings.json` (enables Copilot agent features, advanced reasoning, MCP integration)
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

## Agent Skills

Agent skills are optional playbooks that can be loaded on-demand to handle specific scenarios. Load a skill when you need specialized handling for complex tasks.

Located in `.github/skills/`, this repo includes 6 ready-to-use skills:

| Skill | Purpose | When to use |
|-------|---------|------------|
| **investigation-mode** | Pause implementation after 2+ consecutive failures and switch to root-cause analysis before resuming | Repeated test failures or validation errors |
| **root-cause-tracing** | Trace bugs backward through call stacks to find the original trigger, not just the symptom | Deep debugging of complex issues |
| **task-direction-approval** | Explain failure root cause, present 2-3 solution options with trade-offs, and wait for explicit user choice | Before switching tech stacks or architectures |
| **uncertainty-verification** | Verify exact commands, configuration keys, API details, and version-specific behavior via official docs—no assumptions | When providing version-dependent or time-sensitive guidance |
| **verification-before-completion** | Run verification commands and confirm output before making any completion claims | Before marking tasks as complete or fixed |
| **minimalist-surgical-development** | Prioritize the smallest diff first, prefer standard libraries, avoid unsolicited refactoring | Code changes and refactoring work |

## Custom Agents

Custom agents define specialized "modes" for focused collaboration. Select an agent profile when you want tailored behavior for your specific task.

Located in `.github/agents/`, this repo includes 3 custom agent profiles:

| Agent | Role | Best for |
|-------|------|----------|
| **Critical Thinking** | Questions assumptions and encourages exploration of alternative approaches and edge cases | Architecture reviews, design decisions, risk analysis |
| **Mentor** | Provides Socratic guidance through critical questioning without providing direct solutions | Learning, skill development, understanding complex systems |
| **Janitor** | Focuses on cleanup, simplification, and technical debt remediation | Code cleanup, refactoring, removing dead code, performance optimization |

## MCP Servers

This repo includes a ready-to-use MCP configuration at `.vscode/mcp.json`.

Model Context Protocol (MCP) servers extend Copilot's capabilities with specialized tools and information sources.

Configured servers:

| Server | Purpose | Launch method |
|--------|---------|-----------------|
| **Sequential Thinking** | Structured multi-step reasoning with built-in revision support for complex problem-solving | `npx` |
| **Context7** | Up-to-date library and framework documentation lookup—always retrieves current version docs | `npx` |
| **Memory** | Lightweight knowledge graph for storing discovered patterns, architectural insights, and recurring solutions | `npx` |
| **Serena** | Project-aware code intelligence: symbol operations, file search, refactoring, and codebase analysis | `uvx` (Python `uv` tooling) |

### Prerequisites & Troubleshooting

- **Node.js**: Required for `npx`-based servers (Sequential Thinking, Context7, Memory)
- **Python `uv` tooling**: Required for Serena MCP server via `uvx`
- **No MCP servers starting?** Verify Node.js is installed (`npm --version`) and `uv` is available (`uv --version`)

## VS Code Settings

Located in `.vscode/settings.json`, the workspace includes optimized Copilot agent configuration.

### Agent & Skill Activation

| Setting | Purpose |
|---------|---------|
| `chat.agent.maxRequests` | Limits agent requests per session (set to 125) |
| `chat.useAgentSkills` | Enables loading skills from `.github/skills/` for specialized task handling |
| `chat.useAgentsMdFile` | Loads custom agent profiles from `.github/agents/*.agent.md` |
| `chat.useNestedAgentsMdFiles` | Supports multi-level agent profile organization |
| `chat.customAgentInSubagent.enabled` | Allows subagents to use custom agent profiles for complex delegation |

### Advanced Reasoning & Code Quality

| Setting | Purpose |
|---------|---------|
| `github.copilot.chat.responsesApiReasoningEffort` | Set to `"high"` for deeper problem analysis and fewer mistakes |
| `github.copilot.chat.responsesApiReasoningSummary` | Set to `"detailed"` for thorough thinking explanations |
| `inlineChat.enableV2` | Enables inline chat suggestions during code editing |
| `github.copilot.nextEditSuggestions.enabled` | Provides contextual edit suggestions based on chat history |

### Context & Search

| Setting | Purpose |
|---------|---------|
| `github.copilot.chat.newWorkspace.useContext7` | Automatically enables Context7 MCP for docs lookup in new workspaces |
| `github.copilot.chat.scopeSelection` | Limits context to the current selection for focused prompts |
| `github.copilot.chat.codesearch.enabled` | Enables semantic code search in chat context |
| `github.copilot.chat.alternateGptPrompt.enabled` | Provides alternative prompt rewriting suggestions |

### MCP & CLI Integration

| Setting | Purpose |
|---------|---------|
| `github.copilot.chat.useResponsesApi` | Enables reasoning and extended analysis capabilities |
| `github.copilot.chat.cli.customAgents.enabled` | Allows custom agents to be used from the CLI |
| `github.copilot.chat.cli.mcp.enabled` | Enables MCP servers in CLI mode for agent workflows |
| `github.copilot.chat.githubMcpServer.enabled` | Activates GitHub MCP for repo operations (issues, PRs, code search) |
| `github.copilot.chat.githubMcpServer.readonly` | Restricts GitHub MCP to read-only mode (set to `true` for safety) |

### Analytics

| Setting | Purpose |
|---------|---------|
| `editor.aiStats.enabled` | Tracks AI-assisted code writing metrics for insights |

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

