# Scenario 6.5: Case Chronology

> **A sourced, court-defensible timeline in one pass (new in v4.9.5)**

**⏱️ Estimated time: 30 minutes**

---

## The Situation

Your client was dismissed after a two-year escalation with their employer. The facts are scattered across a warning letter, dozens of emails, meeting notes, and the termination letter — and on two key points, your client's dates and the employer's letter contradict each other. The cantonal court will expect a chronology that shows, for every event, where it comes from and which facts are actually disputed.

**Client message:**
> "I've put everything in a folder — the warning, the emails with HR, my notes. Can you build the timeline for the submission? The hearing is in six weeks."

---

## Step-by-Step Walkthrough

### Step 1: Set Up Your Workspace (2 min)

Create a dedicated directory and CLAUDE.md listing the parties, the dispute, and the document inventory (warning letter, HR correspondence, meeting notes, termination letter).

### Step 2: Collect the Sources (5 min)

Place every dated document in the matter's `docs/` folder. The timeline is only as good as its sources — include the documents both sides rely on, not just your client's favorites.

### Step 3: Build the Timeline (5 min)

**Type:**
```text
/legal-timeline Build the case chronology from the documents in docs/:
warning letter, HR correspondence, meeting notes, termination letter.
Include all dated events relevant to the dismissal dispute.
```

The `chronology-builder` agent extracts the events and writes the timeline to `bcc-output/timeline/` as `timeline.md`, `timeline.html`, and `timeline.docx`.

### Step 4: Check Provenance and Dispute Labels (5 min)

Open `timeline.md` and verify for each event:

- **Source**: which document (and page/paragraph) it comes from — every event carries its provenance
- **Label**: *undisputed* (both sides agree), *alleged* (only one side asserts it), or *contested* (both sides assert, differently)
- **Date conflicts**: where sources disagree on a date, the timeline keeps **both** dates with a note — it never silently picks one

### Step 5: Close the Gaps (5 min)

Events 30+ days apart are flagged as gaps. Ask your client about each gap:

- Is there a document that covers it (search again)?
- Is the gap itself the story (e.g., no reaction to the warning)?
- Should the gap be acknowledged in the submission?

### Step 6: Check Deadlines and Keep It Current (8 min)

The timeline also computes procedural deadlines under ZPO Art. 142–149 (BGG Art. 46 / 100–101 for federal matters), including cantonal holidays. Two rules:

- **Verjährung (statute of limitations) dates are always marked "indicative"** — never rely on them as definitive; verify the interruption facts yourself
- When new documents arrive, don't rebuild from scratch:
  ```
  /legal-timeline --merge [new documents]
  ```
  `--merge` folds the new events into the existing timeline.

---

## What to Validate

### Sourcing
- [ ] Every event carries a source reference
- [ ] Events traceable to a specific document, not "client says"
- [ ] All sources in `docs/` actually used (or deliberately excluded)

### Dispute Discipline
- [ ] Every fact labeled undisputed / alleged / contested
- [ ] Conflicting dates show **both** values with a note
- [ ] No contested fact quietly upgraded to undisputed

### Completeness
- [ ] All gaps of 30+ days explained or filled
- [ ] Deadline list checked against the court's calendar
- [ ] Verjährung dates treated as indicative only

---

## Sample Output Structure

```markdown
# Case Timeline: [Client] v. [Employer]

## Events

| # | Date(s) | Event | Source | Status |
|---|---------|-------|--------|--------|
| 1 | 2024-03-04 | Written warning issued | Warning letter p. 1 | Undisputed |
| 2 | 2024-03-06 / 2024-03-11 | Client's objection email | Client: email; Employer: "letter of 11.3." | **Date conflict — both dates kept** |
| 3 | 2024-04-02 | Meeting with HR | Client meeting notes | Alleged (employer denies) |
| … | | | | |

## Date Conflicts

### Event 2 — Objection email
- Client's sent folder: 2024-03-06
- Employer's warning response cites "letter of 11.3.2024"
- Action: obtain server logs / registered-mail receipt

## Gaps (30+ days)

| Between | Gap | Assessment |
|---------|-----|------------|
| Event 3 → termination | 47 days | Unexplained — ask client |

## Deadlines

| Deadline | Date | Basis |
|----------|------|-------|
| Hearing brief | [date] | ZPO Art. 142–149 (incl. cantonal holidays) |
| Verjährung (claim X) | [date] | **Indicative only — verify interruption facts** |
```

---

> ⚠️ **A timeline with unlabeled facts is advocacy, not chronology.**
> - If everything is "undisputed," you haven't read the other side
> - Never drop the date you don't like — keep both and source them
> - A gap you hide becomes the opponent's cross-examination highlight

---

**Next**: [NDA Triage Scenario](./nda-triage.md) →
