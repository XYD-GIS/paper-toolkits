# 三段式叙事图形摘要 · Narrative GA

> **何时用**：Elsevier / Cell / 大多数生命科学期刊**要求的 Graphical Abstract**。一张图讲完 **"问题 → 方法 → 结果"** 的故事弧线
> **适用比例**：Cell 1328×531 像素 / Elsevier 横向 / 16:9

## 🎨 预期输出长什么样

```
═════════════════════════════════════════════════════════════════════════
                     A Novel Framework for X
═════════════════════════════════════════════════════════════════════════
┌──────────────────┐ → ┌──────────────────┐ → ┌──────────────────┐
│ PROBLEM (红条)   │   │ METHOD  (蓝条)   │   │ RESULT  (绿条)   │
│ ───────────      │   │ ───────────      │   │ ───────────      │
│                  │   │                  │   │                  │
│  困惑用户面对    │   │  pipeline:       │   │  bar chart: 30%  │
│  复杂图表的图标  │   │  ┌─┐ ┌─┐ ┌─┐    │   │  improvement,    │
│                  │   │  └─┘─└─┘─└─┘    │   │  happy user 图标 │
│                  │   │                  │   │                  │
│ Existing methods │   │ Our method does  │   │ Achieves X%      │
│ cannot handle X  │   │ X using Y        │   │ improvement      │
└──────────────────┘   └──────────────────┘   └──────────────────┘
```

横向 3 等分，每段一个色头标题 + 视觉比喻 + 短文字 caption，段间箭头。

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
A horizontal graphical abstract for an academic paper, divided into THREE equal sections from left to right by thin vertical dashed lines. Each section has a colored header band at the top with the section title in white bold Arial uppercase.

LEFT SECTION — "PROBLEM" (header band color: soft red #E8A6A6)
Render a simple flat-vector illustration depicting the research problem: {问题视觉描述}. Below the illustration, add a short caption in italic gray text (max 8 words): "{问题 caption}"

CENTER SECTION — "METHOD" (header band color: soft blue #A6C3E8)
Render a simplified flat-vector diagram of your method: {方法视觉描述}. Each stage shown as a labeled rounded rectangle. Below the diagram, add caption: "{方法 caption}"

RIGHT SECTION — "RESULT" (header band color: soft green #A6E8A6)
Render a flat-vector visualization of the key result: {结果视觉描述}. Below, add caption: "{结果 caption}"

BETWEEN SECTIONS: thin black arrows pointing from PROBLEM → METHOD → RESULT.

At the very top center, place the paper title in bold Arial (max 12 words): "{论文标题}"

Style: flat vector illustration, Arial sans-serif throughout, pastel palette, white background, journal-quality (Cell / Nature / Elsevier style). Aspect ratio 1328:531 (Elsevier standard) or 16:9.

Negative constraints: NO photorealistic photos, NO 3D shading, NO drop shadows, NO cartoon style, NO emoji that look childish, NO complex equations, NO long sentences (max 8 words per text label), NO unreadable text, NO logos or watermarks.
```

---

## ✏️ 填空示例

```text
{论文标题} = Dynamic Transformers for Streaming Time-Series Forecasting
{问题视觉描述} = a confused user looking at a chaotic time-series graph with question marks
{问题 caption} = Existing methods cannot adapt to non-stationary streams.
{方法视觉描述} = a horizontal pipeline showing 3 stages: encoder → dynamic attention block → predictor
{方法 caption} = We propose dynamic attention with adaptive routing.
{结果视觉描述} = a bar chart comparing 5 benchmarks, our method bars 12-30% higher
{结果 caption} = Achieves 12–30% improvement across 5 benchmarks.
```

## 📐 期刊提交规格速查

| 期刊 / 出版社 | GA 比例 | 像素 / 物理尺寸 | 文件格式 |
|---|---|---|---|
| Cell | 横向 | 13.4 × 5 cm，300 dpi | TIFF / EPS |
| Elsevier（通用）| 横向 | 1328 × 531 px | JPG / PNG / TIFF |
| Nature 系列 | 不强制 GA，但建议 1:1 或 4:3 | 单栏 8.9 cm，双栏 18.3 cm | TIFF / EPS / PDF |
| ACS（化学）| 横向 | 8.47 × 4.45 cm | TIFF / EPS |
| Wiley | 横向 | 50 × 50 mm 起 | TIFF / EPS |

## 💡 调优提示

- **3 秒读懂规则**：审稿人/读者最多花 3 秒看 GA。如果他们读完 caption 没明白故事，就需要重写——caption 越短越好
- **字号要够大**：300 dpi 下字号 ≥ 7 pt
- **色盲友好**：不要仅靠"红绿"区分语义（PROBLEM 红 / RESULT 绿 的对比可以，但 caption 文字必须明确）
- **生命科学方向**：考虑用 [biological.md](biological.md) 替代

## 🔗 相关

- 闭环系统 / RL / 反馈循环 → [circular.md](circular.md)
- 多层级理论框架 → [pyramid.md](pyramid.md)
- 生物医学方向 → [biological.md](biological.md)
- 强调 with vs without 方法 → [comparison.md](comparison.md)
