# Appendix E: Team Features Deep-Dive

> **Collaboration capabilities for law firm workflows**

---

## Team Orchestration Overview

BetterCallClaude supports multi-lawyer workflows through:

1. **Shared CLAUDE.md**: Persistent case memory accessible to all
2. **Team commands**: Orchestrate multiple specialists
3. **Session handoffs**: Resume work started by colleagues
4. **Parallel execution**: Independent work streams

---

## Team Commands

### /team - Orchestrate Multiple Specialists

**Purpose**: Coordinate multiple AI specialists on complex matters

**Basic usage:**
```
/team research parallel streams on:
1. Contractual liability under Art. 97 OR
2. Damages calculation methods
3. Precedents on limitation periods
```

**What happens:**
1. BetterCallClaude identifies independent research streams
2. Spawns parallel research specialists
3. Each specialist works independently
4. Results synthesized into unified output

**When to use:**
- Multiple independent research questions
- Tight deadlines requiring parallel work
- Complex matters with distinct legal areas

---

### /delegate - Assign to Specific Specialists

**Purpose**: Send work to a specific specialist agent

**Available specialists:**
- `swiss-legal-researcher`: BGE/ATF/DTF research
- `swiss-legal-drafter`: Document drafting
- `swiss-case-strategist`: Litigation strategy
- `swiss-legal-adversary`: Argument challenge
- `citation-specialist`: Citation verification

**Example:**
```
/delegate to swiss-legal-researcher: Find all BGE decisions on Art. 97 OR contractual liability from the last 5 years
```

**When to use:**
- Specific expertise needed
- Clear, bounded task
- Want focused specialist attention

---

### /sync - Team Synchronization

**Purpose**: Update shared context and coordinate

**Usage:**
```
/sync Update CLAUDE.md with:
- Today's client meeting outcomes
- New deadline: filing by 2024-02-15
- Strategy change: focus on settlement
```

**What happens:**
1. CLAUDE.md updated with new information
2. Team notified of changes (if using shared workspace)
3. Next session will have current context

**When to use:**
- After significant developments
- Before handing off to colleague
- When strategy changes
- After client meetings

---

## Shared Workspace Patterns

### Pattern 1: Central CLAUDE.md with Git

**Setup:**
```
📁 cases-git/ (git repository)    ├── 📁 2024-001_Smith_v_AG/    │   ├── 📄 CLAUDE.md (tracked, merge-capable)    │   ├── 📁 research/    │   └── 📁 drafts/    └── .git/
```

**Workflow:**
1. Lawyer A works on matter, updates CLAUDE.md
2. Lawyer A commits: `git commit -am "Update: client meeting, strategy change"`
3. Lawyer B pulls: `git pull`
4. Lawyer B sees updates, continues work
5. Lawyer B commits their updates

**Advantages:**
- Full history of who changed what, when
- Can revert to previous versions
- Clear audit trail

**Challenges:**
- Requires basic git knowledge
- Merge conflicts possible (resolve like any text file)

---

### Pattern 2: Network Drive with Naming Convention

**Setup:**
```
📁 //firmserver/cases/    ├── 📁 2024-001_Smith_v_AG/    │   ├── 📄 CLAUDE.md    │   ├── 📄 CLAUDE_2024-01-15_FC.md (snapshot)    │   └── 📄 CLAUDE_2024-01-20_MS.md (snapshot)
```

**Workflow:**
1. Before major work: Create dated snapshot (`CLAUDE_YYYY-MM-DD_Initials.md`)
2. Work on main CLAUDE.md
3. After major changes: Create new snapshot

**Advantages:**
- No special software
- Snapshots provide history
- Simple file locking (if supported)

**Challenges:**
- Manual snapshot discipline required
- No automatic merge
- Can have conflicting versions if not careful

---

### Pattern 3: COWORK Shared Workspace

**Setup:**
Use COWORK's built-in workspace sharing features.

**Workflow:**
1. Create shared workspace for matter
2. Invite team members
3. CLAUDE.md automatically synced
4. Changes visible to all members

**Advantages:**
- Built-in sync
- No extra tools
- Integrated with COWORK features

**Challenges:**
- COWORK-specific
- Requires COWORK sharing setup

---

## Handoff Protocols

### Standard Handoff Checklist

**Before handing off, complete:**

```markdown
## Handoff Notes - [Date]

### Current Status
- Phase: [e.g., "Drafting complaint"]
- Active tasks: [what's in progress]
- Completed: [what's done]

### Key Developments
1. [Development 1]
2. [Development 2]

### Immediate Priorities
1. [Priority 1] - Deadline: [date]
2. [Priority 2] - Deadline: [date]

### Important Context
- [Context that's not obvious from documents]
- [Client preferences]
- [Opposing counsel behavior]

### Where Things Are
- Key documents: [location]
- Research: [location]
- Drafts: [location]

### Handoff To
- Lawyer: [Name]
- Date: [Date]
- Urgency: [High/Medium/Low]
```

---

### Resuming Another Lawyer's Work

**When picking up from colleague:**

1. **Read CLAUDE.md completely**
2. **Check for handoff notes** (usually at top or bottom)
3. **Review recent research/drafts**
4. **Run briefing with --resume:**
   ```
   /briefing --resume
   ```

5. **Confirm understanding before proceeding**

---

## Parallel Work Guidelines

### What Can Run in Parallel

| Task A | Task B | Why Parallel Works |
|--------|--------|-------------------|
| Research contract law | Research damages calculation | Independent legal questions |
| Draft sections 1-3 | Draft sections 4-6 | Non-overlapping content |
| Analyze document A | Analyze document B | Different source material |
| Research Zurich precedent | Research Bern precedent | Different jurisdictions |

### What Must Be Sequential

| Task A | Task B | Why Sequential Required |
|--------|--------|------------------------|
| Research findings | Strategy based on research | Strategy depends on research |
| Client instructions | Draft based on instructions | Draft reflects client wishes |
| Initial draft | Review and revision | Review needs draft complete |

---

## Team Best Practices Summary

### Directory Naming
```
[Year]-[Number]_[Matter]_[Client]
Example: 2024-001_Smith_v_AG_MuellerGmbH
```

### CLAUDE.md Discipline
- Lead lawyer: Primary responsibility for updates
- All lawyers: Add to research notes, notify lead for CLAUDE.md
- Update after: client meetings, strategy changes, major findings

### Communication Cadence
- **Daily**: Sync on blocking issues (if active matter)
- **Weekly**: Review status, update CLAUDE.md
- **At milestones**: Full team review

### Documentation
- **CLAUDE.md**: Case memory (persistent)
- **research_notes.md**: Research findings (append over time)
- **drafts/**: Working documents (version control if using git)

---

## See Also

- **[Collaboration Tutorial](../collaboration.md)** - Step-by-step collaboration guide
- **[CLAUDE.md Templates](./claude-md-templates.md)** - Ready-to-use templates
- **[Troubleshooting](./troubleshooting.md)** - When collaboration features don't work
