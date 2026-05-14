# 图形摘要（Graphical Abstract）prompt 模板

图形摘要（Graphical Abstract，GA）是 Cell / Nature / 大多数 Elsevier 期刊**强制要求**的一类示意图：一张图讲清整篇论文的"问题 → 方法 → 结果"。

GA 与普通架构图的区别：
- **更叙事化**：有明确的"故事弧线"（问题 → 方法 → 结果）
- **更视觉化**：常用比喻、图标、生物/物理形象，而非纯抽象方块
- **比例严格**：Elsevier 要求 1328 × 531 px 横向、或 1:1 方形，Cell 要求 13.4 × 5 cm

---

# 通用风格基调

- 一张图讲完"问题 → 方法 → 结果"三段式
- 极简、平面化、矢量风格
- 纯白背景
- 用图标 + 短文字标签，**禁止长句**（最多 5 个英文单词一条）
- 色彩柔和（pastel）、色盲友好

---

# 模板 1：三段式叙事 GA（问题 → 方法 → 结果）

最经典的 GA 结构，适合大多数实验/方法类论文。

```text
A horizontal graphical abstract for an academic paper, divided into THREE equal sections from left to right by thin vertical dashed lines. Each section has a colored header band at the top with the section title in white bold Arial uppercase.

LEFT SECTION — "PROBLEM" (header band color: soft red #E8A6A6)
Render a simple flat-vector illustration depicting the research problem: {argument name="problem_visual" default="a confused user facing a complex graph / unknown data"}. Below the illustration, add a short caption in italic gray text (max 8 words): "{argument name="problem_caption" default="Existing methods cannot handle X scenario."}"

CENTER SECTION — "METHOD" (header band color: soft blue #A6C3E8)
Render a simplified flat-vector diagram of your method: {argument name="method_visual" default="a pipeline with three stages: input → encoder → predictor"}. Each stage shown as a labeled rounded rectangle. Below the diagram, add caption: "{argument name="method_caption" default="Our method does X using Y."}"

RIGHT SECTION — "RESULT" (header band color: soft green #A6E8A6)
Render a flat-vector visualization of the key result: {argument name="result_visual" default="a bar chart showing 30% improvement, or a happy user looking at a clear graph"}. Below, add caption: "{argument name="result_caption" default="Achieves X% improvement / new insight Z."}"

BETWEEN SECTIONS: thin black arrows pointing from PROBLEM → METHOD → RESULT.

At the very top center, place the paper title in bold Arial (max 12 words): "{argument name="paper_title" default="A Novel Framework for X"}"

Style: flat vector illustration, Arial sans-serif throughout, pastel palette, white background, journal-quality (Cell / Nature / Elsevier style). Aspect ratio 1328:531 (Elsevier standard) or 16:9.

Negative constraints: NO photorealistic photos, NO 3D shading, NO drop shadows, NO cartoon style, NO emoji that look childish, NO complex equations, NO long sentences (max 8 words per text label), NO unreadable text, NO logos or watermarks.
```

---

# 模板 2：环形 GA（输入 → 处理 → 反馈循环）

适合强化学习、在线学习、闭环系统、生物反馈循环。

```text
A circular graphical abstract for an academic paper, arranged as a clockwise loop of {argument name="num_steps" default="four"} stages around the center.

LAYOUT: A large circle (90% of frame) divided into {argument name="num_steps" default="four"} equal pie slices. Each slice contains:
- A 2-word English label in bold Arial at the outer edge
- A simple flat-vector icon in the middle of the slice
- A short 5-word caption in italic gray text at the inner edge

CENTER OF CIRCLE: A small circular badge with the paper title in bold Arial (max 10 words): "{argument name="paper_title" default="Closed-Loop Learning Framework"}"

ARROWS BETWEEN SLICES: Curved arrows along the outer edge of the circle, going clockwise, indicating the loop direction.

COLOR ASSIGNMENT (clockwise from 12 o'clock):
- Slice 1: soft blue #D6E4F0
- Slice 2: soft green #D8E8D0
- Slice 3: soft orange #F5E0CB
- Slice 4: soft purple #E0D4EC
(repeat or extend palette if num_steps > 4)

At the bottom of the figure, in small gray italic text, add the one-sentence takeaway: "{argument name="takeaway" default="Each iteration refines X using feedback from Y."}"

Style: flat vector, Arial sans-serif, pastel palette, white background, biology / systems-paper aesthetic. Aspect ratio 1:1.

Negative constraints: NO photorealistic, NO 3D, NO cartoon, NO drop shadows, NO emoji, NO long sentences, NO unreadable text.
```

---

# 模板 3：金字塔 / 层级 GA（多层关系）

适合理论框架、层级模型、多尺度分析。

```text
A pyramid-shaped graphical abstract for an academic paper, with {argument name="num_levels" default="three"} horizontal levels stacked from bottom (broadest) to top (most specific).

LEVEL 1 (bottom, widest): "{argument name="level1_name" default="Foundation / Raw Data"}"
- A horizontal band 80% of frame width
- Soft blue fill #D6E4F0
- Inside: 4-5 small icons representing the foundation elements
- Right side: italic gray caption (max 6 words)

LEVEL 2 (middle): "{argument name="level2_name" default="Intermediate Representation"}"
- A horizontal band 60% of frame width, centered
- Soft green fill #D8E8D0
- Inside: 2-3 medium icons or block diagrams
- Right side: italic gray caption (max 6 words)

LEVEL 3 (top, narrowest): "{argument name="level3_name" default="Decision / Insight"}"
- A horizontal band 40% of frame width, centered
- Soft orange fill #F5E0CB
- Inside: 1 prominent icon representing the final output
- Right side: italic gray caption (max 6 words)

VERTICAL ARROWS on the left side connecting bottom → middle → top, indicating abstraction direction.

At the very top, in bold Arial, the title: "{argument name="title" default="From Data to Decision: A Hierarchical Framework"}"

Style: flat vector, white background, scientific paper aesthetic, Arial sans-serif. Aspect ratio 4:3 or 1:1.

Negative constraints: NO photorealistic, NO 3D, NO drop shadows, NO cartoon, NO long sentences, NO emoji.
```

---

# 模板 4：分子/细胞/生物 GA（生命科学专用）

适合生物医学、化学、材料、药学论文。

```text
A graphical abstract for a {argument name="domain" default="biomedical"} research paper, arranged horizontally from left to right with biological / molecular illustrations.

LEFT — "Source": Render a flat-vector illustration of {argument name="source" default="a cell, a tissue, or a molecular structure"}. Soft pink #F2D7D5 background circle.

CENTER — "Mechanism": Render the proposed mechanism: {argument name="mechanism" default="a pathway with arrows showing molecular interactions"}. Use clean black arrows and labeled molecular structures (simplified, schematic).

RIGHT — "Outcome": Render the outcome: {argument name="outcome" default="a healthy cell / improved tissue / quantitative readout"}. Soft green #D5E8D4 background circle.

CONNECTING ELEMENTS:
- Between LEFT and CENTER: a labeled arrow "{argument name="arrow1_label" default="treatment"}"
- Between CENTER and RIGHT: a labeled arrow "{argument name="arrow2_label" default="effect"}"

TITLE at top center, bold Arial: "{argument name="title" default="A Novel Mechanism for X"}"

OPTIONAL ICONS to add domain feel (use sparingly):
- DNA double helix, cell membrane, mitochondria icon, drug molecule, protein structure
- Use grayscale or single-color outlines; do NOT use realistic 3D rendering

Style: flat vector, Cell-paper-style aesthetic, Arial sans-serif, white background, pastel palette. Aspect ratio 1328:531 (Cell journal standard).

Negative constraints: NO photorealistic biology, NO 3D molecular renders, NO microscope photos, NO cartoon characters, NO drop shadows, NO long sentences, NO emoji.
```

---

# 模板 5：对比型 GA（with / without 我们的方法）

适合证明"有 vs 没有方法"差异显著的论文。

```text
A graphical abstract for an academic paper, designed as a vertical comparison split by a horizontal thin gray line in the middle.

UPPER HALF — "Without {argument name="method_name" default="Our Method"}"
- Light gray background tint #F2F2F2
- Left side: render a starting scenario (a small flat-vector illustration)
- Right side: render the negative outcome (problem, error, slow result)
- Connecting arrow in the middle, labeled with the problematic process
- Below, in italic gray: "{argument name="without_caption" default="Existing approach: X% accuracy, Y minutes."}"

LOWER HALF — "With {argument name="method_name" default="Our Method"}"
- White background, with subtle warm yellow accent
- Left side: same starting scenario
- Right side: render the positive outcome (clear result, fast finish, correct answer)
- Connecting arrow in the middle, labeled with our method's name
- Below, in italic dark: "{argument name="with_caption" default="Our method: X+30% accuracy, Y/2 minutes."}"

At the bottom center, in bold Arial: "{argument name="conclusion" default="Our method achieves Z by enabling W."}"

Style: flat vector, white background, Arial sans-serif, journal-quality. Aspect ratio 4:3 or 1:1.

Negative constraints: NO photorealistic, NO 3D, NO drop shadows, NO cartoon, NO emoji, NO sarcastic tone in captions, NO long sentences.
```

---

# 期刊提交规格速查

| 期刊 / 出版社 | 标准 GA 比例 | 像素 / 物理尺寸 | 文件格式 |
|---|---|---|---|
| Cell | 横向 | 13.4 × 5 cm，300 dpi | TIFF / EPS |
| Elsevier (general) | 横向 | 1328 × 531 px | JPG / PNG / TIFF |
| Nature 系列 | 不强制 GA，但 main figure 1:1 或 4:3 | 单栏 8.9 cm，双栏 18.3 cm | TIFF / EPS / PDF |
| ACS（化学）| 横向 | 8.47 × 4.45 cm | TIFF / EPS |
| Wiley（多刊）| 横向 | 50 × 50 mm 起 | TIFF / EPS |

提交前必查：
- [ ] 比例符合目标期刊要求
- [ ] 所有文字英文，font ≥ 7 pt（300 dpi 下）
- [ ] 没有版权图（不要用网图、不要用他人 GA）
- [ ] 故事弧线清晰：3 秒内读懂"problem-method-result"
- [ ] 颜色色盲友好（避免红绿对比 + 仅靠色相区分）
