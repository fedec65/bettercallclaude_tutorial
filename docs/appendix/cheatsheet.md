# BetterCallClaude Cheatsheet

> **Complete Reference** — Skills, Commands, Agents, Hooks, MCP Servers, and Workflows

---

## Quick Navigation

| [Skills](#skills) | [Commands](#commands) | [Agents](#agents) | [Hooks](#hooks) | [MCP Servers](#mcp-servers) | [Workflows](#building-workflows) |
|:------------------:|:--------------------:|:----------------:|:-------------:|:-------------------------:|:---------------------------:|

---

## What Are These Components?

BetterCallClaude is built on an ecosystem of interconnected components that work together to handle Swiss legal work:

```
┌─────────────────────────────────────────────────────────────────────┐
│                         YOUR REQUEST                                │
│                     "Find BGE 147 IV 73"                            │
└─────────────────────────┬───────────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────────────┐
│                        SKILLS (Auto-Activate)                        │
│   swiss-legal-research • swiss-citation-formats • privacy-routing  │
└─────────────────────────┬───────────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────────────┐
│                         COMMANDS (You Type)                          │
│              /bettercallclaude:research "BGE 147 IV 73"             │
└─────────────────────────┬───────────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────────────┐
│                       AGENTS (Specialists)                           │
│   researcher → citation → compliance → drafter → strategist        │
└─────────────────────────┬───────────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────────────┐
│                      MCP SERVERS (Data Sources)                      │
│    entscheidsuche → bge-search → fedlex-sparql → onlinekommentar    │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Skills

Skills **auto-activate** based on what you're asking. You don't invoke them directly—they detect patterns in your requests and activate automatically.

| Skill | Auto-Activates When |
|-------|---------------------|
| `swiss-legal-research` | Legal research queries, BGE/ATF/DTF references, statute analysis |
| `swiss-legal-drafting` | Document creation, contract drafting, court submissions |
| `swiss-legal-strategy` | Litigation planning, risk assessment, case strategy questions |
| `swiss-citation-formats` | Citation formatting, BGE/ATF/DTF references in text |
| `swiss-jurisdictions` | Canton-specific questions, federal vs. cantonal law routing |
| `privacy-routing` | Sensitive client data patterns detected (Anwaltsgeheimnis) |
| `federal-law` | Federal statute analysis, BV/ZGB/OR/StGB questions |
| `cantonal-law` | Canton-specific legal questions |
| `multilingual-law` | Multi-language legal terminology needs (DE/FR/IT/EN) |
| `legal-briefing` | Complex queries needing structured pre-execution intake |

### How Skills Work

```
You: "What does Art. 27 OR say about mistake?"
     │
     ▼
[privacy-routing] → No sensitive data detected
     │
     ▼
[swiss-legal-research] → Federal statute query detected
     │
     ▼
[federal-law] → OR is federal law
     │
     ▼
→ Activates researcher agent → Queries fedlex-sparql MCP
```

---

## Commands

Commands are explicit instructions you type. They give you direct control over specific functions.

### Core Commands

| Command | Description |
|---------|-------------|
| `/bettercallclaude:legal` | **Intelligent gateway** — Auto-routes complex queries to optimal workflow |
| `/bettercallclaude:research` | Search BGE/ATF/DTF decisions, statutes, and legal sources |
| `/bettercallclaude:strategy` | Litigation strategy analysis, risk assessment, case planning |
| `/bettercallclaude:draft` | Draft legal documents (contracts, submissions, opinions) |

### Jurisdiction Commands

| Command | Description |
|---------|-------------|
| `/bettercallclaude:federal` | **Force federal law mode** — Use when you know the matter is federal |
| `/bettercallclaude:cantonal` | **Force cantonal law mode** — Use when you know the matter is cantonal |

### Analysis Commands

| Command | Description |
|---------|-------------|
| `/bettercallclaude:doc-analyze` | Analyze uploaded legal documents for key issues |
| `/bettercallclaude:precedent` | Search and analyze BGE precedent chains |
| `/bettercallclaude:validate` | Batch validate citations in documents |
| `/bettercallclaude:adversarial` | **Three-agent adversarial analysis** — Stress-test your legal position |

### Workflow Commands

| Command | Description |
|---------|-------------|
| `/bettercallclaude:workflow` | Define and execute multi-step pipelines |
| `/bettercallclaude:briefing` | Structured pre-execution briefing for complex matters |
| `/bettercallclaude:translate` | Translate legal documents (DE/FR/IT/EN) |

### Reference Commands

| Command | Description |
|---------|-------------|
| `/bettercallclaude:cite` | Format and verify citations |
| `/bettercallclaude:setup` | Check MCP server status and configuration |
| `/bettercallclaude:version` | Display plugin version information |
| `/bettercallclaude:summarize` | Consolidate multi-agent pipeline output |
| `/bettercallclaude:help` | Display command reference |

---

## Agents

Agents are specialized AI assistants. The framework automatically routes your requests to the right agents based on context.

### Core Pipeline Agents

These agents handle the most common legal tasks:

| Agent | Domain | When It Activates |
|-------|--------|-------------------|
| `researcher` | Swiss legal research, BGE/ATF/DTF search | Any research query |
| `strategist` | Litigation strategy, risk assessment | Case planning, risk questions |
| `drafter` | Legal document drafting | Document creation requests |
| `citation` | BGE citation verification | Citation-heavy work |
| `compliance` | FINMA, AML/KYC compliance | Regulatory questions |

### Specialized Domain Agents

These agents handle specific legal domains:

| Agent | Domain | Example Use |
|-------|--------|-------------|
| `data-protection` | GDPR, nDSG/FADP privacy | DPA analysis, DPIA |
| `risk` | Case outcome probability | Settlement evaluation |
| `procedure` | ZPO/StPO deadlines | Procedural planning |
| `translator` | DE/FR/IT legal terminology | Multi-language documents |
| `fiscal` | Tax law, DTAs | Tax planning, disputes |
| `corporate` | AG/GmbH governance, M&A | Company law matters |
| `cantonal` | All 26 Swiss cantonal systems | Canton-specific research |
| `realestate` | Property law, Grundbuch | Real estate transactions |

### Three-Agent Analysis System

For balanced legal analysis, three agents work together:

| Agent | Role | Output |
|-------|------|--------|
| `advocate` | Builds **strongest case** for your position | Arguments, precedents, evidence |
| `adversary` | **Challenges and stress-tests** your position | Weaknesses, counter-arguments, risks |
| `judicial` | **Synthesizes balanced assessment** | Objective evaluation, recommendations |

### Orchestration Agents

| Agent | Role |
|-------|------|
| `briefing` | Pre-execution intake and context gathering |
| `orchestrator` | Multi-agent coordination |
| `summarizer` | Pipeline output consolidation |

---

## Hooks

Hooks are automatic triggers that run in the background. They protect confidentiality without you having to think about it.

### Privacy Routing Hook

| Hook | Purpose | Protection |
|------|---------|------------|
| `privacy-routing` | Detects attorney-client privilege content | **Anwaltsgeheimnis** (Art. 321 StGB) |

#### How It Works

```
Your message contains: "My client Müller wants to..."
                              │
                              ▼
[privacy-routing hook scans for patterns]
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
        ▼                     ▼                     ▼
   [No sensitive]      [Client names]        [Case details]
        │                     │                     │
        ▼                     ▼                     ▼
   Normal cloud       → Redacted or      → Local Ollama
   processing            routed              processing
```

#### Privacy Modes

| Mode | Description | Use When |
|------|-------------|----------|
| **strict** | All privileged content → local Ollama only | Maximum confidentiality required |
| **balanced** | Smart routing based on content analysis | Default mode (recommended) |
| **cloud** | Explicit opt-out of local processing | Non-sensitive work only |

#### Pattern Detection (Multi-Lingual)

The hook detects privilege indicators in German, French, and Italian:

| Language | Patterns Detected |
|----------|-------------------|
| **DE** | Anwaltsgeheimnis, streng vertraulich, mandant, klientel |
| **FR** | secret professionnel, strictement confidentiel, client |
| **IT** | segreto professionale, strettamente confidenziale, cliente |

---

## MCP Servers

MCP servers are the data connections. They connect BetterCallClaude to Swiss legal databases and services.

| Server | Purpose | Data Source |
|--------|---------|-------------|
| `entscheidsuche` | Swiss court decision search | entscheidsuche.ch API |
| `bge-search` | Federal Supreme Court decisions | BGE/ATF/DTF database |
| `legal-citations` | Citation verification and formatting | Fedlex + internal |
| `fedlex-sparql` | Federal legislation database | admin.ch/fedlex |
| `onlinekommentar` | Swiss legal commentaries | onlinekommentar.ch |
| `ollama` | Local LLM for privacy | Your machine |

### What Each Server Provides

```
┌─────────────────────────────────────────────────────────────────┐
│                    entscheidsuche                                │
│  • Full-text search of Swiss court decisions                    │
│  • Federal + cantonal coverage                                   │
│  • Similar case finding                                          │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                      bge-search                                  │
│  • BGE/ATF/DTF decision retrieval by citation                    │
│  • Chamber filtering (I-V)                                       │
│  • Legal area classification                                     │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                    legal-citations                               │
│  • Citation format conversion (DE/FR/IT/EN)                      │
│  • Statute article lookup                                        │
│  • Version comparison over time                                  │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                     fedlex-sparql                                │
│  • Official federal legislation                                  │
│  • Article text retrieval                                        │
│  • Cross-references and amendments                               │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                   onlinekommentar                                │
│  • Scholarly commentary on Swiss law                             │
│  • Article-specific analysis                                     │
│  • Academic references                                           │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                        ollama                                    │
│  • Local LLM processing                                          │
│  • Privacy-preserving AI                                         │
│  • No cloud data transmission                                    │
└─────────────────────────────────────────────────────────────────┘
```

---

## Building Workflows

Workflows chain multiple components together to handle complex legal tasks.

### Natural Language Chaining

You can describe workflows in plain language:

```
"Research BGE precedents on Art. 27 OR mistake,
then draft a memo summarizing the key findings,
and validate all citations"
```

This automatically chains:
1. **Research** → BGE search for Art. 27 OR cases
2. **Draft** → Memo creation with findings
3. **Validate** → Citation verification

### Sequential vs Parallel Operations

```
SEQUENTIAL (one after another):
  research → analyze → draft → review
  (Each step depends on previous results)

PARALLEL (at the same time):
  ├── Federal law research
  ├── Cantonal law research
  └── Precedent search
  (Independent searches run simultaneously)
```

### Predefined Workflows

| Workflow | Steps | Use For |
|----------|-------|---------|
| `litigation-prep` | Research → Strategy → Draft → Review | Case preparation |
| `due-diligence` | Multi-domain parallel analysis | M&A, transactions |
| `contract-lifecycle` | Draft → Review → Validate → Translate | Contract management |

### Example Workflow Constructions

#### Due Diligence Workflow
```
/bettercallclaude:workflow due-diligence --target "Acme AG acquisition"

Parallel execution:
├── Corporate structure (corporate agent)
├── Compliance check (compliance agent)
├── Litigation history (researcher agent)
└── Real estate holdings (realestate agent)

Then sequential:
→ Risk synthesis (risk agent)
→ Summary report (summarizer agent)
```

#### Litigation Preparation Workflow
```
/bettercallclaude:workflow litigation-prep --matter "Breach of contract"

Sequential:
1. /bettercallclaude:research "contract breach BGE precedents"
2. /bettercallclaude:strategy --analyze
3. /bettercallclaude:adversarial --stress-test
4. /bettercallclaude:draft "Klageentwurf"
5. /bettercallclaude:validate --all-citations
```

#### Contract Lifecycle Workflow
```
/bettercallclaude:workflow contract-lifecycle --type "NDA"

1. Draft initial (drafter agent)
2. Adversarial review (adversary → advocate → judicial)
3. Citation validation (citation agent)
4. Multi-language version (translator agent)
```

---

## Quick Reference Card

### Most Common Commands (Daily Use)

| I want to... | Command |
|--------------|---------|
| Look up a BGE decision | `/bettercallclaude:research "BGE 147 IV 73"` |
| Find similar cases | `/bettercallclaude:precedent --similar "fact pattern"` |
| Draft a document | `/bettercallclaude:draft "Klageentwurf"` |
| Analyze my position | `/bettercallclaude:adversarial "my argument"` |
| Validate citations | `/bettercallclaude:validate --document` |
| Check a statute | `/bettercallclaude:research "Art. 97 OR"` |

### Decision Flowchart

```
What do you need?
       │
       ├── Look up something ──→ /bettercallclaude:research
       │
       ├── Create a document ──→ /bettercallclaude:draft
       │
       ├── Plan a case ────────→ /bettercallclaude:strategy
       │
       ├── Check citations ────→ /bettercallclaude:validate
       │
       ├── Stress-test position → /bettercallclaude:adversarial
       │
       └── Complex task ────────→ /bettercallclaude:workflow
                                   or
                                   /bettercallclaude:legal
```

### Jurisdiction Quick Check

| Legal Area | Jurisdiction | Command |
|------------|--------------|---------|
| Contract law (OR) | Federal | `/bettercallclaude:federal` |
| Civil procedure (ZPO) | Federal | `/bettercallclaude:federal` |
| Criminal law (StGB) | Federal | `/bettercallclaude:federal` |
| Tenancy law | Cantonal | `/bettercallclaude:cantonal` |
| Construction law | Cantonal | `/bettercallclaude:cantonal` |
| Administrative law | Mixed | Let auto-detect |

### Privacy Quick Reference

| Situation | Mode | How |
|-----------|------|-----|
| General research | balanced | Default (no action needed) |
| Client-specific work | strict | Add `--privacy strict` |
| Non-sensitive drafting | cloud | Add `--privacy cloud` |
| Unsure | balanced | Default is safe |

---

## Related Documentation

- **[Command Reference](./command-reference.md)** — Detailed command documentation
- **[Mastering Workflows](../mastering-workflows.md)** — Deep dive into workflow design
- **[Troubleshooting](./troubleshooting.md)** — When things don't work as expected
- **[Privacy & Responsibility](./privacy-responsibility.md)** — Professional obligations with AI

---

*Last updated: March 2026*
