# 4 种困难场景应对

---

## 场景 1：审稿人意见相互矛盾

**情况**：Reviewer 1 让你加更多数学推导；Reviewer 2 让你删掉数学推导改成直觉解释。

**处理**：
1. **不要假装两边都同意**——会显得敷衍
2. 在 cover letter 中**主动向编辑说明矛盾**
3. 选择**有更强证据支持的一方**作为主线
4. 必要时**两种方案并报**（主文 + 附录）

模板：
```text
**Note to the Editor:**

Reviewer 1 (R1.3) suggested adding more formal derivations, while Reviewer 2 
(R2.5) suggested moving them to the appendix for readability. We have chosen 
a middle path: the key derivation is in Section 3.2 (in line with R1.3), while 
extended derivations have been moved to Appendix A (in line with R2.5). We hope 
this satisfies both reviewers.
```

---

## 场景 2：要求做不可能的实验

**情况**：Reviewer 要求"在临床试验中验证"，但你是早期方法研究。

**处理**：
1. **委婉指出可行性边界**（不直接说"做不到"）
2. **提供替代证据**
3. **引用同类研究的可行精度**
4. 在 Discussion 中加入"未来工作"

模板：
```text
**R3.2** (Action: DEFEND + ACCEPT_TEXT)

> The method should be validated in a clinical setting before publication.

We thank the reviewer for emphasizing real-world validity. A full clinical 
trial is beyond the scope of this methodological paper, as it requires IRB 
approval, multi-year follow-up, and clinical-grade infrastructure. 

However, we have strengthened our validation by (1) extending experiments to 
two additional retrospective cohorts (n=3,200 patients total) and (2) 
benchmarking against published clinical baselines (Section 5.5, Table 6). 

We have also added an explicit "Future Work" subsection (Section 7, page 13) 
outlining the clinical translation pathway.
```

---

## 场景 3：Major Revision 缺关键证据

**情况**：审稿人要求的实验你跑不完。

**处理**：
1. **不要回避**——主动承认
2. **说明已补的部分**
3. **给出时间表与责任人**
4. 标记 `AUTHOR_INPUT_NEEDED`，提醒自己/合作者

模板：
```text
**R1.4** (Action: AUTHOR_INPUT_NEEDED → ACCEPT_ANALYSIS partial)

> Please add ablation on the embedding dimension (32, 64, 128, 256, 512).

We thank the reviewer. We have completed ablations for dimensions 32, 64, 
128, 256 (Table 7, Section 4.3). The dimension-512 experiment is currently 
running on our larger compute cluster and is expected to complete by 
[YYYY-MM-DD]. We will include it in the next revision and update the table 
accordingly. Preliminary results suggest performance plateaus around 
dimension 128.
```

---

## 场景 4：Minor Revision

**特点**：意见琐碎、修改快

**处理原则**：
- 每条 1–2 句即可，不要为了显得"重视"而写一大段
- 直接说"已修改"+ 位置

模板：
```text
**R1.5** (Action: ACCEPT_TEXT)

> Typo on page 6, line 200: "recieved" → "received".

Corrected. See page 6, line 200.
```
