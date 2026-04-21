# Scenario 6.1: Contract Review

> **Real-world example you can adapt**

**⏱️ Estimated time: 30 minutes**

---

## The Situation

Your client sends you a commercial lease agreement they've been asked to sign. They want you to review it quickly and flag any issues before they commit.

**Client email:**
> "Can you take a look at this lease? It's for a retail space in Zurich, 5 years. They want an answer by Friday."

---

## Step-by-Step Walkthrough

### Step 1: Set Up Your Workspace (2 min)

Create a dedicated directory and CLAUDE.md for this review:

```markdown
# Matter: Retail Lease Review - Zurich

## Client
- **Name**: [Client Name]
- **Type**: Retail business owner
- **Business**: [Type of retail]

## Opposing Party
- **Name**: [Landlord Name]
- **Type**: Property company
- **Property**: Retail space, [Address], Zurich

## Key Terms (from quick scan)
- **Duration**: 5 years
- **Rent**: CHF [amount]/month
- **Security Deposit**: [months] rent

## Client's Concerns
- Wants to understand obligations
- Concerned about flexibility if business doesn't work out
- Budget is tight

## Status
- **Phase**: Initial review
- **Deadline**: Friday
```

### Step 2: Initial Document Analysis (5 min)

**Type:**
```
/doc-analyze [paste lease text or attach document]

Extract: key terms, unusual clauses, potential risks, Swiss law compliance
```

**What you're looking for:**
- Standard Swiss commercial lease provisions (OR 253ff)
- Unusual limitation of liability clauses
- Hidden cost provisions
- Termination flexibility
- Exclusivity or non-compete clauses

### Step 3: Research Unfamiliar Terms (5 min)

If the lease has unfamiliar provisions:

**Type:**
```
/research [unfamiliar term, e.g., "Indexklausel commercial lease Switzerland"]
```

**Common research needs:**
- Index adjustment mechanisms
- Maintenance cost allocation
- Subleasing restrictions
- Early termination penalties

### Step 4: Risk Assessment (5 min)

**Type:**
```
/adversarial Analyze this lease from tenant's perspective. What are the risks?
```

**Focus on:**
- What could go wrong for your client?
- What clauses favor the landlord?
- What protections are missing?

### Step 5: Draft Client Memo (10 min)

**Type:**
```
/draft client memo summarizing:
1. Key terms and obligations
2. Significant risks identified
3. Recommended negotiations
4. Go/no-go recommendation

Format: Executive summary first, then details
```

### Step 6: Verify Key Points (3 min)

Before sending to client, verify:

```
/cite [any BGE citations in your memo]
```

---

## What to Validate

### Swiss Law Compliance
- [ ] Lease complies with OR 253ff requirements
- [ ] Notice periods align with statutory minimums
- [ ] Security deposit within legal limits

### Commercial Reasonableness
- [ ] Rent is market-appropriate for location
- [ ] Duration matches client's business plan
- [ ] Termination options are reasonable

### Risk Assessment
- [ ] Identified clauses favoring landlord
- [ ] Flagged unusual or one-sided provisions
- [ ] Noted missing protections

---

## Sample Output Structure

```markdown
# Lease Review: [Address], Zurich

## 📊 Executive Summary

**Recommendation**: [Proceed with negotiation / Do not sign / Sign as-is]

**Key Finding**: [Most important issue]

**Timeline**: Response needed by Friday

---

## 🔍 Key Terms

| Term | Details | Assessment |
|------|---------|------------|
| Duration | 5 years, no early termination | ⚠️ R/r Risk |
| Rent | CHF X/month + annual index | Standard |
| Deposit | 6 months rent | ⚠️ High side |

---

## ⚠️ Significant Risks

### 1. [Risk Name]
**Clause**: [reference]
**Issue**: [explanation]
**Impact**: [what could happen]
**Recommendation**: [what to negotiate]

### 2. [Risk Name]
[Same structure]

---

## 💡 Recommended Negotiations

1. **[Topic]** - Request: [what] - Rationale: [why]

---

## ✅ Go/No-Go

**Factors supporting GO**:
- [List]

**Factors supporting NO-GO**:
- [List]

**Bottom line**: [Your recommendation]
```

---

> ⚠️ **No issues found? That's suspicious.**
> - Most commercial leases favor the landlord
> - Check your analysis depth
> - Consider what's NOT in the lease (missing protections)
> - Ask client about verbal assurances not in writing

---

## Adapting This Scenario

**For employment contracts:**
- Focus on: non-compete, bonus structures, termination rights
- Research: OR 319ff, case law on non-compete reasonableness

**For service agreements:**
- Focus on: limitation of liability, termination, SLAs
- Research: OR 394, standard commercial terms

**For purchase agreements:**
- Focus on: warranties, liability caps, payment terms
- Research: OR 187ff (sales law), standard terms

---

**Next**: [Litigation Preparation Scenario](./litigation-prep.md) →
