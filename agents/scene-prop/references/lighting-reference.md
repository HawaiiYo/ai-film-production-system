# 光源设计参考 (Scene Lighting Reference)

> 场景光设计的核心参考：光源类型、色温选择、光线情绪、光位。

## 一、光源设计框架

| 光源类型 | 设计要素 | 描述要点 |
|---------|---------|---------|
| 主光源（Key Light） | 位置 + 方向 + 类型 + 色温 + 强度 | 如：左侧45度高角度窗光，日光色温5600K，强度中高 |
| 辅光源（Fill Light） | 位置 + 方向 + 类型 + 色温 + 强度 | 如：右侧低位反射光，暖色3200K，强度低，柔化阴影 |
| 环境光（Ambient） | 整体环境光线描述 | 如：室内散射光，由窗外天光和室内墙面反射形成 |
| 特殊光源（Practical） | 画面中可见的实际光源 | 如：桌上的台灯（暖黄2700K）、壁炉火光（琥珀色1800K）、霓虹灯招牌（粉紫） |
| 轮廓光（Rim Light） | 分离主体与背景的边缘光 | 如：来自后方的逆光，冷色，勾勒人物轮廓 |
| 光影特点 | 阴影质量和风格 | 硬影（点光源/直射阳光）/ 柔影（阴天/散射光）/ 长影（低角度光）/ 无影（完全漫射） |

## 二、光线类型参考（按色温）

```
┌───────────────────────────────────────────────────────────────┐
│  时间/场景        色温（K）     光线特征        色彩倾向        │
├───────────────────────────────────────────────────────────────┤
│  日出/日落      2000-3500    低角度、长影、柔和   暖金/橙红     │
│  （黄金时刻）                                                │
│                                                               │
│  正午阳光       5500-6500    顶光、硬影、高对比    中性白/偏冷   │
│                                                               │
│  阴天           6500-7500    漫射光、柔影、低对比  冷灰蓝       │
│                                                               │
│  蓝调时刻       8000-10000   极低照度、深蓝        深蓝紫       │
│  （暮光）                                                    │
│                                                               │
│  月光           4000-4500    极弱、硬影（如有云则柔）冷银蓝    │
│                                                               │
│  白炽灯/钨丝灯   2700-3200    暖光、点光源          暖橙黄      │
│                                                               │
│  日光灯/荧光灯   4000-4500    冷光、轻微频闪感      冷绿白      │
│                                                               │
│  LED/霓虹灯     可变         高饱和、点光源         任意颜色    │
│                                                               │
│  烛光/火光      1800-2000    闪烁、极暖、局部        琥珀/橙红   │
│                                                               │
│  手机/屏幕光     6500        冷白、正面、点光源      冷白偏蓝    │
└───────────────────────────────────────────────────────────────┘
```

## 三、光线方向与情绪映射

| 光源方向 | 情绪效果 | 叙事用途 |
|---------|---------|---------|
| 顶光 | 压抑/诡异/神圣 | 反派出场、超自然场面、教堂 |
| 底光 | 恐怖/不安 | 恐怖片、戏剧性揭示 |
| 侧面（45°） | 戏剧性/经典电影感 | 商业电影标准用光 |
| 顺光（正面） | 平淡/清晰/纪实 | 纪录片、广告、对话 |
| 逆光 | 浪漫/神秘/希望 | 黄昏镜头、英雄时刻 |
| 散射光 | 柔和/亲密/温暖 | 浪漫场景、回忆段落 |
| 高对比硬光 | 紧张/黑色电影/悬疑 | noir、戏剧冲突 |

## 四、光线设计原则

```
- 主光源的方向决定场景的情绪：顶光 = 压抑/神圣，底光 = 恐怖/诡异，
   侧光 = 戏剧性，逆光 = 浪漫/神秘

- 光比（主光:辅光）决定画面风格：
   高光比 = 戏剧性/黑色电影
   低光比 = 自然/日常

- 色温对比制造视觉张力：
   暖主光 + 冷环境 = 温暖中的疏离感

- 特殊光源（practical lights）增加场景的真实感和层次

- 光影质量（硬/柔）影响画面的年代感和类型感：
   硬影 = 老电影/黑色电影/黑色幽默
   柔影 = 现代/浪漫/梦幻
```

## 五、Seedance Prompt 中的光线描述

```
将光线描述嵌入 Seedance prompt 时，使用如下结构：

"Lighting: [主光源] + [辅光源] + [环境/特殊光]
[时间]光线特征: [如：硬光/柔光/侧光]
色温: [K值或描述]
强度: [低/中/高]
"

示例：
"Lighting: 45° window light from upper-right (5600K, medium intensity) as key,
bounce fill from lower-left (3200K, low intensity),
neon street signs outside as practical lights (cyan/magenta).
Key-to-fill ratio 4:1, high contrast.
Color temperature: cool overall with warm practical accents."
```

## 六、GPT-image-2 Prompt 中的光线关键词

| 光线效果 | GPT-image-2 关键词 |
|---------|-------------------|
| 黄金时刻 | `golden hour lighting, warm sunlight, long shadows, magic hour` |
| 蓝调时刻 | `blue hour, deep blue ambient, twilight atmosphere` |
| 顶光 | `overhead lighting, top-lit, dramatic ceiling light` |
| 侧光 | `side lighting, raking light, dramatic chiaroscuro` |
| 逆光 | `backlit, rim light, silhouette, contre-jour` |
| 烛光 | `candlelit, intimate warm glow, flickering light` |
| 霓虹 | `neon lighting, cyan/magenta glow, cyberpunk atmosphere` |
| 月光 | `moonlight, cool silver light, nocturnal lighting` |
| 阴天 | `overcast, soft diffused light, no harsh shadows` |
