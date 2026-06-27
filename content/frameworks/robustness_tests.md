---
title: Robustness Test 回答框架
type: framework
topic: coding_exercise
question: "What robustness tests did you run / would you run?"
language: zh-CN
status: active
---

# Robustness Test 回答框架

## 开口框架句

> "I think about robustness tests along three dimensions: are the standard errors correctly specified, is the sample clean, and is the functional form appropriate."

先说三维框架，再逐一展开。即使某个具体方法说错了，框架本身已经展示了方法论思维层次。

## 三个维度

**维度一 — 标准误假设**
- 基础版：HC robust SE（异方差稳健标准误）
- 如果处理变量在班级/小组层面分配：在该层面 cluster SE（更保守）
- 三种变体：HC1（Stata `vce(robust)` 默认）、HC2（leverage 调整）、HC3（高杠杆观测适用）

**维度二 — 样本完整性**
- 如果参与是自愿的：检验脱落（attrition）是否与处理组分配随机无关
- 方法：将脱落指标对处理变量回归
- 如果脱落非随机：用 Lee bounds 进行偏识别

**维度三 — 函数形式**
- 如果因变量是二值/有序分类变量：用 ordered probit 作为 OLS 的替代
- 检验线性设定是否影响结论

## 示例回答（英文，直接用于面试）

> "I can think of three directions. On standard errors—beyond HC1, if treatment was assigned at the classroom level, clustering at that level would be more conservative. On sample integrity—participation was voluntary and some children didn't complete all tasks; I'd test whether attrition is random with respect to treatment, and potentially run Lee bounds. On functional form—since the outcome is ordered categorical, ordered probit as an alternative to OLS would check whether the linear specification is driving the results."

## 常见追问

- "Why HC1 specifically? Why not HC2 or HC3?"
- "Given the binary outcome, what OLS assumption is violated beyond heteroskedasticity?"
- "What are the potential confounding variables?"
- "Why not bootstrap?"

## 关键概念区分

**Robustness test**：检验结果在不同数据生成过程假设下是否稳健（标准误设定、样本、函数形式）。

**Specification test**：检验加入/去掉控制变量后系数是否变化。这不是 robustness test。

加控制变量 ≠ robustness test。不能混淆。

## 关联资产

- 知识：`content/knowledge/robustness_tests_technical.md`
- 教练红线：`content/coaching/predoc_interview_red_lines.md`
