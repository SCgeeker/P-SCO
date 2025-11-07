# Changelog

All notable changes to P-CSO Writing Skills will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.9.0] - 2025-11-07

### Changed - Marketplace Format Migration

**🚀 Major Update: Claude Code Marketplace Format**

This release represents a complete restructuring to support Claude Code marketplace distribution.

#### Added
- `.claude-plugin/marketplace.json` - Marketplace configuration file
- YAML frontmatter to all SKILL.md files with `name` and `description` fields
- Comprehensive README.md in Traditional Chinese with:
  - Installation instructions for marketplace
  - Complete workflow examples (A/B/C/D)
  - Quick reference tables
  - Best practices guide
  - P-CSO principles overview
- LICENSE file (MIT License)
- CHANGELOG.md (this file)
- Enhanced .gitignore

#### Changed
- Renamed all `skill.md` → `SKILL.md` (uppercase, marketplace requirement)
- Restructured repository for marketplace compatibility:
  - Root-level `.claude-plugin/` directory
  - Simplified directory structure
  - Skills-only distribution (agents removed)
- Updated README.md from English to Traditional Chinese
- Consolidated documentation from separate `docs/` folder into README

#### Removed
- `agents/writing-manager/` - Moved to separate development repository
- `docs/` directory - Content integrated into README.md
- Legacy file naming conventions
- English-only documentation

### Technical Details

**Skills Included (6 total):**
1. `p-cso-workflow` - Complete notes-to-manuscript pipeline
2. `pinker-syntax` - Sentence-level syntax optimization (Chapter 4)
3. `pinker-coherence` - Discourse-level coherence optimization (Chapter 5)
4. `pinker-quick` - Rapid cognitive cleanup for active drafting
5. `notes-to-manuscript` - Ethical AI-assisted scaffolding
6. `english-editing` - Academic English copyediting

**Installation:**
```bash
/plugin marketplace add SCgeeker/P-SCO
/plugin install p-cso-skills
```

**Status:** Preview/Beta - Ready for testing and feedback

---

## [1.0.0] - 2025-10-26

### Initial Release

**Personal Writing System (Pre-Marketplace Format)**

First implementation of P-CSO (Pinker's Cognitive Style Optimization) framework for academic writing assistance.

#### Components
- 1 agent: writing-manager (orchestration)
- 6 skills: p-cso-workflow, pinker-syntax, pinker-coherence, pinker-quick, notes-to-manuscript, english-editing
- Documentation: p-cso-writing-workflow.md, skills-vs-agents-guide.md, cross-device-setup.md
- Academic manuscript example

**Format:** Personal `.claude/` directory structure
**Language:** English
**Total:** ~25,000 words of prompts and documentation

---

## Future Plans

### [1.0.0] - Planned
- Incorporate user feedback from 0.9.0 preview
- Refine YAML descriptions based on usage patterns
- Add troubleshooting section based on common issues
- Potential addition of example use cases
- Consider multilingual support (English version of README)

### [1.1.0] - Ideas
- Advanced skills for specific academic disciplines
- Integration guides for popular tools (Zotero, Obsidian)
- Video tutorials or interactive examples
- Community-contributed examples

---

**Framework:** Based on Steven Pinker's "The Sense of Style" (2014)
**Maintainer:** Sau-Chin Chen (pmsp96@gmail.com)
**Repository:** https://github.com/SCgeeker/P-SCO
