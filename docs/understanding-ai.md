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

> 🏗️ **Architecture Note**: Commands are now thin entry points (typically 5-13 lines) that delegate to **skills** — the single source of truth. Domain methodology has migrated from 13 commands into 14 skills. Infrastructure commands (`legal`, `setup`, `help`, `workflow`, `briefing`, `version`) remain full-featured, while domain commands act as wrappers.

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

### Key Skills (14 Total)

| Skill | What It Provides | Best For |
|-------|-------------------|---------|
| `swiss-legal-research` | Comprehensive legal research | Deep precedent analysis, statutory interpretation |
| `swiss-legal-strategy` | Case strategy development | Litigation planning, risk assessment |
| `swiss-legal-drafting` | Document generation | Contracts, opinions, briefs, correspondence |
| `swiss-legal-adversarial` | Counter-argument analysis | Stress-testing positions, finding weaknesses |
| `swiss-legal-citations` | Citation verification | Verifying BGE/ATF/DTF references |
| `swiss-legal-briefing` | Structured intake by specialist panel | Starting complex matters, due diligence, litigation prep |
| `swiss-legal-workflow` | Multi-agent workflow execution | Due diligence, litigation prep, contract lifecycle |
| `swiss-legal-translation` | Legal text translation | Cross-language work with terminology preservation |
| `swiss-document-analysis` | Document review and extraction | Contract analysis, issue identification |
| `output-summarization` | Multi-agent output consolidation | Deduplicating pipeline outputs, length control |
| `legal-query-refinement` | Query structuring via Socratic dialogue | Clarifying vague legal questions |
| `swiss-federal-analysis` | Federal law analysis | ZGB, OR, StGB, BV research |
| `swiss-cantonal-analysis` | Cantonal law analysis | All 26 cantons |
| `swiss-precedent-analysis` | Precedent chain tracking | BGE/ATF/DTF evolution analysis |

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
- **Command**: `/cite BGE 147 IV 73` → Delegates to `swiss-legal-citations` skill → Returns the citation
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
| **OnlineKommentar.ch** | Legal commentaries | Academic database |
| **opencaselaw.ch** | Case law, citation graphs, appeal chains | Public database |
| **Ollama (local)** | AI processing | Your machine (privacy mode) |

### Privacy: What Stays Local vs. Cloud

| Mode | What Happens | When to Use |
|------|--------------|-------------|
| **Strict** | All processing on your machine | Highly sensitive matters, client confidentiality critical |
| **Balanced** | Most local, some cloud for research | Standard matters with some sensitivity |
| **Cloud** | Full cloud access | Non-sensitive matters, speed priority |

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
| **strict** | Local processing only, no cloud APIs | Attorney-client communications, highly sensitive |
| **balanced** | Smart routing: sensitive→local, other→cloud | Most matters, flexible security |
| **cloud** | Full capabilities, all databases | Non-sensitive matters, speed priority |

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
└──────────────┴──────────┴─────────────────────────────────────┘
```

**Key Insight**: Commands are your tools, skills orchest specialists, who access databases through connectors. Hooks ensure everything stays private.

---

**Next**: [Building Confidence](./building-confidence.md) →
