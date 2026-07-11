# 🎬 分镜表模板 — Storyboard Table Template

> 将剧本转化为详细的可执行分镜脚本，每个镜头包含Seedance视频生成prompt

---

## 分镜表 — [场景名称]（Scene [编号]）

### 场景信息

| 属性 | 内容 |
|------|------|
| 场景编号 | [S001] |
| 场景名称 | [名称] |
| 场景描述 | [一句话概述] |
| 出场角色 | [角色列表] |
| 场景时长估算 | [总时长] |

### 镜头情绪曲线

```
紧张度
  ▲
  │     ╱‾‾‾‾╲
  │    ╱      ╲
  │   ╱        ╲___
  │  ╱             ╲
  │ ╱               ╲
  └────────────────────▶ 时间
   S1  S2  S3  S4  S5  S6
```

---

### 分镜详情

#### 🎬 镜头 S[编号]-001

| 属性 | 内容 |
|------|------|
| 镜号 | S[编号]-001 |
| 景别 | [ELS/LS/FS/MS/MCU/CU/ECU] |
| 镜头运动 | [固定/推/拉/摇/移/跟/升降/手持/变焦] |
| 构图方式 | [三分法/对称/引导线/框架/对角线/中心/浅景深] |
| 拍摄角度 | [平视/俯视/仰视/鸟瞰/Dutch Angle] |
| 时长估算 | [N]秒 |
| 转场方式 | [切/淡入淡出/叠化/划/匹配剪辑] → 下一镜头 |

**画面描述**：
[中文详细描述画面内容——谁在哪里做什么，画面中能看到什么，情绪如何]

**关键元素**：
- 主体：[角色名/物体] — 在画面中的位置和状态
- 前景：[描述]
- 背景：[描述]
- 特殊视觉：[特效/光线特殊效果/颜色处理等]

**声音参考**（可选）：
- 对白：[角色的对白]
- 音效：[环境音/特殊音效]
- 配乐：[情绪/风格]

**🌐 Seedance Prompt（英文）**：

```
[Mode: Text-to-Video / Image-to-Video]

[完整英文视频生成prompt，包含：
- 场景/主体描述
- 具体运动/动作
- 镜头运动方式
- 光线/氛围
- 风格参考
- 技术参数]

Duration: [N]s, 24fps, cinematic quality.

Negative: jittery, flickering, morphing artifacts, blurry, low resolution,
warped anatomy, inconsistent frames.
```

**参考图**（图生视频模式）：
- 关键帧文件：[filename.png]（GPT-image-2生成）
- 关键帧描述：[描述参考图的内容]

---

#### 🎬 镜头 S[编号]-002

[同上格式，重复每个镜头]

---

#### 🎬 镜头 S[编号]-003

[同上格式]

---

### 镜头总览表

| 镜号 | 景别 | 运动 | 构图 | 时长 | 转场 | 模式 |
|------|------|------|------|------|------|------|
| S1-001 | ELS | Crane Up | 三分法 | 6s | Cut | 图生视频 |
| S1-002 | MS | Static | 中心 | 4s | Cut | 图生视频 |
| S1-003 | CU | Dolly In | 浅景深 | 5s | Dissolve | 图生视频 |
| ... | | | | | | |

---

### 场景拍摄顺序建议

```
推荐拍摄/生成顺序：
1. 先拍建立镜头（Establishing Shot）：S1-001
2. 再拍主镜头（Master Shot）：S1-003
3. 然后拍中近景覆盖：S1-002, S1-005
4. 最后拍特写和插入镜头：S1-004, S1-006
```

---

## 📋 一致性检查清单

- [ ] 所有镜头中的角色描述是否与角色圣经一致？
- [ ] 所有镜头中的场景描述是否与场景圣经一致？
- [ ] 镜头运动是否与场景的情绪曲线匹配？
- [ ] 每个镜头的Seedance prompt是否包含技术参数？
- [ ] 景别变化是否有节奏（大景别→小景别→大景别）？
- [ ] 转场是否自然（避免连续使用同一种转场）？
- [ ] 总时长是否符合目标？
- [ ] 箭头符号是否正确标注（镜头运动箭头 vs 角色运动箭头）？
- [ ] 如有复杂走位，是否补充了俯视平面图？

---

## 🎨 分镜板布局模板（Storyboard Layout Templates）

> 除表格格式外，分镜还可以按以下布局输出——适合直接用于GPT-image-2生成可视化分镜板

### 布局1: 缩略图板 (Thumbnail Board) — 12格快速探索

```
┌─────────────────────────────────────────┐
│  场景：___  页：___  日期：___           │
├──────┬──────┬──────┬──────┐
│ S-01 │ S-02 │ S-03 │ S-04 │
│ ELS  │ MS   │ CU   │ MS   │
├──────┼──────┼──────┼──────┤
│ S-05 │ S-06 │ S-07 │ S-08 │
│ FS   │ CU   │ MS   │ LS   │
├──────┼──────┼──────┼──────┤
│ S-09 │ S-10 │ S-11 │ S-12 │
│ MCU  │ CU   │ LS   │ ECU  │
└──────┴──────┴──────┴──────┘
```

**GPT-image-2缩略图板Prompt**：
```
Storyboard thumbnail grid, 12 panels arranged 4x3,
scene: [场景描述],
style: rough pencil sketches, stick figures and simple shapes,
each panel labeled with shot number and shot size,
camera movement arrows drawn inside panels,
black and white, quick gesture drawings,
professional storyboard thumbnail sheet.
Negative: detailed rendering, color, photorealistic.
```

### 布局2: 标准6格板 (6-Panel Board) — 3×2 ⭐最常用

```
┌──────────────────────────────────────────────┐
│  项目：___  场景：___  页：___                │
├──────────┬──────────┬──────────┤
│ S-01     │ S-02     │ S-03     │
│ [景别]    │ [景别]    │ [景别]    │
│          │          │          │
│[线稿画面] │[线稿画面] │[线稿画面] │
│          │          │          │
│[镜头运动] │[镜头运动] │[镜头运动] │
│[角色箭头] │[角色箭头] │[角色箭头] │
│[N]s      │[N]s      │[N]s      │
├──────────┼──────────┼──────────┤
│ S-04     │ S-05     │ S-06     │
│ [景别]    │ [景别]    │ [景别]    │
│          │          │          │
│[线稿画面] │[线稿画面] │[线稿画面] │
│          │          │          │
│[镜头运动] │[镜头运动] │[镜头运动] │
│[角色箭头] │[角色箭头] │[角色箭头] │
│[N]s      │[N]s      │[N]s      │
└──────────┴──────────┴──────────┘
```

**GPT-image-2标准6格板Prompt**：
```
Professional storyboard, 6 panels in 3x2 grid layout,
scene: [场景描述],
each panel showing: [镜头1简述], [镜头2简述], ...
style: clean pencil line art with grey tone shading,
camera movement arrows clearly visible in each panel
(←→ dolly, ↙ pan, ↑ crane, ≈≈ handheld),
character movement arrows showing blocking and walking paths,
each panel labeled with shot number, shot size abbreviation, duration,
black and white, professional film production storyboard,
suitable for director and cinematographer communication.
Negative: color, photorealistic, messy composition, missing arrows.
```

### 布局3: 标准4格板 (4-Panel Board) — 2×2 关键节拍

```
┌─────────────────────────────────────────┐
│  项目：___  场景：___  页：___           │
├──────────────────┬──────────────────┤
│  🎬 S-01 [景别]   │  🎬 S-02 [景别]   │
│                  │                  │
│   [线稿画面]      │   [线稿画面]      │
│                  │                  │
│  [镜头运动箭头]    │  [镜头运动箭头]    │
│  [角色运动箭头]    │  [角色运动箭头]    │
│  [N]s             │  [N]s             │
│                  │                  │
│  说明：_____      │  说明：_____      │
│  氛围：_____      │  氛围：_____      │
├──────────────────┼──────────────────┤
│  🎬 S-03 [景别]   │  🎬 S-04 [景别]   │
│                  │                  │
│   [线稿画面]      │   [线稿画面]      │
│                  │                  │
│  [镜头运动箭头]    │  [镜头运动箭头]    │
│  [角色运动箭头]    │  [角色运动箭头]    │
│  [N]s             │  [N]s             │
│                  │                  │
│  说明：_____      │  说明：_____      │
│  氛围：_____      │  氛围：_____      │
└──────────────────┴──────────────────┘
```

**GPT-image-2标准4格板Prompt**：
```
Professional storyboard, 4 large panels in 2x2 grid,
scene: [场景描述],
each panel is a key story beat:
  Panel 1 (S-01): [建立镜头描述],
  Panel 2 (S-02): [关键动作描述],
  Panel 3 (S-03): [情绪转折描述],
  Panel 4 (S-04): [结束镜头描述],
style: detailed pencil line art with grey tone shading,
clear camera movement arrows and character blocking arrows,
each panel labeled with shot number, shot size, duration, camera notes,
black and white, professional film production storyboard.
Negative: color, photorealistic, small panels, missing arrow notations.
```

### 布局4: 宽幅横板 (Widescreen Board) — 3~4格横排

```
┌──────────────────────────────────────────────┐
│  项目：___  场景：___  宽高比：2.35:1         │
├──────────────────────────────────────────────┤
│  🎬 S-01 [景别]  ← [镜头运动] [N]s           │
│  ┌──────────────────────────────────────────┐
│  │         [宽银幕线稿画面]                    │
│  │         [运动箭头标注]                     │
│  └──────────────────────────────────────────┘
│  说明：_____  氛围：_____
├──────────────────────────────────────────────┤
│  🎬 S-02 [景别]  ← [镜头运动] [N]s           │
│  ┌──────────────────────────────────────────┐
│  │         [宽银幕线稿画面]                    │
│  └──────────────────────────────────────────┘
│  说明：_____  氛围：_____
├──────────────────────────────────────────────┤
│  🎬 S-03 [景别]  ← [镜头运动] [N]s           │
│  ┌──────────────────────────────────────────┐
│  │         [宽银幕线稿画面]                    │
│  └──────────────────────────────────────────┘
│  说明：_____  氛围：_____
└──────────────────────────────────────────────┘
```

**GPT-image-2宽幅板Prompt**：
```
Widescreen storyboard, 3 panels vertical stack, 2.35:1 aspect ratio per panel,
scene: [场景描述],
style: detailed pencil line art, cinematic wide composition,
camera movement arrows (pan, dolly, crane) clearly drawn,
character placement and movement arrows visible,
each panel labeled with shot number, shot size, duration, camera notes,
black and white with grey tone, cinematic film production storyboard.
Negative: square panels, 16:9, color, photorealistic.
```

---

## 📐 走位平面图模板 (Blocking Floor Plan)

> 当场景涉及复杂的角色走位或多摄影机位时，补充此模板

```
┌─────────────────────────────────────────┐
│  📐 场景___ 走位平面图 (Blocking Map)     │
│  比例：示意  方向：N↑                    │
├─────────────────────────────────────────┤
│                                          │
│        N                                 │
│        ↑                                 │
│   ┌──────────────────┐                  │
│   │  🚪 入口          │                  │
│   │  [角色A]路径：     │                  │
│   │  A1──→A2──→A3    │                  │
│   │                  │                  │
│   │  ┌─────────┐     │                  │
│   │  │ 关键物体  │     │                  │
│   │  │  (桌/台) │     │                  │
│   │  │   A3    │     │                  │
│   │  │   ●     │     │                  │
│   │  │        │     │                  │
│   │  │   B1   │     │                  │
│   │  │   ●    │     │                  │
│   │  └────────┘     │                  │
│   │          B2─→B3 │                  │
│   │            ●    │                  │
│   │       ┌──┐      │                  │
│   │       │窗│      │                  │
│   └───────┴──┴──────┘                  │
│                                          │
│  📷 摄影机位：                            │
│     CAM1: [位置] — 镜头___               │
│     CAM2: [位置] — 镜头___               │
│     CAM3: [位置] — 镜头___               │
│                                          │
│  🚶 走位时间线：                          │
│  ├── 镜头001: [角色A]在A1, [角色B]在B1    │
│  ├── 镜头002: [角色A]走到A2              │
│  ├── 镜头003: [角色A]到A3坐下            │
│  ├── 镜头004: [角色B]走向B2              │
│  └── 镜头005: [角色B]转身到B3面对[角色A]  │
└─────────────────────────────────────────┘
```

**GPT-image-2走位平面图Prompt**：
```
Top-down floor plan / blocking diagram,
scene: [场景空间描述],
showing: character movement paths with numbered markers,
  Character A: A1(entrance) → A2(walking) → A3(seated at table),
  Character B: B1(standing) → B2(walking to window) → B3(turning to face A),
camera positions marked: CAM1, CAM2, CAM3 with field of view cones,
furniture and architectural features drawn in plan view,
arrows showing exact movement direction for each character,
clean architectural line drawing style, black and white,
professional film production blocking diagram.
Negative: 3D perspective, color, photorealistic, clutter.
```

---

## 🎞️ 关键姿势分解模板 (Key Pose Breakdown)

> 适合复杂的角色动作（打斗、舞蹈、特技等）

```
┌──────────────────────────────────────────────┐
│  🎬 镜头___ [动作名称] — 关键姿势分解          │
│  总时长：[N]s   帧率：24fps                    │
│                                              │
│  Pose 1: [姿势名]    Pose 2: [姿势名]          │
│  ┌──────────┐       ┌──────────┐            │
│  │          │       │          │            │
│  │ [线稿]    │  ───→ │ [线稿]    │            │
│  │          │       │          │            │
│  └──────────┘       └──────────┘            │
│     [t=0s]             [t=Ns]               │
│                                              │
│  运动弧线：[角色部位] ╮╭╮╯ (运动轨迹描述)      │
│  力度变化：[加速/减速/匀速]                    │
│  重心转移：[描述重心变化]                      │
└──────────────────────────────────────────────┘
```

---

*此模板用于分镜故事板Agent输出*