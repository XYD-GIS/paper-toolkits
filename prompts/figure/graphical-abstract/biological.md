# 生物医学图形摘要 · Biological GA

> **何时用**：生物医学、化学、材料、药学论文。用**分子 / 细胞 / 通路**风格的视觉比喻
> **目标期刊**：Cell, Nature Medicine, Science Translational Medicine, JACS, Angewandte Chemie

## 🎨 预期输出长什么样

```
                       A Novel Mechanism for X

        ┌──────────────┐              ┌──────────────┐
        │  (pink ring) │   treatment  │ (green ring) │
        │   🧬 Source  │ ────────────▶│   🟢 Outcome │
        │  细胞/组织/   │              │  健康细胞/    │
        │   分子结构    │              │  改善结果     │
        └──────────────┘              └──────────────┘
              │                              ▲
              │  mechanism (中央通路展开)     │
              ▼                              │
        ┌──────────────────────────────────┐ │
        │                                  │ │
        │   🧪  ─→  🔗  ─→  ⚛️  ─→  💊      │ │
        │   (反应通路 / 分子相互作用)        │ │ effect
        │                                  │ │
        └──────────────────────────────────┘─┘
```

左侧"起源"圆 + 中央"机制"通路 + 右侧"结果"圆，整体生命科学风格。

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
A graphical abstract for a {领域，如 biomedical} research paper, arranged horizontally from left to right with biological / molecular illustrations.

LEFT — "Source": Render a flat-vector illustration of {起源描述，如 a cell, a tissue, or a molecular structure}. Soft pink #F2D7D5 background circle.

CENTER — "Mechanism": Render the proposed mechanism: {机制描述，如 a pathway with arrows showing molecular interactions}. Use clean black arrows and labeled molecular structures (simplified, schematic).

RIGHT — "Outcome": Render the outcome: {结果描述，如 a healthy cell / improved tissue / quantitative readout}. Soft green #D5E8D4 background circle.

CONNECTING ELEMENTS:
- Between LEFT and CENTER: a labeled arrow "{第 1 段箭头标签，如 treatment}"
- Between CENTER and RIGHT: a labeled arrow "{第 2 段箭头标签，如 effect}"

TITLE at top center, bold Arial: "{论文标题}"

OPTIONAL ICONS to add domain feel (use sparingly):
- DNA double helix, cell membrane, mitochondria icon, drug molecule, protein structure
- Use grayscale or single-color outlines; do NOT use realistic 3D rendering

Style: flat vector, Cell-paper-style aesthetic, Arial sans-serif, white background, pastel palette. Aspect ratio 1328:531 (Cell journal standard).

Negative constraints: NO photorealistic biology, NO 3D molecular renders, NO microscope photos, NO cartoon characters, NO drop shadows, NO long sentences, NO emoji.
```

---

## ✏️ 填空示例（药物治疗机制）

```text
{领域} = biomedical
{起源描述} = a cancer cell with overactive receptor protein on its membrane
{机制描述} = drug molecule binding to receptor → signaling cascade blocked → 4 downstream effects shown as arrows
{结果描述} = the same cell now in apoptosis (programmed death) with reduced size and fragmented DNA
{第 1 段箭头标签} = drug treatment
{第 2 段箭头标签} = mechanism activated
{论文标题} = Targeted Inhibition of Receptor X Induces Apoptosis in Tumor Cells
```

## 💡 调优提示

- **不要太"卡通"**：在 prompt 末尾加 "scientific illustration style, NOT children's textbook style, NOT cartoon"
- **分子结构要标准**：如果涉及具体分子，在 prompt 中明确化学结构特征，如 "show benzene ring with 3 substituents at positions 1, 3, 5"
- **避免审美翻车**：生物 GA 最容易翻车的是"显微镜照片化"。一定强调 "schematic, NOT photorealistic, NOT microscope-style"
- **多步通路**：在 Mechanism 描述中明确步骤数，如 "5 sequential reaction steps"

## ⚠️ 期刊审稿易翻车点

- **Cell 系列**：禁止使用任何看起来像真实细胞照片的元素
- **JACS / Angewandte**：化学结构必须正确（不要画错键角、原子价数）
- **Nature Medicine**：人体器官示意图必须解剖学正确

如果你的图需要科学准确性而不是只是 GA 美感，建议**手绘草图 + 找专业插画师**或用 BioRender / ChemDraw 而不是 AI 图像模型。

## 🔗 相关

- 非生物领域 → [narrative.md](narrative.md)
- 强调闭环 → [circular.md](circular.md)
- 强调层级 → [pyramid.md](pyramid.md)
