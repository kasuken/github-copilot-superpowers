# Changelog

## [1.0.0] - 2026-01-20

### 🎉 Initial Release

**GitHub Copilot SuperPowers** is an opinionated, repo-local configuration system that transforms GitHub Copilot from a helpful assistant into a disciplined development partner with built-in quality gates, systematic debugging, and context-efficient workflows.

This release provides a complete, production-ready configuration system designed to reduce "agent drift", prevent hallucinations, and enforce evidence-based development practices.

### ✨ New Features

#### Instruction System
- **feat:** Add comprehensive instruction hierarchy with 4 core files ([copilot-agent.instructions.md](.github/instructions/copilot-agent.instructions.md), [subagents.instructions.md](.github/instructions/subagents.instructions.md), [taming-copilot.instructions.md](.github/instructions/taming-copilot.instructions.md), [task-direction-approval.instructions.md](.github/instructions/task-direction-approval.instructions.md))
- **feat:** Implement 6-phase execution protocol with mandatory pre-work status template
- **feat:** Add SSOT-based delegation framework preventing direct investigation I/O
- **feat:** Create Context Package contract for subagent returns (summary + citations + next actions)

#### Agent Skills (Playbooks)
- **feat:** Add `investigation-mode` skill - pauses implementation after 2+ failures, switches to root-cause investigation
- **feat:** Add `root-cause-tracing` skill - traces bugs backward through call stack with systematic instrumentation
- **feat:** Add `task-direction-approval` skill - requires user approval before architecture/library changes
- **feat:** Add `uncertainty-verification` skill - enforces verification via official docs, bans assumption-based answers
- **feat:** Add `verification-before-completion` skill - requires running tests before claiming "fixed" or "complete"
- **feat:** Add `minimalist-surgical-development` skill - prioritizes simplest solution, surgical edits only

#### Custom Agent Profiles
- **feat:** Add `Critical Thinking` agent - challenges assumptions, encourages alternative approaches
- **feat:** Add `Mentor` agent - provides Socratic guidance without direct solutions
- **feat:** Add `Janitor` agent - focuses on cleanup, simplification, tech debt remediation

#### Reusable Prompts
- **feat:** Add `repo-story-time.prompt.md` - generates narrative walkthroughs of repository evolution
- **feat:** Add `create-readme.prompt.md` - produces comprehensive README.md files
- **feat:** Add `create-agentmd.prompt.md` - documents agent configurations and workflows
- **feat:** Add `create-release-notes.prompt.md` - generates structured release notes and changelog entries

#### MCP Server Integration
- **feat:** Configure Sequential Thinking MCP - structured multi-step reasoning with revision support
- **feat:** Configure Context7 MCP - up-to-date library and framework documentation lookup
- **feat:** Configure Memory MCP - lightweight knowledge graph for discovered patterns
- **feat:** Configure Serena MCP - project-aware code intelligence and symbol operations

### ⚙️ Configuration Changes

#### VS Code Workspace
- **config:** Add `.vscode/settings.json` with Copilot agent feature flags enabled
- **config:** Enable `github.copilot.chat.codeGeneration.instructions` for custom instruction loading
- **config:** Enable `github.copilot.chat.useProjectTemplates` for prompt template discovery

#### MCP Server Setup
- **config:** Add `.vscode/mcp.json` with 4 pre-configured MCP servers
- **config:** Configure Sequential Thinking MCP via `npx` (`@modelcontextprotocol/server-sequential-thinking`)
- **config:** Configure Context7 MCP via `npx` (`@upshift-dev/context7-mcp-server`)
- **config:** Configure Memory MCP via `npx` (`@modelcontextprotocol/server-memory`)
- **config:** Configure Serena MCP via `uvx` (`serena-mcp`)

### 📚 Documentation

#### Core Documentation
- **docs:** Add comprehensive [README.md](README.md) with quickstart, component catalog, and repo layout
- **docs:** Add [.github/copilot-instructions.md](.github/copilot-instructions.md) as tech stack entry point
- **docs:** Document all 6 skills in `.github/skills/*/SKILL.md` with usage triggers and examples
- **docs:** Document all 3 custom agents in `.github/agents/*.agent.md` with prompts and use cases

#### Instruction Documentation
- **docs:** Add detailed execution protocol with 6 phases (Request Analysis → MCP Detection → Subagent Dispatch → Violation Check → Implementation → Terminal Verification)
- **docs:** Document forbidden MCP patterns and pre-call gate enforcement
- **docs:** Add Context Package contract specification
- **docs:** Document quality standards (SOLID, DRY, YAGNI, KISS, Clean Code principles)

#### Integration Guides
- **docs:** Add MCP server prerequisites (Node.js for `npx`, Python `uv` for Serena)
- **docs:** Document customization options for instruction strictness levels
- **docs:** Add troubleshooting section for MCP server startup failures

### 🙏 Acknowledgments

This configuration system evolved from real debugging sessions, refactoring battles, and "agent drift" frustrations. It packages the patterns that consistently produced the most reliable and maintainable results when working with GitHub Copilot in agent mode.

Special thanks to the Model Context Protocol (MCP) community for providing the extensibility framework that makes this integration possible.

### 📄 License

See [LICENSE](LICENSE) file for details.

---

## Getting Started

**Quick Setup:**
1. Copy `.github/` and `.vscode/` folders to your repository
2. Review and customize `.github/instructions/` to match your team's preferences
3. Open in VS Code with GitHub Copilot enabled

**Prerequisites:**
- Visual Studio Code with GitHub Copilot extension
- Node.js (for MCP servers using `npx`)
- Python `uv` tooling (for Serena MCP server)

**Customization:**
This configuration is intentionally opinionated. Adjust strictness by editing instruction files in `.github/instructions/` or removing specific skills from `.github/skills/`.

---

[1.0.0]: https://github.com/OWNER/REPO/releases/tag/v1.0.0
