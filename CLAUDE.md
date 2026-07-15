# 🎬 AI Filmmaking Multi-Agent System (AI电影工坊) v1.1

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

### v1.1 新增功能
- 🎛️ **Agent注册中心**：三层检索架构 + 智能路由，大幅降低token消耗
- 🎭 **情绪系统Agent**：情绪→运镜映射，逐镜头情绪参数输出
- 🔗 **分镜连贯性系统**：空间坐标系 + 180度规则 + 视线匹配 + 连贯性检查
- 🎬 **Seedance Composer**：即时对话式prompt生成 + 参数调优 + 迭代优化

### v1.2 优化（2026-07）
- **Agent 瘦身**：SKILL.md 总行数 7,076 → 3,426 (-52%)
- **领域知识本地化**：references/ 从 7 个 → 30+ 个独立知识文件
- **导演文档本地化**：31 位导演详细风格从外部项目 → `agents/director-style/directors/`
- **Storyboard 大瘦身**：1,966 → 309 行 (-84%)，原 910 行参考知识拆为 14 个独立 references
- **Prompt Engineer 重写**：1,230 → 391 行 (-68%)，融入最新 GPT-image-2 / Seedance 实践
- **检索式 SKILL.md**：每个 Agent 的 SKILL.md 末尾含"检索指引速查"，告诉 Claude 何时读哪个 references

## 系统架构

```
用户输入故事概念
    → 🎛️ Agent Registry (智能路由 + token预算管理)
        → 🎯 流程统筹Agent (组建虚拟剧组)
            → 🎨 导演风格Agent (匹配导演+风格指南) ← 检索 agents/director-style/directors/
            → 📖 剧本Agent (完整剧本+场景分解)
            → 🎭 情绪系统Agent (情绪分析+运镜映射) ← v1.1新增
            → 👤 角色设计Agent (角色圣经+GPT-image-2 prompt) ← 检索 character-design-reference.md
            → 🏗️ 场景道具Agent (场景圣经+参考图prompt) ← 检索 scene-type-reference.md
            → 🎬 分镜故事板Agent (分镜表+连贯性检查+Seedance prompt) ← 检索 cinematography 14 文件
            → 🔧 Prompt工程Agent (优化prompt+一致性检查) ← 检索 prompt 模板库
            → 🎬 Seedance Composer (即时对话式prompt生成) ← v1.1新增
                → 🖼️ 最终AI生成指令 (可执行输出)
```

## Agent角色说明

### 元Agent（1个，v1.1新增）

| Agent | 角色 | 核心产出 |
|-------|------|---------|
| 🎛️ Agent Registry | Agent注册中心 | 智能路由、Token预算管理、Agent CRUD |

### 核心Agent（8个，含v1.1新增）

| Agent | 角色 | 核心产出 |
|-------|------|---------|
| 🎯 Executive Producer | 流程统筹 | 项目计划、全局风格手册、制作手册 |
| 🎨 Director Style | 导演风格 | 导演组合、视觉风格指南 |
| 📖 Screenplay | 剧本 | 完整剧本、场景列表、人物关系图 |
| 🎭 Emotion System | 情绪系统（v1.1新增） | 情绪坐标、运镜情绪映射、情绪曲线 |
| 👤 Character Design | 角色设计 | 角色圣经、GPT-image-2角色prompt |
| 🏗️ Scene & Prop | 场景道具 | 场景圣经、GPT-image-2场景prompt |
| 🎬 Storyboard | 分镜故事板 | 分镜表、连贯性检查、Seedance prompt |
| 🔧 Prompt Engineer | Prompt工程 | 优化后的完整AI生成指令集 |

### 执行Agent（1个，v1.1新增）

| Agent | 角色 | 核心产出 |
|-------|------|---------|
| 🎬 Seedance Composer | Seedance Prompt即时生成 | 对话式prompt生成、参数调优、迭代优化 |

### 扩展Agent（2个）

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
- `情绪分析` / `运镜情绪` — 情绪→摄影映射（v1.1新增）
- `Seedance生成` / `视频prompt` — 即时生成Seedance prompt（v1.1新增）
- `Agent管理` / `token优化` — Agent注册中心操作（v1.1新增）

### 工作流
1. 用户提供故事概念或剧本
2. **Agent Registry**解析意图，智能路由，控制token预算（v1.1新增）
3. 统筹Agent解析需求，组建虚拟剧组
4. 导演风格Agent匹配导演组合，输出风格指南
5. 剧本Agent生成完整剧本
6. **情绪系统Agent**分析情绪曲线，输出逐镜头情绪参数（v1.1新增）
7. 角色/场景Agent生成视觉设计（融入情绪基调）
8. 分镜Agent生成详细分镜（含连贯性约束检查 + 情绪参数）
9. Prompt工程Agent输出最终AI生成指令
10. **Seedance Composer**随时待命，即时生成/优化Seedance prompt（v1.1新增）
11. 用户将指令输入GPT-image-2和Seedance执行

## 协作模式

继承自DirectorAgents的设计：
- **顺序链（Sequential Chain）**：按工种流水线依次执行
- **辩论投票（Debate & Voting）**：多方案比选，投票决策
- **主席团（MoA - Mixture of Agents）**：首席导演统筹，专家提供建议

### Token预算模式（v1.1新增）
- **🟢 轻量模式**（<30K tokens）：快速原型，跳过非必要Agent
- **🟡 标准模式**（30-60K tokens）：常规项目，完整7-Agent链
- **🔴 深度模式**（60-100K tokens）：精品项目，含辩论和所有扩展Agent

## 文件结构

```
nicol-skills/
├── CLAUDE.md                    ← 当前文件
├── README.md                    # 用户文档
├── SKILL.md                     # 主技能入口
├── agents/                      # Agent定义（每个Agent本地references）
│   ├── agent-registry/          # Agent注册中心（v1.1新增）
│   │   ├── SKILL.md
│   │   └── references/          # （如需本地化）
│   ├── executive-producer/      # 流程统筹
│   │   └── SKILL.md
│   ├── screenplay/              # 剧本
│   │   └── SKILL.md
│   ├── emotion-system/          # 情绪系统（v1.1新增）
│   │   └── SKILL.md
│   ├── character-design/        # 角色设计
│   │   ├── SKILL.md
│   │   └── references/
│   │       └── character-design-reference.md
│   ├── scene-prop/              # 场景道具
│   │   ├── SKILL.md
│   │   └── references/
│   │       ├── lighting-reference.md
│   │       ├── material-reference.md
│   │       └── scene-type-reference.md
│   ├── storyboard/              # 分镜故事板
│   │   ├── SKILL.md
│   │   └── references/          # 13个镜头技术文件
│   │       ├── shot-size-guide.md
│   │       ├── camera-movement-guide.md
│   │       ├── composition-types.md
│   │       ├── transition-types.md
│   │       ├── storyboard-layouts.md
│   │       ├── lens-tech-reference.md
│   │       ├── arrow-notation-system.md
│   │       ├── blocking-notation.md
│   │       ├── audio-notation.md
│   │       ├── lighting-notation.md
│   │       ├── vfx-notation.md
│   │       ├── annotation-standards.md
│   │       └── extended-board-types.md
│   ├── director-style/          # 导演风格
│   │   ├── SKILL.md
│   │   └── directors/            # 32个文件：INDEX.md + 31位导演详细分析
│   ├── prompt-engineer/         # Prompt工程
│   │   ├── SKILL.md
│   │   └── references/          # 5个prompt模板库
│   │       ├── gpt-image2-templates.md
│   │       ├── seedance-prompt-templates.md
│   │       ├── negative-prompt-library.md
│   │       ├── seed-management-guide.md
│   │       └── consistency-check-template.md
│   ├── seedance-composer/       # Seedance Prompt生成（v1.1新增）
│   │   └── SKILL.md
│   ├── post-production/         # 后期制作（扩展）
│   │   └── SKILL.md
│   └── marketing-assets/        # 宣传物料（扩展）
│       └── SKILL.md
├── references/                  # 全局共享知识库（跨agent）
│   ├── agent-registry-index.md  # Agent元数据索引
│   ├── emotion-cinematography-mapping.md  # 情绪→摄影映射
│   ├── continuity-rules.md      # 连贯性规则
│   ├── 180-degree-rule.md       # 180度规则
│   ├── film-production-pipeline.md
│   ├── prompt-engineering-guide.md
│   ├── gpt-image2-guide.md
│   ├── seedance-guide.md
│
├── templates/                   # 输出模板（全局共用）
├── examples/                    # 使用示例（全局共用）
└── agents/[name]/directors/ 等 # 仅 director-style 独有 directors/ 子目录
```

### v1.2 references 文件分布策略

| 位置 | 文件数 | 说明 |
|------|--------|------|
| `references/` (全局) | 8 | 跨 agent 共享的全局知识 |
| `agents/director-style/directors/` | 32 | 31 位导演 + INDEX.md（director-style 专属） |
| `agents/storyboard/references/` | 13 | 镜头技术专属 |
| `agents/prompt-engineer/references/` | 5 | Prompt 模板库专属 |
| `agents/scene-prop/references/` | 3 | 场景设计参考专属 |
| `agents/character-design/references/` | 1 | 角色设计参考专属 |
| **总计** | **62 个** references 文件 | |
| + `templates/`（4 个全局共用）| 4 | 输出模板（跨 agent） |
| + `examples/`（2 个全局共用）| 2 | 示例项目（跨项目） |

## 关键设计原则

1. **一致性优先**：全局风格手册 + 角色圣经 + 场景圣经，确保视觉一致性
2. **结构化输出**：所有Agent产出遵循固定模板，便于下游Agent消费
3. **中英混合**：Agent内部逻辑用中文，AI工具prompt用英文
4. **可执行性**：最终输出是可直接复制粘贴到AI工具的prompt
5. **渐进增强**：核心Agent先做深做透，再扩展其他Agent
6. **Token效率**（v1.1新增）：三层检索架构 + 增量加载协议，最小化上下文消耗
7. **情绪驱动**（v1.1新增）：情绪分析贯穿全流程，每个镜头都有精确的情绪参数
8. **连贯性约束**（v1.1新增）：空间坐标系 + 连贯性规则引擎，确保镜头间一致性

## 依赖参考

- DirectorAgents（`../nicol-skills-d/DirectorAgents/`）：31位导演风格库作为参考
- Claude Code Skill规范：所有Agent遵循SKILL.md格式
- Claude Prompt Caching：利用缓存机制优化参考文档加载
