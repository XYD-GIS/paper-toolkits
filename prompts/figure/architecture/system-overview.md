# 系统总览图 · System Overview

> **何时用**：复杂系统——多个子模块、多个数据源、训练与推理并存。要让读者**一图看懂整个系统的层次**。

## 🎨 预期输出长什么样

```
                          System Overview

  ╔════════════════════════════════════════════════════════════╗
  ║ Data Layer (蓝色背景带)                                    ║
  ║                                                            ║
  ║  ┌──────────┐    ┌────────────────┐    ┌──────────────┐    ║
  ║  │  Sensor  │    │ Curated Dataset │    │ External KB  │   ║
  ║  └────┬─────┘    └────────┬───────┘    └──────┬───────┘    ║
  ╚═══════│══════════════════│════════════════════│════════════╝
          │                  │                    │
          ▼                  ▼                    ▼
  ╔════════════════════════════════════════════════════════════╗  ┐
  ║ Model Layer (绿色背景带)                                  ║   │
  ║                                                            ║  │
  ║  ┌────────┐  ┌────────┐  ┌─────────┐  ┌────────┐         ║   │
  ║  │Encoder │  │Decoder │  │Attention│  │ Memory │         ║   │
  ║  └────┬───┘  └────┬───┘  └────┬────┘  └────┬───┘         ║   │ 反馈回路
  ╚═══════│═══════════│════════════│════════════│════════════╝   │ (虚线)
          ▼           ▼            ▼            ▼                  │
  ╔════════════════════════════════════════════════════════════╗  │
  ║ Application Layer (橙色背景带)                             ║  │
  ║                                                            ║  │
  ║  ┌─────────────┐   ┌──────────┐   ┌────────────┐          ║  │
  ║  │Classification│   │Generation│   │ Retrieval  │          ║──┘
  ║  └─────────────┘   └──────────┘   └────────────┘          ║
  ╚════════════════════════════════════════════════════════════╝
                    Feedback / Online Update
```

三层水平带（Data / Model / Application），各层间用箭头连接。右侧可选反馈回路（虚线弧线）。

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
A high-level system overview diagram for an academic paper, showing all major components of a complex {领域，如 machine learning system}. The diagram is organized into THREE horizontal bands separated by faint gray dashed lines:

TOP BAND — "Data Layer":
- 2-3 rounded rectangles representing data sources (e.g., {数据源列表，如 "Raw Sensors, Curated Dataset, External Knowledge Base"}).
- Soft blue palette (#D6E4F0).

MIDDLE BAND — "Model Layer":
- 3-5 rounded rectangles representing model components (e.g., {模型组件列表，如 "Encoder, Decoder, Attention Module, Memory"}).
- Soft green palette (#D8E8D0).
- Arrows connect TOP BAND nodes down into MIDDLE BAND.

BOTTOM BAND — "Application Layer":
- 2-3 rounded rectangles representing downstream tasks (e.g., {任务列表，如 "Classification, Generation, Retrieval"}).
- Soft orange palette (#F5E0CB).
- Arrows connect MIDDLE BAND nodes down into BOTTOM BAND.

ON THE RIGHT EDGE, place a vertical "feedback loop" arrow: a thin curved arrow going from BOTTOM BAND back up to TOP BAND, labeled "Feedback / Online Update" in italic.

At the top center, place the title in bold Arial: "{系统名}"

Style: flat vector, white background, paper-quality figure aesthetic, Arial sans-serif. Aspect ratio 16:9 or 4:3.

Negative constraints: NO photorealistic, NO 3D shading, NO drop shadows, NO cartoon, NO emoji, NO logos, NO over-saturated colors.
```

---

## ✏️ 填空示例（典型 ML 系统）

```text
{领域} = machine learning system
{数据源列表} = Raw Sensors, Curated Dataset, External Knowledge Base
{模型组件列表} = Encoder, Decoder, Attention Module, Memory
{任务列表} = Classification, Generation, Retrieval
{系统名} = System Overview
```

## 💡 调优提示

- **不止 3 层**：可以扩展到 4 层（Data / Preprocessing / Model / Application），把 prompt 中的"THREE bands"改为"FOUR bands"
- **某一层内部要细分**：在该 BAND 描述下加 "this band is further divided into two sub-rows: training-time components above, inference-time below"
- **无反馈回路**：删除 "ON THE RIGHT EDGE..." 段落
- **想强调跨层连接**：在 prompt 末尾加 "Some Model components also connect directly to Application: e.g., Memory ↔ Retrieval bidirectionally"

## 🔗 相关

- 简化版（单层主流程）→ [main-figure.md](main-figure.md) 或 [pipeline.md](pipeline.md)
- 强调数据流而非层次 → [dataflow.md](dataflow.md)
- 含子流程展开 → [../flowchart/nested.md](../flowchart/nested.md)
