# 标准参考文献格式分类（7 种文献类型）

---

## 1. 期刊论文（最常见）

**标准格式**（GB/T 7714 数字 + 字母混合）：

```text
[1] AUTHOR A B, AUTHOR C D, AUTHOR E F. Article title in lowercase[J]. Journal Name in Title Case, Year, Volume(Issue): Pages.
```

实例：
```text
[1] ZHANG L, WANG M, LIU H. A novel framework for spatial analysis[J]. Nature Communications, 2024, 15(3): 1234-1248.
```

**关键点**：
- 作者姓全大写，名缩写大写带句点
- 论文标题首字母大写，其余小写（除专有名词）
- 期刊名 Title Case
- 卷号必有，期号在括号里（若期刊有期）
- 末尾**页码**或**论文编号**二选一，与期刊实际编排一致

---

## 2. 会议论文

```text
[2] AUTHOR A B, AUTHOR C D. Conference paper title[C]//Proceedings of Conference Name (Acronym). City: Publisher, Year: Pages.
```

实例：
```text
[2] HE K, ZHANG X, REN S, et al. Deep residual learning for image recognition[C]//Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR). Las Vegas: IEEE, 2016: 770-778.
```

**关键点**：
- 必须有会议地点、出版方
- 会议有 "In: Proceedings of XXX" 或 "//Proceedings of XXX" 格式
- `[C]` 表示会议论文

---

## 3. 学位论文

```text
[3] AUTHOR A B. Thesis title[D]. City: University, Year.
```

实例：
```text
[3] LI M. A study on transformer attention mechanisms[D]. Beijing: Tsinghua University, 2023.
```

**关键点**：
- `[D]` 表示学位论文
- 必须有学位授予单位与城市

---

## 4. 标准 / 技术报告

```text
[4] PUBLISHER. Standard number, Title[S]. Place: Publisher, Year.
```

实例：
```text
[4] ISO. ISO/IEC 27001:2022, Information security management systems[S]. Geneva: ISO, 2022.
```

**关键点**：
- `[S]` 表示标准
- 标准编号在前

---

## 5. 数据集

```text
[5] CREATOR A B. Dataset title (Version)[DS]. Publisher/Repository, Year. DOI or URL. Accessed: YYYY-MM-DD.
```

实例：
```text
[5] ZHAO Y, LIU X. Odyssey traffic dataset (v1.2)[DS]. Zenodo, 2024. DOI: 10.5281/zenodo.1234567. Accessed: 2026-04-26.
```

**关键点**：
- `[DS]` 表示数据集
- 必须有版本号
- 必须有访问日期（不同于论文，数据集会更新）
- DOI 优先，URL 次之

---

## 6. 预发表（arXiv / bioRxiv）

```text
[6] AUTHOR A B. Preprint title[arXiv preprint]. arXiv:1234.56789, Year.
```

实例：
```text
[6] BROWN T, MANN B. Language models are few-shot learners[arXiv preprint]. arXiv:2005.14165, 2020.
```

**关键点**：
- 标明 "arXiv preprint" 或 "bioRxiv preprint"
- 没有期刊名、卷期、页码——不要硬编造
- 给出 arXiv ID（带年.编号）

⚠️ **避免引用预发表**：经验法则——预发表不是稳定文献，能引正式发表的就引正式发表的。万不得已才引 arXiv。

---

## 7. 网络资源（最后选项）

```text
[7] AUTHOR/ORG. Page title[EB/OL]. URL. Accessed: YYYY-MM-DD.
```

实例：
```text
[7] OPENAI. GPT-5 system card[EB/OL]. https://openai.com/research/gpt-5. Accessed: 2026-04-26.
```

**关键点**：
- `[EB/OL]` 表示电子资源/网络资源
- **能找到论文的就别引网页**——网页随时可能失效
