# Part 4: The Briefing Phase

> **Structuring complex work with specialist panel consultation**

## What You'll Learn

By the end of this section, you will understand:

- When to use briefing vs. direct commands
- How to prepare for a briefing session
- What to expect during the question flow
- How to use briefing output for execution

> **📖 Context**: This section covers Phase 1 (Briefing) of the unified 5-phase framework. For the complete methodology overview, see [Framework Methodology](./framework-methodology.md).

---

## 4.1 What is Briefing?

### The Problem It Solves

Complex legal matters often have:
- Multiple interrelated issues
- Unclear scope at the outset
- Need for specialized expertise across different areas
- Potential for costly mistakes if scope is misunderstood

**Briefing solves this by:**
1. **Structured intake**: Specialist panel asks targeted questions
2. **Scope clarification**: Understanding exactly what you need
3. **Execution planning**: Building a clear roadmap before starting

### How Briefing Works

```
You start /briefing → Specialist panel activated → Panel asks questions → You answer → Panel builds plan → You approve → Execution begins
```

### When to Use Briefing

| Use Briefing When... | Use Direct Commands When... |
|---------------------|---------------------------|
| Matter involves multiple legal areas | Simple, single-issue query |
| Scope is unclear at outset | You know exactly what you need |
| Significant client consequences | Quick lookup or verification |
| Multi-step research required | Standard drafting task |
| Cross-canton issues | Single-jurisdiction matter |
| Team collaboration needed | Solo work |

---

## 4.2 Running a Briefing Session

### Starting a Briefing

**Type:**
```
/briefing I need to prepare a legal opinion on whether my client can terminate a commercial lease early due to COVID-19-related revenue loss
```

### The Question Flow

The specialist panel will ask questions like:

**Round 1: Factual Clarification**
```
📋 Panel: To assess your termination question, I need to understand:

1. What is the term of the lease and how much remains?
2. What does the termination clause specifically state?
3. What COVID-related measures affected the tenant's business?
4. What financial impact has the tenant experienced (revenue loss figures)?
5. Has the tenant paid rent during the affected period?
```

**Your answers might be:**
```
1. 5-year lease signed March 2022, 2.5 years remaining
2. Clause 12 allows termination with 6 months notice, no force majeure provision
3. Government mandated closure from March-May 2020, then capacity restrictions
4. Revenue dropped 70% during closure, 40% during restrictions
5. Tenant paid full rent until June 2020, then partial payments
```

**Round 2: Legal Framework**
```
📋 Panel: Now I need to understand the legal arguments:

6. Is there any case law on COVID-19 as hardship (Notlage)?
7. What canton is the property in? (Some cantons had special rules)
8. Has the landlord offered any rent reduction?
9. What is the tenant's argument for termination—hardship, impossibility, or changed circumstances?
```

**Round 3: Client Priorities**
```
📋 Panel: Finally, to plan our approach:

10. What is the client's primary goal—full termination or renegotiation?
11. Is there a relationship to preserve with this landlord?
12. What is the client's risk tolerance for litigation?
```

---

### Building the Execution Plan

After answering the panel's questions, you'll receive:

```markdown
## 📋 Execution Plan

### Phase 1: Legal Research (Est. 2 hours)
- Research BGE decisions on commercial lease hardship (Notlage)
- Identify cantonal emergency measures for commercial leases
- Analyze comparable cases in your canton

### Phase 2: Risk Assessment (Est. 1 hour)
- Run /adversarial on hardship termination argument
- Assess probability of success
- Identify counter-arguments landlord will raise

### Phase 3: Client Consultation (Est. 30 min)
- Present findings to client
- Discuss litigation vs. negotiation
- Get client decision on approach

### Phase 4: Execution (Est. 3-5 hours)
- If negotiate: Draft proposal for rent reduction or early termination
- If litigate: Draft termination notice and prepare for potential dispute

### Estimated Total: 6.5-8.5 hours
### Critical Path: Research → Risk Assessment → Client Decision
```

---

## 4.3 Briefing Best Practices

### What Information to Have Ready

Before starting a briefing, gather:

**Essential Documents:**
- [ ] Core contract(s) or legal document(s)
- [ ] Key correspondence
- [ ] Timeline of events
- [ ] Any existing legal opinions

**Client Context:**
- [ ] Client's business situation
- [ ] Client's goals (what does "success" look like?)
- [ ] Client's risk tolerance
- [ ] Budget and timeline constraints

**Legal Context:**
- [ ] Relevant jurisdiction(s)
- [ ] Known legal issues
- [ ] Opposing party information

### How to Answer Effectively

**DO:**
- Be specific with facts ("Revenue dropped 70%" not "revenue dropped significantly")
- Provide exact dates and amounts where available
- State what you know vs. what you assume
- Mention relevant documents you have

**DON'T:**
- Volunteer legal conclusions (let the panel draw those)
- Be vague ("some time ago")
- Guess at answers you don't know

### Using `--resume` for Cross-Session Work

If a briefing spans multiple sessions or you need to pick up later:

```
/briefing --resume
```

This tells BetterCallClaude to load your previous briefing context and continue where you left off.

---

## 4.4 From Briefing to Execution

### Reviewing the Execution Plan

The briefing output includes a structured plan. Before proceeding:

1. **Verify scope**: Does this match what you thought you need?
2. **Check estimates**: Are the time estimates reasonable?
3. **Identify dependencies**: Which tasks must to finish before others start?

### Starting Execution

**Option 1: Let BetterCallClaude execute**
```
Please execute Phase 1: Legal Research as planned
```

**Option 2: Execute step by step**
```
Start with Phase 1.1: Research BGE decisions on commercial lease hardship
```

**Option 3: Modify the plan**
```
The plan looks good, but let's add a comparison with German and French approaches to hardship clauses before Phase 1
```

---

## 4.5 Briefing Example: Full Walkthrough

### Scenario: Litigation Preparation

**Your briefing prompt:**
```
/briefing Client wants to sue former employer for wrongful termination. Employment was in Zurich, client worked there for 8 years, terminated last month with 2 weeks notice, claiming "restructuring"
```

**Panel questions (abbreviated):**
1. What was the client's role and salary?
2. What notice period is in the employment contract?
3. What were the stated reasons for termination?
4. How many others were terminated in this "restructuring"?
5. Does the client have a new job yet?
6. What is the client claiming (amount, basis)?
7. Are there any written communications about the termination?
8. What is the client's goal—reinstatement or damages?

**Your answers:**
```
1. Senior Marketing Manager, CHF 180,000/year
2. Contract states 3 months notice, or immediate termination for cause
3. Letter says "Due to restructuring, your role is eliminated"
4. 12 people terminated from department of 40, client was oldest and highest-paid
5. No, actively searching
6. CHF 540,000 (6 months salary) plus CHF 50,000 job search costs
7. Termination letter and exit interview notes
8. Primarily damages, open to settlement negotiation
```

**Execution plan output:**
```markdown
## 📋 Execution Plan

### Phase 1: Evidence Gathering (Est. 1 hour)
- Compile all termination documents
- Gather comparables: ages, tenure, salaries of terminated employees
- Document client's job search efforts

### Phase 2: Legal Research (Est. 2 hours)
- Research BGE decisions on wrongful termination (Art. 337 OR)
- Analyze Zurich employment court tendencies
- Identify age discrimination arguments (client was oldest)

### Phase 3: Strategy Development (Est. 1.5 hours)
- Run /adversarial on age discrimination claim
- Assess settlement range
- Prepare negotiation strategy

### Phase 4: Draft Legal Opinion (Est. 2 hours)
- Draft internal memo on case assessment
- Include probability assessment
- Recommend negotiation vs. litigation

### Estimated Total: 6.5 hours
```

---

> ⚠️ **Briefing taking too long? Try this:**
> - You may be over-answering. Briefing questions are targeted—keep responses brief.
> - You might be starting with too broad a scope. Try `/briefing --scope narrow` to focus.
> - The panel may be asking about information you don't have. Say "I don't have that information yet" rather than guessing.
> - If you're stuck on a loop of questions, you can say "Let's proceed with what we have" to move forward.

---

## ✅ Briefing Phase Checklist

Before moving to execution, verify:

- [ ] I understand when to use briefing vs. direct commands
- [ ] I have had a full briefing session with question flow
- [ ] I understand how to answer effectively
- [ ] I have reviewed and approved an execution plan
- [ ] I know how to use --resume for cross-session work

---

**🎉 You're ready to design your own workflows!**

**Next**: [Mastering Workflows](./mastering-workflows.md) →
