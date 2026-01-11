---
title: AI：Advanced Tool Use
name: advanced_tool_use
date: 2025-12-21
draft: false
tags:
  - blog
  - AI
share: "true"
---

## Advanced Tool Use

来源：[`https://www.anthropic.com/engineering/advanced-tool-use`](https://www.anthropic.com/engineering/advanced-tool-use)

### 图示

Tool Search Tool 对比图（Context Usage: Traditional vs. Tool Search Tool）

![](/img/advanced_tool_use.png)

Programmatic Tool Calling 流程图（Programmatic Tool Calling Flow）

![](/img/advanced_tool_use-2.png)

### 核心要点

- **整体目标**：解决三个老问题  
  - **工具太多**：定义太长，把上下文挤爆  
  - **链路太长**：工具链一长，来回调用慢且耗 tokens  
  - **仅靠 Schema 不够**：只有 JSON Schema 时，模型仍会经常填错参数/用错工具

- **Tool Search Tool（工具搜索）**：  
  不再一次性把几十上百个工具定义全部塞进上下文，而是只提前加载一个“搜索工具 + 少数高频工具”。当 Claude 需要某类能力时，先用搜索工具按名字/描述去检索，再按需把少量匹配工具的定义展开进上下文。  
  - **收益**：减少 token 开销（官方示例：上下文消耗可降低 80%+），同时降低“选错工具”的概率  
  - **适用**：MCP 多服务、工具数量 10+ 的场景

- **Programmatic Tool Calling（编程式工具调用）**：  
  以前是“自然语言 → 一次推理 → 调一个工具 → 结果全丢回模型上下文”，多步流程就意味着多次推理 + 大量中间数据灌进上下文。现在改成：Claude 写一段 Python 脚本，在沙盒里 orchestrate 工具调用（循环、并发、条件分支都写在代码里），工具结果先在代码里处理，最后只把“结论”返回给 Claude。  
  - **收益**：大数据场景下只让模型看到汇总结果，而不是几 MB 的原始日志；显著省 tokens、降延迟，也更不容易“算错账”

- **Tool Use Examples（工具使用示例）**：  
  JSON Schema 只能描述“结构合法”，但描述不了“怎么用才对”。因此 Anthropic 在工具定义旁补充高质量的示例调用，显著提升准确率。

### 启发

以后设计“AI + 工具”的系统，可以记三条：

1. **工具多** → 用“搜索 + 延迟加载”，别一股脑塞定义  
2. **链路长 / 数据大** → 让模型写代码 orchestrate，把重计算放在代码里做  
3. **工具复杂** → Schema 旁边必须配高质量示例调用，不要只给一份 JSON 结构说明