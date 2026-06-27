# Refactor Execution Report
**Date:** 2026-06-27
**Scope:** Full structural refactor per audit_topic_structure.md

---

## 1. Files Changed

### Created (Merges)
| New File | Merged From |
|---|---|
| `content/knowledge/academic_path_decision.md` | `career_planning.md` + `path_planning.md` |
| `content/frameworks/academic_path_decision.md` | `frameworks/career_planning.md` + `frameworks/path_planning.md` |
| `content/frameworks/research_interest_narrative.md` | `frameworks/research_interest.md` + `frameworks/research_interest_transition.md` |
| `content/knowledge/mock_interview.md` (updated) | behavioral_interview content merged in |
| `content/coaching/predoc_interview_coaching.md` | `predoc_interview_principles.md` + `predoc_interview_patterns.md` |

### Created (Splits)
| New File | Split From | Rules |
|---|---|---|
| `content/decision_rules/path_selection.md` | `predoc_path_selection.md` | 1–3 |
| `content/decision_rules/interview_recovery.md` | `predoc_path_selection.md` | 4, 6, 8, 9 |
| `content/decision_rules/materials_structure.md` | `predoc_path_selection.md` | 7, 10 |
| `content/knowledge/pi_communication.md` (updated) | rule 5 merged in | 5 |

### Created (Elevations)
| New File | Elevated From |
|---|---|
| `content/frameworks/core_principles.md` | `content/coaching/general_principles.md` |
| `content/frameworks/mental_models.md` | `content/coaching/mental_models.md` |
| `content/frameworks/reframe_as_extension.md` | Scattered across 4+ files |
| `content/frameworks/evaluator_centric_design.md` | Scattered across 5+ files |
| `content/frameworks/staged_asset_building.md` | Scattered across 3 files |
| `content/decision_rules/signal_replacement.md` | Scattered across 3 files |

### Deleted
| File | Reason |
|---|---|
| `content/knowledge/career_planning.md` | Merged → academic_path_decision |
| `content/knowledge/path_planning.md` | Merged → academic_path_decision |
| `content/frameworks/career_planning.md` | Merged → academic_path_decision |
| `content/frameworks/path_planning.md` | Merged → academic_path_decision |
| `content/frameworks/research_interest.md` | Merged → research_interest_narrative |
| `content/frameworks/research_interest_transition.md` | Merged → research_interest_narrative |
| `content/coaching/predoc_interview_principles.md` | Merged → predoc_interview_coaching |
| `content/coaching/predoc_interview_patterns.md` | Merged → predoc_interview_coaching |
| `content/coaching/general_principles.md` | Elevated → frameworks/core_principles |
| `content/coaching/mental_models.md` | Elevated → frameworks/mental_models |
| `content/decision_rules/predoc_path_selection.md` | Split → 3 files + pi_communication |
| `content/knowledge/behavioral_interview.md` | Merged → mock_interview |
| `content/knowledge/predoc.md` | Empty stub, content covered by predoc_strategy |
| `content/frameworks/predoc_decision.md` | Empty stub, covered by path_selection |
| `assets/decision_rules/ai_usage.md` | 100% duplicate of content/decision_rules/ |
| `assets/decision_rules/background_fit.md` | 100% duplicate of content/decision_rules/ |
| `assets/decision_rules/identification_honesty.md` | 100% duplicate of content/decision_rules/ |
| `assets/decision_rules/research_interest_transition.md` | 100% duplicate of content/decision_rules/ |
| `assets/playbooks/predoc_interview_preparation_sop.md` | 100% duplicate of content/SOP/ |
| `config/taxonomy.yaml` | Empty file, superseded by meta/taxonomy.yaml |
| `taxonomy/topics/predoc.yaml` | Superseded by meta/taxonomy.yaml v3.0 |
| `taxonomy/topics/predoc_interview.yaml` | Superseded by meta/taxonomy.yaml v3.0 |
| `taxonomy/hubs/academic-careers.yaml` | Superseded by meta/taxonomy.yaml v3.0 |

### Updated (Reference Fixes)
`content/decision_rules/research_interest_transition.md`,
`content/coaching/predoc_interview_red_lines.md`,
`content/frameworks/answer_structure.md`,
`content/frameworks/cover_letter.md`,
`content/frameworks/behavioral_interview.md`,
`content/frameworks/recommendation_letter.md`,
`content/frameworks/ai_assisted_coding.md`,
`content/frameworks/background_fit.md`,
`content/frameworks/causal_inference.md`,
`content/coaching/common_mistakes.md`,
`content/knowledge/predoc_strategy.md`,
`content/knowledge/recommendation_letter.md`,
`content/knowledge/predoc_interview.md`,
`content/SOP/predoc_interview_preparation_sop.md`,
`content/SOP/academic_career_planning_sop.md`,
`assets/faq/predoc_application.md`,
`assets/golden_sentences/academic_career.md`,
`assets/checklists/predoc_interview_24h.md`,
`assets/playbooks/import_knowledge_protocol.md`

---

## 2. New Folder Structure

```
content/
├── SOP/
│   ├── academic_career_planning_sop.md
│   └── predoc_interview_preparation_sop.md
├── coaching/                            # 3 files (was 6)
│   ├── common_mistakes.md
│   ├── predoc_interview_coaching.md     # NEW (merge of principles + patterns)
│   └── predoc_interview_red_lines.md
├── decision_rules/                      # 8 files (was 5)
│   ├── ai_usage.md
│   ├── background_fit.md
│   ├── identification_honesty.md
│   ├── interview_recovery.md            # NEW (split)
│   ├── materials_structure.md           # NEW (split)
│   ├── path_selection.md                # NEW (split)
│   ├── research_interest_transition.md
│   └── signal_replacement.md           # NEW (elevation)
├── frameworks/                          # 21 files (was 19)
│   ├── academic_path_decision.md        # NEW (merge)
│   ├── ai_assisted_coding.md
│   ├── answer_structure.md
│   ├── background_fit.md
│   ├── behavioral_interview.md
│   ├── causal_inference.md
│   ├── core_principles.md              # NEW (elevation from coaching)
│   ├── cover_letter.md
│   ├── evaluator_centric_design.md     # NEW (elevation)
│   ├── field_experiment_design.md
│   ├── future_plans.md
│   ├── mental_models.md               # NEW (elevation from coaching)
│   ├── mock_interview.md
│   ├── recommendation_letter.md
│   ├── reframe_as_extension.md        # NEW (elevation)
│   ├── replication_walkthrough.md
│   ├── research_experience.md
│   ├── research_interest_narrative.md # NEW (merge)
│   ├── robustness_tests.md
│   ├── staged_asset_building.md       # NEW (elevation)
│   └── visualization_interpretation.md
├── knowledge/                          # 10 files (was 13)
│   ├── academic_path_decision.md       # NEW (merge)
│   ├── cover_letter.md
│   ├── cv.md
│   ├── mock_interview.md              # UPDATED (behavioral merged in)
│   ├── pi_communication.md            # UPDATED (rule 5 added)
│   ├── predoc_interview.md
│   ├── predoc_strategy.md
│   ├── recommendation_letter.md
│   ├── research_experience.md
│   └── robustness_tests_technical.md
└── opinions/
    └── predoc.md

meta/
└── taxonomy.yaml  ← SINGLE SOURCE OF TRUTH (v3.0)

assets/
├── checklists/         (unchanged)
├── faq/                (1 ref fixed)
├── golden_sentences/   (1 ref fixed)
└── playbooks/
    └── import_knowledge_protocol.md  (updated for new taxonomy + filenames)
```

---

## 3. Unresolved Conflicts

None. All planned transformations executed without content conflicts.

**Note on `merged_from` / `split_from` / `elevated_from` provenance fields:** New files contain YAML frontmatter metadata referencing the deleted source files for traceability. These are intentional provenance records, not broken links.

---

## 4. Verification Checklist

- [x] **No duplicate topics** — career_planning/path_planning merged; behavioral_interview merged; why_this_lab merged
- [x] **No duplicate files** — assets/decision_rules/ (4 files) deleted; duplicate SOP deleted
- [x] **Single taxonomy source** — meta/taxonomy.yaml v3.0; config/taxonomy.yaml deleted; taxonomy/ YAML deleted
- [x] **All 61 taxonomy asset references resolve to existing files** — verified by script
- [x] **Zero orphan content files** — verified by script
- [x] **Clean type separation:**
  - `coaching/` = 3 files: all genuine teaching/coaching content
  - `frameworks/` = 21 files: includes 5 newly elevated cross-topic frameworks
  - `decision_rules/` = 8 files: atomic, topic-scoped rules
- [x] **All broken internal references fixed** — 19 files updated
- [x] **decision_rules/ has single canonical location** — content/decision_rules/ only
