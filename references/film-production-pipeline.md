# 🎬 电影制作工业流程参考

> Film Production Pipeline Reference — 理解传统电影制作流程，指导AI Agent模拟

---

## 一、传统电影制作五阶段

### 阶段1: 开发期（Development）
**时长**：数月~数年

| 步骤 | 内容 | 对应Agent |
|------|------|-----------|
| 概念/故事 | 一句话梗概（logline）、故事概念 | 用户输入 |
| 剧本大纲 | 故事大纲、人物关系 | 📖 Screenplay Agent |
| 完整剧本 | 三幕结构、场景分解、对白 | 📖 Screenplay Agent |
| 项目包装 | 导演/演员/预算方案 | 🎯 Executive Producer |

**关键决策**：
- 故事类型和核心主题
- 目标观众和市场需求
- 预算范围和制作规模

### 阶段2: 前期制作（Pre-Production）
**时长**：2~6个月

| 步骤 | 内容 | 对应Agent |
|------|------|-----------|
| 导演阐述 | 导演创作意图和视觉方向 | 🎨 Director Style Agent |
| 美术设计 | 角色造型、场景设计、道具 | 👤 Character + 🏗️ Scene & Prop |
| 分镜故事板 | 镜头设计、运动、构图 | 🎬 Storyboard Agent |
| 选角/试镜 | 角色气质匹配 | 👤 Character Design Agent |
| 勘景 | 拍摄地点确认 | 🏗️ Scene & Prop Agent |
| 拍摄计划 | 日程排期、预算分配 | 🎯 Executive Producer |

**关键产出物**：
- 导演视觉阐述（Director's Vision Statement）
- 角色设计稿 / 定妆照
- 场景概念图 / 氛围图
- 完整分镜表 / 动态故事板（Animatic）
- 拍摄日程表

### 阶段3: 拍摄期（Production）
**时长**：1~4个月

| 步骤 | 内容 | AI对应 |
|------|------|--------|
| 现场拍摄 | 按分镜逐镜头拍摄 | Seedance视频生成 |
| 导演监视 | 画面构图、表演指导 | (人类导演主导) |
| DIT | 数字影像技术、数据管理 | — |
| 同期录音 | 现场对白和环境音 | — |

**注意**：在AI电影制作中，此阶段对应**Seedance视频生成**。
传统拍摄被替换为AI视频模型生成。

### 阶段4: 后期制作（Post-Production）
**时长**：1~6个月

| 步骤 | 内容 | 对应Agent |
|------|------|-----------|
| 剪辑 | 粗剪 → 精剪 → 定剪 | ✂️ Post-Production Agent |
| 调色 | 色彩校正 + 风格化调色（Color Grading） | ✂️ Post-Production Agent |
| 视觉特效（VFX） | CGI、合成 | (当前版本不涉及) |
| 声音设计 | 环境音、音效（Foley） | ✂️ Post-Production Agent |
| 配乐 | 原创配乐/选曲 | ✂️ Post-Production Agent |
| 混音 | 最终音频混合 | — |

### 阶段5: 发行/宣传（Distribution & Marketing）
| 步骤 | 内容 | 对应Agent |
|------|------|-----------|
| 海报设计 | 主海报、角色海报 | 📢 Marketing Assets Agent |
| 预告片 | 先行预告、正式预告 | 📢 Marketing Assets Agent |
| 宣发物料 | 剧照、花絮、社交媒体 | 📢 Marketing Assets Agent |

---

## 二、AI电影制作流程映射

传统流程 → AI Agent化流程：

```
传统流程:
  开发期 → 前期制作 → 拍摄期 → 后期制作 → 发行宣传
      ↓          ↓         ↓          ↓          ↓
AI流程:
  剧本Agent   导演Agent  Seedance  后期Agent  宣传Agent
  角色Agent   场景Agent  视频生成   (Phase 5)  (Phase 5)
              分镜Agent
              Prompt Agent
```

### AI流程特点
1. **前期制作被大幅扩展**：因为AI视频生成对前期设计的要求极高——必须非常精确地描述才能生成符合预期的视频
2. **拍摄期被压缩**：不再需要实际拍摄，改为AI视频模型生成
3. **一致性是关键挑战**：传统拍摄一旦选定演员/场景就不会变，AI生成需要额外的机制来保证一致性
4. **迭代速度快**：从数月缩短到数天/数小时

---

## 三、关键电影概念（Agent需要理解的）

### 3.1 视觉语言

| 概念 | 英文 | 定义 | 应用场景 |
|------|------|------|---------|
| 景别 | Shot Size | 画面中主体的大小比例 | 分镜设计 |
| 镜头运动 | Camera Movement | 摄影机的移动方式 | Seedance prompt |
| 构图 | Composition | 画面元素的安排 | GPT-image-2 prompt |
| 景深 | Depth of Field | 清晰范围的控制 | 氛围营造 |
| 色温 | Color Temperature | 光源的暖冷程度 | 场景设计 |
| 高调/低调 | High Key / Low Key | 整体亮度的风格 | 场景设计 |

### 3.2 景别详解

| 景别 | 英文/缩写 | 主体比例 | 情感距离 | 典型用途 |
|------|----------|---------|---------|---------|
| 大远景 | Extreme Long Shot (ELS) | 人极小，环境为主 | 非常远 | 建立空间感、史诗感 |
| 远景 | Long Shot (LS) | 人全身 + 环境 | 远 | 展示人物与环境关系 |
| 全景 | Full Shot (FS) | 人全身 | 中远 | 展示角色整体形象 |
| 中景 | Medium Shot (MS) | 人膝以上 | 中 | 对话场景、人物互动 |
| 近景 | Medium Close-Up (MCU) | 人胸以上 | 近 | 表达情感、对话 |
| 特写 | Close-Up (CU) | 人脸为主 | 很近 | 强调情绪、关键信息 |
| 大特写 | Extreme Close-Up (ECU) | 眼睛/嘴唇等局部 | 极近 | 强烈情感冲击 |

### 3.3 镜头运动详解

| 运动 | 英文 | 效果 | Seedance Prompt关键词 |
|------|------|------|----------------------|
| 固定 | Static/Fixed | 稳定、客观、凝视 | static shot, locked off |
| 推 | Dolly In / Push In | 靠近主体、增强关注 | dolly in, push in, moving forward |
| 拉 | Dolly Out / Pull Out | 远离主体、揭示环境 | dolly out, pull back, revealing |
| 摇 | Pan | 水平旋转、扫描 | pan left/right, sweeping |
| 俯仰 | Tilt | 垂直旋转 | tilt up/down |
| 移/轨 | Track / Truck | 横向跟随 | tracking shot, lateral movement |
| 跟 | Follow | 跟随主体移动 | following shot, tracking |
| 升降 | Crane / Jib | 垂直升降 | crane up/down, jib shot |
| 手持 | Handheld | 晃动、真实感、紧张 | handheld, shaky cam, documentary style |
| 变焦 | Zoom | 推拉焦距 | zoom in/out, crash zoom |
| 希区柯克变焦 | Dolly Zoom / Vertigo | 推轨+反向变焦 | dolly zoom, vertigo effect |

### 3.4 构图方式详解

| 构图 | 英文 | 特点 | 适用场景 |
|------|------|------|---------|
| 三分法 | Rule of Thirds | 主体放在画面1/3处 | 通用、自然 |
| 中心构图 | Center Composition | 主体居中 | 强调、庄严、对称美 |
| 对称构图 | Symmetrical | 左右/上下对称 | 形式感、秩序感（Wes Anderson风格） |
| 引导线 | Leading Lines | 线条引导视线 | 深度感、方向感 |
| 框架构图 | Frame within Frame | 用前景框住主体 | 偷窥感、层次感 |
| 对角线 | Diagonal | 沿对角线排列 | 动感、紧张、不平衡 |
| 留白/负空间 | Negative Space | 大面积空白 | 孤独、极简、呼吸感 |
| 浅景深 | Shallow DOF | 背景虚化 | 突出主体、梦幻感 |
| 深焦 | Deep Focus | 前后都清晰 | 全景展示、层次丰富 |

### 3.5 光线类型

| 光线 | 英文 | 效果 | Prompt关键词 |
|------|------|------|-------------|
| 主光 | Key Light | 主体主要光源 | key light, main light source |
| 辅光 | Fill Light | 减少阴影 | fill light, soft fill |
| 逆光/背光 | Backlight / Rim Light | 轮廓光、剪影 | backlit, rim lighting, silhouette |
| 侧光 | Side Light | 强烈立体感 | side lit, dramatic shadows |
| 顶光 | Top Light | 神秘/压抑 | top lighting, overhead |
| 底光 | Bottom Light | 诡异/恐怖 | bottom light, under lighting |
| 柔光 | Soft Light | 温暖柔和 | soft diffused light, golden hour |
| 硬光 | Hard Light | 锐利阴影 | hard light, harsh shadows |
| 实用光源 | Practical Light | 画面内可见光源 | practical lighting, diegetic light |
| 霓虹光 | Neon Light | 赛博朋克风格 | neon lighting, cyberpunk aesthetic |

### 3.6 色彩理论

| 色彩方案 | 英文 | 效果 | 适用类型 |
|---------|------|------|---------|
| 互补色 | Complementary | 强烈对比、戏剧性 | 动作、科幻 |
| 类似色 | Analogous | 和谐统一、舒适 | 文艺、爱情 |
| 三色 | Triadic | 活泼丰富 | 动画、喜剧 |
| 单色 | Monochromatic | 统一、忧郁/冷静 | 悬疑、恐怖 |
| 暖色调 | Warm Palette | 温暖、怀旧、热情 | 爱情、史诗 |
| 冷色调 | Cool Palette | 冷静、疏离、科技 | 科幻、悬疑 |
| 去饱和 | Desaturated | 压抑、现实感 | 战争、社会题材 |
| Teal & Orange | 青橙调色 | 电影工业标准 | 商业大片 |

---

## 四、各类型片视觉参考

### 科幻片（Sci-Fi）
- **色调**：冷蓝/青为主，点缀暖色（橙色/金色）
- **光影**：高对比度、硬光、霓虹点光源
- **场景**：未来都市、太空、实验室、废墟
- **质感**：金属、玻璃、全息投影、湿润的街道
- **参考**：《银翼杀手2049》《降临》《星际穿越》

### 悬疑惊悚片（Thriller）
- **色调**：低饱和度、青绿偏色、暗部偏蓝
- **光影**：低调光（Low Key）、强烈阴影、单一光源
- **构图**：不对称、框架构图、负空间
- **镜头**：缓慢推进、手持晃动、窥视视角
- **参考**：《七宗罪》《消失的爱人》《囚徒》

### 文艺爱情片（Romance/Drama）
- **色调**：暖色调、金色时刻、柔和饱和度
- **光影**：柔光、逆光、窗光（Window Light）
- **构图**：三分法、浅景深、近距离
- **镜头**：平稳、慢推、手持微晃
- **参考**：《花样年华》《爱在黎明破晓前》《请以你的名字呼唤我》

### 动作片（Action）
- **色调**：高饱和度、暖金色/深蓝对比
- **光影**：硬光、动态光源
- **镜头**：快速切换、跟拍、航拍、慢动作
- **运动**：手持、轨道、高速运动
- **参考**：《疾速追杀》《疯狂的麦克斯：狂暴之路》

### 武侠/古装（Wuxia/Period）
- **色调**：水墨黑白/浓烈红金/诗意青绿
- **光影**：自然光、烟雾、灯笼暖光
- **构图**：对称、留白、中国画式构图
- **运动**：慢推、上升、旋转
- **参考**：《英雄》《卧虎藏龙》《刺客聂隐娘》

### 动画/奇幻（Animation/Fantasy）
- **色调**：高饱和、纯色大块面、梦幻过渡
- **光影**：风格化（非物理写实）
- **质感**：手绘质感、CG精致、材质表现
- **参考**：宫崎骏作品、皮克斯、《蜘蛛侠：平行宇宙》

---

## 四、分镜绘制与布局系统

### 4.1 分镜布局类型

分镜（Storyboard）是电影预可视化（Pre-visualization）的核心工具。根据制作阶段和沟通需求，采用不同的布局格式：

| 布局类型 | 每页格数 | 画面大小 | 适用阶段 | 画法风格 |
|---------|---------|---------|---------|---------|
| 缩略图板 (Thumbnail) | 9/12/16格 | 极小 | 早期概念/头脑风暴 | 火柴人+极简线 |
| 4格板 (4-Panel) | 2×2=4格 | 大 | 关键节拍展示 | 清晰线稿+阴影 |
| 6格板 (6-Panel) | 3×2=6格 | 中 | 日常制作/沟通 | 线稿+箭头+注释 |
| 9格板 (9-Panel) | 3×3=9格 | 小~中 | 快节奏场景 | 线稿+关键帧 |
| 宽幅横板 (Widescreen) | 3~4格横排 | 大(宽银幕) | 史诗/风景场景 | 精细+灰度 |
| 单列竖板 (Single Col) | 1格/行 | 最大 | 投融资展示 | 精细+全彩 |

### 4.2 分镜箭头符号系统

专业分镜使用**标准化箭头**来传达两类运动：

#### 镜头运动箭头（画在画框边缘/外部）
- **推(Dolly In)**：→→→→ 向画面中心汇聚的四方向箭头
- **拉(Dolly Out)**：←←←← 从画面中心向外四散的箭头
- **左/右摇(Pan L/R)**：画框顶部←───或───→长箭头
- **上/下摇(Tilt Up/Dn)**：画框左侧↑或↓垂直箭头
- **跟/轨(Track)**：沿主体移动方向的平行箭头→→→
- **升降(Crane)**：标注 `Crane Up↑` 或 `Crane Down↓`
- **手持(Handheld)**：画框边缘 ≈≈≈≈ 波浪线
- **变焦(Zoom)**：四角标注 `[Zoom In]→` 或 `←[Zoom Out]`

#### 角色/物体运动箭头（画在画面内部）
- **直线行走**：──→ 实线箭头，从角色出发指向行走方向
- **奔跑**：══▶ 粗实线箭头
- **曲线/迂回**：╭──╮虚线或细实线曲线箭头
- **进出画面**：←──●──→（圆点=起点/终点）
- **视线方向**：······→ 点线箭头
- **物体飞行**：~~~~→ 虚线+箭头（子弹/箭矢等）

**关键规则**：
- 箭头方向 = 摄影机/角色/物体实际移动的方向
- 箭头长度 ≈ 移动幅度；箭头粗细 ≈ 移动速度
- 镜头箭头画在画面外部/边缘；角色箭头画在画面内部

### 4.3 角色走位指示（Blocking Notation）

#### 方式1：画面内箭头（In-Frame）
直接在分镜画面中画角色运动轨迹箭头，最直观常用。

#### 方式2：俯视平面图（Floor Plan / Overhead Diagram）
用建筑平面图+编号标记(C1→C2→C3)精确描述角色在每个时刻的位置，
同时标注摄影机位(CAM1/CAM2/CAM3)。

#### 方式3：关键姿势分解（Key Pose Panels）
将一连串复杂动作拆分为3-4个关键姿势格，
适合打斗、舞蹈、特技等需要精确动作设计的场景。

### 4.4 分镜标注缩略语

| 缩略语 | 全称 | 含义 |
|--------|------|------|
| ELS/LS/FS/MS/MCU/CU/ECU | — | 景别（大远景→大特写） |
| OTS | Over The Shoulder | 过肩镜头 |
| POV | Point of View | 主观视角 |
| LA/HA/DA | Low/High/Dutch Angle | 仰拍/俯拍/斜角 |
| 2S/3S | 2-Shot/3-Shot | 双人/三人镜头 |
| INS | Insert | 插入镜头 |
| EXT/INT | Exterior/Interior | 外景/内景 |
| DAY/NGT | Day/Night | 白天/夜晚 |
| CONT | Continuous | 连续时间 |

---

## 五、AI视频生成的电影美学要点

1. **明确而非模糊**：AI不像摄影师能"理解氛围"，必须用具体描述
2. **技术参数是风格的一部分**：帧率、分辨率、宽高比都是美学选择
3. **图生视频是最佳路径**：先生成关键帧图（GPT-image-2），再以图驱动视频（Seedance）
4. **分段生成、后期拼接**：AI视频目前适合短片段（2-10秒），长视频需分段生成后拼接
5. **一致性靠"模板化"**：固定角色/场景的描述模板，每个prompt中复用相同描述片段

---

*本参考文档用于指导所有Agent理解电影制作流程和术语*
