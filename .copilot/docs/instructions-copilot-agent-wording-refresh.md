# copilot-agent.instructions.md — wording refresh (developer-oriented)

## Summary

- Rename the “EXECUTION PROTOCOL” section family to “DEVELOPER RUNBOOK” (headings + inline references), keeping the 6-phase structure and all rule semantics intact.
- Rename the “PRE-WORK EXECUTION STATUS” block label to “PREFLIGHT CHECK” (including all inline references to that label).
- Refresh the preflight block’s header icon and a couple of labels to read more like a developer checklist, while preserving the **✅/❌/⏭️** semantics and the existing integrity constraints.
- Keep changes minimal: pure wording/icon swaps; no rule reordering, no new requirements, no behavior changes.

## Minimal rename map (old → new)

### Core section renames

- `EXECUTION PROTOCOL` → `DEVELOPER RUNBOOK`
- `EXECUTION PROTOCOL - 6 PHASES` → `DEVELOPER RUNBOOK - 6 PHASES`
- `Execution protocol` (inline mention in hierarchy description) → `Developer runbook` (same sentence shape)

### Template block rename

- `PRE-WORK EXECUTION STATUS` → `PREFLIGHT CHECK`

### Inline reference updates (keep meaning)

- `See "EXECUTION PROTOCOL - 6 PHASES" below for details.` → `See "DEVELOPER RUNBOOK - 6 PHASES" below for details.`
- `Display PRE-WORK EXECUTION STATUS` → `Display PREFLIGHT CHECK`

## Preflight block label/icon refresh (minimal, developer-oriented)

Keep the integrity constraints and check semantics exactly as-is, but:

- Change the preflight header line icon + label:
  - `⚒️ **PRE-WORK EXECUTION STATUS**` → `🛠️ **PREFLIGHT CHECK**`

- (Optional, minimal) tighten one label to sound more dev-checklist-y while retaining meaning:
  - `**Forbidden MCP Gate**` → `**SSOT Tool Gate**`

Everything else in the template block should remain unchanged unless a rename-map rule above requires it.

## Citations (current text that needs updates)

> All citations refer to: `c:\_GITHUB_\github-copilot-superpowers\.github\instructions\copilot-agent.instructions.md`

### “EXECUTION PROTOCOL” occurrences

- Execution protocol mentioned in hierarchy list item: `... (this file) - Execution protocol & quality standards`  
  Citation: `.github/instructions/copilot-agent.instructions.md:L12-L12`

- Inline reference to the 6-phase section: `See "EXECUTION PROTOCOL - 6 PHASES" below for details.`  
  Citation: `.github/instructions/copilot-agent.instructions.md:L35-L35`

- Main heading: `## 🚨 EXECUTION PROTOCOL - 6 PHASES`  
  Citation: `.github/instructions/copilot-agent.instructions.md:L65-L65`

- Subheading: `### Execution Protocol` (under “🎯 IMPLEMENTATION RULES”)  
  Citation: `.github/instructions/copilot-agent.instructions.md:L168-L168`

### “PRE-WORK EXECUTION STATUS” occurrences

- Template header inside the fenced block: `⚒️ **PRE-WORK EXECUTION STATUS**`  
  Citation: `.github/instructions/copilot-agent.instructions.md:L43-L43`

- Phase 1 step text: `Display PRE-WORK EXECUTION STATUS`  
  Citation: `.github/instructions/copilot-agent.instructions.md:L73-L73`

- Phase 6 instruction: `Display PRE-WORK EXECUTION STATUS, then proceed ...`  
  Citation: `.github/instructions/copilot-agent.instructions.md:L123-L123`

### Integrity constraints / surrounding anchor text (should remain semantically identical)

- “INTEGRITY CHECK” paragraph that constrains the checklist’s truthfulness  
  Citation: `.github/instructions/copilot-agent.instructions.md:L37-L40`

- “Execution order” line that introduces the response template (keep meaning; only update any renamed references)  
  Citation: `.github/instructions/copilot-agent.instructions.md:L34-L35`

## Next actions (for implementation subagent)

1. Apply the rename map to `c:\_GITHUB_\github-copilot-superpowers\.github\instructions\copilot-agent.instructions.md`.
2. Update all inline references identified above (including the hierarchy list item and both “Display PRE-WORK…” lines).
3. Update the template block header icon + label to `🛠️ **PREFLIGHT CHECK**`.
4. (Optional) Rename `**Forbidden MCP Gate**` → `**SSOT Tool Gate**` in the preflight block only, ensuring semantics remain unchanged.
5. Re-scan the file to confirm there are **zero** remaining instances of:
   - `EXECUTION PROTOCOL`
   - `PRE-WORK EXECUTION STATUS`
6. Sanity-check that no meaning changed: the integrity constraints still refer to the same requirements and ✅/❌/⏭️ semantics.
