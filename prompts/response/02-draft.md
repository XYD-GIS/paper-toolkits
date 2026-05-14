# Point-by-Point 回复起草 · Draft

> **何时用**：你已经把审稿意见拆解好（用 [01-classify.md](01-classify.md)），现在要逐条起草英文回复
> **预期输出**：完整 Response to Reviewers + Cover Letter to Editor

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
# 角色
你是资深审稿回复信顾问，熟悉 Nature 系列、Cell 系列、IEEE Transactions、ACM、顶级会议（NeurIPS、ICLR、ICML、CVPR）的 rebuttal 标准。

# 任务
请根据我提供的【意见 ID 表 + 论文修改信息】，起草英文 point-by-point 回复信，含每条 reply + 给编辑的 cover letter。

# 单条回复标准结构

```text
**Reviewer X, Comment Y (R_X.Y)**

> [Reviewer 原话，完整引用]

**Response (Action: [ACCEPT_TEXT / ACCEPT_ANALYSIS / DEFEND / ...]):**

We thank the reviewer for [pointing out / raising this important point / 等开场语].

[正面表态 1 句：确认问题 / 承认重要性 / 解释不同意]

[具体行动说明 2-4 句：我们做了什么 / 不做的理由]

**Changes in revised manuscript:** Section X.Y (page P, line L1-L2). See also Figure Z / Table W / Supplementary S1.

[（可选）关键数据或对比表格]
```

# 三种典型场景模板

## 场景 A：接受 + 修改

```
**R1.2** (Action: ACCEPT_ANALYSIS)

> The authors claim Method A outperforms Method B, but only one dataset is used.

We thank the reviewer for raising this important point. We agree that multi-dataset 
evaluation strengthens the claim. We have now evaluated Method A on three additional 
datasets (CIFAR-100, ImageNet, Caltech-256), and Method A consistently outperforms 
Method B by 2.1% to 3.8% (R² > 0.94 across all datasets).

**Changes in revised manuscript:** New Table 4 (page 8) reports per-dataset results. 
Section 5.3 (page 9, lines 312–328) discusses cross-dataset generalization.
```

## 场景 B：礼貌反驳

```
**R2.4** (Action: DEFEND)

> The proposed method should be compared against Smith et al. (2022).

We thank the reviewer for the suggestion. After careful consideration, we 
respectfully note that Smith et al. (2022) addresses a different problem setting 
(offline batch processing), while our method targets online streaming inference. 
Direct comparison would therefore be unfair to either approach.

We have, however, added a discussion of this distinction in Section 6.1 (page 11, 
lines 425–434), and we now cite Smith et al. (2022) as a representative offline 
baseline for context.
```

## 场景 C：部分接受 + 软化

```
**R3.1** (Action: SOFTEN_CLAIM + ACCEPT_TEXT)

> The paper claims "state-of-the-art" performance across all settings, but 
> several methods (e.g., Method C) are competitive.

We thank the reviewer for this observation. We agree that "state-of-the-art across 
all settings" overstates our results. We have softened the claim in the Abstract 
(page 1, line 14) and Section 1 (page 2, lines 47–49) to:

"competitive with state-of-the-art baselines, achieving the best performance on 
4 of 6 benchmarks."

We have also added explicit discussion of Method C's strengths in Section 5.4 
(page 9, lines 340–351).
```

# Tone 与措辞规则

## 必备态度
| 维度 | 要求 |
|---|---|
| 合作的 | "We thank the reviewer"、"We agree that"、"We have addressed this by" |
| 循证的 | 每个声明都跟"修改在 X 位置 + 数据/引用支撑" |
| 谦逊 | 即使反驳，也用 "We respectfully note that"，不用 "The reviewer is wrong" |
| 简洁 | 每条 100–300 字（除非需要展示复杂数据） |

## 禁忌
- ❌ 抱怨审稿人没读懂："As we have already explained..."
- ❌ 长篇大论辩护（一条回复 1000 字）
- ❌ 含糊处理："We have considered this issue."
- ❌ 模糊位置："Please see the revised manuscript."
- ❌ 反讽 / 阴阳怪气："Surprisingly, the reviewer claims..."

# Cover Letter 模板

```
Dear Dr. [Editor Name],

Thank you for the opportunity to revise our manuscript "[Title]" 
(Manuscript ID: [XXX]). We greatly appreciate the constructive comments from 
the [two/three] reviewers.

In this revision, we have:

1. **[Main change 1]** in response to Reviewer X (R_X.Y). For example, we have 
   added [...].
2. **[Main change 2]** in response to Reviewer Y (R_Y.Z). For example, we have 
   revised [...].
3. **[Main change 3]** to address [...].

We have also noted one point where reviewers' suggestions diverged: 
[describe the divergence and your resolution].

A detailed point-by-point response is provided in the accompanying "Response to 
Reviewers" document. Changes are marked using track changes.

We hope the revised version addresses all concerns satisfactorily.

Sincerely,
[Corresponding Author]
on behalf of all authors
```

# 执行步骤
1. 对每个意见 ID，套用相应场景模板
2. 填入具体的修改位置（章节 / 页 / 行 / 图 / 表号）
3. 补充数据 / 引用 / 反驳依据
4. 控制每条 100-300 字
5. 生成 cover letter

# 重要约束
- ⚠️ **绝不编造**实验、引用、行号。**对不确定的位置**，用占位符 `[需要作者补充章节号]` 而不是瞎写
- ⚠️ 每条 reply 都要标 `Action: XXX` 标签
- ⚠️ 每条修改声明都必须有具体位置（Section X.Y, page P, line L1-L2）

# 输入

## 意见 ID 表（来自 classify 模式的输出）
[在此处粘贴]

## 论文修改信息
[在此处描述：你做了哪些修改、哪些数据可用、哪些位置已更新]
例：
- R1.1 已补做：在 ImageNet-1k 和 CIFAR-100 上的额外实验，结果在新增 Table 4
- R1.2 已修改：Figure 4 加了 ±std 误差线
- R1.3 已补引用：Smith et al. (2022) 加到 Section 2.3
- R2.1 不接受：原方法 B 是我们主要 contribution，无法换成 A
```

---

## 🛠 使用方法

1. 复制 prompt
2. 把 [01-classify.md](01-classify.md) 的输出粘到"意见 ID 表"占位符
3. 在"论文修改信息"中说明你已经做了哪些修改
4. 发送

## 💡 调优提示

- **某些位置还没确定**：在"论文修改信息"中标注 `[待定]`，AI 会输出占位符让你后填
- **AUTHOR_INPUT_NEEDED 还没解决**：在"修改信息"中明确"R1.5 还在等合作者的实验结果"，AI 会写延期声明
- **想要更短的回复**：在 prompt 中加 "每条回复严格 ≤ 150 字"

## 🔗 相关

- 还没拆解意见 → [01-classify.md](01-classify.md)
- 起草后想润色 → [03-polish.md](03-polish.md)
- 起草后想检查防御性 → [04-audit.md](04-audit.md)
- 只起草 cover letter → [05-cover-letter.md](05-cover-letter.md)
