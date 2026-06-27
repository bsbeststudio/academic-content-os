---
title: Research Asset Building 缺口补强优先级
type: decision_rule
topic: predoc_strategy
language: zh-CN
status: active
related_framework: content/frameworks/research_asset_building.md
---

# Research Asset Building 缺口补强优先级

本规则定义四类资产缺口（A=推荐信、B=研究经历、C=Coding、D=叙事）的执行顺序。

## 优先级排序

**Step 0：工作授权约束前置**  
IF 候选人存在 OPT / 工作授权约束  
→ 首先排除无法解决授权问题的岗位，否则所有补强都是无效投入  
→ 见 `visa_constraints` topic  

**Step 1：推荐信优先（缺口 A）**  
IF 推荐信组合存在明显缺口（无强力推荐人 / 推荐人拒绝 / 组合不匹配）  
→ 优先执行缺口 A 补强路径  
REASON：推荐信是面试获取率的第一影响因子，其他缺口补强在推荐信不达标时收益边际递减  

**Step 2：研究经历（缺口 B）**  
IF 推荐信已确认 AND 研究经历不可叙述或严重不足  
→ 执行缺口 B 补强路径  
REASON：研究经历是 Predoc 招聘的核心信号，且与推荐信常互为因果（有经历才有可写的推荐）  

**Step 3：叙事一致性并行（缺口 D）**  
在 A、B 补强进行中，同步执行叙事修复  
REASON：叙事修复不产生新信号，但整合和放大现有信号；应全程并行而非最后才做  

**Step 4：Coding 最后（缺口 C）**  
IF 前三项已达可用状态  
→ 再投入 Coding 补强  
REASON：Coding 是门槛性信号，而非差异化信号。在 A/B 未解决时，Coding 补强的竞争优势边际接近零  

## 特殊情形

**时间窗口 <1 个月：**  
只执行叙事整合（D）和 Coding 样本微调（C3），不尝试启动 A/B 新信号建设。

**工作授权为硬约束且无法解决：**  
跳出本规则，转入 Profile Diagnosis Dimension 4（Positioning）进行市场重定向。
