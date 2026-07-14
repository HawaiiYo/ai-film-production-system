# 🎛️ Agent Registry Index — AI电影工坊元数据索引

> 三层检索架构的Layer 1：所有Agent和参考文档的元数据索引，用于快速路由和token预算管理

---

## 一、Agent能力卡片

### 🎯 Executive Producer（流程统筹）
```yaml
agent_id: executive-producer
name: 流程统筹Agent
role: Executive Producer / 总指挥
trigger_words: ["虚拟剧组", "电影策划", "项目统筹"]
capabilities:
  - 解析用户创作需求（类型/主题/情绪/时长/风格）
  - 组建虚拟剧组（匹配导演 + 调度Agent执行顺序）
  - 建立全局风格手册（Global Style Bible）
  - 质量审查（一致性交叉检查）
  - 输出完整AI电影制作手册
input_types: ["故事概念", "一句话梗概", "剧本片段", "创作需求描述"]
output_types: ["项目分析", "剧组组建方案", "全局风格手册", "制作手册"]
token_estimate: { light: "~8K", medium: "~15K", heavy: "~25K" }
depends_on: []
feeds_into: ["director-style", "screenplay", "character-design", "scene-prop", "storyboard", "prompt-engineer"]
load_strategy: "eager"  # always loaded first
priority: 1
```

### 🎨 Director Style（导演风格）
```yaml
agent_id: director-style
name: 导演风格匹配Agent
role: Director Style Matcher / 风格策展人
trigger_words: ["导演风格匹配", "导演组合", "风格指南"]
capabilities:
  - 31位世界导演风格匹配
  - 输出统一视觉风格指南（色调/光影/构图）
  - 协作模式选择（顺序链/辩论投票/主席团）
  - 风格冲突解决
input_types: ["电影类型", "主题", "情绪基调", "视觉偏好"]
output_types: ["导演组合推荐", "视觉风格指南", "色调方案", "叙事风格建议"]
token_estimate: { light: "~6K", medium: "~12K", heavy: "~18K" }
depends_on: ["executive-producer"]
feeds_into: ["screenplay", "character-design", "scene-prop", "storyboard"]
load_strategy: "lazy"  # load after executive-producer
priority: 2
```

### 📖 Screenplay（剧本）
```yaml
agent_id: screenplay
name: 剧本Agent
role: Screenwriter / 编剧
trigger_words: ["剧本创作", "场景分解", "故事结构"]
capabilities:
  - 三幕/五幕结构设计
  - 场景分解（Scene Breakdown）
  - 人物列表+人物弧光
  - 关键对白创作
  - 叙事节奏控制
input_types: ["故事概念", "风格指南", "角色/场景约束"]
output_types: ["完整剧本", "场景列表", "人物关系图", "对白样例"]
token_estimate: { light: "~8K", medium: "~15K", heavy: "~22K" }
depends_on: ["executive-producer", "director-style"]
feeds_into: ["character-design", "scene-prop", "storyboard"]
load_strategy: "on_demand"
priority: 3
```

### 👤 Character Design（角色设计）
```yaml
agent_id: character-design
name: 角色设计Agent
role: Character Designer / 美术指导（角色方向）
trigger_words: ["角色设计", "角色圣经", "角色外观"]
capabilities:
  - 角色外观详细设计（年龄/体型/面容/发型/服装）
  - 角色圣经（Character Bible）建立
  - GPT-image-2角色参考图prompt生成
  - 角色表情/姿态变化设计
input_types: ["角色列表", "人物描述", "风格指南", "情绪基调"]
output_types: ["角色圣经", "角色GPT-image-2 prompt", "角色表情板"]
token_estimate: { light: "~5K", medium: "~10K", heavy: "~15K" }
depends_on: ["screenplay", "director-style"]
feeds_into: ["storyboard", "prompt-engineer"]
load_strategy: "on_demand"
priority: 4
```

### 🏗️ Scene & Prop（场景道具）
```yaml
agent_id: scene-prop
name: 场景道具Agent
role: Production Designer / 美术指导（场景方向）
trigger_words: ["场景设计", "道具设计", "场景圣经"]
capabilities:
  - 场景氛围设计（时间/地点/光线/天气/色彩）
  - 关键道具设计（外观+剧情功能）
  - 场景圣经（Scene Bible）建立
  - GPT-image-2场景/道具参考图prompt生成
input_types: ["场景列表", "风格指南", "空间需求", "时代背景"]
output_types: ["场景圣经", "道具清单", "场景GPT-image-2 prompt", "道具GPT-image-2 prompt"]
token_estimate: { light: "~5K", medium: "~10K", heavy: "~15K" }
depends_on: ["screenplay", "director-style"]
feeds_into: ["storyboard", "prompt-engineer"]
load_strategy: "on_demand"
priority: 4
```

### 🎬 Storyboard（分镜故事板）
```yaml
agent_id: storyboard
name: 分镜故事板Agent
role: Cinematographer + Storyboard Artist / 摄影师+分镜师
trigger_words: ["分镜设计", "故事板", "镜头设计", "Seedance prompt"]
capabilities:
  - 场景→分镜分解（Shot List）
  - 镜头语言设计（景别/运动/构图/转场/时长）
  - 情绪曲线绘制
  - Seedance视频生成prompt
  - 拍摄顺序建议
  - 连贯性约束检查（v1.1新增）
input_types: ["剧本场景分解", "角色圣经", "场景圣经", "风格指南"]
output_types: ["分镜表", "情绪曲线", "Seedance prompt", "连贯性检查报告"]
token_estimate: { light: "~10K", medium: "~20K", heavy: "~35K" }
depends_on: ["screenplay", "character-design", "scene-prop", "emotion-system"]
feeds_into: ["prompt-engineer"]
load_strategy: "lazy_summary_first"  # large file, load summary first
priority: 5
```

### 🔧 Prompt Engineer（Prompt工程）
```yaml
agent_id: prompt-engineer
name: Prompt工程Agent
role: Post-Production Supervisor + Technical Director + QC Inspector
trigger_words: ["Prompt优化", "AI生成指令", "生成指令表", "Prompt工程", "AI Generation Sheet", "最终输出"]
capabilities:
  - 收集所有上游Agent产出
  - GPT-image-2 prompt优化
  - Seedance prompt优化
  - 全量一致性交叉检查
  - Negative prompts管理
  - 技术参数建议（分辨率/帧率/seed值）
  - 组装AI Generation Sheet
input_types: ["所有上游Agent产出", "角色圣经", "场景圣经", "分镜表"]
output_types: ["AI Generation Sheet", "完整prompt合集", "一致性检查报告", "参数建议表"]
token_estimate: { light: "~10K", medium: "~18K", heavy: "~25K" }
depends_on: ["storyboard", "character-design", "scene-prop", "director-style"]
feeds_into: []  # final output agent
load_strategy: "eager"  # always loaded last
priority: 6
```

### 🎭 Emotion System（情绪系统）— v1.1新增
```yaml
agent_id: emotion-system
name: 情绪系统Agent
role: Emotional Cinematography Advisor / 情绪摄影顾问
trigger_words: ["情绪分析", "情绪映射", "情绪曲线", "运镜情绪", "情感调色"]
capabilities:
  - 剧本情绪解析（4轴8极情绪维度模型）
  - 情绪→运镜映射（愤怒/悲伤/恐惧/喜悦/沉思/震惊/平静/紧张）
  - 情绪参数输出（运镜方式+色调偏移+节奏+声音方向）
  - 情绪曲线可视化
  - 情绪一致性验证
input_types: ["剧本场景分解", "每个镜头的叙事目标"]
output_types: ["情绪参数表", "情绪曲线图", "运镜情绪建议", "色调情绪建议"]
token_estimate: { light: "~5K", medium: "~10K", heavy: "~15K" }
depends_on: ["screenplay"]
feeds_into: ["character-design", "scene-prop", "storyboard"]
load_strategy: "on_demand"
priority: 3.5  # after screenplay, before character-design
```

### 🎛️ Agent Registry（Agent注册中心）— v1.1新增
```yaml
agent_id: agent-registry
name: Agent注册中心
role: Meta-Agent / Agent Orchestrator
trigger_words: ["Agent管理", "路由", "注册中心", "token优化", "加载策略"]
capabilities:
  - 维护Agent元数据索引
  - 智能路由到Agent组合
  - Agent CRUD操作管理
  - Token预算管理和监控
  - 增量加载协议执行
  - 一致性视图维护
input_types: ["用户请求", "Agent调用请求", "CRUD操作"]
output_types: ["路由决策", "加载策略", "Token预算报告", "CRUD确认"]
token_estimate: { light: "~2K", medium: "~5K", heavy: "~8K" }
depends_on: []
feeds_into: ["*"]  # routes to all agents
load_strategy: "eager_minimal"  # always load minimal metadata first
priority: 0  # before everything
```

### 🎬 Seedance Composer（Seedance提示词生成）— v1.1新增
```yaml
agent_id: seedance-composer
name: Seedance Composer Agent
role: Video Prompt Engineer / AI视频提示词工程师
trigger_words: ["Seedance生成", "视频prompt", "图生视频", "文生视频", "即梦AI prompt"]
capabilities:
  - 即时Seedance prompt生成（对话式）
  - 上下文感知（自动提取角色/场景/分镜信息）
  - 双模式支持（文生视频+图生视频）
  - 参数调优（motion strength/CFG/时长/帧率）
  - 迭代优化（基于用户反馈调整prompt）
  - 批量化生成（从分镜表批量出prompt）
input_types: ["镜头描述", "角色信息", "场景信息", "分镜参数", "用户反馈"]
output_types: ["Seedance prompt", "参数建议", "优化建议", "批量prompt清单"]
token_estimate: { light: "~3K", medium: "~8K", heavy: "~12K" }
depends_on: ["storyboard", "character-design", "scene-prop"]
feeds_into: []  # direct-to-user agent
load_strategy: "on_demand"
priority: 7
```

### ✂️ Post-Production（后期制作）
```yaml
agent_id: post-production
name: 后期制作Agent
role: Post-Production Supervisor / 后期统筹
trigger_words: ["后期制作", "剪辑方案", "调色方案", "音效设计"]
capabilities:
  - 剪辑节奏方案
  - 调色方案（Color Grading）
  - 音效设计方案
  - 配乐方向建议
input_types: ["分镜表", "全局风格手册", "Seedance prompt合集"]
output_types: ["剪辑方案", "调色LUT参考", "音效清单", "配乐风格建议"]
token_estimate: { light: "~4K", medium: "~8K", heavy: "~12K" }
depends_on: ["storyboard", "prompt-engineer"]
feeds_into: []
load_strategy: "on_demand"
priority: 8
```

### 📢 Marketing Assets（宣传物料）
```yaml
agent_id: marketing-assets
name: 宣传物料Agent
role: Marketing Creative Director / 宣传创意总监
trigger_words: ["海报设计", "预告片", "宣传物料", "营销方案"]
capabilities:
  - 海报概念设计
  - 预告片结构方案
  - 社交媒体宣传物料
  - GPT-image-2海报prompt
input_types: ["项目概览", "角色圣经", "场景圣经", "关键帧"]
output_types: ["海报方案", "预告片结构", "宣传prompt", "社交媒体策略"]
token_estimate: { light: "~4K", medium: "~8K", heavy: "~12K" }
depends_on: ["character-design", "scene-prop", "storyboard"]
feeds_into: []
load_strategy: "on_demand"
priority: 9
```

---

## 二、参考文档索引

| 文档 | 路径 | 大小 | 缓存策略 | 适用Agent |
|------|------|------|---------|----------|
| 电影制作流程 | `references/film-production-pipeline.md` | ~351行 | cache_stable | ALL |
| Prompt工程指南 | `references/prompt-engineering-guide.md` | ~329行 | cache_stable | prompt-engineer, character-design, scene-prop, storyboard |
| Seedance指南 | `references/seedance-guide.md` | ~239行 | cache_stable | storyboard, prompt-engineer, seedance-composer |
| GPT-image-2指南 | `references/gpt-image2-guide.md` | — | cache_stable | character-design, scene-prop, prompt-engineer |
| 情绪→运镜映射 | `references/emotion-cinematography-mapping.md` | 新建 | cache_stable | emotion-system, storyboard |
| 连贯性规则 | `references/continuity-rules.md` | 新建 | cache_stable | storyboard |
| Agent注册索引 | `references/agent-registry-index.md` | 本文件 | cache_stable | agent-registry |

---

## 三、模板文档索引

| 模板 | 路径 | 大小 | 使用Agent |
|------|------|------|----------|
| 角色圣经 | `templates/character-bible.md` | — | character-design |
| 场景圣经 | `templates/scene-bible.md` | — | scene-prop |
| 分镜表 | `templates/storyboard-table.md` | ~403行 | storyboard |
| AI生成指令表 | `templates/ai-generation-sheet.md` | — | prompt-engineer |

---

## 四、路由决策树

```
用户输入
    │
    ▼
┌─────────────────────────────────────┐
│ Agent Registry 解析意图              │
│ ├── 匹配触发词                      │
│ ├── 识别所需Agent组合               │
│ └── 确定加载策略                    │
└──────────────┬──────────────────────┘
               │
    ┌──────────┼──────────┐
    ▼          ▼          ▼
 单Agent    流水线链    辩论模式
 (精确匹配)  (顺序执行)  (并行投票)
```

### 意图→Agent映射表

| 用户意图 | 触发Agent | 加载策略 |
|---------|----------|---------|
| "AI电影工坊" / 完整电影策划 | executive-producer → 全链 | eager: executive-producer, lazy: others |
| "导演风格匹配" | director-style | on_demand |
| "剧本创作" / "写剧本" | screenplay | on_demand |
| "角色设计" / "设计角色" | character-design | on_demand |
| "场景设计" / "设计场景" | scene-prop | on_demand |
| "分镜设计" / "故事板" | storyboard | lazy_summary_first |
| "Prompt优化" / "生成指令" | prompt-engineer | on_demand |
| "情绪分析" / "运镜情绪" | emotion-system | on_demand |
| "Seedance生成" / "视频prompt" | seedance-composer | on_demand |
| "Agent管理" / "注册" / "CRUD" | agent-registry | eager_minimal |

---

## 五、Token预算管理策略

### 加载策略说明

| 策略 | 行为 | 适用场景 | 预估token |
|------|------|---------|----------|
| `eager` | 立即加载完整SKILL.md | 流程入口Agent | 完整文件大小 |
| `eager_minimal` | 立即加载精简摘要 | 元Agent | ~2K |
| `lazy` | 延迟到需要时加载完整内容 | 流程中段Agent | 按需 |
| `lazy_summary_first` | 先加载摘要，确认需要再加载完整 | 大文件Agent（如storyboard） | 摘要~5K + 完整按需 |
| `on_demand` | 仅在直接调用时加载 | 可选/辅助Agent | 按需 |
| `cache_stable` | 标记为可缓存（内容不常变） | 参考文档 | 单次加载+后续缓存 |

### Token预算分配建议

| 项目规模 | token预算 | Agent组合 | 加载策略 |
|---------|----------|----------|---------|
| 🟢 轻量（快速原型） | <30K | executive-producer + screenplay + 1-2个视觉Agent | summary_first |
| 🟡 标准（常规项目） | 30-60K | 完整7-Agent链 | lazy + on_demand |
| 🔴 深度（精品项目） | 60-100K | 全部Agent + 辩论模式 | eager关键Agent + lazy其他 |

---

*本索引文件由Agent Registry维护，随Agent增删改同步更新*
