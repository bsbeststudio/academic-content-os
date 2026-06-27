---
title: Import Knowledge Protocol
type: playbook
scope: cross-topic
language: en
status: active
---

# Import Knowledge Protocol

## Purpose

Transform raw conversations into reusable knowledge assets stored in the Academic Content OS repository.

> **Not** summarizing conversations. **Transforming** them into atomic, reusable knowledge units.

---

## Asset Type Priority

```
Knowledge → Framework → Decision Rule → Opinion → Coaching →
Checklist → Playbook → FAQ → Golden Sentence → Article Idea
```

### Asset Type Definitions

**Knowledge**
Objective information. Examples: why interviewers ask a question, common follow-up questions, typical interview process, definitions.
- Must never contain personal advice.

**Framework**
Reusable structures. Examples: three-step answer structure, decision framework, research narrative template.
- Must be reusable across students.

**Decision Rule**
If-Then knowledge. Always use explicit `IF → THEN` logic.
- Example: If the student changes research interests → explain it as an extension rather than a switch.
- Example: If AI was used → describe AI as implementation instead of reasoning.

**Opinion**
Professional judgment. Clearly separated from objective knowledge.
- Signals: "I generally recommend…", "I think…", "In my experience…"

**Coaching**
Teaching experience. Examples: common mistakes, practice advice, interview signals, psychological coaching.

**Checklist**
Step-by-step preparation. Examples: 24-hour checklist, coding review checklist, interview preparation checklist.

**FAQ**
Questions students frequently ask.

**Golden Sentence**
Reusable sentences. Store each sentence independently — never bury inside articles.

**Playbook**
Multi-step consulting workflow. Examples: predoc interview preparation SOP, mock interview SOP, student onboarding SOP.

**Article Idea**
Potential future articles. Generate titles only.

---

## Repository Structure

```
taxonomy/
  topics/
  hubs/
content/
  knowledge/
  frameworks/
  opinions/
  coaching/
assets/
  decision_rules/
  checklists/
  faq/
  playbooks/
  golden_sentences/
generated/
```

---

## Steps

### Step 1 — Identify Knowledge Units

Read the entire conversation. Identify every independent knowledge unit.

- Think in **atomic concepts**, not paragraphs.
- One paragraph may contain: one knowledge point + one coaching principle + one FAQ + one golden sentence → these become **different files**.

### Step 2 — Classify Every Unit

Assign each unit one of the asset types above.

### Step 3 — Locate the Destination

- **Prefer updating existing files** over creating new ones.
- Only create a new file when the topic genuinely does not exist.

### Step 4 — Maintain Atomicity

Each markdown file answers **ONE question**.

Good: `research_interest_narrative.md`, `replication_walkthrough.md`, `robustness_tests.md`

Bad: `predoc_interview_everything.md`

### Step 5 — Update Taxonomy

If a new topic appears, update the single taxonomy source of truth:
- `meta/taxonomy.yaml`

### Step 6 — Maintain Cross-References

Update related fields inside affected files:
- Related Topics
- Related Frameworks
- Related Decision Rules
- Article Ideas

### Step 7 — Preserve Existing Knowledge

Do not rewrite everything. Only **append, merge, improve, or reorganize**.
Never duplicate content.

---

## Migration Report Format

Produce this report at the end of every import session:

```
## Migration Report

### Files Updated
- content/frameworks/research_interest_narrative.md

### Files Created
- content/decision_rules/ai_usage.md
- assets/golden_sentences/predoc_phrases.md

### Article Ideas Generated
- How to Explain Research Interest Changes
- Common Predoc Interview Mistakes

### Summary
Knowledge extracted: X
Frameworks extracted: X
Decision Rules extracted: X
Golden Sentences extracted: X
```
