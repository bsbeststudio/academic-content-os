# Academic Content OS — Topic Structure Audit
**Date:** 2026-06-27
**Auditor:** Knowledge System Architect (Claude)
**Scope:** Full repo structural analysis — no new content generated

---

# 1. Redundant Topics

```
Topic A: career_planning ↔ Topic B: path_planning
理由：两者共同覆盖"应该走哪条路"这一核心问题。
  - career_planning.md (knowledge): 学术 vs 工业、HK PhD 限制、Why PhD 框架
  - path_planning.md (knowledge): Master / Predoc / 直申 PhD 三路径判断、OPT 约束、欧洲 Predoc
  - frameworks/career_planning.md: "Why PhD" 三层结构 + career goal 表述策略
  - frameworks/path_planning.md: 路径决策树 + 签证约束核查 + 欧洲 vs 北美逻辑
  两对 knowledge + framework 文件，语义重叠 > 70%。
  "为什么读 PhD"同时出现在两个 framework 中（career_planning 的 Why PhD 框架，
  path_planning 的路径决策树）。
建议：MERGE INTO ONE TOPIC: academic_path_decision
  - knowledge 合并为 path_planning.md（保留，扩充 career 维度）
  - framework 合并为 path_decision_framework.md
  - career_planning 降级为 path_planning 的子节点

Topic A: research_interest (framework) ↔ Topic B: research_interest_transition (framework)
理由：两个 framework 共享同一底层原则（"延伸不是转变"），taxonomy 已注明它们
  构成"两连问"，必须作为整体训练。三步结构几乎相同（起点 → 延伸 → 落地）。
  两个文件分开存在导致训练时需要人为协调一致性。
建议：MERGE INTO ONE FRAMEWORK: research_interest_narrative_framework.md
  保留两题的分别示例答案，但放在同一框架文件中。
  taxonomy subtopic 保留 research_interest_motivation + research_interest_transition，
  但指向同一 framework 文件。

Topic A: mock_interview (topic) ↔ Topic B: behavioral_interview (topic)
理由：behavioral_interview 是 mock_interview 问题集结构中的第5个模块（见
  frameworks/mock_interview.md）。两个 topic 各有独立的 knowledge + framework 文件，
  但 behavioral_interview 没有独立的面试场景，它只在 mock_interview 中出现。
  knowledge/behavioral_interview.md 的内容（高频题 + STAR 结构）完全可以
  作为 mock_interview 知识文件的一个章节存在。
建议：MERGE behavioral_interview INTO mock_interview
  behavioral_interview 框架和知识合并为 mock_interview 的子节点，
  不再作为独立 topic。

Topic A: why_this_lab (taxonomy) ↔ Topic B: research_interest_narrative (taxonomy)
理由：taxonomy.yaml 已标注 why_this_lab 与 research_interest_narrative "有重叠，待拆分"。
  why_this_lab 当前无任何内容文件。"Why this lab"问题在 research_interest.md
  framework 中已被覆盖（第三层：落地到具体 lab）。
建议：MERGE why_this_lab INTO research_interest_narrative，消除空 topic。
```

---

# 2. Over-Split Topics

```
Parent Concept: 路径决策（Which path to take）
Current Split:
  - content/knowledge/career_planning.md
  - content/knowledge/path_planning.md
  - content/frameworks/career_planning.md
  - content/frameworks/path_planning.md
  - content/frameworks/predoc_decision.md（不完整，无 frontmatter）
  - content/decision_rules/predoc_path_selection.md（101行，混杂10条规则）
建议：CONSOLIDATE INTO 2 FILES
  - knowledge/academic_path_planning.md（合并两个 knowledge）
  - frameworks/path_decision_framework.md（合并三个 framework）
  decision_rule 中路径相关规则（规则 1–3，8–9）留在 predoc_path_selection，
  其余规则拆出（见第3节）

Parent Concept: 研究兴趣叙事（Research Interest Narrative）
Current Split:
  - content/frameworks/research_interest.md
  - content/frameworks/research_interest_transition.md
  - content/decision_rules/research_interest_transition.md（assets/ 和 content/ 各一份）
  - taxonomy subtopic: research_interest_motivation + research_interest_transition
建议：MERGE frameworks 为一个文件（见第1节）
  decision_rule 文件保留但仅保留 content/ 版本，删除 assets/ 副本。

Parent Concept: Predoc 面试 Coaching（教练视角）
Current Split:
  - content/coaching/predoc_interview_principles.md（76行）
  - content/coaching/predoc_interview_patterns.md（79行）
  - content/coaching/predoc_interview_red_lines.md（103行）
理由：principles 和 patterns 存在大量语义重叠——principles 中多个原则
  直接描述了 patterns 中出现的诊断模式（如"内容问题与形式问题分开"）。
  两者的使用场景相同（session 准备），不需要分开查找。
建议：MERGE principles + patterns INTO predoc_interview_coaching.md
  red_lines 保持独立（有独特功能：训练前必读红线清单）。
```

---

# 3. Under-Split Topics

```
Topic: content/decision_rules/predoc_path_selection.md（101行，10条规则）
理由：该文件名为"路径选择"，但内容横跨 5 个不相关领域：
  - 路径选择（规则 1–3）→ 属于 path_planning topic
  - 面试红线补救（规则 4）→ 属于 predoc_interview topic
  - PI 沟通方向变更（规则 5）→ 属于 pi_communication topic
  - Coding Exercise 表现（规则 6）→ 属于 predoc_interview / coding_exercise topic
  - CV/材料结构（规则 7、10）→ 属于 cv / cover_letter topic
  - 职业规划表述（规则 8–9）→ 属于 career_planning topic
建议拆分为：
  - decision_rules/path_selection.md（规则 1–3，核心路径决策）
  - decision_rules/interview_recovery.md（规则 4、6，面试中的实时策略）
  - decision_rules/pi_communication.md（规则 5，PI 关系）→ 或并入 pi_communication topic
  - decision_rules/materials_structure.md（规则 7、10，申请材料）→ 或并入 cover_letter / cv

Topic: content/coaching/common_mistakes.md（93行，18条跨 topic 错误）
理由：18条错误分属 5 个 topic（申请材料、研究经历、面试、PI 关系、推荐信），
  按 topic 查找时无法直接定位。作为 cross-topic 文件功能正确，但内部没有
  按 topic 分组的索引，导致与各 topic 自有的 coaching 内容重复风险高。
建议拆分为：
  - common_mistakes/application_materials_mistakes.md（错误 1–5）
  - common_mistakes/interview_mistakes.md（错误 9–12）
  - common_mistakes/pi_relationship_mistakes.md（错误 13–15）
  - common_mistakes/recommendation_mistakes.md（错误 16–18）
  或：保持单文件但在每个 topic 文件中增加到对应错误的 anchor 链接。
```

---

# 4. Misclassified Topics

```
Topic: content/frameworks/predoc_decision.md
当前类型: framework（位于 frameworks/ 目录）
建议类型: decision_rule
理由：内容是一棵决策树（"Do you want a research career? → Yes → ...?"），
  这是 decision_rule 的典型形式。文件无 frontmatter，内容不完整（仅 stub）。
  与 content/decision_rules/predoc_path_selection.md 功能重复。
建议：DELETE（内容完整版已在 predoc_path_selection.md）或
  补全后迁移至 decision_rules/。

Topic: content/SOP/predoc_interview_preparation_sop.md
当前类型: type: playbook（frontmatter 声明）
建议类型: type: SOP
理由：文件位于 content/SOP/ 目录，命名含 _sop，内容是多步骤顺序工作流，
  符合 SOP 的结构定义。frontmatter 中 type: playbook 与目录和命名不一致。
建议：修正 frontmatter type 为 SOP。

Topic: content/coaching/general_principles.md
当前类型: coaching
建议类型: framework
理由：文件包含 6 条可以跨 topic 重复应用的结构性判断规则（如"信号可验证性原则"、
  "以评估者为中心原则"）。这是 framework 的标准形式，而非教练经验记录。
  coaching 类型应该是教练视角的主观经验；general_principles 是客观判断准则。
建议：迁移至 content/frameworks/core_principles.md，type 改为 framework。

Topic: content/coaching/mental_models.md
当前类型: coaching
建议类型: framework
理由：mental_models 是结构稳定的认知框架（如"PI 是在招工作人员"、
  "委员会是信息处理机器"），可以独立于教练经验被直接应用。
  coaching 类型暗示主观性和经验性，但 mental_models 内容是客观结构描述。
建议：迁移至 content/frameworks/mental_models.md，type 改为 framework，
  或创建 content/frameworks/mental_models/ 目录统一管理。

Topic: content/knowledge/predoc.md
当前类型: knowledge（status: draft，内容全为占位符 "..."）
建议类型: 删除或 stub 标注
理由：文件内容为空骨架（7个章节全为"..."），无实质知识。
  content/knowledge/predoc_strategy.md 已覆盖其应有内容。
建议：删除 predoc.md，或将其定位明确为"Predoc 基础定义"并补全，
  避免与 predoc_strategy.md 内容重叠。
```

---

# 5. Missing Coverage

```
Missing Topic: PhD Application System（PhD 申请策略）
重要性: High
理由：taxonomy.yaml 中 phd_application topic 已存在但内容为空（"内容待积累"）。
  这是 predoc lifecycle 的核心下游节点，缺失导致咨询 SOP Step 8 无内容支撑。
建议新增位置: content/knowledge/phd_application_strategy.md
  需要覆盖：申请时间线、推荐信请求策略、Statement of Purpose 结构、
  PhD vs Predoc 时间线协调。

Missing Topic: Offer Decision 框架
重要性: High
理由：SOP 的 Step 8 是"Offer Decision"，但 offer_decision topic 无任何内容文件。
  taxonomy 中已预留 topic，咨询 SOP 中有完整的输入/输出定义，但框架本身缺失。
建议新增位置:
  - content/frameworks/offer_decision.md（以 PhD placement 记录为核心评估维度）
  - content/decision_rules/offer_comparison.md

Missing Topic: First-year PhD Adaptation（PhD 一年级适应）
重要性: Medium
理由：当前系统覆盖 predoc 路径直到"进入 PhD"，但进入 PhD 后的系统性适应
  完全缺失。这是服务于已有 predoc offer 候选人的自然延伸。
建议新增位置: content/knowledge/phd_year1_adaptation.md

Missing Topic: Research Productivity System（科研生产力系统）
重要性: Medium
理由：现有内容覆盖"如何讲述研究"，但不覆盖"如何做研究"——
  文献管理、写作系统、进度管理、与 PI 的周报结构等均缺失。
建议新增位置: content/SOP/research_productivity_sop.md

Missing Topic: Academic Writing System（学术写作）
重要性: Medium
理由：taxonomy 中 replication_literature 有 subtopic 但内容空。
  当前 replication_walkthrough framework 只覆盖"面试中如何讲"，
  不覆盖"如何真正做 replication"。
建议新增位置: content/knowledge/academic_writing.md
  content/frameworks/paper_replication_methodology.md

Missing Topic: Working with PI（进组后管理）
重要性: Medium
理由：pi_communication.md 覆盖冷邮件和关系管理，但 working_with_pi
  在 taxonomy 中存在（"进组后"）却无内容。
  进组后的第一个月行为、任务接受策略、进度汇报结构均缺失。
建议新增位置: content/knowledge/working_with_pi.md

Missing Topic: Staggered DID / 计量方法
重要性: Medium
理由：taxonomy 中已预留 staggered_did topic，robustness_tests 框架和知识已有，
  但没有系统覆盖 Callaway-Sant'Anna、Sun-Abraham 等方法的知识文件。
  这是 Coding Exercise 和技术面试中的高频考察内容。
建议新增位置: content/knowledge/staggered_did_methods.md

Missing Topic: CV Structure（简历）
重要性: Low（已有 knowledge/cv.md，但无 framework）
理由：cv.md 是 knowledge 文件，但没有对应的 framework 文件（定义 CV 结构的
  决策逻辑）。与其他 topic（cover_letter、recommendation_letter）不对称。
建议新增位置: content/frameworks/cv_structure.md
```

---

# 6. Abstraction Opportunities

```
Candidate Knowledge → Framework:
"延伸而非转变"重构策略（Reframe-as-Extension）
理由：
  - 在 research_interest_transition.md 中作为核心策略
  - 在 pi_communication.md 中再次出现（方向变更时用延伸框架）
  - 在 career_planning.md 中出现（新方向 = 对旧问题的当代化）
  - 在 common_mistakes.md 错误 14 中隐含
  这是一个跨 topic 的通用叙事策略，不只适用于面试，也适用于 PI 沟通、
  申请材料、SOP。
建议升级为: content/frameworks/reframe_as_extension.md（cross-topic framework）

Candidate Knowledge → Decision Rule:
"用强信号替代，而非直接否认弱信号"
理由：
  - 出现在 knowledge/mock_interview.md（红线补救章节）
  - 出现在 decision_rules/predoc_path_selection.md（规则 4）
  - 隐含在 coaching/predoc_interview_red_lines.md 的多条规则中
  这是一个独立的、可单独查询的决策规则，当前分散在三处。
建议升级为: content/decision_rules/signal_replacement.md（独立决策规则）

Candidate Knowledge → Framework:
"阶段性资产建设"决策框架
理由：
  - coaching/general_principles.md 原则 4（阶段性投资原则）
  - knowledge/path_planning.md（每个阶段的核心任务表格）
  - decision_rules/predoc_path_selection.md 规则 1–2（缺失资产优先）
  这个框架跨越路径规划、predoc 选择、PhD 申请全链条，且逻辑高度结构化，
  适合升级为独立 framework。
建议升级为: content/frameworks/staged_asset_building.md

Candidate Knowledge → Framework:
"以评估者为中心"原则（Evaluator-Centric Design）
理由：
  - coaching/general_principles.md 原则 2
  - frameworks/cover_letter.md（PI-centered writing）
  - frameworks/future_plans.md（贡献在前，个人发展在后）
  - frameworks/mock_interview.md（面试官信号解读）
  - coaching/mental_models.md 模型 1 和 2
  这一原则在至少 5 个 topic 中重复出现，是整个系统的底层设计原则之一。
建议升级为: content/frameworks/evaluator_centric_design.md（cross-topic framework）
  并在所有相关 framework 中引用，而非各自独立叙述。
```

---

# 7. System Design Recommendations

## Should Merge

- `career_planning` + `path_planning` → `academic_path_decision`（knowledge + framework 各合并一份）
- `research_interest` + `research_interest_transition`（frameworks）→ 单一 framework 文件
- `behavioral_interview` 并入 `mock_interview`（降级为子节点）
- `why_this_lab`（空 topic）并入 `research_interest_narrative`
- `coaching/predoc_interview_principles.md` + `predoc_interview_patterns.md` → `predoc_interview_coaching.md`

## Should Split

- `decision_rules/predoc_path_selection.md`（10条规则，5个 topic）→ 按 topic 拆分为 4 个文件
- `coaching/common_mistakes.md`（18条跨 topic 错误）→ 按 topic 建立 anchor 索引，或拆分

## Should Elevate

- `coaching/general_principles.md` → `frameworks/core_principles.md`（coaching → framework）
- `coaching/mental_models.md` → `frameworks/mental_models.md`（coaching → framework）
- "延伸而非转变"策略 → `frameworks/reframe_as_extension.md`（知识点 → 独立 framework）
- "用强信号替代弱信号" → `decision_rules/signal_replacement.md`（散落知识 → 独立 decision_rule）
- "阶段性资产建设" → `frameworks/staged_asset_building.md`（散落原则 → 独立 framework）

## Should Downgrade

- `content/frameworks/predoc_decision.md`（空壳决策树）→ 删除（已被 predoc_path_selection 覆盖）

## Taxonomy Fixes

- `config/taxonomy.yaml`：当前为空文件（无内容），与 `meta/taxonomy.yaml` 重复存在。
  建议：删除 `config/taxonomy.yaml` 或合并为单一 taxonomy 入口。
- `taxonomy/` 目录（含 topics/ 和 hubs/ YAML）与 `meta/taxonomy.yaml` 存在三套 taxonomy 并存。
  建议：确认 single source of truth，其余删除或设为生成物。
- `assets/decision_rules/` 目录（4 个文件）与 `content/decision_rules/`（相同 4 个文件，内容完全一致）：
  **100% 重复**。建议：删除 `assets/decision_rules/`，taxonomy YAML 中更新引用路径。
- `assets/playbooks/predoc_interview_preparation_sop.md` 与 `content/SOP/predoc_interview_preparation_sop.md`：
  **100% 重复**。建议：删除 `assets/playbooks/` 版本，保留 `content/SOP/` 版本。

## Structural Risks

- **双重存储风险（HIGH）：** `assets/decision_rules/` 和 `content/decision_rules/` 完全重复，
  未来更新任一处时另一处不会同步，必然导致版本分叉。需立即清除一个来源。

- **Taxonomy 三元悖论（HIGH）：** `config/taxonomy.yaml`（空）、`meta/taxonomy.yaml`（完整）、
  `taxonomy/` 目录 YAML（部分）三套并存，系统无明确 single source of truth。
  当 topic 新增时，需要同步修改三处，极易遗漏。

- **Predoc-only 单点集中风险（MEDIUM）：** 当前 80%+ 内容集中于 predoc_interview topic，
  缺乏 PhD Application、First-year Adaptation、Offer Decision 等下游内容，
  系统只能服务于 predoc 面试阶段，无法覆盖完整的学术职业路径。

- **coaching / framework 类型边界模糊（MEDIUM）：** general_principles 和 mental_models
  被标注为 coaching 但功能上是 framework，导致框架检索时这两个高价值文件不会被
  framework 查询命中。

- **空 topic 污染 taxonomy（LOW）：** why_this_lab、working_with_pi、phd_application、
  offer_decision、sop、staggered_did 等 6 个 topic 在 taxonomy 中有条目但无内容文件。
  这些空节点会误导基于 taxonomy 的检索和内容完整性验证。
```
