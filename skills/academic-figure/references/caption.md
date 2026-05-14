# 图标题与表标题生成

---

# 一、图标题生成

## 格式规范

- 如果翻译结果是**名词性短语**：使用 **Title Case**（所有实词首字母大写，末尾不加句号）
- 如果翻译结果是**完整句子**：使用 **Sentence case**（仅第一个单词首字母大写，专有名词除外，末尾必须加句号）

## 写作风格

- **极简原则**：去除 "The figure shows"、"This diagram illustrates" 这类冗余开头
- 直接以 Architecture、Performance comparison、Visualization 等开头
- **去 AI 味**：避免使用复杂生僻词（如 showcase、depict、delve into、unveil），保持用词平实准确

## 输出格式

- 只输出翻译后的英文标题文本
- **不要**包含 `Figure 1:` 这样的前缀，只输出内容本身
- 必须对特殊字符进行转义（如 `%`、`_`、`&`）
- 保持数学公式原样（保留 `$` 符号）

---

# 二、表标题生成

## 常用句式

对于表格，推荐使用以下标准学术表达：
- "Comparison with X"
- "Ablation study on X"
- "Results on X"
- "Performance of X under Y"
- "Statistics of X dataset"

## 去 AI 味

避免使用 showcase、depict、unveil，直接使用 show、compare、present、report、summarize。
