# Seedance Prompt 模板库

> Seedance 2.0/2.5 视频生成 Prompt 模板、优化规则和参数指南。

## 一、T2V 文生视频模板

### 黄金结构

```
Seedance 文生视频 Prompt 黄金结构：

[Scene Description in Motion] + [Subject Action] + [Environment Details] + 
[Lighting Changes] + [Camera Movement] + [Mood/Atmosphere] + 
[Style Reference] + [Duration + FPS + Quality]

末尾追加：
Negative: [video-specific negative prompts]
```

### T2V 5 条优化规则

```
规则1：动作具体化 ✅
❌ "walks" → ✅ "walks slowly, each step echoing, rain dripping from coat"
❌ "looks around" → ✅ "slowly turns head left to right, eyes scanning, alert"
❌ "tense atmosphere" → ✅ "tense atmosphere, shallow breathing implied, 
    beads of sweat visible"

规则2：环境动态化 ✅
为场景添加动态元素：
- 天气动态：rain falling, snow drifting, fog rolling, lightning flickering
- 光线动态：shadows shifting, neon flickering, candlelight dancing, 
            sunrise light gradually filling the room
- 自然动态：leaves rustling, water rippling, dust floating, fire crackling
- 城市动态：traffic passing, crowd moving, signs blinking

规则3：镜头运动精确化 ✅
❌ "camera moves" → ✅ "Camera slowly dollies forward at eye level, 
    maintaining 2-meter distance from subject"
❌ "pan" → ✅ "Slow pan from left to right, starting at the broken window, 
    ending on the frozen clock face"

规则4：时长+FPS统一标注 ✅
每个T2V prompt末尾固定格式：
"[Duration]s, [FPS]fps, cinematic quality, smooth motion"

规则5：Style Anchor追加 ✅
每个prompt包含全局Style Anchor
```

### T2V Prompt 示例

```
[A woman in her mid-30s walks slowly through a rain-soaked narrow alley in 2049 Shanghai at midnight. 
Neon signs reflect on wet asphalt in cyan and magenta. Steam rises from manhole covers. 
The woman reaches the end of the alley and stops, looking up at the flickering holographic advertisement. 
Camera slowly dollies forward at eye level, maintaining 2-meter distance from the subject. 
Mist swirling around her combat boots. Ambient city sounds: distant traffic, muffled rain, neon buzzing. 
Mood: contemplative, lonely, melancholic. 

Style: cinematic, hyperrealistic, in the style of Wong Kar-wai. 

5s, 24fps, cinematic quality, smooth motion]

Negative: jittery, inconsistent frames, blurry, deformed face, plastic texture, watermark
```

## 二、I2V 图生视频模板

### 黄金结构

```
Seedance 图生视频 Prompt 黄金结构：

Image-to-video mode.
Starting from the reference image: [与GPT-image-2关键帧完全一致的场景描述].
[Scene fixed description fragment].
[Character fixed description fragment] — 如场景中有角色.
Motion: [具体运动描述 — 从参考图的静态开始].
Camera: [镜头运动描述].
Duration: [N]s, [FPS]fps, cinematic quality, smooth transition.
[Global Style Anchor]
Negative: [video-specific negative prompts]
```

### I2V 4 条特殊优化规则

```
规则A：参考图描述一致性 ⭐⭐⭐（最重要）
"Starting from the reference image"后的描述必须与该镜头的GPT-image-2关键帧prompt中的场景描述严格一致
→ 从对应的关键帧prompt中复制场景/角色描述部分

规则B：链条式运动描述
从"静态参考图"→"开始发生运动"的链条式描述：
"Starting from reference image: [静态]. 
Motion: She slowly raises her hand, fingers trembling, 
reaching toward the object on the table. 
Dust particles disturbed by her movement float into the light beam."

规则C：运动边界提示
Seedance对复杂快速运动处理不稳定，识别并标记潜在风险：
⚠️ 标记：动作包含"快速转身+跑动+跳跃"→ 建议拆分为2个镜头
⚠️ 标记：多角色同时运动 → 建议每个角色独立镜头
⚠️ 标记：物体形变 → 建议降低复杂度或换用T2V

规则D：过渡平滑性
确保运动描述从参考图的静态状态自然过渡：
❌ 参考图：角色坐着 → Motion: She runs across the room
✅ 参考图：角色坐着 → Motion: She slowly stands up from the chair, 
    then takes a step forward
```

### I2V Prompt 示例

```
[Image-to-video mode.
Starting from the reference image: a rain-soaked narrow alley in 2049 Shanghai at midnight, neon signs reflecting on wet asphalt in cyan and magenta, steam rising from manhole covers.
A woman in her mid-30s, athletic lean build, sharp jawline, almond-shaped dark eyes with tired shadows, short choppy black hair, standing still at the center of the frame, wearing a worn black leather jacket over grey hoodie.
Motion: She slowly steps forward, left foot first, water splashing slightly under her combat boot. Her hair sways gently. She looks up, eyes reflecting the neon signs.
Camera: Slow dolly in, eye level, maintaining focus on her face. Slight handheld subtle movement.
4s, 24fps, cinematic quality, smooth transition.

Style: cinematic, hyperrealistic, in the style of Wong Kar-wai.]

Negative: jittery, deformed face, inconsistent character appearance, jitter, watermark
```

## 三、Seedance 关键词增强表

| 分镜 Agent 原始描述 | Seedance 增强版 |
|---|---|
| "角色走路" | "walks slowly, steady pace, footsteps echoing, slight sway in shoulders, natural arm swing" |
| "镜头推近" | "Slow dolly in, smooth steady movement, gradually closing distance, maintaining focus on subject's face" |
| "紧张氛围" | "tense atmosphere, shallow breathing, barely perceptible movement, held breath quality, slow-burn tension" |
| "雨夜" | "rain falling steadily, water droplets on surfaces, wet reflections on pavement, distant thunder flash, atmospheric haze" |
| "转头" | "slowly turns head, deliberate movement, eyes move first then head follows, revealing expression change" |

## 四、T2V vs I2V 模式选择决策树

```
Decision Tree:
├── 镜头是否包含关键角色（有角色圣经的人物）？
│   ├── YES → 推荐I2V（图生视频）⭐
│   │   └── 理由：角色一致性是最高优先级，从GPT-image-2关键帧开始最可控
│   └── NO → 继续判断
│       ├── 是否为纯风景/空镜/环境建立镜头？
│       │   └── YES → 推荐T2V（文生视频）
│       │       理由：无需角色一致性，T2V更快更灵活
│       ├── 是否为抽象/风格化过渡镜头？
│       │   └── YES → 推荐T2V
│       │       理由：需要AI创意随机性，I2V过于受限于参考图
│       └── 是否为角色特写（面部/手部）？
│           └── YES → 推荐I2V
│               理由：面部一致性至关重要

最终决策标记格式：
🎬 镜头 S[场景]-[序号] → 推荐模式：[T2V / I2V]
理由：[一句话]
```

## 五、Seedance Prompt 长度限制

```
最短：~30 词
推荐：80-200 词
最长（建议）：~400 词

超出长度的处理：
- 拆分场景描述为多个章节
- 用句号切分逻辑
- 删除重复描述
- 重点放在动作和镜头上，弱化静态描述（这些可从参考图中读取）
```

---

## 参考来源

- `../../references/seedance-guide.md` - 模型能力详细说明
- `../../references/emotion-cinematography-mapping.md` - 情绪→参数映射
- ../../agents/seedance-composer/SKILL.md - 即时对话式 prompt 生成
