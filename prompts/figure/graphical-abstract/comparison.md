# 对比型图形摘要 · Comparison GA

> **何时用**：要证明"**有 vs 没有**方法"差异显著时

## 🎨 预期输出长什么样

```
═══════════════════════════════════════════════════════════════
   Our method achieves Z by enabling W.
═══════════════════════════════════════════════════════════════
┌─────────────────────────────────────────────────────────────┐
│  Without Our Method                       (灰底)             │
│  ──────────────────                                          │
│                                                              │
│   ┌────────┐    问题/慢/错  ──▶    ┌─────────┐               │
│   │ Start  │   ━━━━━━━━━━━        │ Bad     │               │
│   │ scene  │                       │ Outcome │               │
│   └────────┘                       └─────────┘               │
│                                                              │
│  Existing approach: X% accuracy, Y minutes.                  │
├─────────────────────────────────────────────────────────────┤
│  With Our Method                          (暖底)             │
│  ────────────                                                │
│                                                              │
│   ┌────────┐    our method  ──▶    ┌─────────┐               │
│   │ Start  │   ━━━━━━━━━━━        │ Good    │               │
│   │ scene  │                       │ Outcome │               │
│   └────────┘                       └─────────┘               │
│                                                              │
│  Our method: X+30% accuracy, Y/2 minutes.                    │
└─────────────────────────────────────────────────────────────┘
```

上下垂直分割，上半"without"灰调，下半"with"暖调，底部一句总结。

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
A graphical abstract for an academic paper, designed as a vertical comparison split by a horizontal thin gray line in the middle.

UPPER HALF — "Without {方法名}"
- Light gray background tint #F2F2F2
- Left side: render a starting scenario (a small flat-vector illustration)
- Right side: render the negative outcome (problem, error, slow result)
- Connecting arrow in the middle, labeled with the problematic process
- Below, in italic gray: "{without 文案：现有方法的指标}"

LOWER HALF — "With {方法名}"
- White background, with subtle warm yellow accent
- Left side: same starting scenario
- Right side: render the positive outcome (clear result, fast finish, correct answer)
- Connecting arrow in the middle, labeled with our method's name
- Below, in italic dark: "{with 文案：本方法的指标}"

At the bottom center, in bold Arial: "{结论一句话}"

Style: flat vector, white background, Arial sans-serif, journal-quality. Aspect ratio 4:3 or 1:1.

Negative constraints: NO photorealistic, NO 3D, NO drop shadows, NO cartoon, NO emoji, NO sarcastic tone in captions, NO long sentences.
```

---

## ✏️ 填空示例（提速 + 提精度）

```text
{方法名} = AdaptiveAttention
{without 文案} = Existing approach: 87% accuracy, 120 minutes per epoch.
{with 文案} = Our method: 93% accuracy, 50 minutes per epoch.
{结论一句话} = AdaptiveAttention achieves higher accuracy in less time by routing inputs adaptively.
```

## 💡 调优提示

- **左右对比 instead of 上下**：把 horizontal divider 改为 vertical divider in the center，调整布局
- **多个指标对比**：在 caption 中并列列出，如 "Acc: 87% → 93% | Latency: 120ms → 50ms | Memory: 4GB → 2GB"
- **想强调时间维度**：把 "starting scenario" 改为 "after 1 epoch", "after 10 epochs", "after 100 epochs"，做时间序列对比

## 🔗 相关

- 普通三段叙事（不强调对比）→ [narrative.md](narrative.md)
- 单纯方法对比图（更详细的模块对比，不是 GA）→ [../architecture/comparison.md](../architecture/comparison.md)
