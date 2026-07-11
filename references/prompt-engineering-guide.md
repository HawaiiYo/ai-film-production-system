# 🎨 Prompt工程最佳实践指南

> Prompt Engineering Guide for AI Filmmaking — 针对GPT-image-2和Seedance的prompt工程方法论

---

## 一、Prompt工程核心原则

### 1. 结构化描述公式

```
图像生成 (GPT-image-2):
[Subject] + [Action/Pose] + [Clothing/Props] + [Environment] + [Lighting] + [Composition] + [Style] + [Quality]

视频生成 (Seedance):
[Subject/Action] + [Camera Movement] + [Lighting] + [Environment] + [Mood] + [Style] + [Duration] + [Technical]
```

### 2. 具体 > 抽象

| ❌ 模糊 | ✅ 具体 |
|---------|--------|
| "好看的" | "对称的面部结构，高颧骨，深邃的眼窝" |
| "电影感" | "cinematic lighting with 3-point setup, shallow depth of field, 24fps, anamorphic lens" |
| "氛围很好" | "misty atmosphere with volumetric light rays breaking through venetian blinds" |
| "很酷的" | "cyberpunk aesthetic, neon purple and teal color palette, wet reflective surfaces" |

### 3. 权重标记（用于GPT-image-2）

使用括号增加关键词权重：
```
(cyberpunk aesthetic:1.3), (neon lighting:1.2), cinematic shot
```
注意：权重语法因工具版本而异，此处为参考格式。

### 4. Negative Prompt策略

Negative prompt告诉AI**不要**生成什么，和正面prompt同等重要：

```
图像通用Negative:
ugly, deformed, blurry, low quality, bad anatomy, extra fingers, 
asymmetric face, watermark, text, logo, jpeg artifacts

视频通用Negative:
jittery, flickering, morphing artifacts, inconsistent frames, 
blurry, low resolution, deformed face, warped anatomy
```

---

## 二、GPT-image-2 Prompt工程

### 角色设计图Prompt结构

```
Character Design Sheet: [角色名]
A [性别] [大致年龄], [体型描述], [肤色], [面部特征详细描述].
Wearing [服装完整描述，含颜色/材质/风格].
[发型/化妆描述].
Standing in [姿势], [表情].
[光线方案], [风格参考].
Character design sheet, full body, front view + side view + back view, 
multiple expression variants (neutral, happy, angry, sad).
8K resolution, hyperrealistic, professional character concept art.
```

**示例**：
```
Character Design Sheet: Detective Maya Chen
A woman in her mid-30s, athletic lean build, East Asian features, pale skin, 
sharp jawline, almond-shaped dark eyes with tired shadows underneath, 
thin scar across left eyebrow.
Wearing a worn black leather jacket over a grey hoodie, dark jeans, 
combat boots, a silver detective badge on a chain around her neck.
Short choppy black hair, no makeup, slightly chapped lips.
Standing in a confident but weary pose, neutral expression with a hint of skepticism.
Film noir lighting, single overhead practical light casting dramatic shadows, 
smoke in the air.
Character design sheet, full body, front view + side view + back view, 
multiple expression variants.
8K resolution, hyperrealistic, professional character concept art, 
in the style of Blade Runner 2049 character designs.
```

### 场景概念图Prompt结构

```
Environment Concept Art: [场景名]
[地点类型], [时间], [天气], [光线条件].
[建筑/空间详细描述], [材质/纹理].
[色彩方案], [氛围].
[构图角度], [镜头选择].
[关键道具/元素描述].
8K resolution, cinematic lighting, professional environment concept art, 
in the style of [参考风格].
```

**示例**：
```
Environment Concept Art: Abandoned Clocktower Interior
A massive abandoned clocktower interior, 3:33 AM, foggy night, 
moonlight streaming through broken stained glass windows.
Victorian gothic architecture, exposed iron gears and mechanisms, 
rusted metal surfaces, cracked marble floor with puddles of water.
Dust particles floating in the moonbeams, volumetric light.
Color palette: deep blues and silvers with warm amber highlights 
from a single flickering lantern on the floor.
Wide angle shot, looking up from ground level, 
emphasizing the towering height and the massive frozen clock face above.
8K resolution, cinematic lighting, ray tracing, 
professional environment concept art, 
in the style of Dark City meets Inception concept art.
```

### 道具/物品Prompt结构

```
Prop Design: [道具名]
[道具整体描述], [材质], [颜色], [尺寸感].
[使用痕迹/磨损状态], [特殊功能/细节].
Isolated on [背景], product photography style.
[光线方案].
8K resolution, hyperrealistic, professional prop design.
```

---

## 三、Seedance 2.5 视频生成Prompt工程

Seedance 2.5 支持两种生成模式：

### 模式A：文生视频（Text-to-Video）

直接从文本描述生成视频。

**文生视频Prompt结构**：
```
[Scene description in motion], [camera movement], [lighting changes], 
[mood/atmosphere], [style], [duration hint], [technical quality].
```

**示例**：
```
A detective walks slowly through a narrow neon-lit alley in the rain. 
Camera slowly dollies forward, following from behind at eye level. 
Neon signs flicker and reflect off wet pavement. 
Moody, tense, film noir atmosphere. 
Cinematic quality, 24fps, smooth motion, anamorphic lens look, 
shallow depth of field, 5 seconds.
```

**Seedance文生视频关键词库**：

| 类别 | 有效关键词 |
|------|-----------|
| 动作 | walking slowly, running, turning around, reaching out, standing up, sitting down, looking up, nodding, fighting |
| 运动质量 | smooth, fluid, graceful, mechanical, jerky, sluggish, explosive |
| 环境变化 | rain falling, snow drifting, leaves blowing, fog rolling, fire flickering, water rippling |
| 光线变化 | light shifting, shadows moving, neon flickering, sunrise/sunset transition |
| 情绪 | tense, peaceful, melancholic, intense, dreamy, energetic |
| 节奏 | slow motion, real time, time-lapse, fast-paced |

### 模式B：图生视频（Image-to-Video）

从参考图像（GPT-image-2生成的关键帧）开始，生成后续运动的视频。

**图生视频Prompt结构**：
```
Image-to-video mode.
Starting from the reference image: [image description matching the reference].
Motion: [specific motion happening in the scene].
Camera: [camera movement description].
Duration: [seconds]s, [fps]fps.
```

**示例**：
```
Image-to-video mode.
Starting from reference image: Female detective stands in abandoned clocktower interior, 
moonlight through broken windows, dust in the air, lantern at her feet.
Motion: She slowly looks up toward the frozen clock face, 
her breath visible in the cold air, dust particles drifting around her.
Camera: Slow tilt up from her face to reveal the massive clock mechanism above, 
maintaining shallow depth of field.
Duration: 6s, 24fps, cinematic quality.
```

### Seedance技术参数

| 参数 | 可选值 | 建议 |
|------|--------|------|
| 分辨率 | 720p, 1080p, 4K | 短片用1080p，全片用4K |
| 帧率 | 24fps, 25fps, 30fps | 电影感用24fps，标准视频用30fps |
| 时长 | 2~10秒/段 | 建议5秒左右，太短不够展开，太长容易崩 |
| 风格强度 | 写实/风格化 | 根据导演风格选定 |

---

## 四、一致性保障Prompt技巧

### 1. 角色描述模板化

为每个角色建立**固定描述片段**，所有涉及该角色的prompt都复用这个片段：

```
角色A固定描述 = "A woman in her mid-30s, athletic lean build, East Asian features, 
sharp jawline, short choppy black hair, tired dark eyes, thin scar across left eyebrow"

场景1 prompt: [角色A固定描述] walking through neon alley...
场景2 prompt: [角色A固定描述] sitting in a dimly lit office...
场景3 prompt: [角色A固定描述] running across a rain-soaked rooftop...
```

### 2. 场景描述模板化

同样为每个场景建立固定描述：

```
场景3固定描述 = "Abandoned Victorian clocktower interior, broken stained glass, 
moonlight beams, dust particles, amber lantern on floor"

镜头1: Wide shot of [场景3固定描述], character enters from left...
镜头2: Close-up inside [场景3固定描述], focusing on the frozen clock face...
镜头3: Dutch angle in [场景3固定描述], shadows dancing on the walls...
```

### 3. 全局风格锚点

在每个prompt中加入统一的风格锚点：

```
全局风格锚点 = "cinematic 24fps, anamorphic lens, teal and orange color grade, 
shallow depth of field, film grain"
```

### 4. Seed值管理

- 同一角色的不同镜头：使用相同或相近的seed值
- 同一场景的不同角度：使用相同seed值
- 完全不同的场景：使用不同的seed值

### 5. 跨帧一致性检查表

在生成所有prompt后，进行检查：
- [ ] 所有角色prompt中，同一角色的描述是否完全一致？
- [ ] 所有场景prompt中，同一场景的描述是否完全一致？
- [ ] 全局风格描述是否在每个prompt中出现？
- [ ] 光线/色彩描述是否与导演风格指南一致？
- [ ] 服装是否在连续时间线中保持一致？

---

## 五、常见问题与解决方案

### 问题1：角色在不同镜头中长得不一样
**原因**：每次生成的描述有差异
**解决**：使用角色描述模板，严格复用完全相同的描述片段

### 问题2：场景风格跳跃
**原因**：不同场景的描述没有统一的风格锚点
**解决**：所有prompt末尾都加入相同的风格锚点描述

### 问题3：视频中动作变形/闪烁
**原因**：Seedance对复杂动作的处理不稳定
**解决**：
- 将复杂动作拆分为多个简单动作（分不同镜头）
- 降低动作描述复杂度
- 使用图生视频模式，从确定的参考图开始

### 问题4：画面中出现不希望的元素
**原因**：Negative prompt不够全面
**解决**：针对性地添加negative prompt

### 问题5：画面太"塑料感"或"CG感"
**原因**：AI过度拟合训练数据中的CG风格
**解决**：添加 `photorealistic, natural skin texture, film grain, practical lighting` 等质

感关键词

---

## 六、Prompt模板速查

### GPT-image-2 — 角色全身像
```
Full body character portrait of [角色名]: [年龄][性别][体型][面部特征].
Wearing [服装].
[发型][化妆].
[姿势][表情].
[光线]: [具体光线描述].
[构图]: full body shot, centered.
Style: [风格参考], professional character concept art, 8K, hyperrealistic.
Negative: ugly, deformed, blurry, low quality, bad anatomy.
```

### GPT-image-2 — 场景概念图
```
Environment concept art: [场景名].
[时间][天气][地点描述].
[光线][色彩方案][氛围].
[空间布局][关键元素].
Wide angle establishing shot, cinematic composition.
Style: [风格参考], professional environment concept art, 8K, hyperrealistic, ray tracing.
Negative: blurry, low quality, distorted perspective.
```

### Seedance — 文生视频
```
[主体动作描述], [环境], [光线变化].
Camera: [镜头运动].
Mood: [情绪].
Style: [风格参考], cinematic, 24fps, [duration]s, smooth motion, [quality].
Negative: jittery, flickering, morphing artifacts, blurry, low resolution.
```

### Seedance — 图生视频
```
Image-to-video mode, reference: [参考图描述].
Motion: [具体运动描述].
Camera: [镜头运动].
Duration: [duration]s, 24fps, cinematic quality, smooth transition.
Negative: jittery, flickering, inconsistent frames, warped anatomy, blurry.
```

---

*持续更新中，随AI工具版本迭代优化*
