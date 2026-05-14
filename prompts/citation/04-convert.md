# 文献格式互转 · Convert

> **何时用**：要把 BibTeX 转成 RIS（Zotero 导入用）/ EndNote（.enw）/ Zotero RDF / 中文期刊纯文本 GB/T 7714，或反过来
> **预期输出**：转换后的目标格式文本

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
# 角色
你是熟悉多种学术文献格式（BibTeX、RIS、EndNote .enw、Zotero RDF、GB/T 7714 纯文本）的资深编辑。

# 任务
请把我提供的【源格式文献清单】转换为 {目标格式}。

# 支持的格式对

| 源格式 | 目标格式 | 用途 |
|---|---|---|
| BibTeX | RIS | 导入 Zotero / EndNote |
| BibTeX | EndNote (.enw) | 直接进 EndNote |
| BibTeX | GB/T 7714 纯文本 | 中文期刊投稿 |
| BibTeX | APA / IEEE / Nature 纯文本 | 投稿英文期刊 |
| RIS | BibTeX | LaTeX 用 |
| Word 列表（纯文本）| BibTeX | 从 Word 论文提取参考文献到 LaTeX |
| EndNote | BibTeX | EndNote 用户转 LaTeX |

# 字段映射表（BibTeX ↔ RIS）

| BibTeX 字段 | RIS 标签 | 含义 |
|---|---|---|
| @article | TY: JOUR | 期刊论文 |
| @inproceedings | TY: CONF | 会议论文 |
| @book | TY: BOOK | 专著 |
| @phdthesis | TY: THES | 学位论文 |
| author | AU | 作者 |
| title | T1 | 标题 |
| journal | JO | 期刊名 |
| year | PY | 年份 |
| volume | VL | 卷 |
| number | IS | 期 |
| pages | SP / EP | 起始 / 结束页 |
| doi | DO | DOI |
| publisher | PB | 出版方 |
| address | CY | 城市 |

# 执行步骤
1. 解析源格式的每一条记录
2. 按字段映射表转换为目标格式
3. 处理类型转换（如 BibTeX `@article` → RIS `TY: JOUR`）
4. 保留所有字段，**不丢失信息**
5. 输出目标格式

# 重要约束
- ⚠️ 不要编造缺失的字段。如果源格式缺某个字段，目标格式也留空（或标记 `// MISSING`）
- ⚠️ 多作者保持顺序，不要重排
- ⚠️ DOI 直接复制，不要"美化"

# 输入

## 目标格式
[填：RIS / EndNote / GB/T 7714 / APA / IEEE / BibTeX]

## 源格式文献清单
[在此处粘贴]
```

---

## 🛠 使用方法

1. 复制 prompt
2. 填目标格式 + 粘贴源格式数据
3. 发送

## ⚙️ 自动化备选（推荐）

如果你要转大量条目（≥ 20），AI 输出可能漏字段。**推荐用专业工具**：

| 工具 | 用法 | 特点 |
|---|---|---|
| **Zotero** | 文件 → 导入（任意格式）→ 文件 → 导出为（任意格式）| GUI，最稳，支持几乎所有格式 |
| **JabRef** | 打开 .bib → File → Export → 选格式 | BibTeX 专家，免费 |
| **bibtex-tidy** | `npx bibtex-tidy in.bib --output=out.bib` | 命令行，整理 BibTeX |
| **pandoc-citeproc** | `pandoc input.bib -t csljson -o output.json` | 转 CSL JSON 用于 Pandoc |

## 💡 调优提示

- **批量 ≥ 50 条**：分批处理，每次 ≤ 30 条
- **GB/T 7714 输出要求**：在 prompt 末尾加 "中文文献用中文期刊名；英文文献用英文期刊全称（不缩写）"
- **想保留所有 BibTeX 字段（即使非标准）**：在 prompt 中加 "Preserve all custom fields as comments in the target format."

## 🔗 相关

- 从 DOI 生成 BibTeX → [03-bibtex.md](03-bibtex.md)
- 检查格式是否正确 → [02-check.md](02-check.md)
- 统一格式（同一种格式内的规范化）→ [01-format.md](01-format.md)
