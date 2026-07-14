# Negative Prompt 库

> 完整的负面提示词分类库，覆盖通用、内容类型、角色特征和流派特定负向词。供 prompt-engineer Agent 使用。

## 一、GPT-image-2 通用 Negative

```
适用于所有 GPT-image-2 图像 prompt：

ugly, deformed, blurry, low quality, bad anatomy, extra fingers,
missing fingers, asymmetric face, distorted features, watermark,
text, logo, signature, jpeg artifacts, oversaturated colors,
motion blur, chromatic aberration, lens flare (unless specified),
poor composition, cropped, out of frame
```

## 二、Seedance 通用 Negative

```
适用于所有 Seedance 视频 prompt：

jittery, flickering, morphing artifacts, inconsistent frames,
blurry, low resolution, deformed face, warped anatomy,
floating limbs, disappearing objects, sudden scene changes,
uncanny valley, distorted perspective, pixelation,
frame drops, stuttering, ghosting, double exposure artifacts
```

## 三、按内容类型分类的 Negative

### 角色人像类（追加）

```
extra limbs, fused body parts, cloned face, bad hands,
too many fingers, missing fingers, disfigured,
poorly rendered hands, poorly rendered face,
bad proportions, gross proportions, mutation
```

### 场景环境类（追加）

```
people (unless specified), characters (unless specified),
face, portrait, person, animal (unless specified),
vehicle (unless specified), text overlay
```

### 科幻类（追加）

```
cartoon, medieval, fantasy elements (unless desired),
steampunk (unless desired), ancient architecture (unless specified),
historical costumes (unless specified), magic, sword and sorcery
```

### 悬疑/惊悚类（追加）

```
bright sunny, cheerful, colorful, cartoonish,
comedy style, daylight (if scene is night),
warm cozy, romantic comedy, sitcom lighting
```

### 古装/武侠类（追加）

```
modern clothing, modern architecture, cars, smartphones,
technology, modern furniture, power lines, satellite dishes,
contemporary signage, neon lights (unless specified)
```

### 赛博朋克类（追加）

```
natural landscape, rural, historical, medieval, ancient,
forest, farmland, traditional architecture (unless juxtaposition),
bright daylight, warm natural lighting, organic materials (excessive)
```

### 写实类（追加）

```
anime, cartoon, illustration, 3D render, CGI look,
stylized, cel-shaded, comic book, manga, vector art,
painting (unless specified), sketch, drawing
```

### 恐怖类（追加）

```
comedy, cute, wholesome, funny, cheerful, bright happy,
children's cartoon, pastel colors, soft lighting
```

### 浪漫/文艺类（追加）

```
horror, gore, violence, dark atmosphere, dystopian,
sci-fi, industrial, gritty, dirty, harsh lighting
```

## 四、角色特定 Negative（防混淆）

### 性别防混淆

```
女性角色：
masculine features, beard, male, stubble, broad shoulders,
Adam's apple, receding hairline

男性角色：
feminine features, female, breasts, soft features,
makeup (unless specified)
```

### 年龄防混淆

```
中年角色：
child, toddler, teenager, elderly, senior citizen,
wrinkled (excessively), gray hair (unless specified)

老年角色：
child, teenager, young adult, baby face, smooth skin

青年角色：
elderly, wrinkles, gray hair, aged, middle-aged spread
```

### 体型防混淆

```
瘦削角色：
obese, overweight, chubby, muscular (unless specified),
bulky, heavyset, large build

健壮角色：
skinny, thin, scrawny, slender, frail, emaciated

高个子：
short, petite, diminutive, small

矮个子：
tall, towering, lanky, long-limbed
```

### 服装防混淆

```
皮夹克角色：
suit, dress, armor, robe, uniform, t-shirt,
casual wear (unless alternate costume)

制服角色：
casual clothes, streetwear, pajamas, beachwear
```

### 特殊标记防混淆

```
有疤痕角色：
smooth skin, flawless skin, perfect complexion

戴眼镜角色：
no glasses, no eyewear (unless scene specifies removal)

有纹身角色：
clean skin, no tattoos
```

## 五、Negative Prompt 组合公式

```
每条 prompt 的最终 Negative = 
  通用 Negative（GPT-image-2 或 Seedance）
  + 内容类型特定 Negative
  + 角色特定 Negative（如 prompt 包含角色）
  + 场景特定 Negative（如 prompt 包含场景）

示例（赛博朋克女性角色设计图）：

Negative: ugly, deformed, blurry, low quality, bad anatomy, extra fingers,
missing fingers, asymmetric face, distorted features, watermark, text, logo,
jpeg artifacts, oversaturated, [通用]

extra limbs, fused body parts, cloned face, bad hands, poorly rendered hands,
[角色人像追加]

cartoon, medieval, fantasy elements, steampunk, ancient architecture,
[科幻追加]

masculine features, beard, male, stubble, broad shoulders,
[角色特定 — 女性]

natural landscape, rural, historical, bright daylight,
[赛博朋克追加]

unrealistic proportions, plastic texture, video game graphics
[额外质量保护]
```

## 六、Negative Prompt 使用最佳实践

1. **始终以通用 Negative 开头**：这是基础质量保证
2. **针对性追加**：根据场景/角色特征按需添加，避免过度堆砌
3. **避免冲突词**：不要在 prompt 中提到某个元素，同时又把它加到 negative
4. **保持简洁**：5-15 个 negative 词足够，过多反而干扰模型
5. **针对模型调整**：Seedance 的 negative 词与 GPT-image-2 略有不同，分开维护
