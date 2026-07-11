# 🎥 Seedance 2.0/2.5 使用指南

> Seedance Reference Guide — 字节跳动即梦AI视频生成模型的能力边界和最佳实践

---

## 一、模型概述

**Seedance**（即梦AI视频生成模型）是字节跳动推出的AI视频生成模型，目前有2.0和2.5版本。

### 核心能力
- **文生视频（Text-to-Video）**：从纯文本描述生成视频
- **图生视频（Image-to-Video）**：从参考图像开始生成动态视频
- **动态镜头**：擅长处理镜头运动和人物动作
- **高画质输出**：支持多种分辨率和帧率

### 在本项目中的角色
Seedance是AI电影工坊的**核心视频生成引擎**：
- 🎬 将分镜脚本转化为实际视频片段
- 🎥 支持图生视频和文生视频两种工作流
- 🎞️ 输出电影感视频片段

---

## 二、Seedance的优势

### 1. 动态表现
- ✅ 人物动作流畅自然
- ✅ 镜头运动（推拉摇移）效果良好
- ✅ 对运动描述的响应准确

### 2. 画面质量
- ✅ 画质清晰
- ✅ 光影变化自然
- ✅ 场景一致性较好

### 3. 风格适配
- ✅ 支持多种视觉风格
- ✅ 对风格描述词的响应较好
- ✅ 支持电影感、动画、写实等多种风格

---

## 三、Seedance的局限

### 1. 时长限制
- ⚠️ 单次生成时长有限（通常2-10秒）
- ⚠️ 长视频需要分段生成再拼接

### 2. 复杂动作
- ⚠️ 过于复杂的动作可能导致变形
- ⚠️ 快速运动可能出现模糊/闪烁

### 3. 一致性
- ⚠️ 文生视频模式下角色一致性较难保证
- ⚠️ 建议使用图生视频模式提升一致性

### 4. 细节控制
- ⚠️ 精确控制特定元素的难度较高
- ⚠️ 复杂的多角色交互场景可能出现问题

---

## 四、两种工作流模式

### 模式A：文生视频（Text-to-Video）

**适用场景**：
- 不需要精确角色一致性的场景
- 风景/空镜/环境镜头
- 抽象/风格化内容
- 快速原型/测试

**工作流**：
```
分镜Agent → Seedance文生视频Prompt → 直接生成视频
```

**Prompt结构**：
```
[场景描述] + [动作/运动] + [镜头运动] + [光线/氛围] + [风格] + [时长] + [技术参数]
```

**示例**：
```
A misty forest at dawn, sunlight breaking through the canopy, 
leaves gently swaying in the breeze.
Camera slowly pans right, revealing a winding path disappearing into the fog.
Atmospheric, peaceful, magical realism.
Cinematic, 24fps, 6 seconds, smooth camera movement.
```

### 模式B：图生视频（Image-to-Video）⭐ 推荐

**适用场景**：
- 需要角色一致性的镜头
- 需要场景一致性的镜头
- 精确构图的镜头
- 高质量要求的镜头

**工作流**：
```
角色/场景Agent → GPT-image-2生成关键帧 → Seedance图生视频 → 视频片段
```

**Prompt结构**：
```
Image-to-video mode.
Starting from the reference image: [与参考图一致的描述].
Motion: [从静态参考图开始的运动描述].
Camera: [镜头运动].
Duration: [时长]s, 24fps.
```

**示例**：
```
Image-to-video mode.
Starting from reference image: Female detective with short black hair stands 
in a neon-lit alley, rain falling, wearing a black leather jacket, 
holding a flickering flashlight.

Motion: She slowly raises the flashlight, scanning the alley walls, 
rain droplets visible on her jacket, her breath misting in the cold air.

Camera: Slow dolly in, from medium shot to close-up, 
shallow depth of field on her face.

Duration: 5s, 24fps, cinematic quality, smooth motion.
```

---

## 五、Seedance Prompt关键词库

### 动作关键词

| 类别 | 关键词 | 适用场景 |
|------|--------|---------|
| 行走 | walking slowly, walking briskly, striding, staggering, tiptoeing | 角色移动 |
| 站/坐 | standing still, sitting down, leaning against, crouching | 静态场景 |
| 手部 | reaching out, holding up, pointing, typing, grabbing | 特写/交互 |
| 头部 | looking up, turning head, nodding, shaking head | 反应/对话 |
| 面部 | smiling slowly, eyes widening, frowning, crying | 情感表达 |
| 全身 | running, jumping, falling, fighting, dancing | 动作场景 |
| 对话 | talking, whispering, shouting, laughing | 对话场景 |

### 镜头运动关键词

| 运动 | 关键词 | 视觉效果 |
|------|--------|---------|
| 静态 | static shot, locked off, tripod | 稳定、观察 |
| 推 | dolly in, push in, moving closer | 靠近、紧张 |
| 拉 | dolly out, pull back, revealing shot | 揭示、孤独 |
| 摇 | pan left/right, sweeping camera | 扫描、过渡 |
| 俯仰 | tilt up/down, crane up/down | 高度变化 |
| 跟 | tracking shot, following, steadicam | 跟随、流动 |
| 手持 | handheld, shaky cam, documentary style | 紧张、真实 |
| 旋转 | orbit shot, circling, 360 degree | 包围感 |
| 变焦 | zoom in/out, crash zoom | 突显、强调 |
| 特殊 | dolly zoom/vertigo effect | 扭曲空间感 |

### 环境/氛围关键词

| 类别 | 关键词 |
|------|--------|
| 天气 | rain falling, snow drifting, fog rolling, lightning flash |
| 光线 | sunlight streaming, neon flickering, candlelight dancing, shadows moving |
| 自然 | leaves rustling, water flowing, fire crackling, clouds drifting |
| 城市 | traffic passing, crowd moving, signs blinking, subway arriving |

### 风格/质感关键词

| 风格 | 关键词 |
|------|--------|
| 电影感 | cinematic, 24fps, anamorphic, film grain, Kodak, Arri Alexa |
| 写实 | photorealistic, natural lighting, practical effects |
| 赛博朋克 | cyberpunk, neon noir, dystopian, blade runner aesthetic |
| 复古 | vintage, 1970s film stock, super 8, retro aesthetic |
| 动画 | anime style, hand-drawn animation, Studio Ghibli style |
| 纪录片 | documentary style, verite, observational, naturalistic |

---

## 六、在本项目中的使用流程

### 标准工作流（推荐）

```
Step 1: 剧本Agent → 确定场景和镜头
Step 2: 角色设计Agent → 用GPT-image-2生成角色关键帧
Step 3: 场景道具Agent → 用GPT-image-2生成场景关键帧
Step 4: 分镜Agent → 为每个镜头设计详细的运动描述
Step 5: Prompt工程Agent → 整合优化为Seedance prompt
Step 6: 用户执行 → 将prompt输入Seedance生成视频
Step 7: (可选) 后期制作Agent → 调色/剪辑方案
```

### 每镜头输出格式

```
🎬 镜头 #001
├── 场景：废弃钟楼内部
├── 景别：大远景
├── 运动：缓慢上升（Crane Up）
├── 时长：6秒
├── 模式：图生视频
├── 参考图：scene_clocktower_establishing.png（GPT-image-2生成）
├── Prompt（英文）：
│   Image-to-video mode.
│   Reference: Abandoned clocktower interior, moonlight through broken
│   stained glass, massive frozen clock mechanism, amber lantern on floor.
│   Motion: Dust particles float in moonbeams, lantern flame flickers
│   gently, slight atmospheric haze drifting.
│   Camera: Slow crane up from ground level, revealing the towering
│   interior and the massive frozen clock face above.
│   Duration: 6s, 24fps, cinematic, anamorphic lens, film grain.
└── Negative Prompt: jittery, flickering, warped architecture,
    inconsistent lighting, blurry, low resolution
```

---

## 七、常见问题

### Q: 图生视频和文生视频哪个更好？
**A**: 图生视频在角色/场景一致性上远优于文生视频。推荐流程：GPT-image-2出关键帧 → Seedance图生视频。

### Q: 如何保持角色在不同镜头中一致？
**A**: 使用图生视频模式，所有涉及该角色的镜头都从同一个角色关键帧图开始。每个镜头的prompt中复用相同的角色描述模板。

### Q: 长视频怎么做？
**A**: 将长视频拆分为2-10秒的片段，分别生成后在剪辑软件中拼接。分镜Agent会帮你规划好拆分方案。

### Q: Seedance 2.0和2.5有什么区别？
**A**: 2.5版本在画质、运动流畅度、一致性方面有提升。两个版本的prompt结构基本相同。

---

*持续更新中，随Seedance版本迭代优化*