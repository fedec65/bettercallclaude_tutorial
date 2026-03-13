# Appendix A: Command Quick Reference

> **All 18 commands at a glance**

---

## Core Research Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/cite` | Look up and verify citations | `/cite BGE 147 IV 73` |
| `/research` | Search legal databases | `/research Art. 97 OR contractual liability` |
| `/translate` | Translate legal texts | `/translate [text] DE to FR` |

---

## Strategy & Analysis Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/strategy` | Develop case strategy | `/strategy Breach of contract claim, CHF 100K damages` |
| `/adversary` | Challenge your position | `/adversary My argument: limitation period is 10 years` |
| `/briefing` | Structured intake and planning | `/briefing Client wants to sue for breach of distribution agreement` |

---

## Document Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/draft` | Generate documents | `/draft client memo on termination rights` |
| `/analyze` | Analyze documents | `/analyze [contract text] for risks` |

---

## Reference & Lookup Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/statute` | Look up statutory provisions | `/statute OR Art. 97` |
| `/precedent` | Find related precedents | `/precedent BGE 145 III 445` |
| `/glossary` | Define legal terms | `/glossary Notlage Swiss law` |

---

## Workflow Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/workflow` | Execute predefined workflows | `/workflow litigation-prep` |
| `/plan` | Create execution plan | `/plan Research and draft legal opinion` |
| `/execute` | Execute a plan | `/execute [plan from /plan]` |

---

## Team & Collaboration Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/team` | Team orchestration | `/team research parallel streams` |
| `/delegate` | Delegate to specialists | `/delegate research to swiss-legal-researcher` |
| `/sync` | Team synchronization | `/sync Update CLAUDE.md with findings` |

---

## Utility Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/help` | Get help | `/help /research` |
| `/config` | View/ modify settings | `/config privacy strict` |
| `/status` | Check current state | `/status` |
| `/resume` | Resume previous work | `/resume --last` |

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
3. **Challenge your position**: `/adversary [your argument]`
4. **Draft a document**: `/draft [document type]`
5. **Plan complex work**: `/briefing [describe matter]`

---

## Command Decision Flowchart

```
I need to...
│
├─ Verify a citation → /cite
│
├─ Research law → /research
│
├─ Challenge my argument → /adversary
│
├─ Assess case strength → /strategy
│
├─ Draft a document → /draft
│
├─ Analyze a document → /analyze
│
├─ Translate legal text → /translate
│
├─ Plan complex work → /briefing
│
├─ Look up a statute → /statute
│
└─ Find related cases → /precedent
```

---

## See Also

- **[Terminology Glossary](./terminology.md)** - Swiss legal terms
- **[Troubleshooting](./troubleshooting.md)** - When commands don't work
- **[Team Features](./team-features.md)** - Collaboration commands deep-dive
