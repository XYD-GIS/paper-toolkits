# 线性流程图 · Linear Flowchart

> **何时用**：你的方法/实验有 **≥ 3 个先后顺序的步骤**，无判断、无循环、无分支

## 🎨 预期输出长什么样

```
┌────────┐    ┌──────────┐    ┌────────────┐    ┌────────────┐    ┌──────────┐
│ Start  │──▶ │ Cleaning │──▶ │ Normalize  │──▶ │  Feature   │──▶ │ Ready    │
│  Data  │    │          │    │            │    │  Selection │    │ Dataset  │
└────────┘    └──────────┘    └────────────┘    └────────────┘    └──────────┘
   蓝色          灰色             灰色              灰色              绿色
                                                                    （结束）
```

横向左到右单行排列，5 个节点。起止为圆角椭圆（蓝/绿），中间过程为圆角矩形（灰）。箭头依次连接。

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
A linear flowchart for an academic paper on {主题}.

LAYOUT: Horizontal flow from left to right, {步骤数量，如 five} nodes arranged in a single row with equal spacing.

NODES:
- Start: rounded oval with thick border, label "{起始节点名}", soft blue fill #D6E4F0
- Step 1: rounded rectangle, label "{步骤 1 名称}", soft gray fill #E5E7EB
- Step 2: rounded rectangle, label "{步骤 2 名称}", soft gray fill #E5E7EB
- Step 3: rounded rectangle, label "{步骤 3 名称}", soft gray fill #E5E7EB
- End: rounded oval with thick border, label "{结束节点名}", soft green fill #D8E8D0

CONNECTIONS:
- Sequential solid black arrows (2-3 px) between adjacent nodes, all pointing right.
- Each arrow optionally labeled with a short verb in italic gray (max 3 words), e.g., "remove outliers", "scale to [0,1]".

TEXT:
- Title at top center, bold Arial: "{图标题}"
- Node labels: bold Arial, ≤ 3 words each
- Arrow labels: italic gray, ≤ 3 words each

STYLE: flat vector illustration, NeurIPS/ICML figure aesthetic, Arial sans-serif throughout, pastel palette, pure white background. Aspect ratio 16:9.

Negative constraints: NO photorealistic photos, NO 3D shading, NO drop shadows, NO cartoon style, NO emoji, NO unreadable text, NO crossing arrows, NO bidirectional arrows (unidirectional flow only), NO chart junk.
```

---

## 🛠 使用方法

1. 把上方 prompt 的 `{占位符}` 全部替换为你的真实内容
2. 复制完整 prompt 到 **图像生成模型**：
   - GPT-Image-2（推荐）
   - DALL-E 3 / GPT-4o image
   - Imagen 3 / nano banana
   - Midjourney（部分支持）
3. 发送

## ✏️ 填空示例（数据预处理流程）

把占位符填好后的 prompt：

```text
A linear flowchart for an academic paper on data preprocessing.

LAYOUT: Horizontal flow from left to right, five nodes arranged in a single row with equal spacing.

NODES:
- Start: rounded oval with thick border, label "Raw Data", soft blue fill #D6E4F0
- Step 1: rounded rectangle, label "Cleaning", soft gray fill #E5E7EB
- Step 2: rounded rectangle, label "Normalization", soft gray fill #E5E7EB
- Step 3: rounded rectangle, label "Feature Selection", soft gray fill #E5E7EB
- End: rounded oval with thick border, label "Ready Dataset", soft green fill #D8E8D0

CONNECTIONS:
- Sequential solid black arrows (2-3 px) between adjacent nodes, all pointing right.
- Each arrow labeled in italic gray (max 3 words): "remove outliers" → "scale to [0,1]" → "select top-k features".

TEXT:
- Title at top center, bold Arial: "Data Preprocessing Pipeline"
- Node labels: bold Arial, ≤ 3 words each
- Arrow labels: italic gray, ≤ 3 words each

STYLE: flat vector illustration, NeurIPS/ICML figure aesthetic, Arial sans-serif throughout, pastel palette, pure white background. Aspect ratio 16:9.

Negative constraints: NO photorealistic photos, NO 3D shading, NO drop shadows, NO cartoon style, NO emoji, NO unreadable text, NO crossing arrows, NO bidirectional arrows (unidirectional flow only), NO chart junk.
```

## 💡 调优提示

- **生成的箭头乱跑**：在 prompt 末尾加 "all arrows strictly horizontal, no curves"
- **节点比例不一致**：加 "all rounded rectangles have the same height and width"
- **文字渲染不准**：把所有节点 label 用双引号严格围住（已默认这样写）
- **想要垂直版本**：把 `Horizontal flow from left to right` 改为 `Vertical flow from top to bottom`，aspect ratio 改为 9:16

## 🔁 想要可矢量、可编辑（Mermaid 代码版）

如果你想要可放进 LaTeX、可永远清晰的版本，用 [Mermaid](https://mermaid.live)：

```mermaid
flowchart LR
    A([Raw Data]) --> B[Cleaning]
    B --> C[Normalization]
    C --> D[Feature Selection]
    D --> E([Ready Dataset])
```

直接粘到 https://mermaid.live 可看预览并导出 SVG/PNG。

## 🔗 相关

- 含判断节点（if-then-else）→ [branched.md](branched.md)
- 多支并行后合并 → [parallel.md](parallel.md)
- 含循环迭代 → [loop.md](loop.md)
