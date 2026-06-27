# Repository Health Report
**Date:** 2026-06-27
**Scope:** Full consistency pass post-refactor
**Files checked:** 53 markdown files

---

## Errors Fixed

| # | File | Error | Fix Applied |
|---|---|---|---|
| 1 | `assets/faq/predoc_application.md` | `type: FAQ` — uppercase, non-standard | Changed to `type: faq` |
| 2 | `assets/golden_sentences/academic_career.md` | `topic: cross-topic` — invalid topic value (cross-topic is a scope, not a topic) | Changed to `scope: cross-topic` |
| 3 | `content/SOP/predoc_interview_preparation_sop.md` | `type: playbook` — file is in SOP/ directory | Changed to `type: SOP` |
| 4 | `content/frameworks/behavioral_interview.md` | `topic: behavioral_interview` — topic no longer exists in taxonomy (merged into mock_interview) | Changed to `topic: mock_interview` |
| 5 | `content/opinions/predoc.md` | No frontmatter at all | Added complete frontmatter with `type: opinion`, `status: draft` |
| 6 | `assets/playbooks/import_knowledge_protocol.md` | Missing `language` field | Added `language: en`, `scope: cross-topic` |

---

## Warnings

None remaining after fixes.

**False positives dismissed (not fixed):**
- `assets/golden_sentences/predoc_interview.md` — flagged for "missing scope" but has valid `topic: predoc_interview`; topic-scoped golden sentence files don't require a scope field
- `type: SOP` in `content/SOP/academic_career_planning_sop.md` — flagged as non-snake_case but SOP is a valid acronym; consistent with directory name

---

## Duplicate Candidates

Do NOT merge automatically. Report only.

### Candidate 1: High Overlap (~85%)
**Files:**
- `content/decision_rules/interview_recovery.md` (Rule 4)
- `content/decision_rules/signal_replacement.md`

**Overlap:** Both express "don't directly deny a negative signal; replace it with a stronger positive signal." Rule 4 in interview_recovery already references signal_replacement.

**Distinction:** interview_recovery Rule 4 is interview-context-scoped and chains to signal_replacement. signal_replacement is the canonical cross-topic standalone rule. This is intentional layering (topic rule → cross-topic rule), not accidental duplication.

**Recommendation:** Keep as-is. interview_recovery Rule 4 should remain a thin pointer; if its body grows, condense it to just the pointer.

### Candidate 2: Moderate Overlap (~65%)
**Files:**
- `content/frameworks/behavioral_interview.md` (57 lines)
- `content/knowledge/mock_interview.md` — Behavioral Interview section (36 lines)

**Overlap:** Both cover STAR structure, high-frequency behavioral questions (advisor disagreement, time management), and the "academic integrity before relationship" principle.

**Distinction:** `frameworks/behavioral_interview.md` is the executable answer framework (how to structure the response); `mock_interview.md` Behavioral section is contextual knowledge (why PI asks, what PI wants to confirm). Different epistemic types.

**Recommendation:** Keep separate. Consider adding a cross-reference note to both files pointing to the other.

---

## Empty / Placeholder Files

| File | Status | Action |
|---|---|---|
| `content/opinions/predoc.md` | All sections were `...` placeholder | Added frontmatter with `status: draft`; content sections retained as scaffold for future fill-in |

---

## Broken Links Fixed

**0 broken links** in this pass.

All 53 files verified. Zero unresolved internal backtick references (`content/...` or `assets/...`).

*(Previous pass fixed 19 files with broken references to deleted/renamed files.)*

---

## Files Modified in This Pass

1. `assets/faq/predoc_application.md` — type normalized
2. `assets/golden_sentences/academic_career.md` — topic → scope
3. `content/SOP/predoc_interview_preparation_sop.md` — type fixed
4. `content/frameworks/behavioral_interview.md` — topic updated
5. `content/opinions/predoc.md` — frontmatter added
6. `assets/playbooks/import_knowledge_protocol.md` — language + scope added

---

## Files Moved

None. All files are in correct directories.

---

## Metadata Normalized

| Field | Before | After | Files |
|---|---|---|---|
| `type` | `FAQ` | `faq` | 1 |
| `type` | `playbook` (in SOP dir) | `SOP` | 1 |
| `topic` | `behavioral_interview` (deleted topic) | `mock_interview` | 1 |
| `topic` | `cross-topic` (invalid topic value) | removed; `scope: cross-topic` added | 1 |
| `language` | missing | `en` | 1 |
| `scope` | missing | `cross-topic` | 1 |
| full frontmatter | absent | added | 1 |

---

## Taxonomy Consistency

- **61 taxonomy asset references** — all resolve to existing files ✓
- **0 orphan content files** — all content/ files registered in taxonomy ✓
- **0 orphan topics** — all topics have at least one asset or explicit `note: content pending` ✓
- **Single source of truth** — `meta/taxonomy.yaml` v3.0 ✓

---

## Remaining Recommendations

1. **`content/opinions/predoc.md`** — Fill in draft content. This is the only active draft stub in the repo. Consider: recommend predoc when candidate has no North American PI network; do not recommend when candidate already has strong recommenders in target programs.

2. **`content/decision_rules/interview_recovery.md` Rule 4** — Consider condensing Rule 4 body to a single pointer sentence now that `signal_replacement.md` exists as the canonical rule. Reduces prose duplication.

3. **6 topics with `note: content pending`** — `phd_application`, `offer_decision`, `working_with_pi`, `replication_literature`, `staggered_did`, `sop`. These are structural placeholders. Priority order for content build-out: `offer_decision` → `phd_application` → `working_with_pi` (all required by the consulting SOP).

4. **`assets/playbooks/import_knowledge_protocol.md`** — Step 5 now correctly points to `meta/taxonomy.yaml`. Verify Step 4 atomicity examples are updated if any future merges occur.
