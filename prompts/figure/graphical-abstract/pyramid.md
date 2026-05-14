# 金字塔层级图形摘要 · Pyramid GA

> **何时用**：理论框架、**层级模型**、多尺度分析。强调"从底层抽象到高层决策"

## 🎨 预期输出长什么样

```
                  From Data to Decision: A Hierarchical Framework

                         ┌────────────────┐
                         │ Decision /     │  ← 顶层（橙色，最窄）
                         │ Insight   🎯   │
                         └────────┬───────┘
                                  ▲
                  ┌───────────────┴───────────────┐
                  │ Intermediate Representation   │  ← 中层（绿色）
                  │           🔄                  │
                  └───────────────┬───────────────┘
                                  ▲
        ┌─────────────────────────┴─────────────────────────┐
        │ Foundation / Raw Data                             │  ← 底层（蓝色，最宽）
        │   📊  📈  📉  🔢                                   │
        └───────────────────────────────────────────────────┘

      ← 左侧垂直箭头：indicates abstraction direction
```

倒金字塔（底部最宽，顶部最窄），三层水平带，左侧箭头指示抽象方向。

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
A pyramid-shaped graphical abstract for an academic paper, with {层数，如 three} horizontal levels stacked from bottom (broadest) to top (most specific).

LEVEL 1 (bottom, widest): "{第 1 层名}"
- A horizontal band 80% of frame width
- Soft blue fill #D6E4F0
- Inside: 4-5 small icons representing the foundation elements
- Right side: italic gray caption (max 6 words)

LEVEL 2 (middle): "{第 2 层名}"
- A horizontal band 60% of frame width, centered
- Soft green fill #D8E8D0
- Inside: 2-3 medium icons or block diagrams
- Right side: italic gray caption (max 6 words)

LEVEL 3 (top, narrowest): "{第 3 层名}"
- A horizontal band 40% of frame width, centered
- Soft orange fill #F5E0CB
- Inside: 1 prominent icon representing the final output
- Right side: italic gray caption (max 6 words)

VERTICAL ARROWS on the left side connecting bottom → middle → top, indicating abstraction direction.

At the very top, in bold Arial, the title: "{论文标题}"

Style: flat vector, white background, scientific paper aesthetic, Arial sans-serif. Aspect ratio 4:3 or 1:1.

Negative constraints: NO photorealistic, NO 3D, NO drop shadows, NO cartoon, NO long sentences, NO emoji.
```

---

## ✏️ 填空示例（从数据到决策）

```text
{层数} = three
{第 1 层名} = Foundation / Raw Data
{第 2 层名} = Intermediate Representation
{第 3 层名} = Decision / Insight
{论文标题} = From Data to Decision: A Hierarchical Framework
```

## 💡 调优提示

- **倒过来**（顶宽底窄）：把每层宽度倒过来 80% / 60% / 40% → 40% / 60% / 80%，箭头方向也倒过来
- **4 层或更多**：宽度逐层递减 90% → 75% → 60% → 45%
- **想强调某一层**：在该层加 "thicker outer border (3 px) to indicate this is the focus of the paper"

## 🔗 相关

- 平面叙事（不强调层级）→ [narrative.md](narrative.md)
- 闭环系统 → [circular.md](circular.md)
- 嵌套子流程（非金字塔）→ [../flowchart/nested.md](../flowchart/nested.md)
