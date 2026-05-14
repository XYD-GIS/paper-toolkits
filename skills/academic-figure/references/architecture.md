# 论文架构图与示意图 prompt 模板

本文件按场景分类，提供 6 套**可直接复制 + 参数化填空**的 prompt 模板，覆盖学术论文最常见的 6 种示意图类型。所有模板都基于 GPT-Image-2 / DALL-E / nano banana / Imagen 3 等模型的通用 prompt 工程结构。

---

# 通用风格基调（所有模板共享）

- 必须具备顶会论文风格：**专业、干净、现代、极简主义**
- 核心美学：**扁平化矢量插画风格**，线条简洁，参考 DeepMind、OpenAI、Google Brain 论文中的图表美学
- 拒绝卡通感、油画感、过度艺术化
- 背景必须**纯白色**，无任何纹理或阴影
- 严格使用**淡色系或柔和色调**，色盲友好
- 图中所有文字使用**英文**，关键模块用清晰标签
- 严禁长句子、描述性段落、复杂公式
- 布局顺序：Left-to-Right / Top-to-Bottom / Circular（根据流程性质选）
- 相关组件视觉上邻接（Gestalt 原则）

## 标准否定约束清单（每个 prompt 末尾必加）

```text
Negative constraints: NO photorealistic photos, NO messy sketches, NO unreadable text, NO 3D shading artifacts, NO cartoon style, NO drop shadows, NO emoji or icons that look childish, NO logos or watermarks, NO low-contrast color combinations.
```

---

# 模板 1：通用论文架构图（main figure / pipeline overview）

适用场景：摘要级别的方法总览图，展示从输入到输出的整体流程。

## 中文版

```text
# Role
你是世界顶尖的学术插画专家，专注于为 CV/AI/科学领域的顶级会议（CVPR、NeurIPS、ICLR、ICML、Nature）绘制高质量、直观且美观的论文架构图。

# Task
请阅读我提供的【论文方法描述】，首先深刻理解其核心机制、模块组成和数据流向。然后，基于你的理解，设计并绘制一张专业的学术架构图。

# Visual Constraints
1. 风格基调：扁平化矢量插画，参考 DeepMind 或 OpenAI 论文的图表美学；纯白色背景；拒绝卡通感、3D 阴影、过度艺术化。
2. 色彩体系：严格使用淡色系或柔和色调；颜色深浅区分模块类型；色盲友好。
3. 内容与布局：模块清晰、数据流箭头明确；适当使用简洁矢量图标增强直观性；布局采用 {argument name="layout" default="Left-to-Right"}。
4. 文字规范：图中所有文字使用英文；关键模块用清晰标签；不出现长句和复杂公式。
5. 禁止事项：不允许逼真照片感、杂乱草图、难辨文本、3D 阴影、卡通元素、廉价 emoji、水印 logo。

# Input Methodology
[在此处粘贴你的论文摘要 + 方法部分描述]
```

## 英文版（对 nano banana / DALL-E 效果更佳）

```text
You are an expert Scientific Illustrator for top-tier AI conferences (NeurIPS / CVPR / ICML / ICLR).
Your task is to generate a professional "Illustration" (main figure for the paper) based on a research paper abstract and methodology.

**Abstract:**
{abstract}

**Methodology:**
{methodology}

**Visual Style Requirements:**
1.  **Style:** Flat vector illustration, clean lines, academic aesthetic. Similar to figures in DeepMind or OpenAI papers.
2.  **Layout:** Organized flow ({argument name="layout" default="Left-to-Right"}). Group related components logically.
3.  **Color Palette:** Professional pastel tones. White background.
4.  **Text Rendering:** You MUST include legible text labels for key modules or equations mentioned in the methodology (e.g., "Encoder", "Loss", "Transformer").
5.  **Negative Constraints:** NO photorealistic photos, NO messy sketches, NO unreadable text, NO 3D shading artifacts.

**Generation Instruction:**
Highlight the core novelty. Ensure the connection logic makes sense.
```

---

# 模板 2：算法 pipeline 流程图（多步骤显式）

适用场景：方法包含 ≥ 3 个清晰阶段，每阶段有输入/输出。

```text
A clean academic pipeline diagram for a {argument name="domain" default="machine learning"} method, arranged horizontally from left to right. The diagram contains exactly {argument name="num_stages" default="four"} sequential stages, each rendered as a rounded rectangle with a 2-3 word English label inside.

STAGE 1 (leftmost): {argument name="stage1_name" default="Input Preprocessing"} — Input shown as small icon on the left side. Soft blue fill (#D6E4F0).
STAGE 2: {argument name="stage2_name" default="Feature Extraction"} — Connected to Stage 1 with a thin black arrow. Soft green fill (#D8E8D0).
STAGE 3: {argument name="stage3_name" default="Model Inference"} — Connected to Stage 2. Soft orange fill (#F5E0CB).
STAGE 4 (rightmost): {argument name="stage4_name" default="Output / Decision"} — Connected to Stage 3. Soft purple fill (#E0D4EC). Output icon on the right edge.

Above each stage, place an italic short description in gray (max 5 words). Below the pipeline, add a horizontal axis line with three time-related markers (training-time, inference-time, deployment-time) — optional, only if relevant.

Style: flat vector illustration, Arial sans-serif, white background, minimal aesthetic similar to NeurIPS / ICML figures. Aspect ratio 16:9.

Negative constraints: NO photorealistic photos, NO messy sketches, NO 3D shading, NO cartoon, NO drop shadows, NO emoji, NO logos.
```

---

# 模板 3：A vs B 模块对比图（before / after, method A / method B）

适用场景：消融对比、方法对比、传统 vs 提出方法。

```text
A side-by-side comparison diagram for an academic paper, split into two equal halves by a thin vertical divider line in the center.

LEFT HALF — {argument name="left_label" default="Baseline (Prior Work)"}:
- Title at top in bold Arial: "{argument name="left_label" default="Baseline"}"
- A simplified block diagram with {argument name="left_modules" default="three modules"} connected by black arrows.
- Use muted gray-blue palette (#9BB3CC, #BFD0E3) to indicate "the old way".
- Below the diagram, in italic gray text, list 2 short limitations (e.g., "Slow inference", "Requires labeled data").

RIGHT HALF — {argument name="right_label" default="Our Method"}:
- Title at top in bold Arial: "{argument name="right_label" default="Ours"}"
- A simplified block diagram with the new structure, {argument name="right_modules" default="three modules including a novel block"} connected by black arrows.
- Use vivid-but-soft accent palette (warm coral #F4A582, soft green #92C5DE) to indicate "the improvement". Highlight the novel block with a slightly thicker outline.
- Below the diagram, in italic dark text, list 2 short advantages (e.g., "2x faster", "No labels needed").

At the very bottom center, in small gray text, place a one-line summary: "{argument name="summary_caption" default="Our method replaces X with Y, yielding Z improvement."}"

Style: flat vector illustration, white background, Arial sans-serif, ICLR/CVPR figure aesthetic. Aspect ratio 16:9.

Negative constraints: NO photorealistic photos, NO 3D, NO heavy shadows, NO cartoon style, NO unreadable text.
```

---

# 模板 4：多阶段方法分镜（method storyboard, 4/6/9 panel grid）

适用场景：方法分多个阶段，每阶段都有可视化输出（如图像处理、序列预测、强化学习轨迹）。

```text
A {argument name="grid" default="2x2"} grid storyboard for an academic paper, arranged in reading order (top-left → top-right → bottom-left → bottom-right). Each panel is a rounded square with a 2-pixel light gray border. Between panels, leave 24 pixels of white gutter.

Above each panel, in bold Arial, place a short panel title:
- Panel 1: "{argument name="panel1_title" default="Step 1: Input"}"
- Panel 2: "{argument name="panel2_title" default="Step 2: Encoding"}"
- Panel 3: "{argument name="panel3_title" default="Step 3: Inference"}"
- Panel 4: "{argument name="panel4_title" default="Step 4: Output"}"

Below each panel title, in italic gray text (max 8 words), place a one-line description of what happens in this step.

INSIDE EACH PANEL: render a simplified, flat-vector illustration of what the step produces — for example a small data matrix, a feature map, a graph, or an output prediction. Use the same soft palette across all panels (consistent style).

Connect adjacent panels with thin curved arrows between their borders to indicate flow.

Style: flat vector, white background, NeurIPS / ICML figure aesthetic, Arial sans-serif. Aspect ratio matches grid (1:1 for 2x2, 1:1 for 3x3, 16:9 for 2x3).

Negative constraints: NO photorealistic, NO 3D shading, NO cartoon, NO emoji, NO low-contrast color combinations, NO drop shadows.
```

---

# 模板 5：数据流向图（data flow / information flow）

适用场景：强调数据/信息在系统中的流转，模块本身次要。

```text
A data flow diagram for an academic paper, focused on tracing how information moves through a system. The diagram uses arrows of varying thickness to represent data volume / importance.

LAYOUT: Horizontal flow from left to right.

NODES (rounded rectangles, 4-6 total):
{argument name="node_list" default="Raw Data → Preprocessor → Encoder → Classifier → Output"}
Each node has an English label (1-3 words) and a small icon hint inside.

ARROWS:
- Thin arrows (1-2 px): represent metadata or control signal
- Medium arrows (3-4 px): represent feature vectors
- Thick arrows (6-8 px): represent raw data or high-volume tensors
- Use the same gray color (#6B7280) for all arrows; vary only thickness.

ANNOTATIONS:
- Above each arrow, in small italic gray text, label the data type (e.g., "RGB image", "embedding 768-d", "class probabilities").
- At the top center, place a clean title in bold Arial: "{argument name="title" default="Data Flow Overview"}".

OPTIONAL BRANCHES: If the flow has any side branches (e.g., auxiliary loss, residual connection), draw them as dashed arrows in a lighter gray.

Style: flat vector, white background, IEEE / ACM figure aesthetic, Arial sans-serif. Aspect ratio 16:9.

Negative constraints: NO photorealistic, NO 3D, NO cartoon, NO heavy shadows, NO unreadable text, NO chaotic crossing arrows.
```

---

# 模板 6：系统总览图（system overview, 多组件视图）

适用场景：复杂系统（多个子模块、多个数据源、训练与推理并存）。

```text
A high-level system overview diagram for an academic paper, showing all major components of a complex {argument name="domain" default="machine learning system"}. The diagram is organized into THREE horizontal bands separated by faint gray dashed lines:

TOP BAND — "Data Layer":
- 2-3 rounded rectangles representing data sources (e.g., {argument name="data_sources" default="Raw Sensors, Curated Dataset, External Knowledge Base"}).
- Soft blue palette (#D6E4F0).

MIDDLE BAND — "Model Layer":
- 3-5 rounded rectangles representing model components (e.g., {argument name="model_components" default="Encoder, Decoder, Attention Module, Memory"}).
- Soft green palette (#D8E8D0).
- Arrows connect TOP BAND nodes down into MIDDLE BAND.

BOTTOM BAND — "Application Layer":
- 2-3 rounded rectangles representing downstream tasks (e.g., {argument name="apps" default="Classification, Generation, Retrieval"}).
- Soft orange palette (#F5E0CB).
- Arrows connect MIDDLE BAND nodes down into BOTTOM BAND.

ON THE RIGHT EDGE, place a vertical "feedback loop" arrow: a thin curved arrow going from BOTTOM BAND back up to TOP BAND, labeled "Feedback / Online Update" in italic.

At the top center, place the title in bold Arial: "{argument name="system_name" default="System Overview"}".

Style: flat vector, white background, paper-quality figure aesthetic, Arial sans-serif. Aspect ratio 16:9 or 4:3.

Negative constraints: NO photorealistic, NO 3D shading, NO drop shadows, NO cartoon, NO emoji, NO logos, NO over-saturated colors.
```

---

# 通用使用方法

## 三步用好这些模板

1. **选模板**：根据图的目标选择 1-6 号模板（不要硬塞，挑最贴合的）
2. **填变量**：把 `{argument name="X" default="Y"}` 形式的占位符按你的论文内容替换
3. **送图模型**：把填好的 prompt 整段复制送入 nano banana / GPT-Image-2 / DALL-E / Imagen，必要时多生成几张选最佳

## 调优要点

- **如果生成的图太密集**：在 prompt 中加 "with generous whitespace, sparse layout"
- **如果颜色太花**：把所有色彩描述都加上 "muted" 或 "soft"
- **如果文字渲染不准**：把图中关键英文标签**用双引号 ""** 严格围住，模型更精确
- **如果模块比例不对**：明确加 "all rounded rectangles have the same height" 或 "Module A is 2x the width of Module B"
- **如果箭头太乱**：明确说 "arrows do not cross each other; route around modules"

## 进阶：参数化变量语法

`{argument name="X" default="Y"}` 是 GPT-Image-2 系列模型支持的**参数化变量**，调用时可以替换。例如：

```text
原始：{argument name="title" default="Data Flow Overview"}
调用：直接写 "Self-Supervised Pretraining Pipeline"
```

让 prompt 模板**一次写好、多场景复用**。
