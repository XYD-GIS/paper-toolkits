# BibTeX 模板 + DOI 验证 + 工具推荐

---

# 一、BibTeX 字段最小集

每种类型必须包含的最少字段：

```bibtex
% 期刊论文 @article
@article{key2024example,
    author = {Zhang, Lei and Wang, Ming and Liu, Hua},
    title = {A Novel Framework for Spatial Analysis},
    journal = {Nature Communications},
    year = {2024},
    volume = {15},
    number = {3},
    pages = {1234--1248},
    doi = {10.1038/s41467-024-12345-6}
}

% 会议论文 @inproceedings
@inproceedings{he2016deep,
    author = {He, Kaiming and Zhang, Xiangyu and Ren, Shaoqing and Sun, Jian},
    title = {Deep Residual Learning for Image Recognition},
    booktitle = {Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
    year = {2016},
    pages = {770--778}
}

% 学位论文 @phdthesis / @mastersthesis
@phdthesis{li2023study,
    author = {Li, Ming},
    title = {A Study on Transformer Attention Mechanisms},
    school = {Tsinghua University},
    year = {2023},
    address = {Beijing}
}

% 预发表 @misc
@misc{brown2020language,
    author = {Brown, Tom and Mann, Benjamin},
    title = {Language Models Are Few-Shot Learners},
    year = {2020},
    eprint = {2005.14165},
    archivePrefix = {arXiv}
}

% 数据集 @misc + note
@misc{zhao2024odyssey,
    author = {Zhao, Yuan and Liu, Xin},
    title = {Odyssey Traffic Dataset (v1.2)},
    year = {2024},
    publisher = {Zenodo},
    doi = {10.5281/zenodo.1234567},
    note = {Accessed: 2026-04-26}
}
```

---

# 二、文献管理工具推荐

| 工具 | 适用场景 |
|---|---|
| **Zotero** | 开源、跨平台、Word/LaTeX 插件齐全。推荐首选 |
| **EndNote** | 商业、Windows/Word 友好、机构常用 |
| **Mendeley** | 跨平台、PDF 高亮注释方便 |
| **JabRef** | LaTeX 用户首选，纯 BibTeX |

---

# 三、自动检索与导入

- **DOI 优先**：拿到 DOI 后用 Crossref/DataCite 自动拉取 BibTeX
- **PubMed**：生物医学 DOI/PMID 互转
- **arXiv**：arXiv ID → BibTeX 自动生成
- **手填禁忌**：不要手敲卷期页码，必出错

---

# 四、DOI 验证流程

提交前每条引用的 DOI 都要核验：

1. 复制 DOI 到 `https://doi.org/`
2. 跳转到的页面是否就是引用的论文？
3. 标题、作者、年份、卷期是否完全一致？
4. 不匹配 → DOI 错误或文献信息错误 → 修正

⚠️ 经验法则：**不要依赖单一网站做 DOI 解析**，至少用 Crossref + DOI.org 交叉验证。

### Crossref API 查询

```bash
curl https://api.crossref.org/works/10.1038/s41467-024-12345-6
```

返回 JSON 中关键字段：
- `title` / `author` / `published-print` / `container-title` / `volume` / `issue` / `page`
