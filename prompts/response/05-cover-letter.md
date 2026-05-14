# Cover Letter 起草 · Cover Letter to Editor

> **何时用**：你只想起草给编辑的 cover letter（不写整套 reply）
> **预期输出**：一页内的专业 cover letter

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
# 角色
你是资深审稿回复信顾问，熟悉 Nature 系列、Cell 系列、IEEE Transactions、ACM 顶会编辑沟通规范。

# 任务
请根据我提供的【主要修改清单 + reviewer 矛盾处理 + 论文信息】起草一份给编辑的 cover letter。

# Cover Letter 标准模板

```
Dear Dr. [Editor Name],

Thank you for the opportunity to revise our manuscript "[Paper Title]" 
(Manuscript ID: [XXX]). We greatly appreciate the constructive comments from 
the [two/three] reviewers.

In this revision, we have:

1. **[Main change 1]** in response to Reviewer X (R_X.Y). 
   For example, we have [...].

2. **[Main change 2]** in response to Reviewer Y (R_Y.Z). 
   For example, we have [...].

3. **[Main change 3]** to address [...].

[Optional: We have also noted one point where reviewers' suggestions diverged: 
[describe the divergence and your resolution].]

A detailed point-by-point response to each comment is provided in the 
accompanying "Response to Reviewers" document. Changes in the revised 
manuscript are marked using track changes.

We hope the revised version addresses all concerns satisfactorily. We are 
happy to make further revisions if needed.

Sincerely,

[Corresponding Author Name]
on behalf of all authors
```

# 写作规则

## 内容（核心 = 让编辑看一眼就知道做了啥）
1. **提炼 3 个主要修改方向**（不要超过 4 个，多了反而显得改的太多 / 没重点）
2. 每个方向**对应一位或多位 reviewer**，用 R_X.Y 标号
3. 给一句话具体描述（"For example, we have ..."）

## 矛盾处理（如有）
如果两位 reviewer 给冲突意见，**必须在 cover letter 中说明**：
- 不要假装两边都同意
- 选择有更强证据支持的一方
- 必要时两种方案并报（主文 + 附录）

模板：
```
We have also noted one point where reviewers' suggestions diverged: 
Reviewer 1 (R1.3) suggested adding more formal derivations, while Reviewer 2 
(R2.5) suggested moving them to the appendix for readability. We have chosen 
a middle path: the key derivation is in Section 3.2 (in line with R1.3), while 
extended derivations have been moved to Appendix A (in line with R2.5).
```

## 简洁性
- **一页以内**（A4 单倍行距约 400-500 字）
- 不要重复 reply 里的细节
- 不要客套话过多（开头致谢 + 结尾"hope" 一句即可）

## 禁忌
- ❌ 抱怨"reviewer 没读懂"
- ❌ 长篇大论自我表扬
- ❌ 在 cover letter 里直接和 reviewer "对线"
- ❌ 给编辑施压（"this paper has been accepted at..."）

# 执行步骤
1. 提炼 3 个主要修改方向
2. 标注审稿人间矛盾的解决方案
3. 套用模板
4. 控制在一页以内

# 输入

## 论文信息
- 论文标题：[在此处填]
- Manuscript ID：[在此处填]
- 编辑姓名：[在此处填，如不知道写 "Dear Editor"]
- Reviewer 数量：[2 / 3]

## 主要修改清单
[在此处粘贴本轮的核心修改，越具体越好]
例：
1. 补充了 3 个数据集上的实验（CIFAR-100, ImageNet, COCO），Table 4 - R1.1
2. 重写了 Method Section 3.2 让 attention 机制更清晰 - R1.3
3. 加入 limitations 子节，承认方法在小样本场景下的局限 - R2.1
4. 补引了 Smith et al. (2022) 和 Liu et al. (2023) - R2.3

## Reviewer 间的矛盾（如有）
[在此处描述：哪两位 reviewer 的意见冲突，你怎么解决的]
例：
- R1.4 让加更多数学推导，R2.5 让删数学推导 → 关键推导留在正文 Section 3.2，扩展推导移到 Appendix A
```

---

## 🛠 使用方法

1. 复制 prompt
2. 在论文信息 / 修改清单 / 矛盾处理三处分别填空
3. 发送

## ✏️ 真实输入示例

```
## 论文信息
论文标题：Dynamic Transformers for Streaming Time-Series Forecasting
Manuscript ID：NEUR-2026-1234
编辑姓名：Dr. Jane Smith
Reviewer 数量：3

## 主要修改清单
1. 补做了 5 个 benchmark 上的对比实验（之前只有 2 个），新增 Table 4 - 回应 R1.1, R2.2
2. 加了消融实验：dim=32/64/128/256（暂缺 512，已说明）- R1.5
3. 软化了 Abstract 中 "state-of-the-art" 表述，改为 "competitive with SOTA" - R3.1
4. Figure 4 加了 ±std 误差线 - R1.2

## 矛盾处理
R1.4 要求加更多公式推导，R2.5 要求简化表述。
解决方案：关键推导（Eq 5-7）留在 Section 3.2，扩展推导（Lemma 1-3 证明）移到 Appendix A。
```

AI 会输出类似：

```
Dear Dr. Smith,

Thank you for the opportunity to revise our manuscript "Dynamic Transformers 
for Streaming Time-Series Forecasting" (Manuscript ID: NEUR-2026-1234). We 
greatly appreciate the constructive comments from the three reviewers.

In this revision, we have:

1. **Expanded benchmark coverage** in response to Reviewer 1 (R1.1) and 
   Reviewer 2 (R2.2). We extended evaluation from 2 to 5 benchmarks 
   (Table 4, page 8), demonstrating consistent improvements across diverse 
   datasets.

2. **Added ablation studies** in response to Reviewer 1 (R1.5). We conducted 
   ablations on embedding dimensions 32, 64, 128, and 256 (Table 7). The 
   dim=512 experiment is ongoing on our larger compute cluster and will be 
   included in the next revision if requested.

3. **Tempered the claim of "state-of-the-art"** in response to Reviewer 3 
   (R3.1). The Abstract (page 1, line 14) now reads "competitive with 
   state-of-the-art baselines, achieving the best performance on 4 of 6 
   benchmarks."

We have also noted one point where reviewers' suggestions diverged: 
Reviewer 1 (R1.4) requested additional formal derivations, while Reviewer 2 
(R2.5) suggested simplifying the technical exposition. We have chosen a 
middle path: the key derivations (Eq. 5–7) remain in Section 3.2, while 
extended proofs (Lemma 1–3) have been moved to Appendix A.

A detailed point-by-point response is provided in the accompanying 
"Response to Reviewers" document. Changes are marked using track changes.

We hope the revised version addresses all concerns satisfactorily.

Sincerely,
[Your Name]
on behalf of all authors
```

## 💡 调优提示

- **没有矛盾意见**：在 prompt 中删除"Reviewer 间的矛盾"段，AI 不会硬编
- **要更长（多页）**：在 prompt 中加 "Expand each point with 2-3 sentences of context"
- **要更短（半页）**：加 "Limit cover letter to 250 words total"
- **特定期刊有格式要求**：在 prompt 顶部加 "目标期刊：Nature Communications，请遵循其 cover letter 规范"

## 🔗 相关

- 起草完整 reply（含 cover letter）→ [02-draft.md](02-draft.md)
- 处理多 reviewer 矛盾 → 见 [02-draft.md](02-draft.md) 中的"困难场景"部分
- 投稿前真实性审查 → [04-audit.md](04-audit.md)
