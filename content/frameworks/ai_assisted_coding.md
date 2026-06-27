---
title: AI 辅助编程回答框架
type: framework
topic: coding_exercise
question: "What role did AI play in your coding? / How do you use AI in your research work?"
language: zh-CN
status: active
---

# AI 辅助编程回答框架

## 核心心智模型

> "AI 更像一个速度很快但没有研究判断能力的初级 RA——它能把 Stata 代码写得完美，但完全不知道论文要证明什么。我的工作是扮演那个知道要做什么、并且能发现初级 RA 出错的高级研究者。"

（面试时用英文表达：见黄金句子资产）

## 三步工作流

**第一步 — 先自己设计（接触 AI 之前）**
独立写出完整规格：
- 因变量
- 处理变量与控制变量
- 样本限制条件
- 标准误处理方式
- 预期输出格式

**第二步 — 精确 prompt**
不说"replicate Table 3"。
说具体规格：因变量、控制变量、vce 选项、输出格式。

**第三步 — 逐行验证（运行前）**
- 对照 codebook 核查变量名。
- 确认样本条件与论文一致。
- 确认回归选项符合意图。

## 定位原则

- 不要隐瞒 AI 使用。公开承认。
- 展示人的判断在前、AI 执行在后的工作逻辑。
- 刻意隐瞒 AI 使用反而损害诚信印象。能掌控 AI 工具才体现研究成熟度。

## 关联资产

- 框架：`content/frameworks/replication_walkthrough.md`
- 决策规则：`content/decision_rules/ai_usage.md`
- 黄金句子：`assets/golden_sentences/predoc_interview.md`
