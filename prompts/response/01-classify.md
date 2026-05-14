# 审稿意见拆解 + 行动映射 · Classify

> **何时用**：刚收到 reviewer 意见，需要先**拆开 + 分类 + 决定每条怎么处理**，再开始写回复
> **预期输出**：意见 ID 表（每条编号 + 类型 + 推荐行动 + 优先级 + 原文）+ 行动汇总 + 需作者输入清单

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
# 角色
你是资深审稿与回复信顾问，熟悉 Nature 系列、Cell 系列、IEEE Transactions、ACM、顶级会议（NeurIPS、ICLR、ICML、CVPR）的审稿与 rebuttal 标准。

# 任务
请把我提供的【审稿人意见全文】拆解为独立条目，每条分配 ID、分类、推荐行动。

# 拆解原则
- **一条意见一个 ID**：R1.1, R1.2, R1.3, R2.1, R2.2 ...
- 一段话里塞了多个问题 → **拆开**，否则会漏答
- 区分"问题（必答）"与"建议（可选）"
- 区分"主要意见"与"次要意见"（reviewer 自己标的优先，没标就你来标）

# 意见类型分类

| 类型 | 表现 | 推荐行动 |
|---|---|---|
| **数据/方法质疑** | "Your sample size of N=15 is too small to support claim X" | ACCEPT_ANALYSIS / SOFTEN_CLAIM |
| **实验补充要求** | "Please add ablation study on parameter Y" | ACCEPT_ANALYSIS |
| **表述 / 语言** | "Section 3.2 is unclear; please revise" | ACCEPT_TEXT |
| **图表问题** | "Figure 4 lacks error bars" | ACCEPT_FIGURE |
| **相关工作缺失** | "You should cite Smith et al. 2023" | ADD_CITATION |
| **范围 / 局限** | "Limitations section is too brief" | ACCEPT_TEXT + SOFTEN_CLAIM |
| **主观偏好** | "I'd prefer if you used method X instead of Y" | CLARIFY 或 DEFEND |
| **越界要求** | "Add a clinical trial" （做不到的）| DEFEND 或 AUTHOR_INPUT_NEEDED |

# 行动标签（8 选 1）

| 标签 | 含义 | 何时用 |
|---|---|---|
| `ACCEPT_TEXT` | 接受 + 修改正文 | 表述、语言、组织问题 |
| `ACCEPT_ANALYSIS` | 接受 + 补充分析或实验 | 数据问题、消融、统计 |
| `ACCEPT_FIGURE` | 接受 + 修改/补充图表 | 图表清晰度、标注、错位 |
| `SOFTEN_CLAIM` | 软化主张/限定范围 | 过度声称、超出证据范围 |
| `ADD_CITATION` | 补充引用 | 相关工作缺失 |
| `CLARIFY` | 不改正文，仅在回复中澄清 | 审稿人误解、已存在但被忽略 |
| `DEFEND` | 不同意，给出有依据的反驳 | 科学/范围层面的不同意 |
| `AUTHOR_INPUT_NEEDED` | 需要作者额外输入 | 实验未跑、合作者讨论、外部资源 |

# 输出格式

## Part 1 [意见 ID 表]
| ID | 类型 | 推荐行动 | 优先级 | 原文摘录 |
|---|---|---|---|---|
| R1.1 | 数据质疑 | SOFTEN_CLAIM + ACCEPT_ANALYSIS | major | "Sample size of N=15 is too small..." |
| R1.2 | 实验补充 | ACCEPT_ANALYSIS | major | "Please add ablation on parameter Y" |
| R1.3 | 表述 | ACCEPT_TEXT | minor | "Section 3.2 is unclear" |
| R2.1 | 相关工作 | ADD_CITATION | minor | "You should cite Smith et al. 2023" |
| ... | | | | |

## Part 2 [行动汇总]
- 需补实验的（ACCEPT_ANALYSIS）：N 条 → 列出 ID
- 需改正文的（ACCEPT_TEXT）：N 条
- 需软化主张的（SOFTEN_CLAIM）：N 条
- 需补引用的（ADD_CITATION）：N 条
- 需反驳的（DEFEND）：N 条
- 需澄清的（CLARIFY）：N 条
- **需要作者额外输入的（AUTHOR_INPUT_NEEDED）**：N 条

## Part 3 [需作者输入清单]
列出所有 AUTHOR_INPUT_NEEDED 项，每条说明需要作者做什么：
- R1.5：需要作者补做"在 ImageNet-1k 上 dim=512 的消融"，预计 1 周
- R2.4：需要作者决定是否承认局限（投稿声明的"通用方法"是否需要降级为"特定场景方法"）
- ...

# 输入

## 审稿人意见全文
[在此处粘贴 reviewer 意见，可以是邮件原文、PDF 解析的文本，或整段 review]
```

---

## 🛠 使用方法

1. 复制 prompt
2. 粘贴 reviewer 意见全文
3. 发送

## ✏️ 典型输入示例

```
Reviewer 1:

This paper proposes a new framework for X. While the idea is interesting,
there are several concerns:

1. The sample size of N=15 is too small to support the strong claim of generalization.
   Please add ablation on larger datasets.

2. Figure 4 lacks error bars; please add std across 3 runs.

3. You should compare against Smith et al. (2022) which is highly relevant.

Minor:
- Section 3.2 is unclear; please revise.
- Typo on page 6, line 200: "recieved" → "received"

Reviewer 2:

The work is solid but the limitations section is too brief.
Also, I would prefer to see method A used instead of B in the experiments.
```

AI 会拆解为：
- R1.1（数据质疑）→ SOFTEN_CLAIM + ACCEPT_ANALYSIS，major
- R1.2（图表）→ ACCEPT_FIGURE，major
- R1.3（相关工作）→ ADD_CITATION，major
- R1.4（表述）→ ACCEPT_TEXT，minor
- R1.5（typo）→ ACCEPT_TEXT，minor
- R2.1（局限）→ ACCEPT_TEXT + SOFTEN_CLAIM，minor
- R2.2（主观偏好）→ CLARIFY 或 DEFEND，可选

## 💡 调优提示

- **意见用中文**：AI 也能拆，无需特别说明
- **意见特别长（> 5000 字）**：分 reviewer 处理
- **想强调严苛**：在 prompt 中加 "默认所有意见都标为 major，除非显然次要"

## 🔗 相关

- 分类后开始起草回复 → [02-draft.md](02-draft.md)
- 想模拟 reviewer 视角自己审稿（投稿前）→ [../writing/06-review.md](../writing/06-review.md)
