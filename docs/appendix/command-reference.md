# Appendix A: Command Quick Reference

> **All 19 commands at a glance**

---

## Intelligent Gateway

| Command | Purpose | Example |
|---------|---------|---------|
| `/legal` | Intelligent gateway — analyzes intent, routes to the appropriate specialist agent, and manages multi-step legal workflows. Use `--refine` to transform vague queries first. | `/legal I need to assess our exposure under Art. 97 OR for late delivery` |

---

## Core Research Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/research` | Search Swiss legal precedents and compile research memoranda. Supports BGE/ATF/DTF databases, doctrine references, and cross-jurisdictional analysis. | `/research Art. 97 OR contractual liability` |
| `/cite` | Verify and format Swiss legal citations across all four national languages (BGE/ATF/DTF formats). | `/cite BGE 147 IV 73` |
| `/precedent` | Search and analyze BGE/ATF/DTF precedents with precedent chain tracking and evolution analysis. | `/precedent BGE 145 III 445` |
| `/validate` | Validate Swiss legal citations in bulk — check format, existence, and cross-language consistency. | `/validate --document` |

---

## Jurisdiction Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/federal` | Analyze a legal question under federal Swiss law (ZGB, OR, StGB, BV, and related federal statutes). | `/federal Art. 97 OR limitation period` |
| `/cantonal` | Analyze a legal question under cantonal law for a specific canton. | `/cantonal ZH Commercial court jurisdiction for contract disputes over CHF 30k` |

---

## Strategy & Analysis Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/strategy` | Develop litigation strategy with risk assessment, cost-benefit analysis, and procedural pathway evaluation. | `/strategy Breach of contract claim, CHF 100K damages` |
| `/adversarial` | Run three-agent adversarial analysis — advocate builds the case, adversary challenges it, judicial analyst synthesizes. | `/adversarial My argument: limitation period is 10 years` |
| `/briefing` | Structured pre-execution briefing — assembles a specialist panel, collects case context, and builds an execution plan before agents start working. | `/briefing Client wants to sue for breach of distribution agreement` |

---

## Document Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/draft` | Draft Swiss legal documents including contracts, court briefs, legal opinions, and memoranda with proper citation formatting. | `/draft Employment contract for a software engineer in Geneva, bilingual DE/FR` |
| `/doc-analyze` | Analyze Swiss legal documents — identify legal issues, extract key clauses, verify citations, assess compliance. Use `@file.pdf` to reference uploaded documents. | `/doc-analyze @contract.pdf Review this commercial lease agreement` |
| `/translate` | Translate Swiss legal documents between DE, FR, IT, and EN while preserving legal terminology precision. | `/translate [text] DE to FR` |
| `/summarize` | Consolidate multi-agent pipeline output — deduplicate disclaimers, terminology, and citations with length control. | `/summarize --short` |

---

## Query Refinement

| Command | Purpose | Example |
|---------|---------|---------|
| `/refine` | Transform vague legal queries into structured prompts through Socratic dialogue. Recommends optimal workflows and introduces Swiss legal terminology. | `/refine I have problems with my landlord` |

---

## Workflow Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/workflow` | Define and execute multi-agent legal workflows (due diligence, litigation prep, contract lifecycle, real estate closing). | `/workflow litigation-prep Personal injury claim against manufacturer` |

---

## Utility Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/setup` | Check MCP server connectivity and display status for all 7 servers. | `/setup` |
| `/version` | Display plugin version, installed components, and system status. | `/version` |
| `/help` | Show complete command reference, available agents, skills, and usage examples. | `/help /research` |

---

## Command Modifiers

These can be appended to most commands:

| Modifier | Effect | Example |
|----------|--------|---------|
| `--short` | Brief output | `/research [topic] --short` |
| `--medium` | Standard output | `/research [topic] --medium` |
| `--long` | Detailed output | `/research [topic] --long` |
| `--de` | German language focus | `/cite BGE 147 IV 73 --de` |
| `--fr` | French language focus | `/cite BGE 147 IV 73 --fr` |
| `--resume` | Resume from previous session | `/briefing --resume` |
| `--explain` | Explain reasoning | `/strategy [case] --explain` |

---

## Most Common Commands for Daily Work

**Start here for most tasks:**

1. **Quick citation check**: `/cite [citation]`
2. **Research a legal issue**: `/research [topic]`
3. **Challenge your position**: `/adversarial [your argument]`
4. **Draft a document**: `/draft [document type]`
5. **Plan complex work**: `/briefing [describe matter]`
6. **Vague query? Start here**: `/refine [your question]`

---

## Command Decision Flowchart

```
I need to...
│
├─ Verify a citation → /cite
│
├─ Research law → /research
│
├─ Challenge my argument → /adversarial
│
├─ Assess case strength → /strategy
│
├─ Draft a document → /draft
│
├─ Analyze a document → /doc-analyze
│
├─ Translate legal text → /translate
│
├─ Plan complex work → /briefing
│
├─ Refine vague query → /refine
│
├─ Federal law question → /federal
│
├─ Cantonal law question → /cantonal
│
└─ Multi-step pipeline → /workflow or /legal
```

---

## See Also

- **[Cheatsheet](./cheatsheet.md)** — Skills, agents, MCP servers, and workflows
- **[Terminology Glossary](./terminology.md)** — Swiss legal terms
- **[Troubleshooting](./troubleshooting.md)** — When commands don't work
- **[Team Features](./team-features.md)** — Collaboration commands deep-dive
