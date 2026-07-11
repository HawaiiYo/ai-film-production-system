# 🎬 AI Filmmaking Multi-Agent System (AI电影工坊)

> AI-Native Film Production Pipeline — 让AI成为你的虚拟剧组

## 项目概述

这是一个基于Claude Code的**多Agent AI电影制作协作系统**。模拟真实电影工业的完整流程，通过多个专业化AI Agent协作，将用户的故事创意转化为结构化的、可直接用于AI视频生成的完整制作方案。

### 核心工具链
- **GPT-image-2**（OpenAI）：角色设计图、场景概念图、道具参考图、关键帧生成
- **Seedance 2.0/2.5**（字节跳动即梦AI）：图生视频、文生视频片段生成

### 核心价值
- 🎯 填补"单点AI工具"到"完整电影制作流程"之间的空白
- 🤖 通过Multi-Agent协作，确保角色/场景/风格在整部影片中的一致性
- 🎨 31位世界著名导演风格库，自动匹配最适合的导演组合
- 📋 输出结构化、可直接执行的AI生成指令，支持中英双语

## 系统架构

```
用户输入故事概念
    → 🎯 流程统筹Agent (组建虚拟剧组)
        → 🎨 导演风格Agent (匹配导演+风格指南)
        → 📖 剧本Agent (完整剧本+场景分解)
        → 👤 角色设计Agent (角色圣经+GPT-image-2 prompt)
        → 🏗️ 场景道具Agent (场景圣经+参考图prompt)
        → 🎬 分镜故事板Agent (分镜表+Seedance prompt)
        → 🔧 Prompt工程Agent (优化prompt+一致性检查)
            → 🖼️ 最终AI生成指令 (可执行输出)
```

## Agent角色说明

### 核心Agent（7个）

| Agent | 角色 | 核心产出 |
|-------|------|---------|
| 🎯 Executive Producer | 流程统筹 | 项目计划、全局风格手册、制作手册 |
| 🎨 Director Style | 导演风格 | 导演组合、视觉风格指南 |
| 📖 Screenplay | 剧本 | 完整剧本、场景列表、人物关系图 |
| 👤 Character Design | 角色设计 | 角色圣经、GPT-image-2角色prompt |
| 🏗️ Scene & Prop | 场景道具 | 场景圣经、GPT-image-2场景prompt |
| 🎬 Storyboard | 分镜故事板 | 分镜表、Seedance视频prompt |
| 🔧 Prompt Engineer | Prompt工程 | 优化后的完整AI生成指令集 |

### 扩展Agent（2个，后续开发）

| Agent | 角色 | 核心产出 |
|-------|------|---------|
| ✂️ Post-Production | 后期制作 | 剪辑节奏、调色方案、音效设计 |
| 📢 Marketing Assets | 宣传物料 | 海报设计、预告片方案 |

## 使用方式

### 触发词
- `AI电影工坊` / `AI Filmmaking` — 启动完整系统
- `虚拟剧组` — 组建虚拟剧组
- `电影策划` — 从概念开始策划
- `角色设计` / `场景设计` / `分镜设计` — 单独调用特定Agent
- `导演风格匹配` — 分析导演风格适配

### 工作流
1. 用户提供故事概念或剧本
2. 统筹Agent解析需求，组建虚拟剧组
3. 导演风格Agent匹配导演组合，输出风格指南
4. 剧本Agent生成完整剧本
5. 角色/场景Agent生成视觉设计
6. 分镜Agent生成详细分镜
7. Prompt工程Agent输出最终AI生成指令
8. 用户将指令输入GPT-image-2和Seedance执行

## 协作模式

继承自DirectorAgents的设计：
- **顺序链（Sequential Chain）**：按工种流水线依次执行
- **辩论投票（Debate & Voting）**：多方案比选，投票决策
- **主席团（MoA - Mixture of Agents）**：首席导演统筹，专家提供建议

## 文件结构

```
nicol-skills/
├── CLAUDE.md                    ← 当前文件
├── README.md                    # 用户文档
├── SKILL.md                     # 主技能入口
├── agents/                      # Agent定义
│   ├── executive-producer/      # 流程统筹
│   ├── screenplay/              # 剧本
│   ├── character-design/        # 角色设计
│   ├── scene-prop/              # 场景道具
│   ├── storyboard/              # 分镜故事板
│   ├── director-style/          # 导演风格
│   ├── prompt-engineer/         # Prompt工程
│   ├── post-production/         # 后期制作（扩展）
│   └── marketing-assets/        # 宣传物料（扩展）
├── references/                  # 共享知识库
├── templates/                   # 输出模板
└── examples/                    # 使用示例
```

## 关键设计原则

1. **一致性优先**：全局风格手册 + 角色圣经 + 场景圣经，确保视觉一致性
2. **结构化输出**：所有Agent产出遵循固定模板，便于下游Agent消费
3. **中英混合**：Agent内部逻辑用中文，AI工具prompt用英文
4. **可执行性**：最终输出是可直接复制粘贴到AI工具的prompt
5. **渐进增强**：核心7个Agent先做深做透，再扩展后期和宣传Agent

## 依赖参考

- DirectorAgents（`../nicol-skills-d/DirectorAgents/`）：31位导演风格库作为参考
- Claude Code Skill规范：所有Agent遵循SKILL.md格式
