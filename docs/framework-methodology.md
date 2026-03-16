# The BetterCallClaude Framework: A Methodology for Legal AI Work

> **The unified workflow that guides lawyers through any case**

## What You'll Learn

By the end of this section, you will understand:

- The 5-phase framework and when to use it
- How to set up your workspace for case management
- How to invoke agents and use command modes
- How to build custom workflows
- How to manage documents and maintain context

---

## Overview

### The Framework at a Glance

BetterCallClaude provides a structured methodology for handling legal work with AI assistance. The framework consists of five interconnected phases:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      THE BETTERCALLCLAUDE FRAMEWORK                          │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐ │
│  │ BRIEFING │ → │ EXECUTION│ → │INTERACTION│ → │ADVERSARIAL│ → │  FINAL   │ │
│  │          │   │          │   │          │   │          │   │ SUMMARY  │ │
│  │ Structured│   │ Carry out │   │ Refine & │   │ Stress-  │   │ Client-  │ │
│  │  intake  │   │ the plan  │   │  deepen  │   │   test   │   │  ready   │ │
│  └──────────┘   └──────────┘   └──────────┘   └──────────┘   └──────────┘ │
│       │              │              │              │              │        │
│    Panel asks    Research &     Q&A to fill    Challenge     Professional  │
│    questions     analysis       gaps          position       document      │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### When to Use the Full Framework vs. Quick Commands

| Use Full Framework When... | Use Quick Commands When... |
|---------------------------|---------------------------|
| Complex, multi-issue matters | Simple, single-issue queries |
| Significant client consequences | Quick lookup or verification |
| Multi-step research required | Standard drafting task |
| Cross-canton or multi-domain issues | You know exactly what you need |
| New matter intake | Follow-up on existing work |
| Team collaboration needed | Solo, focused task |

**Quick Command Examples:**
```
/cite BGE 147 IV 73                          → Citation lookup (30 seconds)
/research Art. 97 OR limitation period       → Focused research (2-5 minutes)
/translate "Klage" from DE to FR             → Quick translation
```

**Full Framework Example:**
```
/briefing Client needs legal opinion on early termination of commercial lease
             due to COVID-19 hardship, with potential for litigation
```

---

## Setting Up Your Workspace

### Why Case-Specific Directories Matter

BetterCallClaude reads your `CLAUDE.md` file at the start of every conversation **in that directory**. This provides:

- **Cross-session persistence**: Resume work days or weeks later without re-explaining
- **Case context**: The AI understands your matter from the start
- **Privacy protection**: Each case is isolated in its own directory
- **Document organization**: Related files stay together

```
❌ WRONG: Working in a generic directory
~/Documents/legal/CLAUDE.md     ← All cases mixed together
                                 ← BetterCallClaude confused about context

✅ RIGHT: One directory per case
~/Documents/legal/cases/
├── mueller-v-schmidt-2024/
│   ├── CLAUDE.md              ← Context for this case only
│   └── docs/
│       ├── contracts/
│       ├── correspondence/
│       └── research/
├── ag-zurich-merger/
│   ├── CLAUDE.md              ← Different context
│   └── docs/
```

### Creating a Case Directory

**Step 1: Create the directory structure**
```bash
mkdir -p ~/Documents/legal/cases/[case-name]/docs/{contracts,correspondence,research,drafts}
```

**Step 2: Create CLAUDE.md from a template**

Use one of the templates from [CLAUDE.md Templates](./appendix/claude-md-templates.md) or start with this minimal structure:

```markdown
# Matter: [Brief Description]

## Client
- **Name**: [Client Name or Code]
- **Type**: [Individual/Company]

## Opposing Party
- **Name**: [Party Name]
- **Counsel**: [If known]

## Matter Summary
[2-3 sentences describing the legal issue]

## Key Facts
1. [Key fact 1]
2. [Key fact 2]

## Legal Issues
- [Issue 1]
- [Issue 2]

## Key Documents
- `/docs/contracts/[document].pdf` - [Relevance]
- `/docs/correspondence/[letter].pdf` - [Relevance]

## Status
- **Phase**: [Intake/Research/Strategy/Drafting/Review]
- **Next Steps**: [What needs to be done]
- **Deadline**: [Next deadline]

## Update Log
### [Date]
- [What was done/decided]
```

**Step 3: Navigate to the directory before starting**
```
cd ~/Documents/legal/cases/[case-name]
```

BetterCallClaude will now read your CLAUDE.md at session start.

### How CLAUDE.md Works

**What BetterCallClaude Reads:**
- Matter summary and legal issues
- Key facts and timeline
- Parties and their positions
- Document locations and relevance
- Current status and next steps

**When to Update CLAUDE.md vs. Just Chat:**

| Update CLAUDE.md when... | Just chat when... |
|-------------------------|-------------------|
| New key facts emerge | Exploring options |
| Legal issues crystallize | Quick questions |
| Strategy decisions are made | Minor clarifications |
| Important documents arrive | Routine updates |
| Significant developments occur | Ephemeral discussions |

**Example Update After Development:**
```markdown
## Status
- **Phase**: Post-initial assessment
- **Key Development**: Opposing party has admitted the contract breach
  but disputes the damages calculation
- **Next Steps**: Research BGE precedents on damages proof
- **Deadline**: Client meeting Friday

## Update Log
### 2024-03-15
- Received opposing party's response letter
- Key admission: Contract breach acknowledged
- Dispute: Damages calculation methodology
- Updated strategy: Focus on damages proof
```

---

## Phase 1: Briefing

### Purpose

Structured intake with specialist panel consultation to ensure you and BetterCallClaude fully understand the matter before diving into work.

### What Happens

1. You describe the matter
2. A specialist panel asks targeted questions
3. You provide facts and context
4. Panel builds an execution plan
5. You approve the plan

### Output

A structured execution plan with:
- Research phases and estimated time
- Strategy development steps
- Document drafting requirements
- Quality checkpoints

### Transition Criteria

Move to Execution when:
- [ ] All panel questions answered
- [ ] Scope is clearly defined
- [ ] Execution plan is approved
- [ ] Time estimates are acceptable

### How to Invoke

```
/briefing [matter description]
```

**Example:**
```
/briefing Client is a software company being sued for alleged copyright
infringement in their flagship product. Opposing party is a former employee
who claims code was stolen. Need to assess exposure and prepare defense strategy.
```

### Using `--resume` for Cross-Session Work

If a briefing spans multiple sessions:
```
/briefing --resume
```

---

## Phase 2: Execution

### Purpose

Carry out the planned research, document analysis, and preliminary drafting according to the execution plan.

### What Happens

- Research agents search BGE/ATF/DTF databases
- Statutory analysis via Fedlex
- Document analysis and extraction
- Initial drafting of findings

### Output

Raw findings, initial analysis, and draft materials ready for refinement.

### Transition Criteria

Move to Interaction when:
- [ ] Core research questions answered
- [ ] Key precedents identified
- [ ] Initial analysis complete
- [ ] Gaps in understanding identified

### Invoking Agents During Execution

**Automatic Invocation (via Skills):**
Most agent invocation happens automatically through skills:

| Your Request | Skill Auto-Activates | Agents Involved |
|--------------|---------------------|-----------------|
| "Research Art. 97 OR" | swiss-legal-research | researcher, citation |
| "Draft a contract" | swiss-legal-drafting | drafter |
| "Assess case strategy" | swiss-legal-strategy | strategist, risk |

**Direct Command Invocation:**
For specific tasks, use commands directly:

| Command | Agent(s) Involved | When to Use |
|---------|-------------------|-------------|
| `/bettercallclaude:research` | researcher | Legal research queries |
| `/bettercallclaude:strategy` | strategist | Case strategy questions |
| `/bettercallclaude:draft` | drafter | Document creation |
| `/bettercallclaude:cite` | citation | Citation verification |
| `/bettercallclaude:precedent` | researcher | Precedent chain analysis |

### Understanding Command Modes

Different situations call for different levels of detail. Use mode flags to control output:

| Mode | Flag | Output Length | When to Use |
|------|------|---------------|-------------|
| **Short** | `--short` | Brief, essential points | Quick lookup, limited time, mobile |
| **Medium** | `--medium` | Standard detail (default) | Most tasks, normal workflow |
| **Long** | `--long` | Comprehensive analysis | Complex matters, written opinions, thorough review |

**Examples:**
```
/research Art. 97 OR --short          → Key points only (30 seconds)
/research Art. 97 OR --medium         → Standard analysis (2 minutes)
/research Art. 97 OR --long           → Comprehensive review (5+ minutes)
```

**When to Choose Each Mode:**

| Mode | Best For |
|------|----------|
| `--short` | Quick citation check, client on phone, confirming a point |
| `--medium` | Standard research, drafting support, case analysis |
| `--long` | Written opinions, due diligence reports, complex multi-issue matters |

---

## Phase 3: Interaction

### Purpose

Refine and deepen the analysis through Q&A, addressing gaps and exploring nuances that emerged during execution.

### What Happens

- You ask follow-up questions
- BetterCallClaude clarifies ambiguities
- Additional research fills gaps
- Analysis becomes more nuanced

### Output

Refined understanding, resolved ambiguities, and analysis ready for adversarial testing.

### Transition Criteria

Move to Adversarial Analysis when:
- [ ] All material issues addressed
- [ ] Key ambiguities resolved
- [ ] Client questions answered
- [ ] Ready to stress-test conclusions

### Referring to Documents in Prompts

**Method 1: Direct Reference**
```
Based on the employment contract in /docs/contracts/employment-2024.pdf,
analyze whether the termination clause is enforceable under Swiss law.
```

**Method 2: Contextual Reference**
```
See the correspondence in /docs/correspondence/ regarding the bonus dispute.
The client's position is stated in the letter dated March 15.
Research whether non-payment of a discretionary bonus can constitute
constructive dismissal under Art. 337 OR.
```

**Method 3: Multi-Document Analysis**
```
Compare the following documents and identify inconsistencies:
- /docs/contracts/master-agreement.pdf
- /docs/contracts/amendment-2023.pdf
- /docs/correspondence/email-2024-02-15.pdf
```

### Iterative Refinement Techniques

**Drill-Down Pattern:**
```
Initial: "Research BGE precedents on Art. 97 OR"
Follow-up: "Focus on cases involving limitation periods over 10 years"
Refinement: "What about cases where the contract specified a shorter period?"
```

**Gap-Filling Pattern:**
```
Initial analysis mentions: "The court might consider hardship..."
Your question: "What BGE decisions have addressed hardship in commercial leases?"
Follow-up: "Have any cantonal courts taken a different approach?"
```

---

## Phase 4: Adversarial Analysis

### Purpose

Stress-test conclusions for supra-partes (impartial) objectivity. Ensure your position can withstand opposing arguments.

### What Happens

1. **Advocate agent** builds the strongest case for your position
2. **Adversary agent** challenges that position with counter-arguments
3. **Judicial agent** synthesizes a balanced, objective assessment

### Output

Balanced assessment including:
- Strengths of your position
- Weaknesses and vulnerabilities
- Counter-arguments to anticipate
- Risk-adjusted recommendations

### Transition Criteria

Move to Final Summary when:
- [ ] Both sides fairly represented
- [ ] Key risks identified
- [ ] Mitigation strategies developed
- [ ] Ready to advise client

### The Three-Agent Analysis System

```
┌─────────────────────────────────────────────────────────────────────┐
│                    ADVERSARIAL ANALYSIS                              │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ┌──────────────┐     ┌──────────────┐     ┌──────────────┐       │
│  │   ADVOCATE   │ ──→ │   ADVERSARY  │ ──→ │   JUDICIAL   │       │
│  │              │     │              │     │              │       │
│  │ Builds your  │     │ Challenges   │     │ Synthesizes  │       │
│  │ strongest    │     │ every point  │     │ balanced     │       │
│  │ case         │     │              │     │ assessment   │       │
│  └──────────────┘     └──────────────┘     └──────────────┘       │
│         │                    │                    │                │
│         ▼                    ▼                    ▼                │
│   Arguments,           Weaknesses,          Objective              │
│   precedents,          counter-args,        evaluation,            │
│   evidence             risks                recommendations        │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### How to Invoke

```
/adversary [your position or argument]
```

**Example:**
```
/adversary My position: The limitation period for the contractual claim is
10 years under Art. 127 OR, not 5 years under Art. 128 OR, because the
claim arises from a written contract and the obligation was not periodic.
```

### What You'll Receive

```markdown
## Advocate Position (Your Case)
[Strongest arguments for your position]

## Adversary Challenge (Counter-Arguments)
[Strongest arguments against your position]

## Judicial Synthesis (Balanced Assessment)
[Objective evaluation of both sides]

### Risk Assessment
- Strength of your position: [X/10]
- Key vulnerabilities: [...]
- Recommended approach: [...]

### Precedent Analysis
- Supporting BGE decisions: [...]
- Contrary BGE decisions: [...]
- Distinguishing factors: [...]
```

---

## Phase 5: Final Summary

### Purpose

Communicate conclusions professionally in a client-ready format.

### What Happens

- Draft client memorandum or opinion
- Format for professional presentation
- Validate all citations
- Ensure practical, actionable advice

### Output

Clear, actionable client document ready for delivery.

### Transition Criteria

Work is complete when:
- [ ] Document addresses all required points
- [ ] Citations verified and properly formatted
- [ ] Language appropriate for recipient
- [ ] Practical advice is clear
- [ ] Professional quality achieved

### How to Invoke

```
/draft [document type] [context]
```

**Examples:**
```
/draft legal opinion for client on termination rights under the lease agreement

/draft client memorandum summarizing the litigation risks and recommended strategy

/draft demand letter to opposing party regarding the contract breach
```

### Document Types Available

| Document Type | Command Example |
|---------------|-----------------|
| Legal opinion | `/draft legal opinion on [topic]` |
| Client memo | `/draft client memo summarizing [issue]` |
| Contract | `/draft service agreement for [context]` |
| Court submission | `/draft Klageschrift for [matter]` |
| Correspondence | `/draft letter to [recipient] regarding [topic]` |
| Demand letter | `/draft demand letter for [claim]` |

---

## Invoking Agents: Complete Reference

### Core Agents and When to Use Them

| Agent | Domain | How It Activates | When You Need It |
|-------|--------|------------------|------------------|
| `researcher` | BGE/ATF/DTF research | Auto via /research | Finding precedents, statutory analysis |
| `strategist` | Litigation strategy | Auto via /strategy | Case planning, risk assessment |
| `drafter` | Document drafting | Auto via /draft | Creating legal documents |
| `citation` | Citation verification | Auto via /cite | Verifying BGE references |
| `compliance` | FINMA, AML/KYC | Auto on regulatory queries | Regulatory compliance |
| `translator` | DE/FR/IT translation | Auto via /translate | Multi-language work |

### Specialized Domain Agents

| Agent | Domain | Example Use |
|-------|--------|-------------|
| `data-protection` | nDSG/FADP, GDPR | Privacy impact assessments |
| `fiscal` | Tax law, DTAs | Tax planning, disputes |
| `corporate` | AG/GmbH, M&A | Company law matters |
| `cantonal` | All 26 cantons | Canton-specific research |
| `realestate` | Property, Grundbuch | Real estate transactions |
| `procedure` | ZPO/StPO deadlines | Procedural planning |
| `risk` | Outcome probability | Settlement evaluation |

### Direct Agent Invocation

Most agents activate automatically through skills. For explicit control:

```
/bettercallclaude:research [query]    → Activates researcher + citation
/bettercallclaude:strategy [query]    → Activates strategist + risk
/bettercallclaude:draft [query]       → Activates drafter
/bettercallclaude:adversary [query]   → Activates advocate + adversary + judicial
```

---

## Building Workflows

### Natural Language Chaining

Describe your workflow in plain language:

```
Research BGE precedents on Art. 97 OR contractual liability, then
assess the strength of our limitation period argument, and finally
draft a client memo summarizing the risks
```

This chains: `/research` → `/strategy` → `/draft`

### Sequential vs. Parallel Operations

**Sequential (one after another):**
```
First research the BGE decisions on hardship clauses, then based on those
findings, draft a legal opinion for the client.
```
Use when: Later steps depend on earlier findings

**Parallel (at the same time):**
```
Research federal BGE decisions on the limitation period AND research
cantonal court tendencies in Zurich, then synthesize both findings.
```
Use when: Independent research streams to combine later

### Workflow Design Pattern

**Step 1: Identify the stages**
```
1. Document review - Understand what we have
2. Legal research - Find applicable law
3. Risk analysis - Identify problems
4. Strategy - Plan approach
5. Draft - Create deliverable
```

**Step 2: Select commands for each stage**
```
Stage 1: /doc-analyze
Stage 2: /research, /cite
Stage 3: /adversary
Stage 4: /strategy
Stage 5: /draft
```

**Step 3: Execute**
```
Run the workflow: Analyze the attached contract, research applicable
law, challenge our position, develop strategy, then draft client recommendations.
```

### Predefined Workflows

| Workflow | Purpose | Stages |
|----------|---------|--------|
| `litigation-prep` | Prepare for litigation | Intake → Research → Strategy → Draft → Review |
| `due-diligence` | Transaction review | Documents → Risk Scan → Analysis → Report |
| `contract-lifecycle` | Contract management | Requirements → Draft → Review → Negotiate → Execute |

**Invoke predefined workflow:**
```
/bettercallclaude:workflow litigation-prep --matter "Breach of contract claim"
```

---

## Document Management

### Organizing Your /docs Subdirectory

```
docs/
├── contracts/           # Agreements, leases, employment contracts
│   ├── master-agreement.pdf
│   ├── amendment-2023.pdf
│   └── related-correspondence/
├── correspondence/      # Letters, emails, memos
│   ├── incoming/
│   ├── outgoing/
│   └── internal/
├── research/           # Research outputs, notes
│   ├── precedent-analysis.md
│   └── statutory-research.md
├── drafts/             # Work in progress
│   ├── opinion-draft-v1.md
│   └── opinion-draft-v2.md
└── filed/              # Final, delivered documents
    └── legal-opinion-final.pdf
```

### Naming Conventions

**Documents:**
```
YYYY-MM-DD_[type]_[parties]_[description].pdf

Examples:
2024-03-15_contract_mueller-schmidt_lease.pdf
2024-03-20_letter_to-opposing-counsel_demand.pdf
2024-03-25_research_BGE-hardship-clauses.md
```

**Drafts:**
```
[document-type]_draft_v[N].md

Examples:
legal-opinion_draft_v1.md
legal-opinion_draft_v2.md
legal-opinion_final.md
```

### Referring to Documents in Prompts

**Single Document:**
```
Based on /docs/contracts/employment-2024.pdf, analyze the non-compete clause.
```

**Multiple Documents:**
```
Review these documents for consistency:
- /docs/contracts/master-agreement.pdf
- /docs/contracts/amendment-2023.pdf
Point out any contradictions or conflicts.
```

**Document + Research:**
```
The termination clause in /docs/contracts/lease-2022.pdf states 6 months notice.
Research whether this can be challenged under Art. 271 OR for hardship.
```

---

## Decision Framework

### When to Use Full Framework vs. Abbreviated Approach

**Use Full Framework (All 5 Phases):**
- New matter intake
- Complex legal questions
- Significant client exposure
- Multi-issue analysis
- Litigation preparation

**Use Abbreviated Approach (Skip Phases):**

| Skip Briefing | Skip Interaction | Skip Adversarial |
|---------------|------------------|------------------|
| Clear scope from start | Single-answer questions | Low-stakes matters |
| Follow-up on known issue | No ambiguity | Internal research only |
| Quick research task | Standard application | Non-controversial issues |

**Use Quick Commands Only:**
- Citation lookup
- Single statute check
- Quick translation
- Document formatting

### Common Pitfalls at Each Phase

| Phase | Pitfall | Solution |
|-------|---------|----------|
| Briefing | Over-answering questions | Keep responses targeted |
| Briefing | Too broad scope | Use `--scope narrow` |
| Execution | Not using mode flags | Match mode to need |
| Execution | Ignoring gaps | Document what's missing |
| Interaction | Asking before research completes | Let execution finish first |
| Adversarial | Only seeing one side | Read adversary output carefully |
| Final | Skipping citation validation | Always run /validate |

### Quality Checkpoints

**After Briefing:**
- [ ] Scope is clear and documented
- [ ] Execution plan is approved
- [ ] Time estimates are reasonable

**After Execution:**
- [ ] Key precedents found
- [ ] Citations verified
- [ ] Gaps identified

**After Adversarial:**
- [ ] Both sides fairly represented
- [ ] Risks understood
- [ ] Mitigation planned

**Before Delivery:**
- [ ] All citations validated
- [ ] Document addresses all issues
- [ ] Language appropriate for client
- [ ] Practical advice is clear

---

## Example Walkthrough

### Complete Framework Application

**Scenario:** Client wants legal opinion on terminating commercial lease early due to COVID-19 hardship.

**Phase 1: Briefing (10 minutes)**
```
/briefing Client operates a restaurant in Zurich. 5-year commercial lease
signed 2022. Government closures in 2020 caused 70% revenue drop. Client
has paid partial rent since June 2020. Wants to terminate early due to
ongoing financial hardship. Landlord refuses rent reduction.
```

Panel asks:
1. What does the termination clause state?
2. What canton is the property in?
3. What is the client's goal—full termination or renegotiation?
4. What is the client's risk tolerance for litigation?

**Phase 2: Execution (45 minutes)**
```
Execute Phase 1: Research BGE decisions on commercial lease hardship
```

Research finds:
- BGE 129 III 145: Hardship doctrine in Swiss law
- Cantonal emergency measures (Zurich specific)
- No direct BGE on COVID-19 hardship yet

```
/research Art. 271 OR termination by tenant --medium
```

```
/doc-analyze /docs/contracts/lease-2022.pdf
```

**Phase 3: Interaction (15 minutes)**
```
The lease doesn't have a force majeure clause. Research whether
hardship (Notlage) under Art. 271 OR can be invoked even without
an explicit clause.
```

```
Are there any Zurich cantonal court decisions on COVID-19
commercial lease hardship?
```

**Phase 4: Adversarial Analysis (10 minutes)**
```
/adversary Client's position: The COVID-19 revenue loss constitutes
hardship (Notlage) that justifies early termination under Art. 271 OR,
even without a force majeure clause in the lease.
```

Output reveals:
- Weakness: Swiss courts interpret hardship narrowly
- Counter-argument: Hardship typically requires impossibility, not just difficulty
- Risk: Court unlikely to grant termination; more likely rent reduction

**Phase 5: Final Summary (20 minutes)**
```
/draft legal opinion for client on commercial lease termination options,
including risk assessment and recommended approach
```

Validates citations:
```
/cite BGE 129 III 145
```

**Total Time: ~1.5-2 hours** for thorough analysis with all framework phases.

---

## ✅ Framework Checklist

Before starting any matter, verify:

- [ ] I have created a case-specific directory
- [ ] I have set up CLAUDE.md with matter context
- [ ] I understand when to use full framework vs. quick commands
- [ ] I know how to invoke agents via commands
- [ ] I understand the three mode options (--short, --medium, --long)
- [ ] I can chain commands in natural language
- [ ] I know how to refer to documents in prompts
- [ ] I understand the 5-phase framework flow

---

**Next**: [Briefing Phase Deep Dive](./briefing-phase.md) →
