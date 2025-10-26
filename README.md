# P-CSO Writing System

**Version**: 1.0
**Created**: 2025-10-26
**Framework**: Steven Pinker's Cognitive Style Optimization (P-CSO)

---

## What's Here

This directory contains your custom writing assistance system for academic writing:

### Agents
- **writing-manager** - Orchestrates drafting and revision workflows
  - Understands Obsidian vault integration
  - Detects project status and recommends appropriate skills
  - Handles both note-to-draft composition and cognitive revision

### Skills

**P-CSO Revision Skills** (Pinker framework):
- **p-cso-workflow** - Complete pipeline: notes → draft → syntax → coherence
- **pinker-syntax** - Chapter 4 optimization (6 rules for sentence clarity)
- **pinker-coherence** - Chapter 5 optimization (7 principles for discourse flow)
- **pinker-quick** - Top 3 rules for rapid iteration during active drafting

**Supporting Skills**:
- **notes-to-manuscript** - Ethical scaffolding from research notes
- **english-editing** - Grammar, articles, and copyediting polish

### Documentation
- **p-cso-writing-workflow.md** - Complete usage guide
- **cross-device-setup.md** - Sync this system across devices
- **skills-vs-agents-guide.md** - When to update skills vs. use agents

---

## Quick Start

### For Drafting
```
Invoke writing-manager agent or use:
  /p-cso-workflow    (full pipeline)
  /notes-to-manuscript (simple scaffold)
```

### For Revision
```
Use writing-manager agent to diagnose, or:
  /p-cso-workflow    (comprehensive)
  /pinker-syntax     (sentence-level only)
  /pinker-coherence  (discourse-level only)
  /pinker-quick      (rapid feedback)
```

### For Final Polish
```
  /english-editing   (grammar, articles, formatting)
```

---

## System Architecture

```
User request
    ↓
writing-manager agent (analyzes need)
    ↓
Invokes appropriate skill(s)
    ↓
Skill provides optimized text + diagnostics
    ↓
User reviews and applies changes
```

---

## Files Inventory

### Agents (1)
- `agents/writing-manager/agent.md` (5,800 words)

### Skills (6)
- `skills/p-cso-workflow/skill.md` (4,200 words)
- `skills/pinker-syntax/skill.md` (2,400 words)
- `skills/pinker-coherence/skill.md` (2,600 words)
- `skills/pinker-quick/skill.md` (1,500 words)
- `skills/notes-to-manuscript/skill.md` (existing, updated)
- `skills/english-editing/skill.md` (existing, updated)

### Documentation (3)
- `docs/p-cso-writing-workflow.md` (5,000 words)
- `docs/cross-device-setup.md` (3,500 words)
- `docs/skills-vs-agents-guide.md` (existing)

**Total**: ~25,000 words of prompts and documentation

---

## Customization

All files are plain markdown and can be edited:

**To customize a skill**:
1. Open `.claude/skills/[skill-name]/skill.md`
2. Edit instructions, examples, or rules
3. Save
4. Restart Claude Code (if needed)
5. Test with sample text

**To customize the agent**:
1. Open `.claude/agents/writing-manager/agent.md`
2. Modify workflow logic, decision trees, or interaction style
3. Save and test

**Version control**: Consider committing to Git after changes

---

## Portability

This entire `.claude/` directory is:
- ✅ Portable across devices (Git, cloud sync, manual copy)
- ✅ Version controllable (commit to Git)
- ✅ Shareable with collaborators
- ✅ Independent of Claude Code installation

See `docs/cross-device-setup.md` for sync instructions.

---

## Learning Resources

**To understand P-CSO framework**:
- Read: Steven Pinker, "The Sense of Style" (Chapters 4 & 5)
- Review: `docs/p-cso-writing-workflow.md` (this implementation)

**To use effectively**:
- Start with: `docs/p-cso-writing-workflow.md`
- Consult: `docs/skills-vs-agents-guide.md` (when to update what)
- Reference: Your P-CSO template (`0_plan/P-CSO guide/Agent Template.md`)

---

## Maintenance

**Monthly**:
- Review skills for accuracy
- Update with new patterns from your writing
- Add domain-specific examples

**When journal requirements change**:
- Update `/english-editing` with new style rules
- Commit changes to Git

**When you discover recurring issues**:
- Add to appropriate skill as new rule/example
- Or customize agent to flag that issue proactively

---

## Support

**For Claude Code issues**: https://github.com/anthropics/claude-code/issues
**For P-CSO questions**: Review Pinker's "The Sense of Style"
**For customization help**: Edit skill files; test iteratively

---

**System Status**: ✅ Fully operational
**Next Step**: Read `docs/p-cso-writing-workflow.md` and test with sample text
