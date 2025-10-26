# Skills vs. Agents: A Maintenance Decision Guide

## Quick Reference

**Skills** = Specialized task templates you create and maintain
**Agents** = System-provided assistants with evolving capabilities
**You control**: Skills (direct file editing)
**Anthropic controls**: Agents (request changes via feedback)

---

## 1. Understanding Skills vs. Agents

### Skills: Your Custom Tools

**What they are:**
- Task-specific prompt templates stored as files (`.md` format)
- Invoked with `/skill-name` or through the Skill tool
- Examples: `/english-editing`, `/notes-to-manuscript`

**Characteristics:**
- **You own them**: Direct file access and editing control
- **Static until you change them**: Behavior remains consistent
- **Task-focused**: Designed for specific, repeatable workflows
- **Local to your system**: Live in your `.claude/skills/` directory

**When to use:**
- Repetitive tasks with consistent patterns
- Domain-specific workflows (your research writing conventions)
- Tasks requiring precise, unchanging instructions
- Situations where you need exact control over the process

### Agents: System Assistants

**What they are:**
- Pre-built specialized assistants with broader capabilities
- Example: **writing-manager agent** (you're interacting with it now)
- Provided and maintained by Anthropic

**Characteristics:**
- **System-managed**: You don't edit the underlying prompts
- **Adaptive**: Can handle varied, complex situations
- **Conversational**: Engage in multi-turn problem-solving
- **Evolving**: Anthropic updates them based on user feedback

**When to use:**
- Complex problems requiring analysis and decision-making
- Situations needing strategic guidance or planning
- Tasks that vary significantly each time
- When you need expert consultation rather than execution

---

## 2. When to UPDATE a Skill

### Triggers for Skill Updates

Update your skill file when:

#### ✅ **Process Changes**
- Your writing conventions evolve
- Journal submission requirements change
- You adopt new formatting standards
- Your preferred editing checklist expands

**Example:** You switch from APA 6 to APA 7 citation format
→ Edit `/english-editing` skill to reflect new rules

#### ✅ **Output Quality Issues**
- The skill consistently misses certain problems
- You find yourself manually correcting the same issues
- The instructions are ambiguous or incomplete

**Example:** `/english-editing` doesn't catch passive voice in methods sections
→ Add explicit passive voice detection to the skill instructions

#### ✅ **Scope Expansion**
- You want the skill to handle additional tasks
- New capabilities become relevant to the workflow
- You need to add context-specific requirements

**Example:** Add discipline-specific terminology checking to `/english-editing`
→ Include psychology jargon guidelines in the skill file

#### ✅ **Efficiency Improvements**
- You discover a better workflow structure
- You want to add templates or examples
- You need to streamline the output format

**Example:** `/notes-to-manuscript` produces overly detailed drafts
→ Adjust skill to create higher-level scaffolds

### How Skills Evolve Over Time

**Phase 1 - Initial Creation:**
- Basic instructions covering core use cases
- General guidelines and expectations

**Phase 2 - Refinement (weeks 1-4):**
- Add edge cases you discover
- Incorporate examples of good outputs
- Clarify ambiguous instructions

**Phase 3 - Maturity (ongoing):**
- Fine-tune based on changing needs
- Add specialized sub-workflows
- Integrate with other skills

### Skill Update Workflow

```
1. Identify the issue or desired change
2. Locate the skill file: .claude/skills/skill-name/skill.md
3. Edit the markdown file directly
4. Test the updated skill on a representative task
5. Iterate if needed
```

---

## 3. When to Engage with Agents

### You CANNOT directly update agents
Agents are system-managed. Instead, you can:

1. **Request assistance** (use the agent for guidance)
2. **Provide feedback** (report issues to Anthropic)
3. **Adapt your approach** (change how you interact with the agent)

### When to Work WITH an Agent

Use an agent when you need:

#### 🤝 **Strategic Planning**
- "How should I structure my literature review?"
- "What writing improvement plan should I follow?"
- "Help me diagnose why my arguments feel weak"

**Action:** Start a conversation with the writing-manager agent

#### 🤝 **Diagnostic Analysis**
- "Why is my writing unclear?"
- "What's causing coherence problems in this section?"
- "Analyze my writing patterns across multiple papers"

**Action:** Engage the agent with specific samples or questions

#### 🤝 **Skill Development Guidance**
- "What should I focus on to improve my academic writing?"
- "How do I develop better argumentation skills?"
- "Create a 6-week writing improvement program"

**Action:** Request a structured development plan from the agent

### When to Report Agent Issues

Report to Anthropic when:

#### ⚠️ **Systematic Problems**
- Agent consistently misunderstands a task type
- Responses are frequently off-target
- Agent lacks necessary domain knowledge

**Action:** Use Claude's feedback mechanism to report specific issues

#### ⚠️ **Missing Capabilities**
- Agent can't perform tasks it seems designed for
- Workflow gaps that skills shouldn't handle

**Action:** Submit feature requests through official channels

#### ⚠️ **Outdated Knowledge**
- Agent provides advice inconsistent with current best practices
- References outdated standards or methods

**Action:** Note the discrepancy in feedback to Anthropic

---

## 4. Decision Matrix

| Scenario | Update Skill | Use/Request Agent Change |
|----------|-------------|-------------------------|
| **Adding APA 7 citation checking** | ✅ Update `/english-editing` skill | ❌ |
| **Need help planning lit review structure** | ❌ | ✅ Ask writing-manager |
| **Editing patterns changed (new journal)** | ✅ Update `/english-editing` skill | ❌ |
| **Want argumentation coaching** | ❌ | ✅ Engage writing-manager |
| **Output format needs tweaking** | ✅ Update relevant skill | ❌ |
| **Need diagnosis of writing problems** | ❌ | ✅ Consult writing-manager |
| **Manuscript scaffold too detailed** | ✅ Update `/notes-to-manuscript` | ❌ |
| **Agent gives bad writing advice** | ❌ | ✅ Report to Anthropic |
| **Adding domain terminology checks** | ✅ Update skill | ❌ |
| **Creating new writing workflow** | ✅ Create new skill | 🤝 First consult agent for design |

### Decision Tree

```
START: "I have a writing-related need"
  |
  ├─→ Is it a REPEATABLE, SPECIFIC TASK?
  |     └─→ YES: Does a skill already exist?
  |           ├─→ YES: Update existing skill
  |           └─→ NO: Create new skill (consult agent for design)
  |
  ├─→ Do I need STRATEGIC GUIDANCE or ANALYSIS?
  |     └─→ YES: Engage writing-manager agent
  |
  ├─→ Is an AGENT behaving incorrectly?
  |     └─→ YES: Report to Anthropic via feedback
  |
  └─→ Am I UNSURE what I need?
        └─→ YES: Start conversation with writing-manager agent
```

---

## 5. Maintenance Workflow

### For Skills (User Responsibility)

**Regular Maintenance:**
```
Monthly Review:
1. Test each skill on current work
2. Note any gaps or errors
3. Batch update skills as needed
4. Document changes in skill file comments

Triggered Updates:
1. When journal requirements change → immediate update
2. When skill produces wrong output → fix within 24 hours
3. When workflow changes → update before next use
```

**Version Control:**
Consider adding version notes to skill files:
```markdown
<!--
Version: 1.2
Last updated: 2025-10-23
Changes: Added APA 7 citation format, passive voice detection
-->
```

### For Agents (Anthropic Responsibility)

**Your Role:**
- **Observe**: Note patterns in agent behavior
- **Document**: Keep examples of issues
- **Report**: Use official feedback channels
- **Adapt**: Adjust how you interact while waiting for updates

**Not Your Role:**
- Trying to "fix" agents through prompting tricks
- Working around agent limitations indefinitely
- Accepting subpar performance without feedback

---

## 6. Practical Examples with Your Skills

### Scenario A: "I want to add APA 7 citation checking"

**Decision:** ✅ **Update `/english-editing` skill**

**Why:**
- Citation format checking is a repeatable, rule-based task
- You need consistent application across all editing sessions
- The rules are static and well-defined

**How:**
1. Open `.claude/skills/english-editing/skill.md`
2. Add section:
```markdown
## Citation Format Verification (APA 7)

Check all citations against APA 7 standards:
- In-text: (Author, Year) or Author (Year)
- Multiple authors: (Smith & Jones, 2023) for 2 authors
- 3+ authors: (Smith et al., 2023)
- References: Hanging indent, alphabetical order
- DOIs formatted as: https://doi.org/10.xxxx
- Flag any deviations for manual review
```
3. Test on a manuscript section
4. Refine as needed

---

### Scenario B: "I need help planning a literature review"

**Decision:** ✅ **Use writing-manager agent**

**Why:**
- Literature review planning requires strategic thinking
- Structure depends on specific research questions and field
- You need adaptive guidance, not a template

**How:**
1. Start conversation with writing-manager agent
2. Provide context: research topic, scope, goals
3. Request: "Create a structured plan for my literature review on [topic]"
4. Engage in discussion to refine the plan

**Consider creating a skill later:**
- After agent helps you develop YOUR preferred lit review structure
- Convert that approach into a reusable template skill
- Skill would then scaffold future lit reviews using your established pattern

---

### Scenario C: "The editing patterns have changed"

**Subcases:**

#### C1: **Your journal switched style guides**
**Decision:** ✅ **Update `/english-editing` skill**
- Modify skill file to reflect new style requirements
- Update examples and checking rules
- Test thoroughly

#### C2: **You discovered your writing has systematic issues**
**Decision:** 🤝 **First consult writing-manager agent, then update skill**
- Ask agent: "I notice I overuse passive voice in methods. How should I address this?"
- Agent provides diagnostic analysis and strategies
- Based on agent guidance, update `/english-editing` to specifically flag this pattern
- Skill becomes a personalized tool targeting YOUR weaknesses

#### C3: **Your research focus shifted domains**
**Decision:** ✅ **Update `/english-editing` skill** + 🤝 **Consult agent**
- Ask agent: "What are key writing conventions in [new domain]?"
- Use agent insights to update skill with domain-specific guidelines
- Add terminology, citation practices, argumentation styles specific to new field

---

### Scenario D: "The manuscript scaffold is too detailed"

**Decision:** ✅ **Update `/notes-to-manuscript` skill**

**Current problem example:**
```
Your notes: "Classifier effects on mental simulation"
Skill output: 3000-word detailed draft with full paragraphs
What you want: 500-word outline with section headers and bullet points
```

**Fix:**
1. Open skill file
2. Modify output instructions:
```markdown
## Output Format

Create a HIGH-LEVEL SCAFFOLD only:
- Section headers (Introduction, Methods, Results, Discussion)
- 2-3 bullet points per section indicating key content
- Suggested paragraph topics, NOT full paragraphs
- Total length: 300-500 words maximum
- Prioritize structure over content
```
3. Test on your research notes
4. Adjust detail level until optimal

---

### Scenario E: "I want both skills to work together"

**Your goal:** Process notes → scaffold → polished draft

**Approach:**
1. Use `/notes-to-manuscript` to create scaffold
2. Flesh out the scaffold manually
3. Use `/english-editing` to polish the draft

**Consider creating a meta-skill:**
```markdown
# research-workflow.md

## Purpose
Orchestrate the complete notes-to-paper workflow

## Steps
1. Invoke `/notes-to-manuscript` on research notes
2. Guide user to develop scaffold sections
3. Invoke `/english-editing` on completed draft
4. Compile final manuscript

## Output
Publication-ready manuscript following full workflow
```

**When to do this:**
- After you've used both skills together multiple times
- When the workflow becomes standardized
- If you want automated handoffs between steps

---

## Summary: The Fundamental Distinction

### Skills = Tools You Build
- **Control:** Direct file editing
- **Purpose:** Repeatable, specific tasks
- **Maintenance:** Your responsibility
- **Updates:** Immediate, as needed
- **Evolution:** Reflects your changing needs

### Agents = Experts You Consult
- **Control:** Conversation and feedback only
- **Purpose:** Strategic guidance, complex analysis
- **Maintenance:** Anthropic's responsibility
- **Updates:** Periodic, system-wide
- **Evolution:** Based on aggregate user feedback

### The Golden Rule
**"Can I write exact instructions for this task?"**
- **YES** → Create or update a skill
- **NO** → Engage an agent

---

## Recommended Next Steps

1. **Create a skills maintenance schedule:**
   - Monthly review of existing skills
   - Update after any journal submission requirements change
   - Revise when you notice repeated manual corrections

2. **Document your interactions:**
   - Keep notes on when skills vs. agents are most helpful
   - Track issues to identify update needs
   - Build your personal decision patterns

3. **Start simple, iterate:**
   - Don't over-engineer skills initially
   - Let natural usage reveal what needs updating
   - Consult agents when designing new skills

4. **Provide feedback:**
   - Report agent issues promptly
   - Share successes too (helps Anthropic know what works)
   - Contribute to the community knowledge base

---

*This guide reflects the Claude Code system as of October 2025. Specific features and capabilities may evolve over time.*
