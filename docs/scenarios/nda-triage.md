# Scenario 6.6: NDA Triage

> **Sign, negotiate, or refuse — fast (new in v4.8.0)**

**⏱️ Estimated time: 20 minutes**

---

## The Situation

A pilot project starts Monday. Four NDAs from the counterparty are sitting in your inbox; your client wants to know tonight which ones can be signed as-is and which need pushback.

**Client message:**
> "Four NDAs came in — one per entity, because of course. I need to sign at least two of them before the pilot starts. Which ones are safe?"

---

## Step-by-Step Walkthrough

### Step 1: Set Up Your Workspace (2 min)

Create a matter directory and drop all four NDAs into `docs/nda-inbox/`. Batch mode works on a folder just as well as a single file.

### Step 2: Run the Triage (5 min)

**Single file:**
```
/nda-triage docs/nda-inbox/nda-alpha-gmbh.pdf
```

**Whole batch:**
```
/nda-triage docs/nda-inbox/
```

Every clause receives a rating:

| Rating | Meaning | Your action |
|--------|---------|-------------|
| 🟢 **GREEN** | Standard, acceptable as-is | Sign |
| 🟡 **YELLOW** | Deviates from market standard | Negotiate |
| 🔴 **RED** | Legally problematic or non-standard and unacceptable | Refuse / rewrite |

### Step 3: Read the RED Findings First (5 min)

The triage flags, with legal basis:

- **Art. 160 ff. OR validity limits** — clauses whose effectiveness depends on statutory formal requirements
- **Lugano forum clauses** — jurisdiction selections that steer disputes somewhere you don't want them
- **Zwingendes Recht overrides** — provisions that mandatory law supersedes anyway, whatever the NDA says

Ask for each RED item: is this negotiable, or is it a reason to walk?

### Step 4: Turn YELLOW into a Markup (5 min)

For the NDAs worth pursuing, generate the negotiation positions with `/draft`, referencing your firm playbook (v4.8.0) if you have one:

```
/draft NDA markup for nda-beta-ag.pdf addressing all YELLOW clauses,
aligned with the firm playbook positions
```

With a playbook, each requested change comes with its deviation class (*conforme* / *accettabile* / *negoziare* / *inaccettabile*), so the client sees what's house style and what's a real concession.

### Step 5: Verify the Batch as a Whole (3 min)

For a multi-NDA batch, wrap the review in a goal-loop so nothing ships half-checked:

```
/legal-goal nda-batch-clean
/legal-loop bcc-output/goals/[the goal record just created]
```

`/legal-goal` builds the Goal Record from the `nda-batch-clean` profile (capped at 3 iterations): a worker agent closes the gaps the evaluator finds, and a final `NOT MET` is reported honestly rather than papered over. The full trail is written to `bcc-output/loops/`. See [Mastering Workflows §5.5](../mastering-workflows.md) for how the loop works.

### Step 6: Deliver the Verdict (2 min)

**Type:**
```
/draft client memo: sign / negotiate / refuse recommendation per NDA,
with the RED findings and the proposed markups attached
```

The memo lands in `bcc-output/YYYY-MM-DD-<slug>/` with a `sources.md` linking each rating to the clause it came from.

---

## What to Validate

### Coverage
- [ ] Every clause in every NDA rated (GREEN clauses were read, not skipped)
- [ ] All schedules and attachments included in the analysis
- [ ] Batch summary covers all files in the folder

### Legal Flags
- [ ] Each RED finding cites its basis (Art. 160 ff. OR, Lugano forum, zwingendes Recht)
- [ ] Jurisdiction and governing-law clauses checked against the client's exposure
- [ ] No clause rated GREEN merely because it is common

### Output
- [ ] Per-NDA verdict: sign / negotiate / refuse
- [ ] Markups reference the firm playbook where one exists
- [ ] Client memo delivered from `bcc-output/`, not from chat

---

## Sample Output Structure

```markdown
# NDA Triage: Pilot Project Inbox

## 📊 Batch Summary

| NDA | Verdict | RED | YELLOW | Blocking issue |
|-----|---------|-----|--------|----------------|
| alpha-gmbh.pdf | ✅ Sign | 0 | 2 | — |
| beta-ag.pdf | ⚠️ Negotiate | 1 | 4 | Lugano forum clause |
| gamma-sa.pdf | ⚠️ Negotiate | 1 | 1 | Art. 160 ff. OR form requirement |
| delta-gmbh.pdf | ❌ Refuse | 3 | 5 | Unlimited liability, zwingendes Recht conflicts |

---

## 🔴 RED Findings

### beta-ag.pdf — Clause 14.2 (Forum)
**Clause**: "Exclusive jurisdiction: [foreign court]"
**Basis**: Lugano forum selection steering disputes away from the client's home forum
**Action**: Replace with client's home court or delete

### delta-gmbh.pdf — Clause 9 (Liability)
**Clause**: "Liability unlimited for any breach"
**Basis**: Non-standard and unacceptable; exceeds market practice
**Action**: Cap at [amount] or refuse

---

## 🟡 YELLOW Positions (per NDA)

| Clause | Issue | Requested change |
|--------|-------|------------------|
| beta-ag 7.1 | 10-year term | Reduce to 3 years |
```

---

> ⚠️ **An all-GREEN 40-page NDA means the schedule wasn't read.**
> - Check that attachments and schedules were part of the triage input
> - "Standard" clauses still interact — read the GREENs together, not just one by one
> - A refusal with reasons is faster than a bad signature

---

**✅ Congratulations! You've completed the scenario library.**

**Next**: [Collaboration & Team Workflows](../collaboration.md) →
