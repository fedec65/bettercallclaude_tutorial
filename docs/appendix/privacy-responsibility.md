# Appendix F: Privacy & Professional Responsibility

> **Understanding Anwaltsgeheimnis and data protection**

---

## The Core Principle: Anwaltsgeheimnis (Art. 321 StGB)

**Anwaltsgeheimnis** (attorney-client privilege under Art. 321 StGB) is fundamental to Swiss legal practice. BetterCallClaude is designed to protect this privilege.

### What Art. 321 StGB Protects

Attorneys may not disclose:
- Client confidences shared in professional capacity
- Client identity (in certain circumstances)
- Facts learned through professional relationship
- Documents received from client

**This applies to:**
- All communications with clients
- All documents related to client matters
- All information about client's legal situation

---

## BetterCallClaude Privacy Architecture

### Privacy Modes

BetterCallClaude offers three privacy modes:

| Mode | Cloud Access | Local-Only | Use When |
|------|--------------|------------|----------|
| **Strict** | Never | Always | Highly sensitive matters, Anwaltsgeheimnis critical |
| **Balanced** | Limited | Core matters | Standard legal work, some cloud queries acceptable |
| **Cloud** | Full | Rarely | Non-sensitive matters, research queries, general work |

### How Each Mode Works

**Strict Mode:**
- All queries processed locally (via Ollama)
- No data leaves your machine
- Maximum privilege protection
- May be slower, less comprehensive results

**Balanced Mode (Default):**
- Privacy hook screens all queries
- Queries with client data → local processing
- General research queries → cloud processing
- Good balance of protection and capability

**Cloud Mode:**
- Full access to cloud capabilities
- Privacy hook still blocks obvious privileged info
- Best for non-sensitive matters
- Fastest, most comprehensive results

---

## Privacy Hooks: Automatic Protection

### What Privacy Hooks Do

Privacy hooks automatically scan your queries for:
- Client names
- Specific case details
- Privileged communications
- Identifying information

**When triggered:**
- Query is blocked
- You're notified why
- Suggested anonymized alternative

### Example

**You type:**
```
/research Mueller GmbH's contract with ABC Corp regarding the 2023 supply agreement breach
```

**Privacy hook response:**
```
⚠️ Privacy Protection Triggered

This query contains potentially identifying information:
- Party names: "Mueller GmbH", "ABC Corp"
- Specific matter: "2023 supply agreement breach"

Suggested anonymized query:
/research supply agreement breach Swiss law limitation period damages

To proceed with original query, switch to cloud mode:
/config privacy cloud
```

---

## Data Handling by Mode

### What Happens to Your Data

| Data Type | Strict Mode | Balanced Mode | Cloud Mode |
|-----------|-------------|----------------|-------------|
| Query text | Local only | Screened, routed appropriately | Sent to cloud |
| Matter context (CLAUDE.md) | Never leaves local | Never leaves local | May be referenced in cloud queries |
| Research results | Local generation | Mixed sources | Primarily cloud-generated |
| Document drafts | Local generation | Local generation | Local generation |

### MCP Server Data Handling

| MCP Server | Data Sent | Privacy Mode Impact |
|------------|-----------|-------------------|
| **BGE/ATF/DTF Search** | Citation queries | All modes: queries sent to entscheidsuche.ch |
| **Fedlex SPARQL** | Statute queries | All modes: queries sent to Fedlex |
| **OnlineKommentar** | Commentary queries | All modes: queries sent to platform |
| **Ollama (Local)** | Everything | Strict mode: all processing local |

**Key insight**: Database queries (BGE, Fedlex) always go to external sources—this is public legal data, not privileged information.

---

## Professional Responsibility Checklist

### Before Using BetterCallClaude on a Matter

- [ ] Assessed sensitivity level of matter
- [ ] Selected appropriate privacy mode
- [ ] Client matter is in dedicated directory
- [ ] CLAUDE.md contains only necessary identifying info

### During Use

- [ ] Anonymizing queries where possible
- [ ] Not including client names in searches
- [ ] Using matter codes instead of names in CLAUDE.md
- [ ] Reviewing AI output before client delivery

### After Use

- [ ] AI output validated for accuracy
- [ ] Citations verified independently
- [ ] Professional judgment applied to all recommendations
- [ ] Documents reviewed before sending to client

---

## Disclaimer (from BetterCallClaude README)

> **IMPORTANT**: BetterCallClaude is a legal research and drafting tool, not a lawyer. While it can assist with legal research, drafting, and analysis, it does not provide legal advice and cannot replace professional legal judgment.
>
> **All output must be reviewed by a qualified legal professional** before use in legal proceedings or client advice. The tool may produce errors, including:
> - Incorrect citations (hallucinated cases that don't exist)
> - Outdated legal interpretations
> - Misunderstanding of nuanced legal distinctions
> - Incomplete analysis missing relevant precedents
>
> **Users are responsible for**:
> - Verifying all citations independently
> - Validating legal analysis against current law
> - Applying professional judgment to all output
> - Ensuring compliance with professional obligations (Anwaltsgeheimnis, etc.)

---

## Best Practices Summary

### DO:
- ✅ Use dedicated matter directories
- ✅ Anonymize queries where possible
- ✅ Select appropriate privacy mode
- ✅ Verify all AI output
- ✅ Maintain professional judgment

### DON'T:
- ❌ Include client names in searches
- ❌ Use cloud mode for highly sensitive matters
- ❌ Send AI output directly to clients without review
- ❌ Rely on citations without verification
- ❌ Assume AI analysis is complete or correct

---

## See Also

- **[Team Features](./team-features.md)** - Privacy in collaborative workflows
- **[Troubleshooting](./troubleshooting.md)** - Privacy hook issues
- **[Quick Start](../quick-start.md)** - Setting up secure workspaces
