# Changelog

## [1.0.2] - 2026-01-22

> License addition, documentation expansion, and new technical debt remediation agent.

### ✨ New Features

- **feat:** Add Technical Debt Remediation Plan agent ([.github/agents/tech-debt-remediation-plan.agent.md](.github/agents/tech-debt-remediation-plan.agent.md))
  - Generates comprehensive technical debt remediation plans with analysis framework
  - Includes core metrics: Ease of Remediation (1-5), Impact with visual icons, Risk indicators (🟢🟡🔴)
  - Covers common debt types: test coverage, documentation, code structure, deprecated dependencies
  - Output format: Summary table + detailed plan with implementation steps and testing methods
  - Analysis only - no code modifications

### 📚 Documentation Updates

- **docs:** Expand README with detailed component documentation ([README.md](README.md))
  - Add comprehensive agent skills table with purpose and usage triggers
  - Add custom agents table with roles and best-use scenarios
  - Add MCP servers table with launch methods and prerequisites
  - Add VS Code settings breakdown organized by category (Agent & Skill Activation, Advanced Reasoning, Context & Search, MCP & CLI Integration, Analytics)
  - Expand MCP server documentation with prerequisites and troubleshooting guidance

### 📄 License

- **license:** Add MIT License file ([LICENSE](LICENSE))
  - Copyright 2026 Emanuele Bartolesi
  - Standard MIT License terms with full permissions and warranty disclaimers
- **fix:** Update copyright holder in LICENSE file to Emanuele Bartolesi

### ⚙️ Configuration Changes

- **chore:** Remove `RELEASE_NOTES.md` as it is superseded by structured CHANGELOG.md format
  - Consolidate version history into single CHANGELOG.md file
  - Maintain consistent format across all releases

### 🙏 Acknowledgments

Thanks to contributors and early adopters providing feedback on agent configuration, documentation structure, and license requirements.

## [1.0.1] - 2026-01-21

> Small clarity pass: make the runbook and status template read like developer tooling, not bureaucracy.

### 📚 Documentation Updates

- **docs:** Rename “Execution protocol” terminology to **Developer runbook** in the instruction guidance
- **docs:** Rename “Pre-work execution status” template to **Preflight check** and refresh template labels for readability

### ⚙️ Configuration Changes

- **config:** Update the mandatory response template naming to match the new terminology (**SSOT Tool Gate**, **Delegation status**)

### 🙏 Acknowledgments

Thanks to everyone providing feedback on wording and ergonomics.

### 📄 License

This repository does not currently include a `LICENSE` file. Add one before publishing or distributing to make the usage terms explicit.

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
[1.0.1]: https://github.com/OWNER/REPO/releases/tag/v1.0.1
[1.0.2]: https://github.com/OWNER/REPO/compare/v1.0.1...v1.0.2
