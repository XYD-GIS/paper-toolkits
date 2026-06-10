# 回复信结构 + 意见拆解 + 行动映射

---

# 一、回复信整体结构

## 标准骨架

```
[1] Cover Letter to Editor （致编辑信，独立 1-2 页）
    - 总结：本轮主要改进了什么
    - 矛盾点说明（如 reviewer 间冲突）
    - 致谢

[2] Response to Reviewer 1
    [R1.1] Reviewer 原话 → Response → 修改位置
    [R1.2] ...
    [R1.3] ...

[3] Response to Reviewer 2
    [R2.1] ...
    [R2.2] ...

[4] Marked-up Manuscript （带 track changes 的修改稿）
```

## 回复信的三个目标

| 受众 | 目标 |
|---|---|
| **编辑** | 快速核查：每条意见是否处理了？修改位置在哪？反驳的理由是否站得住？ |
| **审稿人** | 感受到尊重 + 充分回应；不被冒犯地接受被反驳 |
| **作者自己** | 每条都有据可查；不留"暗债"（未处理的意见）|

---

# 二、Reviewer 意见拆解

## 拆解原则

审稿意见常常一段话包含多个问题，必须拆分编号后逐一回应，否则容易漏答。

- **一条意见一个 ID**：R1.1, R1.2, R1.3, R2.1, R2.2 ...
- 不要合并多个独立问题
- 区分"问题（必答）"与"建议（可选）"
- 区分"主要意见"与"次要意见"（一般 reviewer 会自己标，没标就你来标）

## 意见类型分类

| 类型 | 表现 | 一般行动 |
|---|---|---|
| **数据/方法质疑** | "Your sample size of N=15 is too small to support claim X" | ACCEPT_ANALYSIS / SOFTEN_CLAIM |
| **实验补充要求** | "Please add ablation study on parameter Y" | ACCEPT_ANALYSIS |
| **表述 / 语言** | "Section 3.2 is unclear; please revise" | ACCEPT_TEXT |
| **图表问题** | "Figure 4 lacks error bars" | ACCEPT_FIGURE |
| **相关工作缺失** | "You should cite Smith et al. 2023" | ADD_CITATION |
| **范围 / 局限** | "Limitations section is too brief" | ACCEPT_TEXT + SOFTEN_CLAIM |
| **主观偏好** | "I'd prefer if you used method X instead of Y" | CLARIFY 或 DEFEND |
| **越界要求** | "Add a clinical trial" （做不到的）| DEFEND 或 AUTHOR_INPUT_NEEDED |

---

# 三、行动映射（8 种标签）

每条意见必须映射到下面 8 个行动之一。**不允许"含糊处理"**——必须明确。

| 行动标签 | 含义 | 何时用 |
|---|---|---|
| `ACCEPT_TEXT` | 接受 + 修改正文 | 表述、语言、组织问题 |
| `ACCEPT_ANALYSIS` | 接受 + 补充分析或实验 | 数据问题、消融、统计 |
| `ACCEPT_FIGURE` | 接受 + 修改/补充图表 | 图表清晰度、标注、错位 |
| `SOFTEN_CLAIM` | 软化主张/限定范围 | 过度声称、超出证据范围 |
| `ADD_CITATION` | 补充引用 | 相关工作缺失 |
| `CLARIFY` | 不改正文，仅在回复中澄清 | 审稿人误解、已存在但被忽略 |
| `DEFEND` | 不同意，给出有依据的反驳 | 科学/范围层面的不同意 |
| `AUTHOR_INPUT_NEEDED` | 需要作者额外输入 | 实验未跑、合作者讨论、外部资源 |

⚠️ **`CLARIFY` 与 `DEFEND` 的区别**：
- CLARIFY：审稿人没读懂或漏看了，问题其实已在正文中（你只需指出位置）
- DEFEND：审稿人理解正确，但你不同意他的判断（你必须给出科学反驳）
