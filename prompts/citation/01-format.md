# 参考文献格式统一 · Format

> **何时用**：你的参考文献列表里**格式混乱**（有的全大写、有的小写；有的卷期全、有的缺；有的带 DOI、有的不带），需要按某种风格（GB/T 7714 / APA / IEEE / Nature）**统一**
> **预期输出**：格式统一后的完整列表 + 修改日志 + BibTeX 版本（可选）

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
# 角色
你是熟悉国内外期刊参考文献规范的资深学术编辑，深谙 GB/T 7714-2015、APA、Nature、IEEE、ACM 等主流引文标准。

# 任务
请把我提供的【参考文献列表】按 {目标风格} 统一格式。

# 7 种文献类型的标准格式

## 期刊论文 @article
```
[N] AUTHOR A B, AUTHOR C D. Article title in lowercase[J]. Journal Name in Title Case, Year, Volume(Issue): Pages.
```
- 作者姓全大写，名缩写大写带句点
- 论文标题首字母大写，其余小写（除专有名词）
- 期刊名 Title Case
- 卷号必有，期号在括号里
- 末尾页码或论文编号二选一

## 会议论文 @inproceedings
```
[N] AUTHOR A B. Conference paper title[C]//Proceedings of Conference Name (Acronym). City: Publisher, Year: Pages.
```
- 必须有会议地点、出版方

## 学位论文 @phdthesis
```
[N] AUTHOR A B. Thesis title[D]. City: University, Year.
```

## 标准 [S]
```
[N] PUBLISHER. Standard number, Title[S]. Place: Publisher, Year.
```

## 数据集 [DS]
```
[N] CREATOR A B. Dataset title (Version)[DS]. Publisher/Repository, Year. DOI or URL. Accessed: YYYY-MM-DD.
```
- 必须有版本号 + 访问日期

## 预发表 arXiv
```
[N] AUTHOR A B. Preprint title[arXiv preprint]. arXiv:1234.56789, Year.
```
- 没有期刊名、卷期、页码——不要硬编造
- 优先引用正式发表版

## 网络资源 [EB/OL]
```
[N] AUTHOR/ORG. Page title[EB/OL]. URL. Accessed: YYYY-MM-DD.
```

# 执行步骤
1. 解析每条文献的类型（期刊/会议/学位/数据集/预发表/网页）
2. 按目标风格的字段顺序与符号约定重排
3. 统一大小写、缩写、卷期格式
4. **合并重复**：同一文献若被列入多次，合并为一条
5. **按正文出现顺序编号**（如果用户提供了正文）；如果只有列表，保持原顺序

# 输出格式
- **Part 1 [格式化列表]**：按目标风格统一后的参考文献（编号顺序）
- **Part 2 [修改日志]**：哪些条目改了什么（如"#3：补充了缺失的卷号"、"#7、#15：合并为同一条"）
- **Part 3 [BibTeX 版本]**（可选）：可粘贴到 .bib 文件的版本

# 输入

## 目标风格
[在此处选：GB/T 7714 / APA 7 / IEEE / Nature / Cell]

## 参考文献列表
[在此处粘贴你的参考文献列表，格式混乱也没关系]
```

---

## 🛠 使用方法

1. 复制 prompt
2. 在 `[目标风格]` 处选一种（不知道选哪个就填 "GB/T 7714"，中文期刊通用）
3. 把列表粘进去（即使格式很乱也行，AI 会解析）
4. 发送

## 💡 调优提示

- **列表超过 50 条**：分批处理，每次 20-30 条，避免 AI 跳过中间条目
- **特定字段缺失**（如某些条目缺 DOI）：在 prompt 末尾加 "对缺失字段标记 `[NEEDS VERIFICATION]`，不要编造"
- **混合中英文献**：在 prompt 中加 "中文文献用中文期刊名（不译为英文），英文文献保持原文"

## 🔗 相关

- 想检查格式问题但不改 → [02-check.md](02-check.md)
- 想生成 BibTeX → [03-bibtex.md](03-bibtex.md)
- 想验证 DOI 是否正确 → [05-verify.md](05-verify.md)
- 想正文引用位置核对 → [06-inline.md](06-inline.md)
