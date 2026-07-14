# GPT-image-2 Prompt 模板库

> 5 套完整的 GPT-image-2 prompt 模板结构，供 prompt-engineer Agent 和任何需要生成图像 prompt 的场景使用。

## 一、GPT-image-2 Prompt 黄金通用结构

```
[Subject Type] + [Subject Details] + [Pose/Action/Expression] + 
[Clothing/Accessories - 如为人像] + [Environment/Background] + 
[Lighting Scheme] + [Composition/Framing] + [Color Palette] + 
[Style Reference] + [Quality Parameters] + [Style Anchor]

末尾追加：
Negative: [negative prompts]
```

## 二、5 套分类模板

### 模板 A：角色设计图 (Character Design Sheet)

```
Character Design Sheet: [Character Name]
[Gender] [Approximate Age], [Body Type], [Skin Tone], [Detailed Facial Features].
Wearing [Complete Clothing Description - color/material/style/layers].
[Hair Style Description]. [Makeup - if any].
Standing in [Pose], [Facial Expression].
[Lighting Scheme], [Style Reference].
Character design sheet, full body, front view + side view + back view,
multiple expression variants (neutral, happy, angry, sad, surprised).
8K resolution, hyperrealistic, professional character concept art,
in the style of [Director Style Reference].
[Global Style Anchor]
Negative: ugly, deformed, blurry, low quality, bad anatomy, extra fingers,
missing fingers, asymmetric face, watermark, text, logo, jpeg artifacts.
```

**优化检查点**：
- [ ] 面部特征是否包含脸型、眼睛形状/颜色、鼻子、嘴、特殊标记（疤/痣/纹身）？
- [ ] 服装描述是否包含颜色、材质、风格、层次？
- [ ] 是否包含全身+三视图+表情变体？
- [ ] 风格参考是否来自导演风格指南？
- [ ] Style Anchor是否已追加？

### 模板 B：角色定妆照 (Character Portrait)

```
Character Portrait: [Character Name]
[A single striking portrait of] [角色固定描述片段].
[表情+情绪状态].
[光线方案 - 通常比设计图更具戏剧性].
[构图]: medium close-up, eye-level, looking slightly off-camera,
cinematic portrait composition.
[风格参考], 8K resolution, hyperrealistic, cinematic portrait photography.
[Global Style Anchor]
Negative: ugly, deformed, blurry, low quality, bad anatomy, asymmetric face,
watermark, text, distorted features.
```

**优化检查点**：
- [ ] 是否使用了角色的固定描述片段？
- [ ] 构图是否指定了景别和视线方向？
- [ ] 光线方案是否有戏剧感（与平光的设计图区分）？

### 模板 C：场景概念图 (Environment Concept Art)

```
Environment Concept Art: [Scene Name]
[Time of Day], [Weather Condition], [Location Type].
[Architecture/Space Detailed Description], [Materials/Textures].
[Lighting Conditions], [Color Palette], [Atmosphere/Mood].
[Composition]: [Specific angle], [Lens choice].
[Key Elements/Props in the scene].
8K resolution, cinematic lighting, ray tracing,
professional environment concept art,
in the style of [Director Style Reference].
[Global Style Anchor]
Negative: blurry, low quality, distorted perspective, flat lighting, cartoon.
```

**优化检查点**：
- [ ] 时间/天气/光线三要素是否齐全？
- [ ] 空间描述是否使用了场景固定描述片段？
- [ ] 构图角度是否明确（wide angle / low angle / bird's eye / etc.）？

### 模板 D：场景关键帧 (Key Frame)

```
Key Frame: [Scene Name] - [Shot Description]
[A cinematic frame showing] [场景固定描述片段].
[如果有角色]: [角色固定描述片段] [动作/姿势].
[具体光线条件], [具体构图].
Cinematic frame, 16:9 aspect ratio, [film stock reference],
hyperrealistic, 8K, ready for video input.
[Global Style Anchor]
Negative: blurry, low quality, distorted perspective, visible artifacts.
```

**优化检查点**：
- [ ] 是否明确标注为"Key Frame"和"ready for video input"？
- [ ] 是否包含角色固定描述（如场景中有角色）？
- [ ] 是否指定了16:9（或其他）宽高比？
- [ ] 这张关键帧的构图是否与对应Seedance镜头一致？

### 模板 E：道具设计图 (Prop Design)

```
Prop Design: [Prop Name]
[Prop Overall Description], [Material], [Color], [Size/Scale].
[Wear and Tear / Condition], [Special Features / Details].
Isolated on [Background], product photography style, studio lighting.
[Lighting Scheme].
8K resolution, hyperrealistic, professional prop design,
multiple angles (front, side, detail close-up).
[Global Style Anchor]
Negative: blurry, low quality, distorted proportions, watermark, background clutter.
```

**优化检查点**：
- [ ] 材质/颜色/尺寸三要素是否齐全？
- [ ] 使用痕迹描述是否与故事时代背景一致？
- [ ] 是否包含多角度展示？

## 三、GPT-image-2 Prompt 七条优化规则

```
规则1：结构完整性 ✅
检查每个prompt是否包含完整结构链：
[Subject][Details][Pose][Clothing][Environment][Lighting][Composition][Style][Quality][Anchor]
缺失项 → 从角色圣经/场景圣经中提取并填入

规则2：风格锚点追加 ✅ ⭐
在每一条prompt末尾添加全局Style Anchor
格式："cinematic, [style anchor], 8K resolution, hyperrealistic"
确保100%覆盖率

规则3：具体化替换 ✅
替换所有模糊描述为具体描述：
❌ "好看的" → ✅ "symmetrical facial structure, high cheekbones, deep-set eyes"
❌ "电影感" → ✅ "cinematic lighting with 3-point setup, shallow depth of field"
❌ "很酷" → ✅ "cyberpunk aesthetic, neon purple and teal color palette"
❌ "氛围很好" → ✅ "misty atmosphere with volumetric light rays"

规则4：画质参数增强 ✅
所有GPT-image-2 prompt必须包含：
"8K resolution, hyperrealistic, [specific style keywords], professional [type] concept art"
type = character design / environment concept art / prop design

规则5：风格参考对齐 ✅
检查prompt中的风格参考是否与导演风格指南一致
如不一致 → 替换为导演风格指南中的风格参考

规则6：权重标记建议 ✅
对关键视觉元素标注建议权重（供高级用户使用）：
"(scar across left eyebrow:1.2), (worn leather texture:1.15)"
注意：在最终prompt中以注释形式标注，基础版prompt不含权重语法

规则7：英文完整性 ✅
所有prompt必须使用纯英文
中文描述 → 翻译为精确的英文视觉描述
中英混杂 → 统一为英文
```

## 四、画质参数标准库

```
分辨率：
├── 4K (3840×2160)        - 标准
├── 8K (7680×4320)        - 高端细节
└── 1080p (1920×1080)     - 快速预览

写实度关键词：
├── 基础：hyperrealistic, photorealistic, natural skin texture
├── 进阶：subsurface scattering, subsurface skin detail
└── 电影级：cinematic lighting, anamorphic lens, film grain

技术参数：
├── 光线：ray tracing, global illumination, volumetric lighting
├── 材质：detailed fabric texture, material reflection, refractive surfaces
└── 镜头：anamorphic lens, shallow DOF, tilt-shift

设计类型标签：
├── 角色：professional character concept art, character design sheet
├── 场景：professional environment concept art, cinematic still
├── 道具：professional prop design, product photography
└── 关键帧：cinematic film still, ready for video input
```

---

## 参考来源

- `../../references/gpt-image2-guide.md` - 模型能力和局限
- `../../references/prompt-engineering-guide.md` - 通用 prompt 工程原则
