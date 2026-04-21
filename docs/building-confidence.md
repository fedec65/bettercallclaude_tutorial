# Part 3: Building Confidence

> **Progressive exercises from simple to complex**

## What You'll Achieve

By the end of this section, you will be able to:

- Perform citation lookups and translations confidently
- Research precedents and statutory interpretation
- Run adversarial analysis on your arguments
- Draft documents with AI assistance

---

## 🎯 Learning Progression

```
Level 1: Simple Lookups (10 min)
        ↓
Level 2: Research & Precedent Analysis (20 min)
        ↓
Level 3: Strategy & Adversarial Analysis (30 min)
        ↓
Level 4: Document Drafting & Review (30 min)
```

---

## Level 1: Simple Lookups and Translations (10 minutes)

### Exercise 1.1: Citation Verification

**Goal**: Verify a BGE citation and understand its components.

**Type:**
```
/cite BGE 145 III 445
```

**What to observe:**
1. **Full citation details**: Court, chamber, date, language
2. **Summary**: What the case is about
3. **Related citations**: Other cases that cite this one

**✅ Success criteria**: You understand what BGE 145 III 445 is about and can locate the full text.

---

### Exercise 1.2: Citation Formatting

**goal**: Format citations in different languages.

**Type:**
```
/cite BGE 147 V 321 in French
```

**What to observe:**
- How the citation format changes (BGE → ATF)
- Whether summary is provided in French
- Link to French version of full text

**✅ Success criteria**: You can format citations for French-speaking clients.

---

### Exercise 1.3: Legal Term Translation

**goal**: Translate legal terms between Swiss national languages.

**Type:**
```
/translate "Vertragshaftung" from German to French and Italian
```

**What to observe:**
1. **Primary translations**: responsabilité contractuelle / responsabilità contrattuale
2. **Context notes**: How the term is used differently in FR vs IT
3. **Related terms**: Other liability concepts

**✅ Success criteria**: You can provide accurate translations for multilingual clients.

---

## Level 2: Research and Precedent Analysis (20 minutes)

### Exercise 2.1: Statutory Interpretation Research

**goal**: Find how courts interpret a specific statutory provision.

**Type:**
```
/research Art. 97 OR contractual liability damages calculation
```

**What to observe:**
1. **Key BGE decisions**: Leading cases on Art. 97 OR
2. **Interpretation patterns**: How courts calculate damages
3. **Recent developments**: Newer cases that might change interpretation

**⚠️ No results? Try this:**
- Use German terms: "Vertragshaftung Schadenersatz"
- Try broader search: "Art. 97 OR" without "damages"
- Search by legal area: "Overtyungsrecht"

---

### Exercise 2.2: Finding Related Precedents

**goal**: Build a citation chain from a known case.

**Type:**
```
/research cases citing BGE 145 III 445
```

**What to observe:**
1. **Direct citations**: Cases that explicitly cite your target
2. **Parallel reasoning**: Cases reaching similar conclusions
3. **Distinguishing cases**: Cases that distinguish or limit the precedent

**✅ Success criteria**: You can identify at least 5 related cases and understand how they relate.

---

### Exercise 2.3: Cantonal Court Research

**goal**: Find cantonal-level decisions on a federal law issue.

**Type:**
```
/research Art. 271d OR commercial lease Zurich
```

**What to observe:**
1. **Cantonal court decisions**: Obergericht Zürich cases
2. **Practical application**: How Zurich courts apply federal law
3. **Local variations**: Canton-specific interpretations

---

## Level 3: Strategy and Adversarial Analysis (30 minutes)

### Exercise 3.1: Case Strategy Assessment

**goal**: Assess the strength of a legal position.

**Scenario**: Your client wants to sue for breach of contract. The limitation period expires in 3 months. You're unsure if you should file now.

**Type:**
```
/strategy Contract breach claim, limitation period 3 months from discovery, damages CHF 100,000
```

**What to observe:**
1. **Risk assessment**: Probability of success (0-100%)
2. **Key factors**: What strengthens or weakens the case
3. **Recommended actions**: Next steps with priority

---

### Exercise 3.2: Adversarial Challenge

**goal**: Stress-test your own argument.

**Scenario**: You believe the limitation period should be 10 years (not 5 years under Art. 127 OR). Challenge this.

**Type:**
```
/adversarial My argument: The limitation period for contractual claims is 10 years under Art. 127 OR, not 5 years
```

**What to observe:**
1. **Counter-arguments**: What the opposing counsel would say
2. **Weak points**: Where your argument is most vulnerable
3. **Supporting precedents**: Cases that help or hurt your position

**✅ Success criteria**: You can identify at least 3 weaknesses in your argument and know how to address them.

---

### Exercise 3.3: Probability Calibration

**goal**: Understand how to interpret AI probability scores.

**Type:**
```
/strategy Simple debt collection claim, undisputed debt, CHF 50,000
```

**Compare to:**
```
/strategy Complex contractual dispute, unclear liability, multiple parties, CHF 500,000
```

**What to observe:**
- How probability scores differ (simple vs complex)
- What factors drive the scores
- How confidence intervals are expressed

---

## Level 4: Document Drafting and Review (30 minutes)

### Exercise 4.1: Simple Contract Clause Drafting

**goal**: Draft a specific contract clause with AI assistance.

**Type:**
```
/draft limitation of liability clause for IT services agreement under Swiss law
```

**What to observe:**
1. **Structure**: How the clause is organized
2. **Swiss law compliance**: References to OR provisions
3. **Language precision**: Unambiguous terms

**✅ Success criteria**: You have a draft clause that addresses key concerns and cites relevant law.

---

### Exercise 4.2: Document Translation

**goal**: Translate a legal document while preserving terminology.

**Type:**
```
/translate [paste a short contract clause] from German to French, preserve legal terminology
```

**What to observe:**
1. **Term preservation**: OR/CO, AG/SA remain consistent
2. **Legal accuracy**: Meaning is preserved
3. **Formatting**: Structure remains clear

---

### Exercise 4.3: Document Analysis

**goal**: Analyze an existing document for issues.

**Scenario**: Client sends you a contract they want to sign. You want to quickly identify key terms and potential issues.

**Type:**
```
/doc-analyze [paste contract text] for Swiss law compliance and key risks
```

**What to observe:**
1. **Key terms identified**: Governing law, jurisdiction, limitation periods
2. **Risk flags**: Unusual clauses, missing protections
3. **Recommendations**: What to negotiate

---

## ✅ Building Confidence Checklist

After completing all levels, verify:

- [ ] I can verify citations in multiple languages
- [ ] I can research precedents and find related cases
- [ ] I understand probability scores in strategy assessments
- [ ] I can run adversarial analysis on my arguments
- [ ] I can draft and review documents with AI assistance

---

**🎉 Excellent! You're ready for structured briefings.**

**Next**: [The Briefing Phase](./briefing-phase.md) →
