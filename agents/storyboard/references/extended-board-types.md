# 扩展分镜板类型 (Extended Board Types)

> 三种专业分镜板扩展类型：BeatBoard、ColorScript、TechnicalBoard。

## 一、BeatBoard 节奏板（情感节奏板）

**用途**：在每个关键情节点（beat）展示情感强度变化，是 Shot List 的"灵魂版本"。

```
┌─────────────────────────────────────────────────┐
│  📈 项目名称 - BeatBoard - 场景1                 │
│                                                  │
│  情感强度（高→低）                                 │
│       ▁▂▃▅▇█▇▅▃                                 │
│       ┌─┐ ┌─┐ ┌─┐                                │
│       │建│ │冲│ │结│                              │
│       │立│ │突│ │束│                              │
│       └──┘ └──┘ └──┘                              │
│                                                  │
│  Beat 1：建立 (情感强度：3/10)                      │
│  [画面：孤独的街道，远景]                            │
│                                                  │
│  Beat 2：转折 (情感强度：7/10)                      │
│  [画面：主角独自走在雨夜，中景-近景]                  │
│                                                  │
│  Beat 3：冲突 (情感强度：9/10)                      │
│  [画面：突然雷电照亮主角的脸，特写]                  │
│                                                  │
│  Beat 4：解决 (情感强度：2/10)                      │
│  [画面：主角消失在黑暗，远景]                        │
└─────────────────────────────────────────────────┘
```

### BeatBoard 元素

| 元素 | 描述 |
|------|------|
| Beat 节点 | 每个情节点 |
| 情感强度 | 1-10 数字评级 |
| 关键画面 | 简化线稿代表画面 |
| 情感曲线 | ASCII 折线图 |
| 转场标记 | 节点间转场描述 |

### AI 生成 BeatBoard 提示词

```
Storyboard beat board, [project name],
emotional arc visualization showing intensity peaks and valleys,
[number] beats, each labeled with emotional intensity (1-10),
key frame thumbnails for each beat,
clean professional film pre-production style,
color coded by emotion (red high, blue low, green transition),
white background.
```

## 二、ColorScript 色板脚本

**用途**：用色彩速写（color rough）展示全片/全场景的色彩走向，配合情绪曲线。

```
┌─────────────────────────────────────────────────┐
│  🎨 ColorScript - 场景1 (Night Alley)             │
│                                                  │
│  [Color 1]     [Color 2]     [Color 3]            │
│  ▓▓▓▓▓         ░░░░░░         ████               │
│  建立镜头     主角登场       关键揭示              │
│  冷蓝灰       蓝黑青         紫电闪光             │
│  #1A2332      #0A1628        #6B3FA0              │
│                                                  │
│  主导色彩：冷青、深蓝、偶尔紫电光                      │
│  色温变化：5600K → 6500K → 7200K（冷）               │
│  饱和度：低→中→高                                   │
│  对比度：中→高→极高                                  │
└─────────────────────────────────────────────────┘
```

### ColorScript 字段

```
┌──────────────────────────────────────┐
│  镜头编号: S[场景]-[序号]               │
│  主导色彩: [主色描述]                  │
│  色温: [色温K值或描述]                  │
│  饱和度: [低/中/高]                  │
│  对比度: [低/中/高]                   │
│  关键色调 HEX: [色值]                   │
│  与全局风格手册的关系: [确认/偏离/调整]   │
└──────────────────────────────────────┘
```

### AI 生成 ColorScript 提示词

```
Color script for [scene name],
showing color palette progression across [N] shots,
[palette description: e.g., "moody cyberpunk, neon cyan and magenta accents on dark grey"],
color swatches with hex codes,
color temperature arc (warm → cool → cold),
[emotional tone] atmosphere,
professional film color script style,
gradient swatches arranged in sequence.
```

## 三、Technical Board 技术板

**用途**：导演/摄影指导使用的技术细节板，包含机位、运动、光线、声音等。

```
┌─────────────────────────────────────────────────┐
│  🎥 Technical Board - 场景1 镜头3                │
│                                                  │
│  Shot ID: S1-003                                  │
│  Description: 主角走向门口                          │
│                                                  │
│  ┌─ CAMERA ──────────────────────────────────┐   │
│  │ Camera: Arri Alexa Mini LF                   │   │
│  │ Lens: 35mm prime, T2.0                       │   │
│  │ Frame Rate: 24fps                            │   │
│  │ Aspect: 2.39:1 (cinemascope)                  │   │
│  │ Resolution: 4K                               │   │
│  └──────────────────────────────────────────────┘   │
│                                                  │
│  ┌─ MOVEMENT ─────────────────────────────────┐   │
│  │ Dolly in, slow (10s), eye-level               │   │
│  │ + Tilt down slightly to follow hands          │   │
│  └──────────────────────────────────────────────┘   │
│                                                  │
│  ┌─ LIGHTING ──────────────────────────────────┐   │
│  │ Key: Window light, L45°, 5600K (cold)         │   │
│  │ Fill: Bounce, R-30°, 0.5x intensity           │   │
│  │ Practical: Desk lamp, amber 2700K             │   │
│  │ Mood: Low-key, high contrast                  │   │
│  └──────────────────────────────────────────────┘   │
│                                                  │
│  ┌─ AUDIO ────────────────────────────────────┐   │
│  │ Background: Rain, distant thunder            │   │
│  │ Music: Tension drone, low frequency          │   │
│  │ SFX: Footsteps on wet floor                  │   │
│  │ Dialogue: None                                │   │
│  └──────────────────────────────────────────────┘   │
│                                                  │
│  ┌─ SEEDANCE PARAMETERS ──────────────────────┐   │
│  │ Mode: I2V                                     │   │
│  │ Reference Image: keyframe_S1_003.png         │   │
│  │ Duration: 6s                                  │   │
│  │ Motion Strength: 4/10                          │   │
│  │ Seed: BASE + 12                              │   │
│  └──────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────┘
```

### Technical Board 重要性

| 项目规模 | 是否需要 Technical Board |
|---------|----------------------|
| 短视频/快速原型 | 否 |
| 标准项目 | 可选（仅关键场景） |
| 精品/商业项目 | 必须（关键+复杂场景） |
| 商业广告/MV | 必须（全场景） |

---

## 四、扩展板型选择指南

```
选择分镜扩展板：
├── 项目周期紧迫 / 快速原型？
│   └── 仅 Standard Shot List
├── 需要让投资方/制片高层快速理解节奏？
│   └── 增加 BeatBoard
├── 导演/摄影指导重视色彩走向？
│   └── 增加 ColorScript
├── 项目包含复杂技术镜头？
│   └── 增加 Technical Board
└── 默认推荐：BeatBoard + ColorScript（叙述向项目）
```

