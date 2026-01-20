# CHANGELOG Structure Reference

**Source**: [GitHub Gist by andreasonny83](https://gist.github.com/andreasonny83/24c733ae50cadf00fcf83bc8beaa8e6a)

## Structure Overview

The gist provides a **RELEASE-NOTES.md** template (also applicable to CHANGELOG.md) with the following key structural elements:

### Version Header Format
```markdown
## [0.5.2](https://github.com/user/repo/compare/v0.5.1...v0.5.2) (2019-07-21)
```

**Pattern**:
- `## [VERSION](COMPARE_LINK) (DATE)`
- Version is linked to GitHub comparison between previous and current version
- Date in `YYYY-MM-DD` format

### Standard Section Order

1. **Upgrade Steps** - Actions required when upgrading
2. **Breaking Changes** - Complete list of breaking changes
3. **New Features** - Newly added functionality
4. **Bug Fixes** - Fixed issues/bugs
5. **Performance Improvements** / **Improvements** - Enhancements and optimizations
6. **Other Changes** - Miscellaneous updates (should ideally be empty)

## Tone and Style

### Writing Characteristics
- **Concise and actionable**: Bullet points with clear, direct language
- **User-focused**: Describes *what* changed and *why* it matters to users
- **Practical guidance**: Includes when/how to use new features
- **Transparent**: Calls out caveats, warnings, and beta features

### Detail Level
- **Upgrade Steps**: Concrete, pseudocode-level instructions
- **Breaking Changes**: Complete enumeration (preferably none for non-major versions)
- **New Features**: Description + use cases + visual aids when applicable
- **Bug Fixes**: What now works as intended
- **Improvements**: Specific areas improved (workflow, performance, UX, logging, error messaging)

## Formatting Patterns

### Commit/Change References

**Example from gist**:
```markdown
* **dependencies:** Bump dependencies  4a4ee13
* **chore(conventionalChangelog):** Add Conventional Changelog  aafcdd9
```

**Pattern**:
- Bullet point starts with scope in bold (e.g., `**dependencies:**`, `**chore(conventionalChangelog):**`)
- Followed by description
- Ends with commit SHA (7-character short hash)
- Uses conventional commit prefixes when applicable

### Section Structure
```markdown
### Section Name

* [ACTION REQUIRED] (for critical upgrade steps)
* Change description  commit_sha
* Another change  commit_sha
```

### Preferability Guidance
> "Preferably, there's nothing here" - Applied to:
- Upgrade Steps (prefer seamless upgrades)
- Breaking Changes (avoid unless major version)
- Other Changes (categorize properly)

## Key Patterns to Follow

1. **Versions in reverse chronological order**: Newest releases at the top
2. **Comparison links**: Link each version to GitHub compare view
3. **Conventional commits**: Use scoped prefixes (`feat:`, `fix:`, `chore:`, `perf:`, etc.)
4. **Action flags**: Use `[ACTION REQUIRED]` for critical upgrade steps
5. **Completeness**: Every change should fit a category; minimize "Other Changes"
6. **Visual aids**: Encouraged for New Features ("Add some pictures!")
7. **Beta warnings**: Call out experimental features explicitly
8. **Empty sections OK**: If no changes in a category, omit the section or use placeholder bullets

## Recommended Sections for v1.0.0 Initial Release

For an initial v1.0.0 release, include:

### Essential Sections
1. **Description** - High-level overview of what this version represents
2. **New Features** - Core functionality being released
3. **Upgrade Steps** - Installation/setup instructions (if applicable)
4. **Known Issues** - Any limitations or caveats (optional but transparent)

### Skip for v1.0.0
- **Breaking Changes**: Not applicable for first release
- **Bug Fixes**: No previous version to fix
- **Performance Improvements**: Baseline performance, no "improvement"
- **Upgrade Steps**: May be minimal if this is the first installation

### Alternative Structure for v1.0.0
Some projects use a simpler structure for initial release:

```markdown
## [1.0.0] - YYYY-MM-DD

Initial release of [Project Name]

### Features
- Core feature 1
- Core feature 2
- Core feature 3

### Installation
- Step 1
- Step 2
```

## Template for Copy-Paste

```markdown
## [VERSION](COMPARE_LINK) (YYYY-MM-DD)

> Brief description

### Upgrade Steps
* [ACTION REQUIRED]
* 

### Breaking Changes
* 
* 

### New Features
* 
* 

### Bug Fixes
* 
* 

### Performance Improvements
* 
* 

### Other Changes
* 
* 
```

## Citation

**Source**: https://gist.github.com/andreasonny83/24c733ae50cadf00fcf83bc8beaa8e6a  
**Based on**: Palantir internal template  
**Example repo**: twilio-remote-cli

---

## Context Package Summary

- **Structure**: Version headers with GitHub compare links, 6 standard sections (Upgrade Steps → Other Changes)
- **Tone**: User-focused, actionable, transparent with caveats/warnings
- **Formatting**: Bullet points with scope prefixes, commit SHAs, conventional commits
- **Key pattern**: Minimize "Other Changes" and "Upgrade Steps" - prefer seamless, categorized updates
- **v1.0.0 recommendation**: Focus on Description + New Features + Installation; skip Breaking Changes/Bug Fixes
- **Action flags**: Use `[ACTION REQUIRED]` for critical upgrade steps
- **Visual aids**: Encouraged for New Features sections
- **Citation**: https://gist.github.com/andreasonny83/24c733ae50cadf00fcf83bc8beaa8e6a

### Next Actions
1. Use this reference when creating CHANGELOG.md for v1.0.0
2. Adapt section names to project conventions (e.g., "Improvements" vs "Performance Improvements")
3. Link versions to GitHub compare URLs when applicable
4. Follow conventional commit patterns for consistency
