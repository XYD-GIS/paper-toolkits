# 5 种工作模式详细步骤

根据 $ARGUMENTS 选择模式。未指定时根据输入内容自动判断。

---

## 模式 1：classify（意见拆解 + 行动映射）

输入：审稿意见全文

执行步骤：
1. 按 reviewer 切块（R1、R2、R3）
2. 每个 reviewer 内部拆出独立意见（R1.1, R1.2 ...）
3. 标注意见类型（数据 / 表述 / 引用 / 实验 / 范围 / 主观）（见 `structure.md`）
4. 映射 8 选 1 行动标签（见 `structure.md`）
5. 标注优先级（major / minor）

输出：
- Part 1：意见 ID 表（ID / 类型 / 行动 / 优先级 / 原文摘录）
- Part 2：行动汇总（需补实验的、需改正文的、需加引用的分别有多少条）
- Part 3：需作者输入的清单（AUTHOR_INPUT_NEEDED）

---

## 模式 2：draft（起草回复）

输入：分类后的意见 ID 表 + 论文修改信息

执行步骤：
1. 对每个 ID，套用 `templates.md` 单条回复模板生成 reply
2. 填入具体修改位置（章节、页、行）
3. 补充数据 / 引用 / 反驳依据
4. 控制每条 100–300 字
5. 套用 `templates.md` § 三模板生成 cover letter

输出：
- Part 1：Response to Reviewers（全文）
- Part 2：Cover Letter to Editor
- Part 3：未填位置的占位符清单（让作者补充）

---

## 模式 3：polish（修改既有草稿）

输入：草稿 + 修改方向

执行步骤：
1. 按 `tone.md` 检查是否有禁忌措辞
2. 按 `templates.md` 模板检查结构完整性
3. 收紧冗长段落（一条意见超过 300 字考虑拆分）
4. 统一措辞库表达

输出：
- Part 1：润色后回复
- Part 2：修改日志

---

## 模式 4：audit（防御性 / 真实性审查）

输入：完成的回复信草稿

执行步骤：按 `checklist.md` 5 大类清单逐项检查

输出：
- 通过：`[审查通过，可提交]`
- 有问题：分点列出违反项 + 修改建议
- 重点警示：编造的实验 / 引用 / 行号
- 重点警示：未解决的 AUTHOR_INPUT_NEEDED

---

## 模式 5：cover（仅起草 cover letter）

输入：主要修改清单

执行步骤：
1. 提炼 3 个主要修改方向
2. 标注审稿人间矛盾的解决方案（参考 `difficult-cases.md` § 场景 1）
3. 套用 `templates.md` § 三模板
4. 简洁、专业、不重复 reply 内容

输出：Cover Letter 全文（一页内）
