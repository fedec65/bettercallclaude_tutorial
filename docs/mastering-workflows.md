# Part 5: Mastering Workflows

> **Design and execute multi-step legal processes**

## What You'll Learn

By the end of this section, you will be able to:

- Think in terms of legal workflows
- Chain commands naturally
- Design your own workflows
- Use quality checkpoints effectively

> **📖 Context**: This section builds on Phases 2-3 (Execution and Interaction) of the unified framework. For the complete methodology overview, see [Framework Methodology](./framework-methodology.md).

---

## 5.1 Thinking in Workflows

### The Natural Legal Process

Legal work naturally flows through stages:

```
Intake → Research → Strategy → Draft → Review → Deliver
```

This mirrors how BetterCallClaude works best. Each stage maps to specific commands:

| Stage | BetterCallClaude Approach | Commands |
|-------|--------------------------|----------|
| Intake | Understand the matter, gather facts | /briefing |
| Research | Find law and precedents | /research, /cite |
| Strategy | Assess strengths, weaknesses | /strategy, /adversarial |
| Draft | Create documents | /draft |
| Review | Check quality, consistency | /adversarial, /cite |
| Deliver | Finalize and communicate | /translate, /draft |

---

## 5.2 Command Chaining

### Natural Language Chaining

You can chain commands naturally by describing the sequence:

**Example 1: Research → Draft**
```
First research Art. 97 OR contractual liability damages, then draft a client memo summarizing the key points
```

**Example 2: Strategy → Adversary → Draft**
```
Assess the strength of our limitation period argument, challenge it with adversarial analysis, then draft a brief memo to the client explaining the risks
```

### Sequential vs. Parallel Operations

**Sequential (one after another):**
```
Research case law on Art. 97 OR. Based on findings, draft legal opinion.
```
Better for: When later steps depend on earlier findings

**Parallel (at the same time):**
```
Research BGE decisions on hardship clauses AND research statutory framework for commercial leases. Then synthesize findings.
```
Better for: Independent research streams that you'll combine later

### When to Chain vs. When to Use a Predefined Workflow

| Use Chaining When... | Use Predefined Workflow When... |
|---------------------|------------------------------|
| Unique matter structure | Standard legal process |
| One-off approach | Repeated similar work |
| Exploring new area | Proven methodology |
| Need flexibility | Need consistency |

---

## 5.3 Designing Your Own Workflow

### Step 1: Identify the Stages

For your matter, break it into stages:

**Example: Contract Review Matter**
```
1. Initial Review - Understand contract structure and key terms
2. Risk Analysis - Identify problematic clauses
3. Research - Find applicable law and precedents
4. Recommendations - Draft advice to client
5. Negotiation Support - Prepare talking points
```

### Step 2: Select Commands for Each Stage

| Stage | Command | Purpose |
|-------|---------|---------|
| Initial Review | /doc-analyze | Extract key terms and structure |
| Risk Analysis | /adversarial | Find weaknesses and risks |
| Research | /research | Find supporting law |
| Recommendations | /draft | Create client memo |
| Negotiation | /strategy | Plan negotiation approach |

### Step 3: Define with /workflow

**Type:**
```
/workflow contract-review
  Stage 1: Analyze document structure and key terms
  Stage 2: Run adversarial analysis on risk clauses
  Stage 3: Research applicable law for identified risks
  Stage 4: Draft client recommendations memo
  Stage 5: Develop negotiation strategy
```

### Step 4: Execute and Iterate

Run the workflow, observe results, and refine:
```
Execute the contract-review workflow for the attached lease agreement
```

---

## 5.4 Predefined Workflows

### litigation-prep

**Purpose**: Prepare for litigation from initial assessment through case strategy

**Stages:**
1. **Intake**: Gather facts and documents
2. **Research**: Find applicable law and precedents
3. **Risk Assessment**: Evaluate strengths and weaknesses
4. **Strategy**: Develop case strategy
5. **Documentation**: Draft initial briefs and memos

**Use when**: Client wants to sue or is being sued

---

### due-diligence

**Purpose**: Systematic review of legal documents in transactions

**Stages:**
1. **Document Intake**: Gather all relevant documents
2. **Risk Scan**: Quick identification of issues
3. **Deep Analysis**: Detailed review of flagged items
4. **Risk Matrix**: Organize findings by severity
5. **Report**: Draft due diligence report

**Use when**: M&A, investment, or major contract review

---

### contract-lifecycle

**Purpose**: From drafting through execution and amendment

**Stages:**
1. **Requirements**: Understand what the contract must achieve
2. **Drafting**: Create initial draft
3. **Review**: Check for risks and compliance
4. **Negotiation**: Prepare for counterparty discussions
5. **Finalization**: Execute and archive

**Use when**: Creating new agreements or major amendments

---

## 5.5 Quality Checkpoints

### When to Stop and Review

**After Research Phase:**
- [ ] Found key precedents for each legal issue?
- [ ] Verified citations are accurate?
- [ ] Identified gaps in research?

**After Strategy Phase:**
- [ ] Assessed both strengths and weaknesses?
- [ ] Considered client's practical constraints?
- [ ] Probability assessment seems reasonable?

**Before Draft Delivery:**
- [ ] Document addresses all required points?
- [ ] Citations verified and properly formatted?
- [ ] Language appropriate for recipient?

### Validating Citations

Always verify AI-generated citations:
```
/cite [citation from AI output]
```

If the citation doesn't exist or is incorrect:
1. Note the error
2. Search for the correct citation
3. Update your document

### Professional Responsibility Reminder

> **You remain responsible for all legal work.** BetterCallClaude is a tool that assists, but all analysis, strategy, and documents must be reviewed and validated by you before use. AI can make mistakes—citation hallucinations, incorrect legal interpretations, or missed nuances. Your professional judgment is the final check.

---

## 5.6 Workflow Example: Full Walkthrough

### Scenario: Client Wants Legal Opinion on Termination Rights

**Step 1: Intake (5 minutes)**
```
/briefing Client needs legal opinion on whether they can terminate employment contract early due to employer's failure to pay agreed bonus
```

**Step 2: Execute Briefing Plan (45 minutes)**

Following the plan, research employment law on bonus agreements, find precedents on constructive dismissal, analyze the contract.

**Step 3: Strategy Check (10 minutes)**
```
/strategy Termination for unpaid bonus, 2 years remaining on contract, employer claims financial hardship
```

**Step 4: Challenge Your Position (10 minutes)**
```
/adversarial Client's position: Non-payment of bonus is fundamental breach justifying immediate termination
```

**Step 5: Draft Opinion (30 minutes)**
```
/draft legal opinion for client on termination rights, addressing both constructive termination argument and employer's hardship defense
```

**Step 6: Final Review (15 minutes)**
```
Verify all citations, check for bias toward client position, ensure practical advice is clear
```

**Total: ~2 hours** for a thorough legal opinion with validated research.

---

> ⚠️ **Workflow not working as expected? Try this:**
> - Break it into smaller stages and run sequentially
> - Check that each command is working before chaining
> - Verify your CLAUDE.md has sufficient context
> - Try the workflow with `--explain` to understand each step

---

## ✅ Mastering Workflows Checklist

Before moving to scenarios, verify:

- [ ] I can describe my legal work as a workflow
- [ ] I can chain commands naturally
- [ ] I know when to use predefined vs. custom workflows
- [ ] I understand quality checkpoints
- [ ] I always validate citations and review AI output

---

**🎉 You're ready for real-world scenarios!**

**Next**: [Scenario Library](./scenarios/) →
