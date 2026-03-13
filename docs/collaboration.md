# Part 7: Collaboration & Team Workflows

> **Enable multiple lawyers to work effectively on the same matters**

---

## What You'll Learn

By the end of this section, you will be able to:

- Set up shared workspaces for teams
- Hand off matters cleanly between lawyers
- Avoid conflicts in parallel work
- Establish team best practices

---

## 7.1 The Shared CLAUDE.md Model

### Why CLAUDE.md Works for Teams

CLAUDE.md is just a text file. This means:

- ✅ It can be stored anywhere accessible to the team
- ✅ Multiple lawyers can view and edit it
- ✅ Version control works naturally (track who changed what, when)
- ✅ No special software required

### Storage Options

| Option | Best For | How It Works |
|-------|---------|--------------|
| **Network Drive** | Firms with shared servers | CLAUDE.md in case folder on firm server |
| **Git Repository** | Tech-savvy teams | Case folders as git repos, CLAUDE.md tracked |
| **Cloud Sync** | Distributed teams | Dropbox/OneDrive folder synced across machines |
| **COWORK Shared Workspace** | All teams using COWORK | Built-in sharing features |

### Setting Up Shared Access

**Network Drive Example:**
```
📁 //firmserver/cases/    ├── 📁 2024-001_Smith_v_AG/    │   ├── 📄 CLAUDE.md (shared)    │   ├── 📁 research/    │   └── 📁 drafts/
```

**Git Repository Example:**
```
📁 ~/cases/ (git repo)    ├── 📁 2024-001_Smith_v_AG/    │   ├── 📄 CLAUDE.md (tracked)    │   └── 📁 .git/ (history)
```

---

## 7.2 Session Handoffs

### When Another Lawyer Picks Up Your Matter

**Scenario**: You're going on vacation. Colleague takes over your active matter.

### What to Document Before Handoff

**Update CLAUDE.md with:**
```markdown
## Handoff Notes (2024-01-15)

### Current Status
- Phase: [current phase]
- Active tasks: [what's being worked on]
- Blocking issues: [what's stuck]

### Recent Developments
- [Key development 1]
- [Key development 2]

### Immediate Priorities
1. [Priority 1] - Deadline: [date]
2. [Priority 2] - Deadline: [date]

### Key Context
- [Important background that's not obvious from documents]
- [Client preferences/ communication style]
- [Opposing counsel behavior patterns]

### Access
- All documents in: [location]
- Key correspondence: [where to find]
- Research notes: [location]
```

### Using `--resume` Effectively

Your colleague starts their session:
```
/briefing --resume
```

BetterCallClaude will:
1. Read CLAUDE.md (including your handoff notes)
2. Understand current state
3. Continue from where you left off

### The Handoff Checklist

Before handing off, verify:

- [ ] CLAUDE.md updated with current status
- [ ] Handoff notes section added
- [ ] All relevant documents in shared location
- [ ] Key deadlines clearly stated
- [ ] Client informed of handover (if appropriate)

---

## 7.3 Parallel Work on Same Matter

### What Works Well

**Sequential handoff** (one lawyer finishes, another starts):
- ✅ Clean context
- ✅ No conflicts
- ✅ Clear responsibility

**Independent research streams** (two lawyers research different aspects):
- ✅ Research can run in parallel
- ✅ Results combined later
- ⚠️ Requires coordination on findings

**Different phases, different lawyers** (one researches, one drafts):
- ✅ Clear phase boundaries
- ✅ Results feed into next phase
- ⚠️ Handoff point required

### What Doesn't Work Well

**Simultaneous CLAUDE.md edits**:
- ❌ Last write wins (overwrites other changes)
- ❌ Context confusion for BetterCallClaude
- ❌ Lost information

**Concurrent BetterCallClaude sessions on same matter**:
- ⚠️ Possible context divergence
- ⚠️ Research duplication
- ⚠️ Conflicting outputs

### How to Handle Parallel Work

**If you must work simultaneously:**

1. **Divide the work clearly**:
   - Lawyer A: Research Phase 1 issues
   - Lawyer B: Research Phase 2 issues

2. **Use separate research notes**:
   - `research_notes_A.md`
   - `research_notes_B.md`

3. **Sync before merging**:
   - Compare findings
   - Resolve any contradictions
   - Update CLAUDE.md together

4. **One person updates CLAUDE.md**:
   - Designate single updater
   - Sync before updating

---

## 7.4 Team Best Practices

### Directory Naming Conventions

**Recommended format:**
```
[Year]-[MatterNumber]_[MatterName]_[ClientName]

Examples:
2024-001_Smith_v_AG_MuellerGmbH
2024-002_Merger_Acquisition_TechStartAG
2024-003_Employment_Termination_Schmidt
```

**Why this works:**
- Chronological sorting
- Quick matter identification
- Client name for quick reference
- Consistent structure

### CLAUDE.md Update Discipline

**Who updates:**
- Lead lawyer on matter: Primary responsibility
- Supporting lawyers: Add findings to research notes, notify lead for CLAUDE.md updates

**When to update:**
- ✅ After client meetings (key decisions, instructions)
- ✅ After significant research findings
- ✅ When strategy changes
- ✅ Before handoffs
- ⚠️ Not after every minor query

**How to update:**
```markdown
## Update Log

### 2024-01-15 (F. Cesconi)
- Client instructed: proceed with litigation
- Deadline set: file by 2024-02-15
- Damages revised: CHF 450,000 (was CHF 500,000)

### 2024-01-10 (M. Schmidt)
- Initial research complete
- Key precedent found: BGE 149 III 123
```

### Weekly Sync Points

For active matters, hold brief syncs:

**Agenda:**
1. Status update (2 min each)
2. Blockers (5 min)
3. CLAUDE.md updates needed (5 min)
4. Next week priorities (5 min)

**Document sync decisions in CLAUDE.md:**
```markdown
## Team Sync - 2024-01-15

Attendees: F. Cesconi, M. Schmidt

Decisions:
- Proceed with litigation (client confirmed)
- M. Schmidt to handle BGE research
- F. Cesconi to draft complaint

Next sync: 2024-01-22
```

### Archiving Completed Matters

**When matter closes:**
1. Final CLAUDE.md update with outcome
2. Move to archive folder
3. Retain for reference period (per firm policy)

**Archive structure:**
```
📁 archive/    ├── 📁 2023/    │   ├── 📁 2023-045_Settled/    │   └── 📁 2023-046_Won/    └── 📁 2024/        └── 📁 2024-001_Settled/
```

---

## Collaboration Workflow Example

### Scenario: Two-Lawyer Litigation Prep

**Setup:**
- Lead: F. Cesconi
- Support: M. Schmidt
- Matter: Breach of contract, CHF 300,000 claim

**Week 1:**
```
Monday: F. Cesconi runs /briefing, creates CLAUDE.md
Tuesday: F. Cesconi delegates research to M. Schmidt
Wednesday: M. Schmidt works on research stream 1 (contract law)
          M. Schmidt works on research stream 2 (damages)
Thursday: M. Schmidt completes research, updates research_notes.md
Friday: F. Cesconi reviews research, updates CLAUDE.md with key findings
```

**Week 2:**
```
Monday: F. Cesconi runs /strategy with research findings
Tuesday: F. Cesconi drafts complaint
Wednesday: M. Schmidt reviews draft, runs /adversary
Thursday: F. Cesconi incorporates feedback
Friday: Final review, client approval
```

**Handoff point**: Thursday review → F. Cesconi incorporates Friday

---

> ⚠️ **CLAUDE.md conflicts do happen. When they do:**
> 1. Check edit history (who changed what, when)
> 2. Compare versions (what was lost)
> 3. Merge manually (combine both updates)
> 4. Communicate change to team (prevent recurrence)

---

## ✅ Collaboration Checklist

Before working as a team, verify:

- [ ] Shared storage location agreed
- [ ] Directory naming convention established
- [ ] CLAUDE.md update discipline understood
- [ ] Handoff checklist available
- [ ] Parallel work limitations understood
- [ ] Weekly sync scheduled (for active matters)

---

**🎉 You've completed the core tutorial!**

**Next**: [Appendix: Reference Materials](./appendix/command-reference.md) →
