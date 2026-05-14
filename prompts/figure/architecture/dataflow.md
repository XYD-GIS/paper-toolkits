# 数据流向图 · Data Flow

> **何时用**：你想强调"**数据**如何在系统中流转"，模块本身次要。箭头的**粗细 / 颜色** 编码数据类型与体量。

## 🎨 预期输出长什么样

```
                    Data Flow Overview

   ┌────────────┐   RGB image    ┌──────────────┐   embedding 768-d
   │  Raw Data  │═══════════════▶│ Preprocessor │───────────────────▶
   └────────────┘  (粗箭头表大数据量)   └──────────────┘   (中等箭头表特征)
                                                                ▼
              class probabilities       ┌─────────────┐
       ◀─────────────────────────────── │  Classifier │
       (细箭头表元数据/控制信号)            └─────────────┘
              ▲
              │
     ┌────────────┐
     │   Output   │
     └────────────┘
```

横向流动，箭头**粗细差异化**：粗 = 原始数据 / 张量；中 = 特征向量；细 = 控制信号 / 元数据。

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
A data flow diagram for an academic paper, focused on tracing how information moves through a system. The diagram uses arrows of varying thickness to represent data volume / importance.

LAYOUT: Horizontal flow from left to right.

NODES (rounded rectangles, 4-6 total):
{节点列表，如 "Raw Data → Preprocessor → Encoder → Classifier → Output"}
Each node has an English label (1-3 words) and a small icon hint inside.

ARROWS:
- Thin arrows (1-2 px): represent metadata or control signal
- Medium arrows (3-4 px): represent feature vectors
- Thick arrows (6-8 px): represent raw data or high-volume tensors
- Use the same gray color (#6B7280) for all arrows; vary only thickness.

ANNOTATIONS:
- Above each arrow, in small italic gray text, label the data type (e.g., "RGB image", "embedding 768-d", "class probabilities").
- At the top center, place a clean title in bold Arial: "{图标题}"

OPTIONAL BRANCHES: If the flow has any side branches (e.g., auxiliary loss, residual connection), draw them as dashed arrows in a lighter gray.

Style: flat vector, white background, IEEE / ACM figure aesthetic, Arial sans-serif. Aspect ratio 16:9.

Negative constraints: NO photorealistic, NO 3D, NO cartoon, NO heavy shadows, NO unreadable text, NO chaotic crossing arrows.
```

---

## ✏️ 填空示例（视觉分类系统）

```text
{节点列表} = Raw Data → Preprocessor → Encoder → Classifier → Output
{图标题} = Data Flow in Vision Classifier
```

每条箭头上方的标签建议在 prompt 末尾追加：

```text
SPECIFIC ANNOTATIONS:
- Raw Data → Preprocessor: thick arrow, label "RGB image (224×224×3)"
- Preprocessor → Encoder: medium arrow, label "normalized tensor"
- Encoder → Classifier: medium arrow, label "embedding (768-d)"
- Classifier → Output: thin arrow, label "logits → softmax → label"
```

## 💡 调优提示

- **有反馈支路**：在 NODES 后加 "Plus a dashed feedback arrow from Output back to Encoder, labeled 'gradient' in light gray"
- **数据量类型超过 3 种**：可以用**颜色**而不是**粗细**编码，但保持色盲友好
- **想强调瓶颈点**：在某条箭头旁加 "label this arrow with a small red badge '⚠ bottleneck'"

## 🔗 相关

- 强调模块本身（数据流次要）→ [main-figure.md](main-figure.md)
- 系统总览（多组件）→ [system-overview.md](system-overview.md)
- 算法步骤（强调顺序）→ [pipeline.md](pipeline.md)
