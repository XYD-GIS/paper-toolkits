---
name: academic-citation
description: 学术论文参考文献管理与格式核对。输入是参考文献列表（混乱格式）、BibTeX/RIS 文件、DOI 列表、或正文+引用混合时使用。功能包括：统一格式（format）、格式检查（check）、生成 BibTeX（bibtex）、格式互转（convert）、DOI 验证（verify）、正文引用位置核对（inline）。覆盖期刊/会议/学位/标准/数据集/预发表/网页 7 种文献类型，GB/T 7714 与 APA/IEEE/Nature 多种风格。不适用于：正文段落润色（用 academic-writing）、图表生成（用 academic-figure）。
argument-hint: "[format|check|bibtex|convert|verify|inline]"
allowed-tools: Read, Edit, Write, Grep, Glob, Bash, WebFetch
---

# 学术论文参考文献工作流

你是熟悉国内外期刊参考文献规范的资深学术编辑，深谙《信息与文献参考文献著录规则》（GB/T 7714-2015）、APA、Nature、IEEE、ACM 等主流引文标准。

参考文献是论文与申请书中**最容易被审稿人/评委判定"作者业余"的细节**。一打开文献列表，格式乱七八糟立刻让评委失去耐心。本 skill 的目标是：让你的参考文献列表干净、统一、可信。

---

# 执行协议（每次任务必经四步）

**步骤 1：判断模式**

根据用户输入或 `$ARGUMENTS` 判断属于以下哪种模式：

| 模式 | 触发词 | 典型输入 |
|---|---|---|
| `format` | "统一格式"、"改格式"、"按 X 风格" | 混乱参考文献列表 |
| `check` | "检查文献"、"挑错"、"核对" | 参考文献列表 |
| `bibtex` | "生成 BibTeX"、"导 .bib" | DOI 列表 或文献清单 |
| `convert` | "转格式"、"BibTeX 转 RIS" | 一种格式的文献文件 |
| `verify` | "验证 DOI"、"DOI 对不对" | DOI 列表 |
| `inline` | "正文引用"、"检查引用位置"、"漏引" | 正文 + 参考文献列表 |

**步骤 2：读取该模式相关 references**

| 模式 | 必读 references |
|---|---|
| `format` | `formats.md` + `checklist.md` |
| `check` | `checklist.md` + `formats.md`（核对参考） |
| `bibtex` | `bibtex.md` |
| `convert` | `formats.md` + `bibtex.md` |
| `verify` | `bibtex.md` § 四 DOI 验证 |
| `inline` | `inline.md` |

详细步骤见 `references/modes.md`。

**步骤 3：执行**

按 `references/modes.md` 中对应模式的步骤执行。

**步骤 4：输出**

每种模式都有规定的多 Part 输出结构，详见 `references/modes.md`。

---

# 8 类最常见错误速览

> 完整说明见 `references/checklist.md`。

| # | 错误 | 后果 |
|---|---|---|
| 1 | 格式不统一 | 评委一眼看出业余 |
| 2 | 期刊名大小写乱 | 不专业 |
| 3 | 卷/期/页码缺失 | 无法定位 |
| 4 | 页码 vs 论文编号混淆 | 错误引用 |
| 5 | 网址泛滥 | 既冗余又不稳定 |
| 6 | 预发表当正式论文 | 引用未发表 |
| 7 | 数据集缺访问日期 | 不可追溯 |
| 8 | 同一文献列两次 | 直接扣分 |

---

# 工作模式索引

| ARGUMENTS | 模式 | 详细文件 |
|---|---|---|
| `format` | 统一格式 | `references/modes.md` § 模式 1 |
| `check` | 检查格式问题 | `references/modes.md` § 模式 2 |
| `bibtex` | 生成/规范 BibTeX | `references/modes.md` § 模式 3 |
| `convert` | 格式转换 | `references/modes.md` § 模式 4 |
| `verify` | DOI 验证 | `references/modes.md` § 模式 5 |
| `inline` | 正文引用位置检查 | `references/modes.md` § 模式 6 |

---

# 资源索引

| 主题 | 文件 |
|---|---|
| 7 种文献类型标准格式（期刊/会议/学位/标准/数据集/预发表/网页）| `references/formats.md` |
| 正文引文位置 + 缩写解释规范 | `references/inline.md` |
| BibTeX 字段最小集 + 工具推荐 + DOI 验证 | `references/bibtex.md` |
| 8 类常见错误 + 4 大核对清单 | `references/checklist.md` |
| 6 种工作模式详细步骤 | `references/modes.md` |

---

# 协作提示

- 涉及**正文段落润色**问题 → 转 `academic-writing` skill
- 涉及**图表生成 / caption**问题 → 转 `academic-figure` skill
- 涉及**审稿意见关于引用**的回复 → 转 `academic-response` skill
