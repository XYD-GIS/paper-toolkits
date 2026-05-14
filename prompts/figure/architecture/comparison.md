# A vs B 模块对比图 · Comparison

> **何时用**：要画"消融对比"、"方法对比"、"传统 vs 我们的方法"、"before / after"

## 🎨 预期输出长什么样

```
┌─────────────────────────────┬─────────────────────────────┐
│  Baseline (Prior Work)      │       Our Method            │
│  ───────────                │       ─────────             │
│                             │                             │
│   ┌──┐    ┌──┐    ┌──┐      │   ┌──┐    ┌🆕─┐    ┌──┐    │
│   │M1│──▶ │M2│──▶ │M3│      │   │M1│──▶ │M2'│──▶ │M3│    │
│   └──┘    └──┘    └──┘      │   └──┘    └───┘    └──┘    │
│   灰蓝调 (旧方法)            │   暖色调 (新方法，关键模块  │
│                             │             粗边框突出)     │
│                             │                             │
│  ✗ Slow inference           │  ✓ 2× faster               │
│  ✗ Requires labeled data    │  ✓ No labels needed        │
└─────────────────────────────┴─────────────────────────────┘

       Our method replaces X with Y, yielding Z improvement.
```

中间垂直分隔线，左右两半同时展示，下方各列优缺点对比，最底一行总结。

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
A side-by-side comparison diagram for an academic paper, split into two equal halves by a thin vertical divider line in the center.

LEFT HALF — {左侧标签，如 "Baseline (Prior Work)"}:
- Title at top in bold Arial: "{左侧标签}"
- A simplified block diagram with {左侧模块数量，如 three modules} connected by black arrows.
- Use muted gray-blue palette (#9BB3CC, #BFD0E3) to indicate "the old way".
- Below the diagram, in italic gray text, list 2 short limitations (e.g., "Slow inference", "Requires labeled data").

RIGHT HALF — {右侧标签，如 "Our Method"}:
- Title at top in bold Arial: "{右侧标签}"
- A simplified block diagram with the new structure, {右侧模块描述，如 "three modules including a novel block"} connected by black arrows.
- Use vivid-but-soft accent palette (warm coral #F4A582, soft green #92C5DE) to indicate "the improvement". Highlight the novel block with a slightly thicker outline.
- Below the diagram, in italic dark text, list 2 short advantages (e.g., "2x faster", "No labels needed").

At the very bottom center, in small gray text, place a one-line summary: "{底部总结句}"

Style: flat vector illustration, white background, Arial sans-serif, ICLR/CVPR figure aesthetic. Aspect ratio 16:9.

Negative constraints: NO photorealistic photos, NO 3D, NO heavy shadows, NO cartoon style, NO unreadable text.
```

---

## ✏️ 填空示例（提出新方法 vs 旧基线）

```text
{左侧标签} = Baseline (Prior Work)
{左侧模块数量} = three modules
{右侧标签} = Our Method
{右侧模块描述} = three modules including a novel attention block
{底部总结句} = Our method replaces global attention with sparse attention, yielding 2× speedup.
```

## 💡 调优提示

- **新增模块要更突出**：在 prompt 中加 "the novel block has a 4 px thick border and a glowing soft yellow halo to highlight it"
- **想加性能数字**：在底部总结句中加具体指标，如 "achieves 92.3% accuracy (vs 87.1%) and 2× faster"
- **上下分割 instead of 左右**：把 vertical divider 改为 horizontal divider，aspect ratio 改为 3:4

## 🔗 相关

- 强调多个方法并行比较（≥ 3 个） → [../flowchart/parallel.md](../flowchart/parallel.md)
- 强调方法演化（不是对比）→ [storyboard.md](storyboard.md)
- 要做带数据的性能对比柱状图 → [../chart-recommendation.md](../chart-recommendation.md)
