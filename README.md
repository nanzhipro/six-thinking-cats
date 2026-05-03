---
title: 一套六帽方法，把纠结变成决策树
slug: six-thinking-cats
summary: 把六顶思考帽工程化成六只思考猫，用结构化分析把纠结的决策收敛成可执行判断与 Mermaid 决策树。
description: Six Thinking Cats 是一个面向个人决策场景的 skill 仓库，把六顶思考帽与苏格拉底式探询结合成可执行的分析流程。它通过父代理编排与六只思考猫分工，把模糊选择整理成结构化结论和 Mermaid 决策树。
---

<!-- markdownlint-disable MD033 -->
<p align="center">
  <img src="imgs/logo.png" alt="Six Thinking Cats logo showing six cats representing the six thinking hats" width="320">
</p>
<!-- markdownlint-enable MD033 -->

六只思考猫是一个面向个人决策场景的 prompt-and-reference 仓库。它把六顶思考帽与苏格拉底式探询结合起来，用六只彼此独立的“思考猫”帮助代理围绕同一个决策问题完成结构化分析，并最终输出一棵可执行的 Mermaid 决策树。

这不是应用代码仓库，也不是通用框架包。这个仓库的核心交付物是 [SKILL.md](SKILL.md)；README 只负责说明这个 skill 是什么、适合什么场景、应该从哪里开始看。

## Overview

* **目标**：把模糊的“我该怎么选”收敛为可执行的判断与下一步行动。
* **方法**：本仓库默认采用父代理先收集决策信息、再由六只猫按各自视角独立分析的工程化编排。
* **交付**：结构化的六猫总结，加上一棵 Mermaid 决策树。
* **约束**：每只猫只在自己的视角里思考，只有最后的蓝猫收束阶段允许跨猫整合。
* **理论边界**：这里描述的是本仓库的默认执行方式，不是把六顶思考帽原著解释成唯一固定顺序。

## Six Thinking Hats, Briefly

* 六顶思考帽由 Edward de Bono 提出，核心不是给人贴标签，而是把思考过程拆成六种可切换的模式。
* 它强调“一次只用一种思维方式”，避免把事实、情绪、风险和创意混在一起，导致越想越乱。
* 六顶帽子分别关注：白帽看事实，黄帽看价值，黑帽看风险，红帽看直觉，绿帽看新方案，蓝帽管流程。
* 本仓库把这六种思维模式工程化成六只“思考猫”，方便代理在真实决策里分阶段执行；更完整的理论背景见 [references/framework.md](references/framework.md)。

## Install / Update

如果你通过 `skills` CLI 使用这个 skill，可以直接从仓库安装：

```bash
npx skills add nanzhipro/six-thinking-cats
```

这个 skill 的安装名是 `six-thinking-cats`。安装后可按 skill 名更新：

```bash
npx skills update six-thinking-cats
```

如果希望跳过交互确认，可额外加 `-y`；如果希望安装到全局作用域，可改用 `-g`。

## Best For

* 工作决策：换工作、职业转型、是否接项目。
* 生活决策：搬家、买房、换车、教育选择。
* 商业决策：创业、合作、产品方向、业务判断。
* 投资决策：资产配置、标的选择、风险取舍。
* 模糊纠结：用户没有明确选项，但明确表达了犹豫、卡住、拿不定主意。

## How It Works

这个 skill 当前采用“父代理编排 + 猫 subagent 执行”的**默认模型**。它服务于仓库的执行稳定性，**不代表六顶思考帽理论只有这一种顺序**：

1. 父代理先获取用户正在做的具体决策。
2. 父代理先做内部的场景深度思考，再补齐必要信息。
3. 父代理整理一份共享资料包，作为所有猫 subagent 的共同输入。
4. ⚪ 白猫事实、🟡 黄猫机会、⚫ 黑猫风险、🔴 红猫直觉、🟢 绿猫方案并行分析。
5. 🔵 蓝猫收束统一整合结果，整理当前综合判断、待验证分歧与下一步行动，并输出 Mermaid 决策树。

详细规约、工作流图和不可协商约束见 [SKILL.md](SKILL.md)。

## Visual Language

这个 skill 采用统一的视觉命名规约来保持阶段辨识度。宿主 UI 的真实颜色不可直接配置，但所有 subagent 标签和阶段标题都使用“emoji + 猫名 + 职责”的固定映射：

* 🔵 蓝猫启动：定义边界、时间窗口、缺失信息清单。
* ⚪ 白猫事实：整理事实、假设和信息缺口。
* 🟡 黄猫机会：盘点价值、收益和上行空间。
* ⚫ 黑猫风险：识别风险、脆弱点和退路。
* 🔴 红猫直觉：表达情绪、直觉和隐藏顾虑。
* 🟢 绿猫方案：提出新路径、试验和组合方案。
* 🔵 蓝猫收束：跨猫整合、阶段性结论、待验证分歧、下一步行动。

## Repository Layout

* [SKILL.md](SKILL.md)：主入口，定义触发条件、执行模型、流程规约、输出契约和视觉命名规约。
* [references/framework.md](references/framework.md)：六顶思考帽整体框架、阶段标题、场景权重和问题链导航。
* [references/socratic-questioning.md](references/socratic-questioning.md)：通用探询原则、提问节奏和共享资料包约束。
* [references/blue-cat.md](references/blue-cat.md)：🔵 蓝猫启动 / 🔵 蓝猫收束的职责、输入输出和收束要求。
* [references/white-cat.md](references/white-cat.md)：⚪ 白猫事实的事实分层与信息质量规则。
* [references/yellow-cat.md](references/yellow-cat.md)：🟡 黄猫机会的上行空间与价值判断规则。
* [references/black-cat.md](references/black-cat.md)：⚫ 黑猫风险的风险分层、最坏情景与安全垫规则。
* [references/red-cat.md](references/red-cat.md)：🔴 红猫直觉的情绪、历史投射与隐藏顾虑规则。
* [references/green-cat.md](references/green-cat.md)：🟢 绿猫方案的新路径、试验与组合方案规则。
* [AGENTS.md](AGENTS.md)：仓库级维护约定，约束如何修改这个 skill 与 reference 文档。

## Start Here

1. 想理解这个 skill 的运行方式，先读 [SKILL.md](SKILL.md)。
2. 想理解六顶思考帽的整体框架，再读 [references/framework.md](references/framework.md)。
3. 想理解提问边界与信息采集方式，读 [references/socratic-questioning.md](references/socratic-questioning.md)。
4. 想修改某一只猫的行为，直接读对应的 cat reference 文件。

## Maintenance Notes

* **README 保持高层概览**，不复制 [SKILL.md](SKILL.md) 或 reference 文件里的长段细节。
* 工作流骨架与不可协商约束写在 [SKILL.md](SKILL.md)；细化规则沉到 [references/](references) 下。
* 如果 README 提到流程，要明确那是本仓库的默认执行编排，而不是六顶思考帽理论的唯一合法顺序。
* 修改工作流或命名规约时，要同步检查 [SKILL.md](SKILL.md)、[AGENTS.md](AGENTS.md) 与相关 reference 文件。
* **最终交付始终是 Mermaid 决策树**，而不是泛化总结或空泛建议。
