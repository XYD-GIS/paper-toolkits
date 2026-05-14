# 环形图形摘要 · Circular GA

> **何时用**：**闭环系统**——强化学习、在线学习、闭环控制、生物反馈循环
> **比例**：1:1 方形

## 🎨 预期输出长什么样

```
                      Slice 1 (top, soft blue)
                     "Observe Environment"
                              ▲
                              │ ↺
                              │
       Slice 4 ────────       │       ──────── Slice 2
       (soft purple)          │              (soft green)
       "Evaluate Reward"    ┌─┴─┐   "Compute Action"
                            │CORE│
                            │ : │
                            │ 闭│
                            │ 环│
                            └─┬─┘
       Slice 3 (bottom, soft orange)
       "Execute Action"
                              │
                              ▼
                       clockwise loop
```

圆环分 4-6 个扇形，每片代表一步，箭头沿外缘顺时针流动。中心是标题徽章。

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
A circular graphical abstract for an academic paper, arranged as a clockwise loop of {阶段数量，如 four} stages around the center.

LAYOUT: A large circle (90% of frame) divided into {阶段数量} equal pie slices. Each slice contains:
- A 2-word English label in bold Arial at the outer edge
- A simple flat-vector icon in the middle of the slice
- A short 5-word caption in italic gray text at the inner edge

CENTER OF CIRCLE: A small circular badge with the paper title in bold Arial (max 10 words): "{论文标题}"

ARROWS BETWEEN SLICES: Curved arrows along the outer edge of the circle, going clockwise, indicating the loop direction.

COLOR ASSIGNMENT (clockwise from 12 o'clock):
- Slice 1: soft blue #D6E4F0
- Slice 2: soft green #D8E8D0
- Slice 3: soft orange #F5E0CB
- Slice 4: soft purple #E0D4EC
(repeat or extend palette if num_stages > 4)

At the bottom of the figure, in small gray italic text, add the one-sentence takeaway: "{结论一句话}"

Style: flat vector, Arial sans-serif, pastel palette, white background, biology / systems-paper aesthetic. Aspect ratio 1:1.

Negative constraints: NO photorealistic, NO 3D, NO cartoon, NO drop shadows, NO emoji, NO long sentences, NO unreadable text.
```

---

## ✏️ 填空示例（强化学习闭环）

```text
{阶段数量} = four
{论文标题} = Closed-Loop Adaptive Control with Reinforcement Learning
{结论一句话} = Each iteration refines the policy using feedback from environment rewards.
```

每片的具体内容（在 prompt 末尾追加）：
```text
SLICE DETAILS:
- Slice 1 (top, 12 o'clock): label "Observe", icon = an eye, caption "Sense environment state."
- Slice 2 (right, 3 o'clock): label "Decide", icon = a brain or compass, caption "Compute next action."
- Slice 3 (bottom, 6 o'clock): label "Act", icon = a hand pressing a button, caption "Execute in environment."
- Slice 4 (left, 9 o'clock): label "Learn", icon = a gear / arrow loop, caption "Update policy from reward."
```

## 💡 调优提示

- **阶段数 = 3**：三角形布局；改 `four` → `three`，注意每片占 120 度
- **阶段数 ≥ 6**：扇片会很窄，文字易溢出；考虑用 [narrative.md](narrative.md) 横向布局替代
- **想突出某一片**：在 prompt 中加 "Slice 2 (Decide) has a thicker outer border (4 px) and slightly darker fill to indicate it's the novel contribution"

## 🔗 相关

- 非闭环 / 单向流程 → [narrative.md](narrative.md)
- 强调层级关系 → [pyramid.md](pyramid.md)
- 强化学习的训练流程（不只是 GA）→ [../flowchart/loop.md](../flowchart/loop.md)
