# P-CSO Writing Workflow Guide

**P-CSO**: Pinker's Cognitive Style Optimization
**Framework**: Steven Pinker's "The Sense of Style" (Chapters 4 & 5)
**System**: writing-manager agent + P-CSO skills

---

## Quick Start

### For Drafting from Notes
```
1. Invoke writing-manager agent (or use /p-cso-workflow skill directly)
2. Provide your Obsidian notes or research materials
3. Receive organized scaffold
4. Rewrite in your own words
5. Apply P-CSO optimization
```

### For Revising Existing Text
```
1. Invoke writing-manager agent (or choose specific skill)
2. Provide draft text
3. Agent diagnoses issues and recommends appropriate skill
4. Receive cognitively optimized revision
5. Polish with /english-editing
```

---

## Understanding the System

### Components

**1. writing-manager Agent** (Orchestrator)
- **Location**: `.claude/agents/writing-manager/agent.md`
- **Role**: Analyzes your needs and invokes appropriate skills
- **When to use**: Starting any writing project; unsure which skill to use
- **How to invoke**: Through Task tool or agent system

**2. P-CSO Skills** (Specialized Tools)
- **Full pipeline**: `/p-cso-workflow` - Complete notes → draft → optimization
- **Syntax only**: `/pinker-syntax` - Sentence-level clarity (Chapter 4)
- **Coherence only**: `/pinker-coherence` - Discourse flow (Chapter 5)
- **Quick feedback**: `/pinker-quick` - Fast iteration during drafting

**3. Supporting Skills**
- `/notes-to-manuscript` - Simple scaffolding without full optimization
- `/english-editing` - Grammar and article polish (final step)

---

## Workflow Decision Tree

```
START: "I need writing help"
│
├─ Have existing text to improve?
│  │
│  ├─ YES: Revision workflow
│  │  │
│  │  ├─ Need comprehensive optimization?
│  │  │  └─ Use: /p-cso-workflow (or writing-manager)
│  │  │
│  │  ├─ Sentences hard to parse?
│  │  │  └─ Use: /pinker-syntax
│  │  │
│  │  ├─ Flow between sentences unclear?
│  │  │  └─ Use: /pinker-coherence
│  │  │
│  │  ├─ Actively drafting, need quick feedback?
│  │  │  └─ Use: /pinker-quick
│  │  │
│  │  └─ Just need grammar/articles?
│  │     └─ Use: /english-editing
│  │
│  └─ NO: Drafting workflow
│     │
│     ├─ Complex project from notes?
│     │  └─ Use: /p-cso-workflow (includes drafting phase)
│     │
│     ├─ Simple scaffold needed?
│     │  └─ Use: /notes-to-manuscript
│     │
│     └─ Just need organization help?
│        └─ Use: writing-manager agent (won't invoke skill)
│
└─ Unsure?
   └─ Use: writing-manager agent (will analyze and recommend)
```

---

## Common Workflows

### Workflow A: Comprehensive (Notes → Publication)
**Best for**: Starting from scratch with research notes

```
Step 1: Organization & Drafting
  └─ Invoke /p-cso-workflow with your notes
  └─ Receive organized focal statements + scaffold
  └─ Rewrite scaffold in your own words (CRITICAL)

Step 2: Cognitive Optimization (automatic in /p-cso-workflow)
  └─ Syntax optimization (Chapter 4: 6 rules)
  └─ Coherence optimization (Chapter 5: 7 principles)
  └─ Receive diagnostic report explaining changes

Step 3: Grammar Polish
  └─ Invoke /english-editing
  └─ Fix articles, grammar, terminology

Step 4: External
  └─ Add citations (Zotero, etc.)
  └─ Format to journal requirements
```

**Time estimate**: 2-4 hours for a full manuscript section

---

### Workflow B: Iterative Drafting
**Best for**: Active writing with real-time feedback

```
Write paragraph 1 (in your own words)
  └─ Invoke /pinker-quick
  └─ Apply quick fixes
  └─ Continue

Write paragraph 2
  └─ Invoke /pinker-quick
  └─ Apply quick fixes
  └─ Continue

[Complete section]

Full revision pass
  └─ Invoke /p-cso-workflow (or /pinker-syntax + /pinker-coherence)
  └─ Review comprehensive optimization
  └─ Invoke /english-editing
```

**Time estimate**: 30-60 min per section

---

### Workflow C: Modular Revision
**Best for**: Targeted improvement of specific issues

```
Diagnosis phase
  └─ Invoke writing-manager agent
  └─ Share problematic text
  └─ Agent identifies issue type

Targeted fix
  ├─ Syntax issues → /pinker-syntax
  ├─ Coherence issues → /pinker-coherence
  ├─ Both → /p-cso-workflow
  └─ Grammar only → /english-editing

Iterate as needed
```

**Time estimate**: 15-30 min per issue type

---

### Workflow D: Minimal (Quick Cleanup)
**Best for**: Time-constrained or already well-written text

```
Step 1: /pinker-quick (catch major issues)
Step 2: /english-editing (grammar polish)
Step 3: Submit
```

**Time estimate**: 15-30 min total

---

## Using writing-manager Agent

### When to Engage the Agent

✅ **Start conversation with writing-manager when**:
- Beginning a new manuscript
- Unsure which skill to use
- Need strategic advice about writing approach
- Want help diagnosing writing problems
- Working on complex multi-section document

### How to Engage

**Option 1: Let agent orchestrate**
```
User: "I need to write a Discussion section from my notes in [location]"
Agent: [Analyzes notes, recommends /p-cso-workflow, invokes skill, provides results]
```

**Option 2: Request specific help**
```
User: "This paragraph feels unclear but I don't know why"
Agent: [Diagnoses issue, explains cognitive problem, recommends /pinker-coherence]
```

**Option 3: Ask for workflow planning**
```
User: "What's the best approach for drafting from my knowledge vault?"
Agent: [Assesses vault structure, project status, recommends workflow]
```

### What Agent Provides That Skills Don't

- **Strategic guidance**: Which approach fits your situation?
- **Diagnosis**: What's causing writing problems?
- **Context awareness**: Adapts to your project status
- **Workflow orchestration**: Invokes multiple skills in sequence
- **Explanation**: Why this skill/approach is appropriate

---

## Obsidian Vault Integration

### How P-CSO Works with Obsidian

**The system understands**:
- Internal links: `[[Other Note]]`, `[[Note|alias]]`
- Frontmatter: YAML metadata (reads project status)
- Tags: `#draft`, `#needs-revision`, `#complete`
- Block references: `[[note#^block-id]]`
- Embedded content: `![[image.png]]`

**Workflow with Obsidian**:
1. Keep notes in Obsidian vault as markdown files
2. Invoke writing-manager or skills, provide note file paths or paste content
3. System preserves internal links and structure
4. Refined text can go back into vault or separate manuscript file

**Example Obsidian frontmatter**:
```yaml
---
status: drafting
project: Classifier Mental Simulation
section: Discussion
last_revision: 2025-10-26
---
```

Agent reads `status: drafting` → Recommends iterative workflow with `/pinker-quick`

---

## Adapting to Project Status

The writing-manager agent adapts workflow based on project phase:

### Planning Phase
**Indicators**: `status: planning`, `#plan` tag, files in `0_plan/`
**Agent focus**:
- Organization and structure
- Focal statement development
- Scaffold creation (not full revision)
**Recommended skills**: `/notes-to-manuscript`, light use of `/pinker-quick`

### Drafting Phase
**Indicators**: `status: drafting`, `#draft` tag
**Agent focus**:
- Section-by-section development
- Quick iterative feedback
- Balance creation with light cleanup
**Recommended skills**: `/pinker-quick` during writing, `/pinker-syntax` after sections complete

### Revision Phase
**Indicators**: `status: revising`, `#needs-revision` tag
**Agent focus**:
- Comprehensive optimization
- Syntax and coherence cleanup
- Full P-CSO application
**Recommended skills**: `/p-cso-workflow`, modular `/pinker-syntax` + `/pinker-coherence`

### Finalization Phase
**Indicators**: `status: finalizing`, `#ready-for-submission` tag
**Agent focus**:
- Grammar and article polish
- Technical correctness
- Minimal content changes
**Recommended skills**: `/english-editing` only

---

## Understanding P-CSO Principles

### Chapter 4: Syntax Optimization (6 Rules)

**What it fixes**: Sentence-level parsing difficulty

| Rule | Problem | Fix | Example |
|------|---------|-----|---------|
| 1. Memory load | Complex phrases at start | Move to sentence end | "We tested..." not "The hypothesis...was tested" |
| 2. Parsing collapse | Nested clauses | Break into simple sentences | Avoid "The X who did Y that Z designed..." |
| 3. Info density | Verbal bloat | Cut needless words | "decide" not "make a decision" |
| 4. Expectation order | New info first | Put known info first | "Results are explained by..." |
| 5. Ambiguity | Garden paths | Add markers, reorder | Restore "that", "which" if needed |
| 6. Consistency | Agreement errors | Fix parallelism | "both X and Y" with matching structure |

**Use `/pinker-syntax` for these issues**

---

### Chapter 5: Coherence Optimization (7 Principles)

**What it fixes**: Discourse-level flow and logic

| Principle | Problem | Fix | Example |
|-----------|---------|-----|---------|
| 1. Topic/Point | Buried lede | State topic & point early | Open with clear main claim |
| 2. Info flow | Broken topic arcs | Maintain consistent topics | Each sentence connects to prior |
| 3. Entity tracking | Confusing references | Use definite articles, avoid synonyms | "a task" → "the task" (not "the paradigm") |
| 4. Logic | Implicit relationships | Add connectives | "Consequently," "However," etc. |
| 5. Comparison | Non-parallel structure | Force parallel syntax | "X increased Y" / "Z increased Y" |
| 6. Abstract reference | Repetition | Nominalize events (2nd mention) | "verified" → "this verification" |
| 7. Metadiscourse | Author-focused text | Cut "I will discuss" phrases | Just discuss directly |

**Use `/pinker-coherence` for these issues**

---

## Output Interpretation

### Reading Diagnostic Reports

All P-CSO skills provide diagnostic explanations:

```markdown
### Issue 1: [Specific Problem]
- **Cognitive burden**: What made this hard for readers
- **Pinker principle**: Which rule/principle was violated
- **Fix applied**: What changed
- **Cognitive gain**: How this helps readers
```

**How to use diagnostics**:
1. **Learn patterns**: Notice recurring issues in your writing
2. **Apply to future**: Use principles when drafting new text
3. **Customize**: Tell agent about your common problems for targeted help

### Acting on Recommendations

**When skill suggests change**:
1. ✅ Review for content accuracy (did meaning change?)
2. ✅ Adjust to your voice if needed
3. ✅ Understand the cognitive rationale
4. ✅ Apply same principle to similar passages

**Don't**:
- ❌ Accept all changes blindly
- ❌ Ignore explanations (you'll repeat mistakes)
- ❌ Fight cognitive principles for style preferences (clarity > elegance)

---

## Customization

### Adapting to Your Needs

**You can customize**:
- Agent prompt (edit `.claude/agents/writing-manager/agent.md`)
- Skill prompts (edit `.claude/skills/[skill-name]/skill.md`)
- Add domain-specific rules
- Adjust diagnostic detail level

**Example customizations**:
- Add field-specific terminology to `/english-editing`
- Include journal-specific style rules
- Adjust verbosity of diagnostic output
- Add examples from your domain

### Providing Feedback to Agent

During writing session:
```
User: "The suggested change in sentence 3 altered my meaning. I meant X, not Y."
Agent: "Thanks for clarifying. Let me revise to preserve your intended meaning while still reducing cognitive load."
```

This helps agent learn your preferences for the session.

---

## Troubleshooting

### "The revision changed my meaning"
**Solution**:
- Tell agent: "This changed my meaning. I need to preserve [specific aspect]."
- Agent will re-optimize within that constraint
- Review diagnostic to understand cognitive principle, then manually apply it

### "Too many changes at once"
**Solution**:
- Use modular skills instead of `/p-cso-workflow`
- Try `/pinker-syntax` first, then `/pinker-coherence` separately
- Or use `/pinker-quick` for gentler iteration

### "I don't understand why a change was made"
**Solution**:
- Review diagnostic explanations
- Ask agent: "Explain the cognitive burden in [sentence] more clearly"
- Agent can provide examples and analogies

### "Diagnostics are too technical"
**Solution**:
- Ask agent: "Explain this in simpler terms"
- Or: "Give me practical examples instead of theory"

### "Agent keeps recommending wrong skill"
**Solution**:
- Be explicit: "Use /pinker-syntax only" or "Skip drafting, just optimize"
- Provide project status: "I'm in final revision phase"
- Update Obsidian frontmatter if agent reads from there

---

## Best Practices

### Do's ✅

1. **Rewrite scaffolds in your own words** (academic integrity)
2. **Review all changes for accuracy** (you're the content expert)
3. **Learn from diagnostics** (understand cognitive principles)
4. **Use skills sequentially** (draft → P-CSO → grammar)
5. **Iterate** (use `/pinker-quick` during writing for better first drafts)
6. **Preserve technical terminology** (don't sacrifice precision for simplicity)

### Don'ts ❌

1. **Don't copy AI text directly** (violates academic integrity)
2. **Don't ignore explanations** (you'll repeat issues)
3. **Don't over-optimize** (diminishing returns; sometimes good enough is enough)
4. **Don't fight all suggestions** (cognitive principles are evidence-based)
5. **Don't skip manual rewriting** (if using scaffolding skills)

---

## Integration with External Tools

### Before P-CSO
- **Literature management**: Zotero, Mendeley (gather sources)
- **Note-taking**: Obsidian, Notion (organize ideas)
- **Outlining**: Mind maps, outlines (structure arguments)

### During P-CSO
- **Drafting**: P-CSO skills (organize, draft, optimize)
- **Iteration**: `/pinker-quick` (real-time feedback)

### After P-CSO
- **Citation formatting**: Zotero, Citation Machine
- **Reference checking**: Grammarly, ProWritingAid (supplementary)
- **Journal formatting**: LaTeX, Word templates
- **Submission**: Journal systems

**P-CSO position**: Core cognitive optimization; external tools handle citations and formatting

---

## Version Control & Collaboration

### Tracking Revisions

**Recommended approach**:
1. Keep drafts in version control (Git)
2. Name files: `manuscript_v1.md`, `manuscript_v2_post-pcso.md`
3. Commit after each major revision pass
4. Tag key milestones: `v1-draft`, `v2-optimized`, `v3-final`

### Collaborating

**If co-authors use Claude Code**:
- Share `.claude/` directory (all have same skills/agent)
- Consistent optimization approach across authors
- Diagnostic reports help justify changes

**If co-authors don't use Claude Code**:
- Run P-CSO on your sections only
- Provide "before/after" for co-author review
- Explain cognitive rationale for major changes
- They can manually apply principles to their sections

---

## Quick Reference Card

| Task | Use This | Time |
|------|----------|------|
| Draft from notes | `/p-cso-workflow` | 2-4h |
| Quick draft feedback | `/pinker-quick` | 5-10min |
| Fix complex sentences | `/pinker-syntax` | 30min |
| Fix paragraph flow | `/pinker-coherence` | 30min |
| Final grammar polish | `/english-editing` | 15-30min |
| Strategic planning | writing-manager agent | 10min |
| Full comprehensive | `/p-cso-workflow` + `/english-editing` | 3-5h |

---

## Further Learning

### Understanding Pinker's Framework

**Read**: Steven Pinker, "The Sense of Style"
- Chapter 4: Syntax and tree-thinking
- Chapter 5: Coherence arcs and information flow

**Key insight**: Good writing reduces cognitive burden for readers

### Practicing P-CSO Principles

1. Run `/p-cso-workflow` on your text
2. Study the diagnostics
3. Identify your recurring issues (e.g., "I always bury the lede")
4. Apply that principle proactively in next draft
5. Use `/pinker-quick` to verify

**Goal**: Internalize principles so first drafts need less revision

---

**Document Version**: 1.0
**Last Updated**: 2025-10-26
**System**: writing-manager agent + P-CSO skills
**Framework**: Pinker's "The Sense of Style"
