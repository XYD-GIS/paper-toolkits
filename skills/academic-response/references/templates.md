# 回复模板（单条 + 典型场景 + Cover Letter）

---

# 一、单条回复模板

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

---

# 二、三种典型场景模板

## 场景 A：接受 + 修改（最常见）

```text
**R1.2** (Action: ACCEPT_ANALYSIS)

> The authors claim that Method A outperforms Method B, but only one dataset is used. 
> A comparison on multiple datasets is needed.

We thank the reviewer for raising this important point. We agree that 
multi-dataset evaluation strengthens the claim. We have now evaluated Method A 
on three additional datasets (CIFAR-100, ImageNet, Caltech-256), and Method A 
consistently outperforms Method B by 2.1% to 3.8% (R² > 0.94 across all datasets).

**Changes in revised manuscript:** New Table 4 (page 8) reports per-dataset 
results. Section 5.3 (page 9, lines 312–328) discusses cross-dataset 
generalization.
```

## 场景 B：礼貌反驳 + 给出依据

```text
**R2.4** (Action: DEFEND)

> The proposed method should be compared against Smith et al. (2022).

We thank the reviewer for the suggestion. After careful consideration, we 
respectfully note that Smith et al. (2022) addresses a different problem 
setting (offline batch processing), while our method targets online streaming 
inference. Direct comparison would therefore be unfair to either approach. 

We have, however, added a discussion of this distinction in Section 6.1 
(page 11, lines 425–434), and we now cite Smith et al. (2022) as a 
representative offline baseline for context.
```

## 场景 C：部分接受 + 部分软化

```text
**R3.1** (Action: SOFTEN_CLAIM + ACCEPT_TEXT)

> The paper claims "state-of-the-art" performance across all settings, 
> but several methods (e.g., Method C) are competitive.

We thank the reviewer for this observation. We agree that "state-of-the-art 
across all settings" overstates our results. We have softened the claim in the 
Abstract (page 1, line 14) and Section 1 (page 2, lines 47–49) to:

"competitive with state-of-the-art baselines, achieving the best performance 
on 4 of 6 benchmarks."

We have also added explicit discussion of Method C's strengths in Section 5.4 
(page 9, lines 340–351).
```

---

# 三、Cover Letter to Editor 模板

```text
Dear Dr. [Editor Name],

Thank you for the opportunity to revise our manuscript "[Title]" 
(Manuscript ID: [XXX]). We greatly appreciate the constructive comments from 
the two/three reviewers.

In this revision, we have:

1. **[Main change 1]** in response to Reviewer X (R_X.Y). For example, we 
   have added [...].
2. **[Main change 2]** in response to Reviewer Y (R_Y.Z). For example, we 
   have revised [...].
3. **[Main change 3]** to address [...].

We have also noted one point where reviewers' suggestions diverged: 
[describe the divergence and your resolution].

A detailed point-by-point response to each comment is provided in the 
accompanying "Response to Reviewers" document. Changes in the revised 
manuscript are marked using track changes.

We hope the revised version addresses all concerns satisfactorily. We are 
happy to make further revisions if needed.

Sincerely,

[Corresponding Author]
on behalf of all authors
```
