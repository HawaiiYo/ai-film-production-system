# 角色走位指示系统 (Character Blocking Notation)

> 三种走位标注方式：画面内箭头、俯视平面图、关键姿势图。供 storyboard Agent 使用。

## 方式1：画面内箭头（In-Frame Arrows）— 最常用

直接在分镜画面内标注角色运动：

```
┌──────────────────────────────┐
│  🎬 S2-003 (LS) — 俯视餐厅   │
│                              │
│   ┌──────────────┐          │
│   │   吧台区域     │          │
│   │  🧑🍳         │          │
│   └──────┬───────┘          │
│          │ ← 服务员A路径      │
│    ┌─────┴──────┐          │
│    │            │          │
│    │  ●────→    │ ← 主角B   │
│    │  客桌区域   │   走向吧台  │
│    │            │          │
│    │    ●       │ ← 配角C   │
│    └────────────┘   原地等待  │
│                              │
│  → 摄影机从窗外缓慢右摇       │
└──────────────────────────────┘
```

## 方式2：俯视平面图（Overhead Floor Plan / Blocking Diagram）— 精确走位

用**俯视平面图+编号标记**来精确描述角色在每个时刻的位置：

```
┌─────────────────────────────────────────┐
│  📐 场景S002 走位平面图 (Blocking Map)    │
│                                          │
│        N                                 │
│        ↑                                 │
│   ┌──────────────────┐                  │
│   │  🚪 入口          │                  │
│   │  A1────→A2       │  ← 主角A的走位    │
│   │                  │     A1入场 →      │
│   │  ┌─────────┐     │     A2走向桌边 →  │
│   │  │ 会议桌   │     │     A3坐下       │
│   │  │    A3   │     │                  │
│   │  │  ●     │     │  配角B的走位      │
│   │  │        │     │     B1原地 →      │
│   │  │   B1   │     │     B2走到窗边 →  │
│   │  │   ●    │     │     B3转身面对A   │
│   │  └────────┘     │                  │
│   │          B2─→B3 │                  │
│   │            ●    │                  │
│   │       ┌──┐      │                  │
│   │       │窗│      │                  │
│   └───────┴──┴──────┘                  │
│                                          │
│  📷 摄影机位：                            │
│     CAM1: 入口处(镜头S2-001/002)         │
│     CAM2: 窗外(镜头S2-003)               │
│     CAM3: 桌对面(镜头S2-004/005)         │
│                                          │
│  走位时间线：                             │
│  S2-001: A在A1, B在B1                   │
│  S2-002: A走到A2, B不动                 │
│  S2-003: A到A3坐下, B走向B2              │
│  S2-004: A坐着, B在B2                   │
│  S2-005: B转身到B3, 面对A               │
└─────────────────────────────────────────┘
```

**AI 俯视走位图 Prompt（GPT-image-2）**：
```
Top-down floor plan / blocking diagram,
scene: [场景空间描述],
showing: character movement paths with numbered markers (A1→A2→A3),
camera positions marked with CAM1/CAM2/CAM3,
clean architectural line drawing style,
black and white, professional film production blocking diagram,
arrows showing movement direction, numbered keyframes.
```

## 方式3：关键姿势图（Key Pose Panels）— 动画式

对关键动作按时间序列展示分解姿势：

```
┌─────────────────────────────────────────────┐
│  🎬 S5-010 动作分解 (5 panels @ 1s/panel)   │
│                                              │
│  [t=0] 站立 → [t=1] 抬手 → [t=2] 抓住 →   │
│  [t=3] 拉动 → [t=4] 完成                     │
│                                              │
│  Panel 1:  角色A站立, 双手自然下垂           │
│  Panel 2:  右手抬起至肩高, 手掌张开          │
│  Panel 3:  手指合拢抓住门把手, 用力           │
│  Panel 4:  手臂后拉, 身体前倾                 │
│  Panel 5:  门被拉开, 角色A身体跟进            │
└─────────────────────────────────────────────┘
```

**AI 关键姿势图 Prompt**：
```
Key pose sequence, [character description],
5 panels showing progressive motion,
[pose 1 to pose 5 description],
sequential action, storyboard pose reference,
clean line art, white background, professional animation keyframes,
arrow indicators between poses.
```

---

## 走位与 Seedance Prompt 的映射

| 走位描述 | Seedance 描述关键词 |
|---------|-------------------|
| "A walks to A2" | `[character] walks from [start position] to [end position], [X] steps, [duration]` |
| "B turns to face A" | `[character B] turns body to face [character A], [X] degree rotation` |
| "A sits down at A3" | `[character A] sits down on the chair at [position], body lowering gradually` |
| "Group moves together" | `all characters move in unison toward [direction], coordinated motion` |

---

## 何时使用哪种方式

- **方式1（画面内箭头）**：分镜数量多、需要快速展示的剧情镜头（首选，80% 场景）
- **方式2（俯视平面图）**：复杂走位（如追逐、舞蹈、群戏、动作场面），需要精确空间关系
- **方式3（关键姿势图）**：复杂的连续动作（如武打、运动、操作器械），需要逐帧分解
