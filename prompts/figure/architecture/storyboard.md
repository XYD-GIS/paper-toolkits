# 多阶段方法分镜 · Storyboard

> **何时用**：方法包含多个阶段，**每个阶段都有可视化输出**（如图像处理、序列预测、强化学习轨迹）

## 🎨 预期输出长什么样

```
┌─────────────────┬─────────────────┐
│ Step 1: Input   │ Step 2: Encoding│
│ ─────────────   │ ─────────────   │
│                 │                 │
│  ┌────────┐     │   ┌─────────┐   │
│  │ Image  │     │   │ Feature │   │
│  │  📷    │     │   │  Map    │   │
│  └────────┘     │   └─────────┘   │
│ "raw RGB photo" │ "via ConvNet"   │
└────────┬────────┴────────┬────────┘
         │                 │
┌────────▼────────┬────────▼────────┐
│ Step 3:Inference│ Step 4: Output  │
│ ─────────────   │ ─────────────   │
│                 │                 │
│   ┌──────┐      │   ┌──────────┐  │
│   │ Pred │      │   │  Class:  │  │
│   │ Vec. │      │   │  "cat"   │  │
│   └──────┘      │   └──────────┘  │
│ "logits → softmax" │ "argmax label"│
└─────────────────┴─────────────────┘
```

2×2 网格（或 2×3、3×3），每格独立展示该阶段的输出，相邻格之间有箭头连接。

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
A {网格规格，如 2x2} grid storyboard for an academic paper, arranged in reading order (top-left → top-right → bottom-left → bottom-right). Each panel is a rounded square with a 2-pixel light gray border. Between panels, leave 24 pixels of white gutter.

Above each panel, in bold Arial, place a short panel title:
- Panel 1: "{第 1 格标题}"
- Panel 2: "{第 2 格标题}"
- Panel 3: "{第 3 格标题}"
- Panel 4: "{第 4 格标题}"

Below each panel title, in italic gray text (max 8 words), place a one-line description of what happens in this step.

INSIDE EACH PANEL: render a simplified, flat-vector illustration of what the step produces — for example a small data matrix, a feature map, a graph, or an output prediction. Use the same soft palette across all panels (consistent style).

Connect adjacent panels with thin curved arrows between their borders to indicate flow.

Style: flat vector, white background, NeurIPS / ICML figure aesthetic, Arial sans-serif. Aspect ratio matches grid (1:1 for 2x2, 1:1 for 3x3, 16:9 for 2x3).

Negative constraints: NO photorealistic, NO 3D shading, NO cartoon, NO emoji, NO low-contrast color combinations, NO drop shadows.
```

---

## ✏️ 填空示例（4 阶段 vision pipeline）

```text
{网格规格} = 2x2
{第 1 格标题} = Step 1: Input
{第 2 格标题} = Step 2: Encoding
{第 3 格标题} = Step 3: Inference
{第 4 格标题} = Step 4: Output
```

## 💡 调优提示

- **3×3 九宫格**：把网格规格改为 `3x3`，更适合 GPT-Image-2 / DALL-E 这类支持高分辨率的模型
- **每格内部要画"真实数据示意"**（如频谱图、注意力热力图）：在 prompt 中具体描述，如 "Panel 2 shows a 4x4 attention heatmap with values from 0 to 1, color-coded in blues"
- **连接箭头乱**：明确指定方向，"all arrows strictly between adjacent panels following reading order; no diagonal arrows"

## 🔗 相关

- 强调"顺序流程"非可视化输出 → [pipeline.md](pipeline.md)
- 多支并行而非顺序 → [../flowchart/parallel.md](../flowchart/parallel.md)
- 含判断 / 循环 → [../flowchart/](../flowchart/)
