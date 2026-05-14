# 算法 Pipeline 流程图 · Pipeline

> **何时用**：方法包含 **≥ 3 个清晰阶段**，每阶段有输入/输出，强调"顺序"

⚠️ 这个模板和 [../flowchart/linear.md](../flowchart/linear.md) 类似，区别是 pipeline 更偏"系统架构"风格，linear flowchart 更偏"流程逻辑"风格。如果你的图需要强调算法步骤而不是模块结构，去看 linear flowchart。

## 🎨 预期输出长什么样

```
┌─────────────┐    ┌────────────────┐    ┌──────────────┐    ┌──────────────┐
│   Input     │──▶ │  Feature       │──▶ │   Model      │──▶ │  Output /    │
│ Preprocess  │    │  Extraction    │    │  Inference   │    │  Decision    │
└─────────────┘    └────────────────┘    └──────────────┘    └──────────────┘
   蓝色             绿色                  橙色                 紫色

  (每个模块上方有 italic 灰色短描述)
  (下方可选时间轴：training-time / inference-time / deployment-time)
```

横向 pipeline，每个阶段独立标识，颜色递进区分。

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
A clean academic pipeline diagram for a {领域，如 machine learning} method, arranged horizontally from left to right. The diagram contains exactly {阶段数量，如 four} sequential stages, each rendered as a rounded rectangle with a 2-3 word English label inside.

STAGE 1 (leftmost): {阶段 1 名} — Input shown as small icon on the left side. Soft blue fill (#D6E4F0).
STAGE 2: {阶段 2 名} — Connected to Stage 1 with a thin black arrow. Soft green fill (#D8E8D0).
STAGE 3: {阶段 3 名} — Connected to Stage 2. Soft orange fill (#F5E0CB).
STAGE 4 (rightmost): {阶段 4 名} — Connected to Stage 3. Soft purple fill (#E0D4EC). Output icon on the right edge.

Above each stage, place an italic short description in gray (max 5 words). Below the pipeline, add a horizontal axis line with three time-related markers (training-time, inference-time, deployment-time) — optional, only if relevant.

Style: flat vector illustration, Arial sans-serif, white background, minimal aesthetic similar to NeurIPS / ICML figures. Aspect ratio 16:9.

Negative constraints: NO photorealistic photos, NO messy sketches, NO 3D shading, NO cartoon, NO drop shadows, NO emoji, NO logos.
```

---

## ✏️ 填空示例（机器学习 pipeline）

```text
{领域} = machine learning
{阶段数量} = four
{阶段 1 名} = Input Preprocessing
{阶段 2 名} = Feature Extraction
{阶段 3 名} = Model Inference
{阶段 4 名} = Output / Decision
```

## 💡 调优提示

- **阶段数 ≥ 6**：考虑拆成"两层"——顶层 4 个大阶段，每个再展开为子图（用 [../flowchart/nested.md](../flowchart/nested.md) 模板）
- **每阶段要标公式 / 参数维度**：在 prompt 中每个 STAGE 描述下加 "with annotation '{公式或维度}' below the rectangle in monospace font"
- **阶段间不是简单顺序而有循环**：直接用 [../flowchart/loop.md](../flowchart/loop.md)

## 🔗 相关

- 含判断 / 分支 → [../flowchart/branched.md](../flowchart/branched.md)
- 含循环 / 迭代 → [../flowchart/loop.md](../flowchart/loop.md)
- 简单总览（非顺序的模块图）→ [main-figure.md](main-figure.md)
