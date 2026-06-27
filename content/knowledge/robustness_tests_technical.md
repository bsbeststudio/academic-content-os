---
title: Robustness Tests 技术知识
type: knowledge
topic: predoc_interview
language: zh-CN
status: active
---

# Robustness Tests 技术知识

客观技术参考资料。不含个人建议。

---

## HC 标准误变体

所有 HC（异方差一致）估计量都纠正方差非恒定问题，区别在于有限样本调整方式。

| 估计量 | 调整方式 | 适用场景 |
|---|---|---|
| HC0 | 无调整 | 仅适用大样本；小样本下有偏 |
| HC1 | 乘以 n/(n-k) | Stata `vce(robust)` 默认；n > 100 时足够 |
| HC2 | 除以 (1 − h_ii)，h_ii 为杠杆值 | 更保守；小样本下更好 |
| HC3 | 除以 (1 − h_ii)² | 最保守；存在高杠杆观测时推荐 |

**选择 HC1 的理由：** 这是 Stata `vce(robust)` 的默认选项。样本量 n ≥ 100 时，HC1 与 HC2/HC3 差异可忽略不计。

---

## 二值因变量的 OLS 假设违反

因变量为二值（0/1）时，OLS 存在两类违反：

**违反一 — 异方差**
误差项方差为 `p(1−p)`，随预测值变化。这是构造性的非恒定方差。

**违反二 — 预测值超出 [0,1] 区间**
OLS 可能产生低于 0 或高于 1 的预测值，违反概率解释。

**实践含义：** HC robust 标准误解决违反一。对于违反二，probit 或 logit 是理论上更合适的替代。但实证经济学中 OLS（线性概率模型）配合 robust SE 依然普遍，因为系数可以直接解读为边际效应——但应承认 [0,1] 边界问题。

---

## Attrition 检验

处理组随机分配但参与是自愿的情况下，差异性脱落（differential attrition）会导致估计有偏。

**检验方法：** 将脱落指标对处理变量回归。如果系数显著，说明脱落与处理组相关，非随机。

**如果存在差异性脱落：** Lee (2009) bounds 提供偏识别——在最坏情形脱落假设下对处理效应进行区间估计，无需假设 MCAR。

---

## 关键概念区分

| 类型 | 定义 | 示例 |
|---|---|---|
| Robustness test | 检验结果在不同 DGP 假设下是否稳健 | Clustering SE、ordered probit 替代 OLS |
| Specification test | 检验加入/去掉控制变量后系数是否变化 | 加入人口学控制变量 |
| Sensitivity analysis | 检验结果随参数选择如何变化 | RD 中变动带宽 |

加控制变量是 **specification** test，不是 robustness test。

---

## 关联资产

- 框架：`content/frameworks/robustness_tests.md`
- 面试知识：`content/knowledge/predoc_interview.md`
