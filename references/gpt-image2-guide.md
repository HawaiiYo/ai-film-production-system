# 🖼️ GPT-image-2 使用指南

> GPT-image-2 Reference Guide — OpenAI图像生成模型的能力边界和最佳实践

---

## 一、模型概述

**GPT-image-2** 是OpenAI推出的图像生成模型，专注于高质量、高可控性的图像生成。

### 核心能力
- **文生图（Text-to-Image）**：从文本描述生成图像
- **高保真度**：人脸、材质、光影的精细呈现
- **风格多样性**：从照片写实到概念艺术，多风格支持
- **编辑能力**：支持图像编辑和变体生成

### 在本项目中的角色
在本AI电影工坊中，GPT-image-2负责**所有静

态视觉素材的生成**：
- 🎭 角色设计图 / 定妆照
- 🏗️ 场景概念图 / 氛围图
- 🔧 道具设计图
- 🎬 关键帧参考图（用于驱动Seedance图生视频）

---

## 二、GPT-image-2的优势

### 1. 角色设计
- ✅ 面部特征精确控制
- ✅ 服装材质表现
- ✅ 多角度角色设计图
- ✅ 表情变体生成

### 2. 场景概念
- ✅ 复杂建筑和空间结构
- ✅ 光线氛围营造
- ✅ 材质纹理呈现
- ✅ 大规模场景构图

### 3. 风格控制
- ✅ 明确风格参考词有效
- ✅ 能理解电影摄影术语
- ✅ 可指定构图方式

---

## 三、GPT-image-2的局限

### 1. 一致性挑战
- ⚠️ 同一角色在不同生成中可能出现差异
- ⚠️ 需要严格的描述模板来维持一致性

### 2. 复杂场景
- ⚠️ 过多元素可能导致某些元素被忽略
- ⚠️ 复杂的手部姿势有时仍会出错

### 3. 文字生成
- ⚠️ 图像中的文字（招牌、海报等）可能不准确
- ⚠️ 如需准确文字，建议后期添加

---

## 四、针对GPT-image-2的Prompt优化

### 角色设计Prompt最佳结构

```
[角色类型] + [年龄+性别+体型] + [面部详细特征] + [发型] + [服装完整描述] +
[姿势+表情] + [光线方案] + [构图] + [风格参考] + [画质参数]
```

### 关键要素优先级
1. **面部特征**（最重要）：脸型、眼睛、鼻子、嘴、特殊标记
2. **服装**：风格、颜色、材质、层次
3. **光线**：方向、色温、质感
4. **构图**：视角、景别
5. **风格**：参考风格、艺术家
6. **画质**：分辨率、细节度

### 风格关键词库

| 风格 | 关键词 |
|------|--------|
| 照片写实 | photorealistic, hyperrealistic, 8K, RAW photo, natural skin texture |
| 概念艺术 | concept art, professional character design, key visual |
| 电影感 | cinematic, anamorphic lens, film grain, Kodak Portra |
| 赛博朋克 | cyberpunk, neon noir, dystopian, high tech low life |
| 科幻 | sci-fi, futuristic, biomechanical, holographic |
| 奇幻 | fantasy, magical realism, ethereal, mythical |
| 水墨/东方 | ink wash painting, Chinese watercolor, wuxia aesthetic |
| 黑暗/惊悚 | dark atmosphere, horror aesthetic, gothic, chiaroscuro |
| 温暖/文艺 | warm tones, golden hour, nostalgic, romantic, soft focus |
| 极简 | minimalist, clean composition, negative space, Scandinavian |

---

## 五、在本项目中的使用场景

### 场景1：角色设计图
```
目的：建立角色视觉形象，供分镜Agent和Seedance参考
输出：多角度角色设计图 + 表情变体
用法：作为角色圣经的一部分
```

### 场景2：场景概念图
```
目的：确定场景的视觉方向
输出：全景场景概念图
用法：作为场景圣经的一部分，指导Seedance生成
```

### 场景3：关键帧
```
目的：为Seedance图生视频提供起始帧
输出：电影画幅比的写实关键帧
用法：输入Seedance作为图生视频的参考
```

### 场景4：道具设计图
```
目的：关键道具的精确视觉设计
输出：独立道具展示图
用法：保持道具在不同镜头中的一致性
```

---

## 六、提示词风格参考库

### 电影风格参考
```
"in the style of Blade Runner 2049 concept art"
"in the style of Denis Villeneuve cinematic"
"in the style of Christopher Nolan's Inception"
"in the style of Wong Kar-wai cinematography"
"in the style of Wes Anderson symmetrical composition"
"in the style of David Fincher color grading"
"in the style of Studio Ghibli background art"
"in the style of Akira Kurosawa epic framing"
```

### 摄影风格参考
```
"shot on Arri Alexa, anamorphic lens"
"shot on IMAX 70mm film"
"shot on vintage Leica, Kodak Portra 400"
"shot on RED camera, Zeiss prime lenses"
"documentary style, handheld"
```

---

*持续更新中，随GPT-image-2版本迭代优化*
