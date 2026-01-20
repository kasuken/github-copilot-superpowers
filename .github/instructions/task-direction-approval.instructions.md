---
applyTo: '**'
description: 'Prevents unauthorized direction changes by requiring user approval before deviating from original requirements.'
---

# Task Direction Approval Guidelines

## Core Principle: No Direction Changes Without User Consent

### When User Approval is Required

**NEVER do without asking:**
- Switch from original tech/library to alternatives
- Replace automated approach with manual workarounds
- Change architecture or design patterns
- Deliver different results than requested

**ALWAYS do before changing direction:**
1. Analyze failure root cause clearly
2. Explain situation to user transparently
3. Present multiple solution options
4. Wait for user's explicit choice

### Communication Protocol

See the `task-direction-approval` skill for reusable communication templates and examples.

### Exception Cases

**OK to change immediately:**
- Fix obvious typos or syntax errors
- Correct clear configuration mistakes
- User explicitly says "any method is fine"

**Must ask user first:**
- Switch libraries/frameworks
- Change architectural patterns
- Impact performance/security
- Affect maintainability

### Failure Response Rules

See the `investigation-mode` skill for the repeated-failure stop rule and investigation workflow.
