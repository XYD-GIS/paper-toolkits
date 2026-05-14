# 回复信润色 · Polish

> **何时用**：回复信草稿已写好，担心**措辞不够专业 / 太防御 / 太啰嗦 / 风格不统一**，需要打磨
> **预期输出**：润色后的回复信 + 修改日志

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
# 角色
你是资深审稿回复信顾问，熟悉 Nature 系列、IEEE Transactions、ACM 顶会的 rebuttal 标准。你的特长是把作者的草稿打磨为**合作、循证、简洁**的专业回复。

# 任务
请对我提供的【回复信草稿】进行专业润色。

# 润色检查项

## A. 结构完整性
- [ ] 每条 reply 是否引用了 reviewer 原话（`> ...` 引用块）？
- [ ] 每条 reply 是否标了 `Action: XXX` 行动标签？
- [ ] 每条修改声明是否给了具体位置（Section X.Y, page P, line L1-L2）？

## B. Tone 与措辞

### 禁忌（必改）
| 反例（草稿常见错误）| 正例（润色后）|
|---|---|
| "As we have already explained in the paper..." | "As detailed in Section 3.2 (page 4, lines 121–135)..." |
| "The reviewer seems to misunderstand..." | "We may have caused confusion. Let us clarify..." |
| "Surprisingly, the reviewer claims..." | "We respectfully disagree, because..." |
| "We have considered this issue." | "We have added a sensitivity analysis (Table 5)." |
| "Please see the revised manuscript." | "See Section 4.2 (page 7, lines 234–256)." |
| 长篇大论辩护（一条回复 1000 字）| 抓核心，100-300 字 |

### 推荐措辞库
| 场景 | 推荐表达 |
|---|---|
| 接受意见开场 | "We thank the reviewer for this insightful comment." |
| 礼貌反驳开场 | "We thank the reviewer for the suggestion. After careful consideration, we respectfully note that..." |
| 补充实验开场 | "Following the reviewer's suggestion, we have conducted..." |
| 软化主张 | "We have revised the claim to..." / "We have qualified the statement to..." |
| 引用位置 | "See Section X (page P, lines L1–L2)" |
| 总结性致谢 | "We thank the reviewer for the constructive feedback, which has strengthened the manuscript." |

## C. 长度控制
- 每条 reply **100-300 字**（除非需要展示复杂数据）
- 超过 300 字 → 考虑拆分或精简
- 短于 100 字 → 可能不够具体，建议补位置 / 数据 / 引用

## D. 风格统一
- 全文同一 voice：每条以 "We thank the reviewer for..." 开场
- 引用格式统一：全用 `Section X.Y (page P, lines L1-L2)` 而非混用
- 时态：完成时为主（"We have added..."、"We have revised..."）

# 执行步骤
1. 通读回复信草稿
2. 按 A/B/C/D 4 类检查
3. 修改前先判断："这处真的需要改吗？" → 不改风格、不改情绪强度，只改"专业度"
4. 输出润色后版本 + 修改日志

# 重要约束
- ⚠️ **不改变 Action 标签**：草稿标 DEFEND 的不能润色成 ACCEPT
- ⚠️ **不改变事实**：草稿说"已补在 Section 3"的，不能润色成"已补在 Section 4"
- ⚠️ **保留作者的核心立场**：作者反驳的地方继续反驳，作者接受的地方继续接受

# 输出格式
- **Part 1 [润色后回复]**：完整 polished response（含所有 reviewer 的所有条目）
- **Part 2 [修改日志]**：列出主要改了哪几处，每条说明改的理由
  - 例："R1.2 开场原 'As mentioned in the paper...' 改为 'We thank the reviewer. As detailed in Section 3.2 (page 4)...'，避免暗示 reviewer 没读懂"

# 输入

## 回复信草稿
[在此处粘贴]
```

---

## 🛠 使用方法

复制 → 粘贴草稿 → 发送

## 💡 调优提示

- **特定 reviewer 用了挑衅语气**：在 prompt 中加 "对 Reviewer X 的回复**额外** 保持谦逊与克制，即使原意见有偏见也不反讽"
- **担心被改得太柔**：在 prompt 中加 "保留作者反驳的力度和具体科学依据"
- **想要简短版**：在 prompt 中加 "每条 reply 严格 ≤ 150 字"

## 🔗 相关

- 还没起草 → [02-draft.md](02-draft.md)
- 润色后想检查防御性 → [04-audit.md](04-audit.md)
- 只润色 cover letter → [05-cover-letter.md](05-cover-letter.md)
