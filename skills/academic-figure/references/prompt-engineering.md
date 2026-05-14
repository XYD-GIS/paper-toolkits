# 图像生成 prompt 工程通用套路

本文件提炼从 521 个 GPT-Image-2 案例中观察到的 prompt 工程规律，并将其**学术化适配**——剔除商业摄影/广告风格元素，保留对学术 figure 生成有用的结构。

写 prompt 不是"写得越花哨越好"，而是**让模型不混淆**。下方 6 类词汇表 + 否定约束清单 + 参数化语法，是学术 figure prompt 的核心。

---

# 一、空间定位词汇表（绝对位置）

| 中文 | 英文（推荐） |
|---|---|
| 左上 / 左下 / 右上 / 右下 | top-left / bottom-left / top-right / bottom-right |
| 上方 / 下方 / 左侧 / 右侧 | top / bottom / left / right |
| 中央 / 中心 | center / middle |
| 前景 / 背景 / 中景 | foreground / background / midground |
| 边缘 / 内部 / 外圈 | edge / interior / outer ring |
| 跨越全图 | spanning the full width / across the entire frame |

**精确表达占比**：用 "approximately 30% of the frame width" / "fills the lower half" 这类**面积/占比**描述，比"large"或"big"更可控。

---

# 二、构图结构语（高级）

| 结构类型 | 英文表达 | 适用学术场景 |
|---|---|---|
| N 宫格 | {N}-panel grid / {N}-cell layout | 多阶段方法分镜 |
| 上下对比 | upper-lower split / horizontal divider in the middle | with vs without |
| 左右对比 | left-right split / vertical divider in the center | A vs B method |
| 三段并列 | three equal columns / three sections separated by thin dashed lines | 问题-方法-结果 GA |
| 流水线 | horizontal pipeline / left-to-right flow | algorithm pipeline |
| 环形 | circular layout / clockwise loop | 闭环系统 / RL |
| 金字塔 / 层级 | pyramid with N levels / hierarchical bands | 多尺度 / 层级模型 |
| 分镜板 | storyboard sheet / sequential panels with arrows | 方法演化轨迹 |

---

# 三、学术风格关键词（替代商业风格）

| 商业 prompt 常见词 | 学术替换 | 适用 |
|---|---|---|
| premium / luxury | academic / scholarly / journal-quality | 整体描述 |
| editorial photography | scientific illustration | 整体描述 |
| commercial product photo | figure for academic publication | 整体描述 |
| cinematic / dramatic lighting | clean / minimal / functional | 灯光（学术图通常不需要灯光） |
| shallow depth of field | flat 2D rendering | 景深（学术图通常 2D） |
| 8K / ultra-detailed | sharp vector edges, legible at print size | 分辨率 |
| moody / atmospheric | informative / explanatory | 氛围 |
| premium typography | Arial sans-serif, regular weight | 字体 |
| warm amber spotlight | uniform diffuse fill | 灯光 |
| photorealistic CGI render | flat vector illustration | 渲染风格 |

**核心心法**：学术 figure 要的是**信息密度高、视觉噪声低**。任何让读者"感受"而非"理解"的词都是冗余。

---

# 四、风格基调词汇库（直接复用）

适合学术 figure 的风格关键词：

```text
flat vector illustration
clean lines
minimal aesthetic
academic publication style
journal-quality figure
similar to figures in DeepMind / OpenAI / Nature / Cell papers
ICLR / NeurIPS / CVPR figure aesthetic
isometric (if 3D needed for structural diagrams)
schematic / diagrammatic style
informative infographic
explanatory illustration
```

避免使用：

```text
photorealistic / hyper-realistic
cinematic / movie-poster style
luxury / premium feel
editorial photography
3D realistic rendering
oil painting / watercolor (除非论文是艺术领域)
neon / glowing / cyberpunk
heavy drop shadows / depth blur
```

---

# 五、配色词汇（学术化）

## 推荐调色板（粘贴可用）

```text
Pastel academic palette:
- Soft blue:    #D6E4F0 / #4C72B0
- Soft green:   #D8E8D0 / #55A467
- Soft orange:  #F5E0CB / #DD8452
- Soft red:     #E8D0D0 / #C44E52
- Soft purple:  #E0D4EC / #8172B3
- Soft gray:    #E5E7EB / #6B7280

Sequential colormap: Blues / Greens / Oranges
Diverging colormap: RdBu_r / PuOr_r
Categorical (colorblind-safe): viridis (8 colors)
```

## 描述配色的标准句式

```text
- "Use a pastel palette of soft blue, green, and orange to differentiate the three module types."
- "Color-coding: input modules in soft blue, processing modules in soft green, output modules in soft orange."
- "Maintain consistent color semantics across all panels."
- "Colorblind-safe: avoid red-green contrast as the only differentiator."
```

---

# 六、否定约束清单（必加在 prompt 末尾）

学术 figure 的标准 negative constraints，按场景选择：

## 通用清单（任何学术图都加）

```text
Negative constraints: NO photorealistic photos, NO messy sketches, NO unreadable text, NO 3D shading artifacts, NO drop shadows, NO cartoon style, NO emoji that look childish, NO logos or watermarks, NO low-contrast color combinations, NO heavy gradients, NO over-saturated colors.
```

## 架构图额外加

```text
NO chaotic arrows that cross each other, NO modules of inconsistent sizes without reason, NO inconsistent color semantics, NO modules placed at random positions.
```

## 图形摘要额外加

```text
NO long sentences (max 8 words per text label), NO realistic biology textures, NO microscope-style images, NO emoji.
```

## 流程图 / pipeline 额外加

```text
NO bidirectional arrows where unidirectional flow is intended, NO unlabeled arrows, NO modules without text labels.
```

---

# 七、参数化变量语法

`{argument name="X" default="Y"}` 是 GPT-Image-2 系列模型支持的**参数化变量**——这种语法在调用时可以替换 default 值，让 prompt 一次写好、多场景复用。

## 基本语法

```text
{argument name="变量名" default="默认值"}
```

## 实际示例

```text
A horizontal pipeline diagram with {argument name="num_stages" default="four"} stages.
```

调用时：
- 不替换 → 输出 four stages
- 替换 num_stages = "six" → 输出 six stages

## 推荐参数化的内容

- 模块数量、阶段数量、面板数
- 模块/阶段的名称
- 颜色（如果不同领域用不同调色板）
- 图的方向（horizontal / vertical / circular）
- 题目 / 子标题 / caption 内容

## 不要参数化的内容

- 通用风格词（"flat vector"、"Arial"）——这些应该是硬编码
- 否定约束——这是必须的硬约束

---

# 八、提示词调试小贴士

写完一版 prompt 生成后，如果效果不好，按下面顺序排查：

## 1. 文字渲染不准

**症状**：模型生成的标签是"Lncuder"而不是"Encoder"，或者整段乱码

**解决**：
- 把关键英文标签用**双引号 ""** 严格围住，模型更精确
- 在 prompt 中显式强调："Render text exactly as written: 'Encoder', 'Decoder', 'Loss'."
- 减少图中文字总量（拆成多段 caption 比一张图塞十个标签效果好）

## 2. 模块比例错乱

**症状**：本应等大的两个模块被画成 3:1 比例

**解决**：
- 明确加："all rounded rectangles have the same height and width unless specified"
- 或反过来："Module A is approximately 2x the width of Module B."

## 3. 箭头混乱 / 交叉

**症状**：箭头乱穿、模块之间没有清晰流向

**解决**：
- 显式加："arrows do not cross each other; route them around modules with right-angle turns"
- 限定方向："all arrows flow strictly left-to-right"

## 4. 颜色太花 / 太暗

**症状**：模型生成 5 种饱和度过高的颜色

**解决**：
- 把所有颜色描述都前缀加 "muted" 或 "soft"
- 或直接给十六进制色码

## 5. 整体太密集

**症状**：所有元素挤在一起，无呼吸感

**解决**：
- 加 "with generous whitespace between modules"
- "sparse layout, avoiding overcrowding"
- "use approximately 30% of the frame for whitespace"

## 6. 整体太"卡通"

**症状**：模块像卡通气泡、人物形象幼稚

**解决**：
- 加 "professional academic style, NOT cartoon"
- "geometric shapes only, no character illustrations"
- "iconographic style similar to The Noun Project, monochrome silhouettes"

---

# 九、完整 prompt 模板骨架（套用即可）

任何学术 figure prompt 都可以套这个 8 段式骨架：

```text
[1. 整体描述]
A {figure_type} for an academic paper, designed for {target_venue}.

[2. 布局]
LAYOUT: {layout_type}, arranged {flow_direction}, with {number} sections / panels / stages.

[3. 元素清单]
ELEMENTS:
- Section 1: {description}, soft {color} fill #{hex}
- Section 2: {description}, soft {color} fill #{hex}
- ...

[4. 文字]
TEXT:
- Title (top center, bold Arial): "{title}"
- Section labels (above each section, bold Arial): "..."
- Captions (italic gray, max N words): "..."

[5. 连接]
CONNECTIONS: {arrow_style}, {arrow_direction}, labeled with {labels}.

[6. 风格关键词]
STYLE: flat vector illustration, Arial sans-serif throughout, pastel palette, white background, {venue}-style aesthetic. Aspect ratio {ratio}.

[7. 否定约束]
Negative constraints: NO photorealistic, NO 3D, NO cartoon, ...

[8. 参数化变量]
{argument name="..." default="..."}
```

把这 8 段填完，生成的图质量在 80 分以上。
