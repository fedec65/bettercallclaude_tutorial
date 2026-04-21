# Scenario 6.4: Due Diligence

> **Multi-document transaction review**

**⏱️ Estimated time: 60 minutes**

---

## The Situation

Your client is acquiring a Swiss AG and needs legal due diligence on the target company.

**Client message:**
> "We're buying [Target AG]. Their lawyer sent over the data room. Can you review the key contracts and flag any issues? We have 3 weeks until signing."

---

## Step-by-Step Walkthrough

### Step 1: Scope Definition and Planning (10 min)

**Type:**
```
/briefing Legal due diligence for acquisition of Swiss AG.

Scope: Review key contracts (employment, commercial, real estate), corporate documents, litigation history, compliance

Documents available: [list document types in data room]

Timeline: 3 weeks to signing

Deliverable: Risk matrix and recommendations
```

### Step 2: Create Document Inventory (5 min)

**Type:**
```
Organize due diligence by category:

1. **Corporate**: Articles of association, share register, board minutes
2. **Employment**: Employment contracts, collective agreements
3. **Commercial**: Customer contracts, supplier agreements
4. **Real Estate**: Lease agreements
5. **Litigation**: Pending/dismissed cases
6. **Compliance**: Permits, licenses

Priority: High-risk categories first (commercial, employment, litigation)
```

### Step 3: Systematic Document Review (30 min)

**Work through each category:**

**3.1 Corporate Documents:**
```
/doc-analyze [articles of association, share register] for:
- Share transfer restrictions
- Protective provisions
- Governance issues
```

**3.2 Employment Documents:**
```
/doc-analyze [employment contracts, collective agreements] for:
- Non-compete clauses
- Termination risks
- Bonus/ pension obligations
```

**3.3 Commercial Contracts:**
```
/doc-analyze [key customer/supplier contracts] for:
- Change of control provisions
- Termination rights upon acquisition
- Long-term commitments
```

**3.4 Real Estate:**
```
/doc-analyze [lease agreements] for:
- Transfer restrictions
- Duration remaining
- Rent adjustment mechanisms
```

**3.5 Litigation:**
```
/research [party name] litigation history Switzerland
```

### Step 4: Risk Assessment (10 min)

**Type:**
```
/adversarial From buyer's perspective, what are the biggest risks in this acquisition?

Consider: undisclosed liabilities, contract terminations, employment disputes, pending litigation
```

### Step 5: Risk Matrix Creation (10 min)

**Type:**
```
/draft due diligence risk matrix:

Categories: Corporate, Employment, Commercial, Real Estate, Litigation, Compliance

For each risk:
- Description
- Severity (High/Medium/Low)
- Probability
- Financial impact
- Mitigation recommendation

Sort by: Severity × Probability
```

### Step 6: Recommendations Memo (15 min)

**Type:**
```
/draft due diligence summary for client including:

1. Executive summary with go/no-go recommendation
2. Critical issues (must resolve before signing)
3. Material risks (represent in SPA)
4. Minor issues (post-closing follow-up)
5. Recommended SPA protections

Format: Board-ready summary
```

---

## Risk Matrix Template

| Category | Risk | Severity | Likelihood | Impact (CHF) | Mitigation |
|----------|------|----------|------------|--------------|------------|
| Employment | Unpaid overtime claims | Medium | High | ~200K | SPA indemnity |
| Commercial | Key customer termination right | High | Medium | ~500K | Represent in SPA |
| Real Estate | Lease transfer restriction | Low | High | ~100K | Landlord consent |
| Litigation | Pending patent dispute | High | Low | ~1M | Insurance + indemnity |

---

## Sample Output: DD Summary

```markdown
# DUE DILIGENCE SUMMARY: [Target AG] Acquisition

## 🎯 Executive Summary

**Recommendation**: PROCEED with conditions

**Critical Issues**: 2 issues requiring pre-signing resolution
**Material Risks**: 4 risks to address in SPA
**Deal-breakers**: None identified

---

## 🚨 Critical Issues (Resolve Before Signing)

### 1. [Issue]
- **Finding**: [description]
- **Risk**: [what could go wrong]
- **Resolution**: [what to require]

### 2. [Issue]
[Same structure]

---

## ⚠️ Material Risks (Address in SPA)

### 1. [Risk Category]
- **Finding**: [description]
- **Exposure**: [CHF amount or range]
- **SPA Protection**: [specific clause recommendation]

---

## 📋 Minor Issues (Post-Closing)

1. [Issue] - Follow up by [date]
2. [Issue] - Monitor for [period]

---

## 💰 Financial Impact Summary

| Risk Category | Potential Exposure | Mitigation | Net Exposure |
|--------------|-------------------|------------|--------------|
| Employment | CHF 200,000 | Indemnity | ~CHF 50,000 |
| Commercial | CHF 500,000 | Warranty | ~CHF 100,000 |
| **Total Estimated** | **CHF 700,000** | | **~CHF 150,000** |

---

## ✅ Recommended SPA Protections

1. **Indemnity**: [specific indemnity language]
2. **Warranty**: [specific warranty coverage]
3. **Escrow**: [amount and release conditions]
4. **Disclosure Schedule**: [items to include]
```

---

## DD Best Practices

### Efficiency Tips
- Start with high-risk categories
- Use batch analysis for similar documents
- Document as you go (don't rely on memory)
- Flag items immediately when seen

### Common Oversights
- Change of control clauses in commercial contracts
- Pension obligations in employment
- Pending regulatory matters
- Related party transactions

### Red Flags
- Reluctance to provide documents
- Inconsistent corporate records
- Unusual related party arrangements
- Pending regulatory inquiries

---

> ⚠️ **Found nothing wrong? Be skeptical.**
> - Every company has issues—the question is whether they're material
> - Review your scope—did you miss categories?
> - Consider whether documents are complete (missing schedules, amendments?)
> - A clean DD might mean incomplete access, not clean company

---

**✅ Congratulations! You've completed the scenario library.**

**Next**: [Collaboration & Team Workflows](../collaboration.md) →
