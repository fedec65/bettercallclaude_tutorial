# Part 2: Understanding Your AI Assistant

> **Build your mental model without technical overwhelm**

## What You'll Learn

By the end of this section, you will understand:

- What commands are and when to use them
- How skills provide specialized capabilities
- When agents handle your requests directly
- How connectors access Swiss legal databases
- How hooks protect client confidentiality

---

## 2.1 Commands — Your Swiss Army Knife

### What Are Commands?

Think of commands as shortcuts that trigger specific actions. You type `/something`, and something happens.

> 🏗️ **Architecture Note**: Commands are thin entry points (typically 5-13 lines) that delegate to **skills** — the single source of truth. Domain methodology lives in 16 skills. Infrastructure commands (`legal`, `start`, `help`, `workflow`, `briefing`, `version`) remain full-featured, while domain commands act as wrappers. Legal work (research, strategy, drafting, translation, citation, adversarial analysis) stays exclusively inside BetterCallClaude's own agents, skills, and MCP servers (v4.7.0 scope enforcement).

### Most Useful Commands for Daily Work

| Command | What It Does | When to Use |
|---------|--------------|-------------|
| `/cite` | Look up and verify citations | Verifying a BGE reference, finding related decisions |
| `/research` | Search legal databases | Finding precedents, statutory interpretation |
| `/adversarial` | Challenge your position | Stress-testing arguments, finding weaknesses |
| `/strategy` | Develop case strategy | Litigation planning, risk assessment |
| `/draft` | Generate documents | Contracts, opinions, briefs, letters |
| `/translate` | Translate legal texts | Cross-language work, terminology preservation |
| `/briefing` | Structured intake | Complex matters, multi-step work |
| `/refine` | Transform vague queries into structured prompts | Unclear legal questions, need help formulating queries |
| `/legal-5step` | Run full 5-phase pipeline in one command | End-to-end analysis from intake to draft |
| `/legal-timeline` | Build a sourced chronology from case documents | Litigation prep, deadline tracking, fact disputes *(v4.9.5)* |
| `/nda-triage` | Classify NDAs GREEN/YELLOW/RED | Quick NDA screening against your playbook *(v4.8.0)* |
| `/legal-goal` + `/legal-loop` | Define a success condition; a separate judge agent verifies each iteration | Automatic quality verification of deliverables *(v4.9.0)* |
| `/start` | Guided onboarding and playbook creation | First-time setup, non-technical users *(v4.8.1)* |
| `/doctor` | Plain-language connection diagnostics | When something isn't working |
| `/privacy` | Check or change privacy mode | Managing confidentiality settings |

### Decision Guide: Which Command When?

```
I need to...                    Use this command
────────────────────────────────────────────────────────
Verify a citation → /cite
Find precedents → /research
Challenge my argument → /adversarial
Plan litigation → /strategy
Write a document → /draft
Translate text → /translate
Start complex matter → /briefing
Clarify my question → /refine
Run full pipeline → /legal-5step
Build a case timeline → /legal-timeline
Triage an NDA → /nda-triage
Verify quality automatically → /legal-goal, then /legal-loop
Set up the plugin → /start
Diagnose problems → /doctor
Check privacy mode → /privacy
```

### Command Examples

**Citation Lookup:**
```
/cite BGE 147 IV 73
```

**Legal Research:**
```
/research Art. 97 OR contractual liability limitation period
```

**Adversarial Analysis:**
```
/adversarial My argument: The limitation period should be 10 years not 5
```

**Case Strategy:**
```
/strategy Breach of contract claim, seeking damages of CHF 50,000
```

**Prompt Refinement:**
```
/refine I need to research something about contract termination and hardship
```

---

## 2.2 Skills — Specialized Capabilities

### What Are Skills?

Skills are pre-packaged expertise for complex tasks. While commands do one thing well, skills orchest multiple steps for sophisticated outcomes.

### Key Skills (16 Total)

| Skill | What It Provides | Best For |
|-------|-------------------|---------|
| `swiss-legal-research` | Comprehensive legal research incl. federal/cantonal jurisdiction routing | Deep precedent analysis, statutory interpretation |
| `swiss-legal-strategy` | Case strategy development | Litigation planning, risk assessment |
| `swiss-legal-drafting` | Document generation, playbook-aware | Contracts, opinions, briefs, correspondence |
| `adversarial-analysis` | Three-agent counter-argument analysis | Stress-testing positions, finding weaknesses |
| `swiss-citation-formats` | Citation verification and formatting | Verifying BGE/ATF/DTF references |
| `swiss-document-analysis` | Document review, clause deviation classification, NDA triage | Contract analysis, playbook comparison |
| `swiss-legal-translation` | Legal text translation | Cross-language work with terminology preservation |
| `compliance-frameworks` | FINMA, AML/KYC, FINIG/DLT frameworks | Regulatory compliance questions |
| `data-protection-law` | GDPR / nDSG-FADP analysis | Privacy, data processing agreements |
| `privacy-routing` | Privilege detection and routing | Anwaltsgeheimnis protection |
| `legal-intake` | Unified intake: refine (single domain) and briefing (multi-domain panel) | Clarifying queries and starting complex matters |
| `legal-5step-framework` | End-to-end 5-phase pipeline | Intake → Research → Strategy → Adversarial → Draft |
| `legal-evaluator` | Goal-loop verdict engine (0–100 score, worker ≠ judge) | Automated quality verification *(v4.9.0)* |
| `citation-content-verify` | Substantive citation verification against live sources | Anti-hallucination gate for drafts *(v4.9.4)* |
| `legal-chronology` | Sourced case chronology with deadline markers | Case timelines from documents *(v4.9.5)* |
| `shared` | Shared conventions (output-as-file, playbook) used by all skills | Loaded on demand |

> 📦 **Consolidation (v4.8.2)**: `legal-briefing` and `legal-query-refinement` merged into `legal-intake`; `swiss-jurisdictions` became an on-demand canton reference loaded by `swiss-legal-research`; `output-summarization` moved into the `/summarize` command.

### Skills vs. Commands: What's the Difference?

```
COMMANDS                     SKILLS
─────────────────────────────────────────────────────────
Thin entry points (5-13 lines)  Single source of truth
Delegate to skills              Contain domain logic
Immediate routing               Multi-step orchestration
You type shortcuts              AI coordinates specialists
```

**Example:**
- **Command**: `/cite BGE 147 IV 73` → Delegates to `swiss-citation-formats` skill → Returns the citation
- **Skill**: `/bettercallclaude:research Art. 97 OR` → Runs `swiss-legal-research` skill → Searches databases, finds precedents, analyzes patterns, provides structured output

---

## 2.3 Agents — Your Specialist Team

### What Are Agents?

Agents are specialist AI colleagues. Each has expertise in a specific area of Swiss law:

- **Swiss Legal Researcher**: Searches decisions and statutes
- **Swiss Case Strategist**: Develops litigation strategy
- **Swiss Legal Drafter**: Generates legal documents
- **Swiss Legal Adversary**: Challenges positions
- **Citation Specialist**: Verifies and formats citations
- **Procedure Specialist**: Analyzes procedural issues
- **Swiss Judicial Analyst**: Provides neutral synthesis
- **Legal Prompt Engineer**: Transforms vague queries into structured legal prompts via Socratic dialogue
- **Chronology Builder**: Extracts sourced events from case documents for timelines *(v4.9.5)*

### How the Framework Routes Requests

BetterCallClaude uses intelligent routing:

```
Your request → Analysis → Right specialist(s) → Coordinated response
```

**Example:** When you ask about contractual liability, the framework might route your request to:
1. Swiss Legal Researcher (for precedents)
2. Swiss Legal Drafter (if you need a document)
3. Citation Specialist (for references)

### When You'll Interact Directly

Most of the time, you won't directly call agents. The framework routes requests automatically. But you can invoke them directly through skills like `/briefing` which assembles a specialist panel.

---

## 2.4 Connectors (MCP Servers) — The Data Pipelines

### What Are Connectors?

Connectors are pipelines to Swiss legal databases. They connect BetterCallClaude to authoritative sources.

### What Databases You're Accessing

| Database | What It Contains | Access |
|----------|-------------------|-------|
| **BGE/ATF/DTF** | Swiss Federal Supreme Court decisions | Official court database |
| **Fedlex** | Federal statutes and legislation | Government database |
| **entscheidsuche.ch** | Cantonal and federal decisions | Public database |
| **legal-citations** | Citation verification, format conversion, statute lookup | HTTP service |
| **OnlineKommentar.ch** | Legal commentaries | Academic database |
| **opencaselaw.ch** | Case law, citation graphs, appeal chains | Public database |
| **legal-persona** | Swiss-law document intelligence (drafting, strategy, analysis, deadline computation) | HTTP service |
| **tas-jurisprudence** | CAS/TAS sports arbitration decisions | HTTP service |
| **Ollama (local)** | AI processing | Your machine (privacy mode) |

### Privacy: What Stays Local vs. Cloud

| Mode | What Happens | When to Use |
|------|--------------|-------------|
| **Strict** | All processing local via Ollama; blocks all non-Ollama tool calls | Highly sensitive matters, client confidentiality critical |
| **Balanced** | Smart routing: sensitive→local, other→cloud; strong patterns trigger confirmation | Standard matters with some sensitivity (default) |
| **Cloud** | Full cloud access; strong patterns still trigger confirmation | Non-sensitive matters, speed priority |

---

## 2.5 Hooks — Your Privacy Guardian

### What Are Hooks?

Hooks are automatic safety checks that run before BetterCallClaude processes your request. They're like a vigilant colleague who catches potential issues.

### Anwaltsgeheimnis Protection (Art. 321 StGB)

Swiss law protects attorney-client privilege. BetterCallClaude's hooks:

1. **Detect privileged content**: Recogn when you're sharing attorney-client communications
2. **Enforce privacy mode**: Ensure sensitive content uses local processing
3. **Prevent accidental disclosure**: Block requests that could expose privileged information

### Privacy Modes

| Mode | Behavior | Best For |
|------|----------|-------------|
| **strict** | Blocks all non-Ollama tool calls; all processing local | Attorney-client communications, highly sensitive |
| **balanced** | Strong patterns trigger confirmation; weak+context allowed; smart routing | Most matters, flexible security (default) |
| **cloud** | Strong patterns trigger confirmation; weak allowed; full capabilities | Non-sensitive matters, speed priority |

> **v4.6.0 update**: These modes are now actively enforced via plugin `userConfig`. Use `/privacy` to check or change your current mode.
>
> **v4.9.6 update**: A critical bug was fixed where the privacy scan silently did not run on plugin paths containing spaces (e.g. user names with spaces). If you handle privileged client content, make sure you are on v4.9.6 or later.

### When Hooks Might Block Your Request

```
⚠️ "This request involves privileged content. Using strict mode."
```

This is protection, not obstruction. The hook is keeping you compliant with Art. 321 StGB.

---

## 2.6 Context Persistence — Your Case Memory

### How CLAUDE.md Works

BetterCallClaude reads your `CLAUDE.md` file at the start of every conversation in that directory. This provides:

- **Cross-session continuity**: Resume work days later
- **Case context**: AI understands your matter without re-explaining
- **Progress tracking**: Pick up where you left off

### The Mental Model

```
CLAUDE.md = Your case file that the AI remembers
```

Think of it like this:
 You have a physical case file with all your notes. BetterCallClaude reads this file at the start of every session, so it understand your case without you re-explaining.

### Deliverables Are Written as Files (v4.8.1)

Long outputs (memos, research, strategy, drafts, triage reports) are no longer dumped into the chat. They are written as files under:

```text
bcc-output/YYYY-MM-DD-<matter-slug>/
├── 01-research.md
├── 02-strategy.md
├── 03-draft.md
└── sources.md        ← citation trail for every source used
```

The chat shows only a 3–5 line summary; the full numbered deliverables live in the folder. The output folder is configurable in your playbook (`bettercallclaude.local.md`). Case timelines are the one exception: they live in `bcc-output/timeline/` as a living case artifact you update with `--merge`.

### The Local Playbook

Alongside `CLAUDE.md`, BetterCallClaude reads an optional playbook file — `bettercallclaude.local.md` — holding your firm's standing positions: governing law, jurisdiction, liability caps, risk thresholds, escalation rules, citation format, and output language. Templates in all four languages (DE/FR/IT/EN) ship with the plugin, and `/start` can create one with you. Contract review and drafting compare work against these positions automatically.

### When to Update CLAUDE.md vs. Just Chat

| Update CLAUDE.md when... | Just chat when... |
|------------------------|-------------------|
| New key facts emerge | Exploring options |
| Legal issues crystallize | Quick questions |
| Strategy decisions are made | Minor clarifications |
| Important documents arrive | Routine updates |
| Significant developments occur | Ephemeral discussions |

### Example Update to CLAUDE.md

After a significant development, update your CLAUDE.md:

```markdown
## Status
- **Phase**: Post-initial assessment
- **Key Development**: AG has admitted the competitor quote but claims it was exploratory
- **Next Steps**: Draft formal demand letter
 quantify damages
```

---

> ⚠️ **Lost context from yesterday? Check:**
> - Are you in the correct directory? (BetterCallClaude only reads CLAUDE.md in your current directory)
> - Is CLAUDE.md updated? (Review and update with key developments)
> - Try `/briefing --resume` (Continues from where you left off)

---

## 🧠 Mental Model Summary

```
┌─────────────────────────────────────────────────────────────┐
│                    YOUR LEGAL AI ASSISTANT                    │
├──────────────┬──────────────┬─────────────────────────────────────┤
│  Commands   │   Skills   │        Agents & Connectors │
│  (Shortcuts) │ (Expertise) │     (Specialists)  │ (Databases)   │
│             │          │                    │                │
│  /cite      │ /briefing │ Legal Researcher │ BGE/ATF/DTF   │
│  /research   │ /strategy │ Case Strategist   │ Fedlex        │
│  /adversarial  │ /draft   │ Legal Drafter    │ entscheidsuche │
│  /legal-5step  │ /privacy  │                  │               │
└──────────────┴──────────┴─────────────────────────────────────┘
```

**Key Insight**: Commands are your tools, skills orchest specialists, who access databases through connectors. Hooks ensure everything stays private.

---

**Next**: [Building Confidence](./building-confidence.md) →
