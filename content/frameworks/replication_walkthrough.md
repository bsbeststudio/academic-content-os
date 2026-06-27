---
title: Replication Walkthrough 回答框架
type: framework
topic: coding_exercise
question: "Walk me through your replication / coding exercise."
language: zh-CN
status: active
---

# Replication Walkthrough 回答框架

## 核心原则

> "I do the thinking. AI does the typing."

Walkthrough 必须证明：所有智识判断由候选人主导，AI 只负责语法生成。

## 三阶段结构

**第一阶段 — 阅读与设定规格（写代码之前）**
- 仔细读论文。
- 识别：因变量、处理变量、控制变量、样本限制、标准误方式。
- 在接触任何 AI 工具之前，写出自己的 specification memo。

**第二阶段 — 执行（AI 辅助，人主导）**
- 给 AI 提供精确的、包含所有技术细节的 prompt，而不是"replicate Table 3"。
- 不直接运行 AI 输出。

**第三阶段 — 逐行验证**
运行之前：
- 对照 codebook 检查所有变量名。
- 核实样本条件与论文一致。
- 确认回归选项符合意图。
- 至少找到并修正一个具体的错误。

## 示例回答（英文，直接用于面试）

> "Before writing any code, I read through the paper carefully to understand the sample construction, treatment variable definitions, and the exact regression specifications in Tables 1 and 3. I wrote out my own specification memo—dependent variable, regressors, controls, sample restrictions—before touching any AI tool.
>
> Once I had a clear picture, I used AI to translate my specification into Stata syntax. But I didn't run the output directly. I went through every line: verified variable names against the codebook, checked the sample conditions, confirmed the vce options. I caught two issues—a variable label mismatch and a missing if-condition in the sample filter. The final numbers matched the paper, which confirmed the replication was correct."

## 常见追问

- "What role did AI play in your coding process?"
- "Can you give me a specific example of an error in the AI-generated code that you caught?"
- "How did you verify the output matched the paper's results?"
- "What software did you use?"

## 关键细节要求

必须准备好至少一个具体的 bug 描述。
"发现了变量 label 不匹配" 远比 "发现了一些错误" 有说服力。

## 关联资产

- 框架：`content/frameworks/ai_assisted_coding.md`
- 教练红线：`content/coaching/predoc_interview_red_lines.md`
- 知识：`content/knowledge/predoc_interview.md`
