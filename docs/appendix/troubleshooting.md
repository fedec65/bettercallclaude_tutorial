# Appendix C & D: Troubleshooting & FAQ

> **When things don't work as expected**

---

## Quick Troubleshooting Guide

### Search & Research Issues

#### "I got no results from my search"

**Possible causes:**
1. Citation format incorrect
2. Search terms too specific
3. Language mismatch (searching in English when DB has German)
4. Database not connected

**Try this:**
```
# 1. Fix citation format
/cite BGE 147 IV 73    # CORRECT
/cite 147 IV 73         # WRONG (missing BGE)

# 2. Broaden search terms
/research contractual liability damages limitation period Switzerland    # Too specific
/research Art. 97 OR damages                                          # Better

# 3. Try multiple languages
/research vertragshaftung schadenersatz    # German terms
/research responsabilité contractuelle     # French terms

# 4. Check database status
/status    # Verify MCP servers connected
```

---

#### "The citation format was wrong"

**Symptoms:**
- AI output shows non-existent citations
- Citation looks unusual (wrong chamber codes, impossible page numbers)

**Immediate fix:**
```
/cite [the suspicious citation]
```

**If it doesn't exist:**
1. Note the error
2. Search for the correct case using case name or topic
3. Verify the correct citation

**Prevention:**
- Always verify AI-generated citations before using in documents
- Use `/cite` on any citation you plan to rely on

---

#### "The AI misunderstood my legal question"

**Symptoms:**
- Response addresses wrong legal issue
- AI focused on peripheral issues, not core question

**Try this:**
```
# More specific rephrase
/research [specific legal question]

# Example transformation:
# Vague:
/research can I terminate the contract

# Better:
/research termination rights Art. 271d OR commercial lease hardship Switzerland
```

---

### Connection & Technical Issues

#### "MCP server connection failed"

**Symptoms:**
- Error message about connection failure
- Searches return no results when they should

**Checklist:**
1. Internet connection working?
2. COWORK platform online?
3. BetterCallClaude plugin enabled?
4. MCP server status?

```
/config    # Check configuration
/status    # Check server status
```

**If servers offline:**
- Try again in a few minutes
- Check COWORK status page
- Contact IT support if persistent

---

#### "Privacy hook blocked my query"

**Symptoms:**
- Query rejected with privacy warning
- "Blocked by privacy protection" message

**This is expected behavior when:**
- Query contains client names
- Query contains privileged information
- Query contains sensitive case details

**Solutions:**
```
# Option 1: Anonymize your query
# Instead of:
/research Smith v. ABC Corp employment termination

# Use:
/research wrongful termination employment law Switzerland

# Option 2: Switch privacy mode (if appropriate)
/config privacy balanced    # Less restrictive (still protects privileged info)

# Option 3: Use local-only mode for sensitive work
/config privacy strict    # Maximum protection
```

---

### Output Quality Issues

#### "Output is too long/short"

**Control output length:**
```
# For brief output
/research [topic] --short

# For standard output
/research [topic] --medium

# For detailed output
/research [topic] --long
```

---

#### "I lost context from yesterday"

**Symptoms:**
- BetterCallClaude doesn't remember previous conversation
- Research is repeated unnecessarily

**Check:**
1. Are you in the correct directory?
2. Does CLAUDE.md exist and have content?
3. Is CLAUDE.md properly formatted?

```
# Check current directory
pwd

# Verify CLAUDE.md exists
ls -la CLAUDE.md

# Resume from previous session
/briefing --resume
```

**Prevention:**
- Always work in matter-specific directories
- Keep CLAUDE.md updated with key developments
- Use `--resume` when continuing work

---

## Frequently Asked Questions

### General

**Q: Is BetterCallClaude a lawyer?**
A: No. It's a research and drafting tool. You remain responsible for all legal work.

**Q: Can I use BetterCallClaude for confidential matters?**
A: Yes, with appropriate privacy settings. See [Privacy & Responsibility](./privacy-responsibility.md).

**Q: Which cantons are covered?**
A: All 26 Swiss cantons, plus federal law.

---

### Research

**Q: How current is the case law database?**
A: Databases are updated regularly. For the most recent decisions, check official sources directly.

**Q: Can BetterCallClaude access foreign law?**
A: Primary focus is Swiss law. Some comparative law capabilities exist, but verify foreign law independently.

**Q: What if I need to research older decisions (before 2000)?**
A: Many older decisions are available. If not found digitally, try the official BGE print volumes.

---

### Citations

**Q: Why do I get different results for BGE vs. ATF?**
A: They're the same decisions in different languages. BGE = German, ATF = French, DTF = Italian.

**Q: How do I cite a cantonal decision?**
A: Format varies by canton. BetterCallClaude will help format correctly when you provide case details.

---

### Documents

**Q: Can BetterCallClaude draft complete legal documents?**
A: Yes, but always review for accuracy, completeness, and professional judgment before use.

**Q: What languages can BetterCallClaude draft in?**
A: German, French, Italian, and English. For official documents, verify terminology.

---

### Privacy

**Q: What happens to my queries?**
A: Depends on privacy mode. See [Privacy & Responsibility](./privacy-responsibility.md) for details.

**Q: Can I use this for Anwaltsgeheimnis-protected matters?**
A: Yes, with strict privacy mode. Client confidences are protected.

---

## Error Messages Reference

| Error | Meaning | Solution |
|-------|---------|----------|
| "MCP connection timeout" | Server not responding | Check internet, retry, contact support |
| "Privacy hook triggered" | Query contains sensitive data | Anonymize query or adjust privacy mode |
| "No results found" | Search returned empty | Broaden terms, try different language |
| "Citation not found" | Citation doesn't exist | Verify format, search by topic |
| "CLAUDE.md not found" | Context file missing | Create CLAUDE.md in current directory |
| "Rate limit exceeded" | Too many requests | Wait a moment, then retry |

---

## Getting Help

**Built-in help:**
```
/help                # General help
/help /research     # Help with specific command
```

**Report bugs:**
- Include exact error message
- Include steps to reproduce
- Note your configuration (privacy mode, connected servers)

---

## See Also

- **[Command Reference](./command-reference.md)** - Full command list
- **[Privacy & Responsibility](./privacy-responsibility.md)** - Privacy deep-dive
- **[CLAUDE.md Templates](./claude-md-templates.md)** - Fix context issues
