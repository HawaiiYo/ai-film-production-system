# 镜头技术标注系统 (Lens & Technical Notation)

> 焦段、景深、摄影机参数的技术标注规范。供 storyboard Agent 和 Seedance prompt 生成使用。

## 一、镜头技术标注速查表

```
┌─────────────────────────────────────────────────┐
│  焦距   │  类型    │ 视觉效果         │ 适用场景       │
├─────────┼─────────┼─────────────────┼──────────────┤
│ 14mm    │ 超广角   │ 极端透视畸变      │ 空间/压迫感    │
│ 18mm    │ 广角     │ 强透视, 边角拉伸  │ 室内/全景      │
│ 24mm    │ 广角     │ 自然透视, 略有夸张 │ 建立镜头/环境   │
│ 35mm    │ 标准广角 │ 接近人眼, 略有广角 │ 纪实/街景       │
│ 50mm    │ 标准     │ 接近人眼视角      │ 中景/人像       │
│ 85mm    │ 中长焦   │ 平实透视, 略压缩   │ 人像/特写      │
│ 100mm   │ 中长焦   │ 透视压缩明显       │ 人像/特写      │
│ 135mm   │ 长焦     │ 强透视压缩         │ 远景特写/偷拍  │
│ 200mm   │ 超长焦   │ 严重压缩,失真敏感   │ 远距离特写      │
└─────────┴─────────┴─────────────────┴──────────────┘
```

## 二、焦段选择原则与叙事意义

| 焦段 | 叙事意义 | 情绪效果 | 典型用途 |
|------|---------|---------|---------|
| **广角 14-24mm** | 环境至上，人物渺小 | 不安、渺小、空间压迫 | 揭示场景规模、困境、梦境 |
| **广角 28-35mm** | 真实感、日常感 | 自然、纪实、客观 | 街景、日常镜头、环境人物 |
| **标准 50mm** | 人眼视角，中立观察 | 自然、亲切、平等 | 中景对话、立等人物关系 |
| **中长焦 85mm** | 人物至上，环境虚化 | 亲近、亲密、聚焦 | 人像特写、情感表意 |
| **长焦 135mm+** | 压缩空间，隔离主体 | 隔离、神秘、窥视 | 远距离威慑、推拽、偷拍 |

## 三、Seedance 焦段关键词

| 焦段范围 | Seedance prompt关键词 | 视觉效果 |
|---------|----------------------|---------|
| 14-20mm | `extreme wide angle, fisheye-like distortion, ultra wide perspective` | 空间变形、冲击感 |
| 24-28mm | `wide angle, expansive frame, environmental context` | 开阔、场景感 |
| 35-50mm | `natural perspective, eye-level, standard focal length` | 自然、真实 |
| 85mm | `medium telephoto, portrait lens, subject isolation` | 人像、虚化 |
| 100mm+ | `long lens, telephoto compression, background blur` | 紧缩、迷离 |

**使用规则**：在 Seedance prompt 中标注焦段 + 画面效果，而非仅仅数字。

## 四、景深标注系统（Depth of Field）

```
┌─────────────────────────────────────────────────┐
│  景深类型          │ 符号    │ 使用场景         │
├──────────────────┼─────────┼────────────────┤
│  深景深/泛焦       │ D-Deep  │ 全景, 所有东西清晰│
│  (Deep DOF)       │         │                 │
│  中等景深/焦点     │ M-Med   │ 主角清晰,背景略虚│
│  (Medium DOF)     │         │                 │
│  浅景深/虚化背景   │ S-Shall │ 人物特写虚化背景 │
│  (Shallow DOF)    │         │ 人物主角         │
│  极浅景深/主角圈  │ XS-Ext  │ 锁定面部，其他全虚│
│  (Extreme Shallow)│         │                 │
│  拉焦/变焦镜头    │ R-Rack  │ 焦点在前后之间   │
│  (Rack Focus)     │         │ 转换              │
└──────────────────┴─────────┴────────────────┘
```

### 景深对应的 Seedance 关键词

| 景深 | Seedance prompt关键词 |
|------|----------------------|
| Deep DOF | `deep focus, all elements sharp, environmental clarity` |
| Medium DOF | `selective focus on subject, slightly soft background` |
| Shallow DOF | `shallow depth of field, bokeh background, subject isolation` |
| Extreme Shallow | `extreme shallow focus, sharp eyes only, dreamy bokeh` |
| Rack Focus | `rack focus shift, focus pulls from [foreground] to [background]` |

## 五、镜头移动速度与情绪映射

| 移动类型 | 速度 | 情绪效果 | Seedance关键词 |
|---------|------|---------|----------------|
| 静态镜头 | 0 | 凝视、压力、紧张 | `static camera, fixed frame` |
| 极慢移动 | 1-2% | 庄严、沉重、苍凉 | `extremely slow [movement], almost imperceptible` |
| 慢速 | 3-5% | 悲伤、沉思、等待 | `slow [movement], measured pace` |
| 中速 | 5-8% | 标准叙事 | `steady [movement] at moderate speed` |
| 快速 | 10-15% | 兴奋、追逐、突然 | `quick [movement], increasing speed` |
| 急速 | 20%+ | 混乱、危机、冲击 | `rapid [movement], handheld urgency` |

**注**：%-表示每秒画面移动的百分比 (例如：画面高度1%表示隐形不可察觉的缓慢移动)

## 六、镜头参考标注速查

```
常用镜头参考：
├── 14mm = 隐形广角, 环境戏剧化
├── 24mm = 建立镜头, 全景
├── 35mm = 主客观中性镜头
├── 50mm = 标准, 人眼视角
├── 85mm = 人像, 静态特写
└── 200mm = 长焦压缩, 远距离

随手记录格式：
[焦距] / [景深] / [移动]
例：50mm / S / Pan-R
```

## 七、为 AI 工具标注镜头参数

在 Seedance prompt 中包含镜头技术参数时，使用以下模板：

```
[Cinematic/Anamorphic] shot
Shot on [camera reference - e.g., Arri Alexa 65, RED Komodo]
Lens: [focal length] mm, [depth of field type]
Camera movement: [movement type] at [speed]
Frame rate: [24/30/60]fps
Aspect ratio: [ratio]
```

## 八、常用配置组合

| 类型片 | 推荐镜头配置 | 光圈特征 |
|--------|------------|---------|
| 文艺片 | 35mm / 50mm 为主, 偶尔 85mm | 中等景深 (T2.8-T4) |
| 史诗片 | 24mm / 35mm 为主 | 深景深 (T5.6-T8) |
| 悬疑/惊悚 | 35mm + 低光圈 | 深景深 (T4-T8) |
| 浪漫/爱情 | 85mm / 50mm | 浅景深 (T1.4-T2) |
| 动作片 | 24mm / 35mm + 长焦 | 中等景深 (T2.8-T4) |
| 喜剧 | 35-50mm | 深景深 (T4-T5.6) |

