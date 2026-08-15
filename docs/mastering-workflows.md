# Part 5: Mastering Workflows

> **Design and execute multi-step legal processes**

## What You'll Learn

By the end of this section, you will be able to:

- Think in terms of legal workflows
- Chain commands naturally
- Design your own workflows
- Use quality checkpoints effectively
- Verify work automatically with goal-loops
- Build sourced case timelines

> **📖 Context**: This section builds on Phases 2-3 (Execution and Interaction) of the unified framework. For the complete methodology overview, see [Framework Methodology](./framework-methodology.md).

---

## 5.1 Thinking in Workflows

### The Natural Legal Process

Legal work naturally flows through stages:

```
Intake → Research → Strategy → Draft → Review → Deliver
```

This mirrors how BetterCallClaude works best. Each stage maps to specific commands:

| Stage | BetterCallClaude Approach | Commands |
|-------|--------------------------|----------|
| Intake | Understand the matter, gather facts | /briefing |
| Research | Find law and precedents | /research, /cite |
| Strategy | Assess strengths, weaknesses | /strategy, /adversarial |
| Draft | Create documents | /draft |
| Review | Check quality, consistency | /adversarial, /cite |
| Deliver | Finalize and communicate | /translate, /draft |

### The `/legal-5step` Shortcut

For matters where you want the full pipeline in one command:

```
/legal-5step [matter description] --medium
```

This runs: Intake → Research → Strategy → Adversarial → Draft with quality gates at Steps 3 and 4. See [Framework Methodology](./framework-methodology.md) for full details.

---

## 5.2 Command Chaining

### Natural Language Chaining

You can chain commands naturally by describing the sequence:

**Example 1: Research → Draft**
```
First research Art. 97 OR contractual liability damages, then draft a client memo summarizing the key points
```

**Example 2: Strategy → Adversary → Draft**
```
Assess the strength of our limitation period argument, challenge it with adversarial analysis, then draft a brief memo to the client explaining the risks
```

### Sequential vs. Parallel Operations

**Sequential (one after another):**
```
Research case law on Art. 97 OR. Based on findings, draft legal opinion.
```
Better for: When later steps depend on earlier findings

**Parallel (at the same time):**
```
Research BGE decisions on hardship clauses AND research statutory framework for commercial leases. Then synthesize findings.
```
Better for: Independent research streams that you'll combine later

### When to Chain vs. When to Use a Predefined Workflow

| Use Chaining When... | Use Predefined Workflow When... |
|---------------------|------------------------------|
| Unique matter structure | Standard legal process |
| One-off approach | Repeated similar work |
| Exploring new area | Proven methodology |
| Need flexibility | Need consistency |

---

## 5.3 Designing Your Own Workflow

### Step 1: Identify the Stages

For your matter, break it into stages:

**Example: Contract Review Matter**
```
1. Initial Review - Understand contract structure and key terms
2. Risk Analysis - Identify problematic clauses
3. Research - Find applicable law and precedents
4. Recommendations - Draft advice to client
5. Negotiation Support - Prepare talking points
```

### Step 2: Select Commands for Each Stage

| Stage | Command | Purpose |
|-------|---------|---------|
| Initial Review | /doc-analyze | Extract key terms and structure |
| Risk Analysis | /adversarial | Find weaknesses and risks |
| Research | /research | Find supporting law |
| Recommendations | /draft | Create client memo |
| Negotiation | /strategy | Plan negotiation approach |

### Step 3: Define with /workflow

**Type:**
```
/workflow contract-review
  Stage 1: Analyze document structure and key terms
  Stage 2: Run adversarial analysis on risk clauses
  Stage 3: Research applicable law for identified risks
  Stage 4: Draft client recommendations memo
  Stage 5: Develop negotiation strategy
```

### Step 4: Execute and Iterate

Run the workflow, observe results, and refine:
```
Execute the contract-review workflow for the attached lease agreement
```

---

## 5.4 Predefined Workflows

### litigation-prep

**Purpose**: Prepare for litigation from initial assessment through case strategy

**Stages:**
1. **Intake**: Gather facts and documents
2. **Research**: Find applicable law and precedents
3. **Risk Assessment**: Evaluate strengths and weaknesses
4. **Strategy**: Develop case strategy
5. **Documentation**: Draft initial briefs and memos

**Use when**: Client wants to sue or is being sued

---

### due-diligence

**Purpose**: Systematic review of legal documents in transactions

**Stages:**
1. **Document Intake**: Gather all relevant documents
2. **Risk Scan**: Quick identification of issues
3. **Deep Analysis**: Detailed review of flagged items
4. **Risk Matrix**: Organize findings by severity
5. **Report**: Draft due diligence report

**Use when**: M&A, investment, or major contract review

---

### contract-lifecycle

**Purpose**: From drafting through execution and amendment

**Stages:**
1. **Requirements**: Understand what the contract must achieve
2. **Drafting**: Create initial draft
3. **Review**: Check for risks and compliance
4. **Negotiation**: Prepare for counterparty discussions
5. **Finalization**: Execute and archive

**Use when**: Creating new agreements or major amendments

---

### legal-5step

**Purpose**: End-to-end legal analysis from intake to final draft

**Stages:**
1. **Intake**: Structured fact gathering and issue identification
2. **Research**: BGE/ATF/DTF precedent search with citation verification
3. **Strategy**: Litigation strategy with risk assessment and probability scoring
4. **Adversarial**: Three-agent stress test (Advocate, Adversary, Judge)
5. **Draft**: Final document generation with traced citations

**Quality gates** at Steps 3 and 4 ensure issues are caught before proceeding.

**Use when**: You want a complete analysis from start to finish in one command

**How to invoke**:
```
/legal-5step [matter description] --medium
```

**Flags**: `--short`, `--medium`, `--long`, `--no-summary`, `--stop-after`, `--lang`, `--canton`

---

## 5.5 Verifying Work Automatically: Goal-Loops (v4.9.0)

The biggest change since v4.6: BetterCallClaude can now **verify its own deliverables against a machine-checkable success condition** — with a separate judge agent, so an agent never grades its own homework.

### The Two Commands

```
/legal-goal [profile or free-text objective]   →  creates a Goal Record (never starts work)
/legal-loop [goal-record]                       →  runs worker → evaluator iterations
```

1. **`/legal-goal`** turns your quality bar into a **Goal Record** — a small file with a YAML header describing exactly what "done and correct" means.
2. **`/legal-loop`** then runs the cycle: a **worker** agent improves the deliverable, an **evaluator** agent (the `legal-evaluator` skill) judges it against the Goal Record, and the loop repeats until the condition is met or a safety rail stops it.

```
        ┌──────────────────────────────────────────┐
        │              /legal-loop                 │
        │                                          │
        │   ┌────────┐      ┌────────────┐         │
        │   │ WORKER │ ───▶ │ EVALUATOR  │─── ✅ pass → stop
        │   │ agent  │      │ (judge)    │         │
        │   └────────┘      └─────┬──────┘         │
        │        ▲               │ fail            │
        │        └───────────────┘ (iterate)       │
        └──────────────────────────────────────────┘
```

### Pre-Wired Profiles

| Profile | Verifies That... | Typical Use |
|---------|------------------|-------------|
| `citations-clean` | Every citation is validated via MCP (R1/R2 anti-hallucination rules) | Any draft before delivery |
| `draft-passes-gate` | Citations + structure + factual support all pass | Full quality gate for deliverables |
| `adversarial-converge` | The position survives repeated stress-testing | Contentious positions |
| `nda-batch-clean` | Every NDA in a folder got a complete triage verdict | NDA folders (max 3 iterations) |
| `reg-watch` | A monitoring pass over Fedlex + swiss-caselaw changes ran cleanly | Scheduled regulatory monitoring (1 pass per run) |
| `timeline-sourced` | Every timeline event has a traceable source, conflicts flagged, deadlines anchored | Case chronologies (v4.9.5) |

**Example: gate a draft before it goes out**
```
/legal-goal draft-passes-gate
/legal-loop bcc-output/goals/2026-08-15-draft-gate.md
```

### Safety Rails (Non-Negotiable)

- **Worker ≠ judge**: enforced at runtime — the same agent never produces and grades the work
- **Finite loops**: max 5 iterations by default, hard cap 20
- **No-progress guard**: stops after 2 consecutive iterations without score improvement
- **Honest termination**: if the condition is not met when the loop stops, the verdict says **NOT MET** and lists residual findings — never a false pass
- **Privacy pre-check every iteration** (Anwaltsgeheimnis)
- **Human-in-the-loop**: the loop never files, sends, signs, or transmits anything

Every iteration leaves an **auditable verdict trail** in `bcc-output/loops/` — you can see exactly what the judge said, with a 0–100 score and itemized findings.

---

## 5.6 Building a Sourced Case Timeline (v4.9.5)

Litigation lives on facts and dates. `/legal-timeline` turns a folder of case documents — contracts, correspondence, court filings, expert reports — into a legal chronology the way a lawyer reads a case.

```
/legal-timeline @case-folder/
```

### What Makes It Different from a Summary

- **Mandatory provenance**: every event carries its document and locus (page/paragraph). An event without a source never appears in any output — this is the R1/R2 anti-hallucination rule applied to facts.
- **Contested-fact model**: each event is marked `undisputed`, `alleged`, or `contested`, with party attribution.
- **Date conflicts are never silently resolved**: when two documents disagree on a date, the timeline records **both** dates and their sources.
- **Evidentiary gap flags**: periods of ≥ 30 undocumented days are flagged, so you know where the record is thin.
- **Deadline markers**: procedural deadlines (ZPO 142–149, BGG 46/100–101, cantonal holiday calendars) are computed via the `legal-persona` MCP; substantive limitation periods (Verjährung) come from the skill's mapping table and are always labelled **indicative** — verify them yourself.

### Three Output Formats

All under `bcc-output/timeline/` (a living case artifact — update it with `--merge` as new documents arrive):

| File | What It's For |
|------|---------------|
| `timeline.md` | Authoritative table — events, sources, statuses, deadlines |
| `timeline.html` | Self-contained interactive view: colour-coded statuses, gap bands, deadline markers, source click-through |
| `timeline.docx` | Case-file export for Word users |

### Combining Both

Chain a timeline with a goal-loop for maximum rigor:

```
/legal-timeline @case-folder/
/legal-goal timeline-sourced
/legal-loop bcc-output/goals/2026-08-15-timeline-goal.md
```

The loop only closes when every event has a traceable source, all conflicts are flagged, and all deadlines are anchored. See the full walkthrough in [Case Chronology](./scenarios/case-chronology.md).

---

## 5.7 Quality Checkpoints

### When to Stop and Review

**After Research Phase:**
- [ ] Found key precedents for each legal issue?
- [ ] Verified citations are accurate?
- [ ] Identified gaps in research?

**After Strategy Phase:**
- [ ] Assessed both strengths and weaknesses?
- [ ] Considered client's practical constraints?
- [ ] Probability assessment seems reasonable?

**Before Draft Delivery:**
- [ ] Document addresses all required points?
- [ ] Citations verified and properly formatted?
- [ ] Language appropriate for recipient?

### Validating Citations

Always verify AI-generated citations:
```
/cite [citation from AI output]
```

If the citation doesn't exist or is incorrect:
1. Note the error
2. Search for the correct citation
3. Update your document

### Substantive Citation Verification (v4.9.4)

Since v4.9.4, checking that a citation *exists* is only half the gate. The `citation-content-verify` skill checks every citation in a draft against the **live source** on two axes: does the cited source exist, and does it actually **support the claim** made for it?

Each citation receives a status:

| Status | Meaning |
|--------|---------|
| `MATCH` | Source exists and supports the claim |
| `PARTIAL` | Source exists but only partly supports the claim (warning) |
| `MISMATCH` | Source exists but contradicts the claim |
| `UNVERIFIED` | Source could not be found — the citation may be fabricated |
| `SKIPPED` | Informal doctrine reference (author/title/margin number) |

**Any `UNVERIFIED` or `MISMATCH` citation blocks automatic delivery** — the draft must be fixed, explicitly disclaimed, or escalated. This gate runs automatically inside `/legal-loop` verdicts and before the orchestrator delivers any citation-bearing document; `/validate` invokes it directly on your drafts. In `strict` privacy mode, claim sentences are never sent to cloud content-checks — verification falls back to existence-only with a `(privacy-gated)` note.

### Professional Responsibility Reminder

> **You remain responsible for all legal work.** BetterCallClaude is a tool that assists, but all analysis, strategy, and documents must be reviewed and validated by you before use. AI can make mistakes—citation hallucinations, incorrect legal interpretations, or missed nuances. Your professional judgment is the final check.

---

## 5.8 Workflow Example: Full Walkthrough

### Scenario: Client Wants Legal Opinion on Termination Rights

**Option A: Manual Step-by-Step (~2 hours)**

**Step 1: Intake (5 minutes)**
```
/briefing Client needs legal opinion on whether they can terminate employment contract early due to employer's failure to pay agreed bonus
```

**Step 2: Execute Briefing Plan (45 minutes)**

Following the plan, research employment law on bonus agreements, find precedents on constructive dismissal, analyze the contract.

**Step 3: Strategy Check (10 minutes)**
```
/strategy Termination for unpaid bonus, 2 years remaining on contract, employer claims financial hardship
```

**Step 4: Challenge Your Position (10 minutes)**
```
/adversarial Client's position: Non-payment of bonus is fundamental breach justifying immediate termination
```

**Step 5: Draft Opinion (30 minutes)**
```
/draft legal opinion for client on termination rights, addressing both constructive termination argument and employer's hardship defense
```

**Step 6: Final Review (15 minutes)**
```
Verify all citations, check for bias toward client position, ensure practical advice is clear
```

**Total: ~2 hours** for a thorough legal opinion with validated research.

**Option B: One-Command Pipeline (~2 hours, less typing)**

```
/legal-5step Client needs legal opinion on whether they can terminate employment
contract early due to employer's failure to pay agreed bonus. 2 years remaining,
employer claims financial hardship. --medium
```

BetterCallClaude runs the full pipeline with quality gates, producing the same deliverable with less manual orchestration.

---

> ⚠️ **Workflow not working as expected? Try this:**
> - Break it into smaller stages and run sequentially
> - Check that each command is working before chaining
> - Verify your CLAUDE.md has sufficient context
> - Try the workflow with `--explain` to understand each step

---

## ✅ Mastering Workflows Checklist

Before moving to scenarios, verify:

- [ ] I can describe my legal work as a workflow
- [ ] I can chain commands naturally
- [ ] I know when to use predefined vs. custom workflows
- [ ] I understand quality checkpoints and the citation content gate
- [ ] I can set up a goal-loop to verify a deliverable automatically
- [ ] I can build a sourced case timeline with `/legal-timeline`
- [ ] I always validate citations and review AI output

---

**🎉 You're ready for real-world scenarios!**

**Next**: [Scenario Library](./scenarios/) →
