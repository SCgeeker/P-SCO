# Cross-Device Setup Guide: P-CSO Writing System

**Goal**: Sync your writing-manager agent and P-CSO skills across all devices
**Benefit**: Consistent writing assistance everywhere you work

---

## What Gets Synced

Your custom writing system lives entirely in the `.claude/` directory:

```
.claude/
├── agents/
│   └── writing-manager/
│       └── agent.md              # Your custom writing orchestrator
├── skills/
│   ├── p-cso-workflow/
│   │   └── skill.md              # Full pipeline
│   ├── pinker-syntax/
│   │   └── skill.md              # Syntax optimization
│   ├── pinker-coherence/
│   │   └── skill.md              # Coherence optimization
│   ├── pinker-quick/
│   │   └── skill.md              # Quick iteration
│   ├── english-editing/
│   │   └── skill.md              # Grammar polish
│   └── notes-to-manuscript/
│       └── skill.md              # Scaffolding
└── docs/
    ├── p-cso-writing-workflow.md # Workflow guide
    ├── cross-device-setup.md     # This file
    └── skills-vs-agents-guide.md # Skills/agents reference
```

**Size**: ~500 KB total (very lightweight)

---

## Sync Methods

### Method 1: Git Version Control (Recommended)

**Best for**: Developers, researchers familiar with Git
**Benefits**: Version history, easy rollback, collaboration-ready
**Complexity**: Moderate (requires Git knowledge)

#### Setup Instructions

**Step 1: Initialize Repository**

```bash
# Navigate to your project root (or .claude directory)
cd "D:/core/Research/projects/Mental_Simulation/Classifier Alter"

# Initialize Git (if not already a repo)
git init

# Create .gitignore (optional: ignore local-only files)
echo "*.log" > .gitignore
echo ".DS_Store" >> .gitignore

# Stage .claude directory
git add .claude/

# First commit
git commit -m "Add P-CSO writing system: agent + skills"
```

**Step 2: Create Remote Repository**

**Option A: Private GitHub repo**
1. Go to github.com → New repository
2. Name it (e.g., `mental-simulation-research` or `claude-writing-config`)
3. Keep it **Private** (contains your custom prompts)
4. Copy the remote URL

```bash
# Add remote
git remote add origin https://github.com/YOUR_USERNAME/REPO_NAME.git

# Push to remote
git push -u origin main
```

**Option B: GitLab, Bitbucket, or private Git server**
- Same process, different platform
- Ensure repo is private

**Step 3: Clone on Other Devices**

On your second device:

```bash
# Navigate to where you want the project
cd ~/Documents/Research/  # (or equivalent Windows/Mac path)

# Clone the repository
git clone https://github.com/YOUR_USERNAME/REPO_NAME.git

# Navigate into the project
cd REPO_NAME

# Verify .claude directory is present
ls .claude
```

**Step 4: Sync Workflow**

**On Device A (after making changes)**:
```bash
git add .claude/
git commit -m "Updated pinker-quick skill for faster iteration"
git push
```

**On Device B (to get changes)**:
```bash
git pull
```

**Recommended routine**: Pull before writing session, push after any customizations

---

#### Git Workflow for Skill Updates

**Scenario**: You updated `/pinker-syntax` skill on your laptop

```bash
# On laptop
git status                    # See what changed
git diff .claude/skills/pinker-syntax/skill.md  # Review changes
git add .claude/skills/pinker-syntax/skill.md
git commit -m "Pinker-syntax: Added domain-specific example for psychology papers"
git push

# On desktop (later)
git pull                      # Receive update
# Skill now identical on both devices
```

---

### Method 2: Cloud File Sync (Easiest)

**Best for**: Non-developers, those wanting automatic sync
**Benefits**: Zero manual steps, continuous sync
**Complexity**: Low
**Services**: Dropbox, Google Drive, OneDrive, iCloud Drive, Syncthing

#### Setup Instructions

**Step 1: Choose Location**

Place your project in a synced folder:

**Option A: Sync entire project**
```
Dropbox/Research/Mental_Simulation/Classifier Alter/
  ├── .claude/         # ← This gets synced
  ├── 0_plan/
  ├── 1_method/
  └── [other project folders]
```

**Option B: Sync only .claude directory**
```
Dropbox/Claude_Configs/
  ├── Classifier_Alter_claude/   # Copy of .claude directory
  │   ├── agents/
  │   ├── skills/
  │   └── docs/
  └── [other project configs]
```

Then symlink on each device:
```bash
# Linux/Mac
ln -s ~/Dropbox/Claude_Configs/Classifier_Alter_claude ~/Projects/Classifier\ Alter/.claude

# Windows (Command Prompt as Admin)
mklink /D "D:\Projects\Classifier Alter\.claude" "C:\Users\YOU\Dropbox\Claude_Configs\Classifier_Alter_claude"
```

**Step 2: Verify Sync**

1. Make small change on Device A (e.g., add comment to agent.md)
2. Wait for sync (check Dropbox icon for completion)
3. Open file on Device B
4. Verify change appears

**Step 3: Avoid Conflicts**

**Best practice**: Don't edit same skill/agent on multiple devices simultaneously

**If conflict occurs**:
- Dropbox/GDrive creates "conflicted copy"
- Compare versions manually
- Keep desired version, delete conflict

---

#### Recommended Services

| Service | Pros | Cons | Free Tier |
|---------|------|------|-----------|
| **Syncthing** | Open source, no cloud, peer-to-peer | Requires setup | Unlimited |
| **Dropbox** | Reliable, fast sync, conflict handling | Limited free space (2GB) | 2 GB |
| **Google Drive** | Large free tier, integrated with workspace | Slower sync | 15 GB |
| **OneDrive** | Built into Windows, Office integration | Windows-centric | 5 GB |
| **iCloud Drive** | Best for Mac/iOS ecosystem | Apple-only | 5 GB |

**Recommendation**: Syncthing (if tech-savvy) or Dropbox (if want simplicity)

---

### Method 3: Manual Copy (Not Recommended)

**Best for**: Air-gapped systems, one-time transfer
**Benefits**: Works without internet
**Complexity**: Low, but tedious
**Risks**: Easy to forget, version drift

#### Instructions

**Step 1: Export .claude directory**

On Device A:
```bash
# Compress .claude directory
tar -czf claude_backup_2025-10-26.tar.gz .claude/

# Or use zip
zip -r claude_backup_2025-10-26.zip .claude/
```

**Step 2: Transfer**

- USB drive
- Email to yourself
- Secure file transfer (if air-gapped)

**Step 3: Import on Device B**

```bash
# Extract
tar -xzf claude_backup_2025-10-26.tar.gz

# Or
unzip claude_backup_2025-10-26.zip

# Move to project directory
mv .claude /path/to/project/
```

**Step 4: Repeat when changes made**

**Problem**: You'll forget. Use Git or cloud sync instead.

---

## Verification Checklist

After setting up sync on new device, verify:

**1. Agent exists**
```bash
cat .claude/agents/writing-manager/agent.md | head -5
```
Should show: `# Writing Manager Agent: Academic Writing with P-CSO Framework`

**2. Skills exist**
```bash
ls .claude/skills/
```
Should show:
- `english-editing/`
- `notes-to-manuscript/`
- `p-cso-workflow/`
- `pinker-coherence/`
- `pinker-quick/`
- `pinker-syntax/`

**3. Test invocation**

In Claude Code session:
```
User: "Use writing-manager agent"
Agent: [Should load with P-CSO capabilities]
```

Or test skill directly:
```
User: "/pinker-quick"
Skill: [Should load Pinker Quick skill prompt]
```

---

## Troubleshooting

### "Agent/skill not found on Device B"

**Cause**: Sync didn't complete or path is wrong

**Fix**:
1. Check sync service status (Dropbox icon, Git pull output)
2. Verify `.claude/` directory exists: `ls .claude`
3. Check permissions: `ls -la .claude`
4. If using symlink, verify link target: `ls -l .claude`

---

### "Changes not syncing between devices"

**Git method**:
- Forgot to `git push` on Device A?
- Forgot to `git pull` on Device B?
- Check: `git status` and `git log`

**Cloud sync method**:
- Check service is running (Dropbox, GDrive app)
- Check for conflicts (look for "conflicted copy" files)
- Check internet connection
- Try manual refresh (pause/resume sync)

---

### "Conflicting versions on two devices"

**Git method**:
```bash
# If merge conflict
git status                    # See conflicted files
git diff .claude/skills/...   # Review differences
# Manually resolve in text editor
git add .claude/skills/...
git commit -m "Resolved conflict in skill"
git push
```

**Cloud sync method**:
- Find "conflicted copy" files
- Open both versions side-by-side
- Manually merge desired changes
- Delete conflicted copy
- Keep merged version

---

### "Skill works on Device A but not Device B"

**Possible causes**:
1. File didn't sync (check file exists)
2. File synced but different Claude Code version (update Claude Code)
3. Path issues (Windows vs. Mac/Linux paths)

**Fix**:
1. Verify file content identical: `diff .claude/skills/X/skill.md` (on both devices)
2. Check Claude Code version: Should be same major version
3. Restart Claude Code to reload skills

---

## Security Considerations

### Sensitive Information

**Your `.claude/` directory contains**:
- Custom prompts and workflows
- Possibly domain-specific terminology
- Your writing patterns and preferences

**Should you keep it private?**

**Low risk**:
- Generic academic writing guidance
- Pinker principles (publicly available)
- Workflow documentation

**Medium risk**:
- Domain-specific customizations
- Proprietary research methods

**High risk**:
- If you hardcoded API keys (DON'T do this)
- If you embedded confidential data in examples

**Recommendation**: Use **private** Git repos or encrypted cloud storage

---

### Encryption Options

**Git method**:
- Use private GitHub/GitLab repos (encrypted in transit)
- For extra security: Encrypt repo with `git-crypt` or `git-secret`

**Cloud sync method**:
- Most services encrypt in transit and at rest
- For paranoia: Use Cryptomator or VeraCrypt to encrypt folder before syncing

**Syncthing**:
- Peer-to-peer (no cloud storage)
- Encrypted in transit

---

## Backup Strategy

**Even with sync, maintain backups**:

### Automated Backups

**Git method**: Remote repo IS your backup
- But also: Periodic export to archive
  ```bash
  git archive --format=zip HEAD .claude > claude_backup_$(date +%Y%m%d).zip
  ```

**Cloud sync method**: Cloud IS your backup
- But also: Periodic local snapshot
  ```bash
  cp -r .claude .claude_backup_$(date +%Y%m%d)
  ```

### Backup Schedule

**Recommended**:
- **Daily**: Handled by Git/cloud sync (automatic)
- **Weekly**: Manual verification (check sync status)
- **Monthly**: Archive snapshot (store separately)
- **Before major changes**: Manual backup (just in case)

---

## Multi-Project Setup

**If you work on multiple projects**, you have options:

### Option 1: Project-Specific Configs

Each project has its own `.claude/` with tailored skills:

```
Project_A/
  └── .claude/
      └── skills/
          └── p-cso-workflow/  # Customized for Project A

Project_B/
  └── .claude/
      └── skills/
          └── p-cso-workflow/  # Customized for Project B
```

**Sync approach**: Sync each project separately

**Pro**: Tailored to each project
**Con**: Redundancy; updates need to propagate to all

---

### Option 2: Shared Config Directory

Create central `.claude/` shared across projects:

```
~/Claude_Shared_Config/
  ├── agents/
  ├── skills/
  └── docs/

Project_A/   # Symlink to shared config
  └── .claude -> ~/Claude_Shared_Config

Project_B/   # Symlink to shared config
  └── .claude -> ~/Claude_Shared_Config
```

**Sync approach**: Sync `~/Claude_Shared_Config` once

**Pro**: Single source of truth; update once, applies everywhere
**Con**: Can't customize per project

---

### Option 3: Hybrid (Recommended)

Shared base + project-specific overrides:

```
~/Claude_Base/
  ├── agents/writing-manager/
  └── skills/
      ├── p-cso-workflow/
      ├── pinker-syntax/
      └── [core skills]

Project_A/.claude/
  ├── agents/   # Symlink to ~/Claude_Base/agents
  ├── skills/   # Symlink to ~/Claude_Base/skills
  └── docs/     # Project-specific docs

Project_B/.claude/
  └── skills/
      └── domain-specific-skill/  # Only in Project B
  # Falls back to ~/Claude_Base for others
```

**Pro**: Best of both worlds
**Con**: Requires understanding of symlinks and fallback behavior

---

## Collaboration with Co-Authors

### Sharing Your P-CSO System

**If co-author uses Claude Code**:

**Option 1: Share entire .claude directory**
1. Add them as collaborator on Git repo
2. They clone repo
3. Instant access to same skills/agent

**Option 2: Export specific skills**
1. Zip `.claude/skills/p-cso-workflow/`
2. Send to co-author
3. They place in their `.claude/skills/`

**If co-author doesn't use Claude Code**:
- Share `.claude/docs/p-cso-writing-workflow.md` as reference
- They can manually apply Pinker principles
- Or share optimized text with explanations

---

### Version Control for Collaboration

**Recommended Git workflow**:

```bash
# Co-author A makes improvement to skill
git checkout -b improve-pinker-syntax
# Edit skill
git add .claude/skills/pinker-syntax/skill.md
git commit -m "Added example for psychology domain"
git push origin improve-pinker-syntax

# Co-author B reviews
git fetch origin
git checkout improve-pinker-syntax
# Test the skill
git checkout main
git merge improve-pinker-syntax
git push
```

**Benefits**:
- Track who changed what
- Review before merging
- Rollback if issues

---

## Updating the System

### When to Update

**Update skills/agent when**:
- Anthropic releases Claude Code updates (may change behavior)
- You discover better prompting patterns
- Your writing needs evolve (new domain, journal)
- You identify recurring issues not caught by current rules

### How to Update

**Step 1: Edit locally**
```bash
# Edit skill file
nano .claude/skills/pinker-syntax/skill.md
# Make changes, save
```

**Step 2: Test**
```bash
# In Claude Code session
/pinker-syntax
# Verify updated behavior
```

**Step 3: Sync**

**Git**:
```bash
git add .claude/skills/pinker-syntax/skill.md
git commit -m "Pinker-syntax: Added rule for passive voice in methods sections"
git push
```

**Cloud sync**: Automatic (just save file)

**Step 4: Pull on other devices**
```bash
git pull  # (Git method)
# Or wait for cloud sync
```

---

### Version Tracking

**Add version metadata to skills**:

```markdown
---
**Skill Version**: 1.1
**Last Updated**: 2025-10-26
**Changes**: Added domain-specific examples
---
```

**Maintain changelog**:

Create `.claude/CHANGELOG.md`:
```markdown
# Changelog

## 2025-10-26
- Updated `pinker-syntax` v1.1: Added psychology examples
- Fixed `p-cso-workflow` diagnostic output format

## 2025-10-20
- Initial P-CSO system setup v1.0
```

---

## Migration Scenarios

### Scenario 1: New Laptop

**You**: Bought new laptop, need writing system

**Steps**:
1. Install Claude Code on new laptop
2. Clone Git repo (or connect to cloud sync)
3. Verify `.claude/` directory present
4. Test agent/skill invocation
5. Done (5 minutes)

---

### Scenario 2: Lab Computer (Shared)

**You**: Work on shared lab computer, want personal writing config

**Challenge**: Can't modify global config; others use same machine

**Solution**: Project-local `.claude/` directory
1. Create project directory: `~/my_research_project/`
2. Clone Git repo with `.claude/` inside project
3. Work in that project directory
4. `.claude/` only active when working in that folder
5. Other users unaffected

---

### Scenario 3: Air-Gapped System

**You**: Secure research environment, no internet

**Steps**:
1. On internet-connected device: `tar -czf claude_config.tar.gz .claude/`
2. Transfer via approved method (USB, secure portal)
3. On air-gapped system: `tar -xzf claude_config.tar.gz`
4. Updates: Repeat transfer process manually
5. Consider: Periodic exports from air-gapped → internet device for backup

---

## Quick Start Summary

**Fastest path to cross-device sync**:

### For Git Users (5 minutes)
```bash
cd your_project
git init
git add .claude
git commit -m "Add P-CSO writing system"
git remote add origin https://github.com/YOU/REPO.git
git push -u origin main

# On other device
git clone https://github.com/YOU/REPO.git
```

### For Non-Git Users (3 minutes)
1. Move project to Dropbox/GDrive folder
2. Wait for sync
3. Open project on other device
4. Verify `.claude/` present

---

## Help & Support

**If sync issues persist**:

1. **Check logs**:
   - Git: `git status`, `git log`
   - Dropbox: Settings → Network → View sync issues
   - Claude Code: Check for errors when invoking skills

2. **Manual verification**:
   ```bash
   # Verify file checksums match across devices
   md5sum .claude/agents/writing-manager/agent.md
   # Run on both devices; should match
   ```

3. **Nuclear option** (if totally broken):
   ```bash
   # On working device: Export
   tar -czf claude_fresh.tar.gz .claude/

   # On broken device: Remove old, import fresh
   rm -rf .claude
   tar -xzf claude_fresh.tar.gz
   ```

---

**Document Version**: 1.0
**Last Updated**: 2025-10-26
**Recommended Method**: Git (for developers) or Cloud Sync (for simplicity)
