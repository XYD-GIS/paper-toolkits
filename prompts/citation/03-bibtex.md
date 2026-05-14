# 生成 BibTeX · BibTeX

> **何时用**：你有一组 DOI / 文献清单，想生成 `.bib` 文件给 LaTeX 用
> **预期输出**：可直接粘到 `.bib` 文件的 BibTeX 文本

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
# 角色
你是熟悉 BibTeX 与 LaTeX 文献管理的资深学术编辑。

# 任务
请根据我提供的【DOI 或参考文献清单】生成符合 BibTeX 标准的条目。

# BibTeX 字段最小集

## 期刊论文 @article
```bibtex
@article{firstauthor2024shortkey,
    author = {Last, First and Last, First},
    title = {Title Case Paper Title},
    journal = {Journal Name},
    year = {2024},
    volume = {15},
    number = {3},
    pages = {1234--1248},
    doi = {10.1038/s41467-024-12345-6}
}
```

## 会议论文 @inproceedings
```bibtex
@inproceedings{firstauthor2016shortkey,
    author = {Last, First and Last, First},
    title = {Paper Title},
    booktitle = {Proceedings of the Conference Name (CVPR)},
    year = {2016},
    pages = {770--778}
}
```

## 学位论文 @phdthesis / @mastersthesis
```bibtex
@phdthesis{firstauthor2023shortkey,
    author = {Last, First},
    title = {Thesis Title},
    school = {University Name},
    year = {2023},
    address = {City}
}
```

## 预发表 @misc + eprint
```bibtex
@misc{firstauthor2020shortkey,
    author = {Last, First and Last, First},
    title = {Paper Title},
    year = {2020},
    eprint = {2005.14165},
    archivePrefix = {arXiv}
}
```

## 数据集 @misc + note
```bibtex
@misc{firstauthor2024dataset,
    author = {Last, First and Last, First},
    title = {Dataset Title (Version)},
    year = {2024},
    publisher = {Zenodo},
    doi = {10.5281/zenodo.1234567},
    note = {Accessed: 2026-04-26}
}
```

# 命名规则
- key 格式：`{firstauthorlastname}{year}{shortkeyword}`
  - 示例：`he2016deep`（He et al., 2016, "Deep Residual..."）
  - 示例：`zhang2024transformer`（Zhang, 2024, "Transformer..."）
- 全小写，无空格
- shortkeyword 取标题第 1 个有意义的英文词
- 重复 key 加序号后缀：`he2016deep1`、`he2016deep2`

# 执行步骤
1. 对每条 DOI，从公开元数据（Crossref / arXiv / Zenodo）的认知推断条目类型与字段
2. 生成符合上述最小集的 BibTeX 条目
3. 字段不全的部分**标记为 `% TODO: verify {field}`**，**禁止编造**
4. 输出所有条目，每条之间空一行

# 重要约束
- ⚠️ **绝不编造 DOI / 卷期 / 页码**。如果你不能从公开知识推断，就标记 TODO
- ⚠️ 中文文献的作者用 `Last, First` 形式：如 "张三" → `Zhang, San`
- ⚠️ 期刊名 / 会议名保持标准缩写（如 NeurIPS 而非 NIPS）

# 输入
[在此处粘贴你的 DOI 列表 / 参考文献清单 / 关键信息]
```

---

## 🛠 使用方法

1. 复制 prompt
2. 在最后粘贴你的 DOI 列表，每行一个，例如：
   ```
   10.1038/s41467-024-12345-6
   10.1109/CVPR52729.2023.01234
   arXiv:2005.14165
   ```
3. 发送

## 💡 调优提示

- **AI 不确定字段时容易瞎编**：在 prompt 末尾再次强调 "If unsure, mark as `% TODO: verify {field}`. Never fabricate."
- **想跑批量自动化**：用 Python `crossref-cli` 或 `bibtexparser` 库直接调 Crossref API，比让 AI 推测更准
- **想要 biblatex 格式**：在 prompt 中加 "Output in biblatex format (use `date` instead of `year`, support `eprinttype` field)"

## ⚙️ 自动化备选（推荐）

如果你的 DOI ≥ 10 条，**直接调 Crossref API 更稳**：

```bash
# Linux/Mac
for doi in $(cat dois.txt); do
  curl -s "https://api.crossref.org/works/$doi/transform/application/x-bibtex" >> output.bib
  echo "" >> output.bib
done
```

```powershell
# Windows PowerShell
foreach ($doi in Get-Content dois.txt) {
  Invoke-WebRequest -Uri "https://api.crossref.org/works/$doi/transform/application/x-bibtex" -OutFile - | Out-String
}
```

或用 Zotero 一键批量导入 + 导出 .bib。

## 🔗 相关

- 验证 DOI 是否正确 → [05-verify.md](05-verify.md)
- 已有 BibTeX 想转其他格式 → [04-convert.md](04-convert.md)
- 想统一已有列表格式 → [01-format.md](01-format.md)
