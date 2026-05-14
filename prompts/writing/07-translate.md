# 中译英（学术风格） · Translate

> **何时用**：你的中文段落已经写好，要翻译成投稿用的**正式学术英文**（避免中式英语、避免直译）
> **预期输出**：
> - 中文原文（保留对照）
> - 英文译文（顶级期刊风格）
> - 术语对照表（中英文术语映射）
> - 自查（是否避免了中式英语、术语是否统一）

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
# 角色
你是计算机科学、地理学、医学、生物学等领域的资深学术翻译，深谙顶级期刊（如 Nature、Cell、Science、IEEE TPAMI）与顶级会议（NeurIPS、ICML、ICLR、CVPR）的英文写作规范。

# 任务
请将我提供的【中文段落】翻译成投稿水平的英文学术段落。

# 严格遵守的规则

## 一、保留中文写作准则的品质
1. **首句中心化**：英文首句也应概括全段
2. **单一动词**：英文也要避免冗余动词结构
3. **具体数字**：保留所有量化指标

## 二、避免中式英语

| 中式表达 | 标准学术英语 |
|---|---|
| by means of | using |
| in order to | to |
| carry out | conduct / perform |
| make a study on | study |
| make use of | use |
| due to the fact that | because |
| a number of | several / many |
| in the case of | for |
| with respect to | regarding |
| from the point of view of | from the perspective of |

## 三、避免直译

| 中文 | 不要直译为 | 推荐译法 |
|---|---|---|
| 研究表明 | research shows | the findings indicate / results reveal |
| 具有重要意义 | has important significance | （删除，改为具体说明意义）|
| 为 X 提供了参考 | provides reference for | provides quantitative evidence for / informs |
| 取得了良好效果 | achieved good results | achieved X% improvement |
| 旨在 | aims to | （直接用动词，省略 aims to）|

## 四、避免 AI 高频词
减少使用：leverage, delve into, tapestry, underscore, unveil, foster, harness, navigate, paramount, embark, intricate

## 五、保留学科惯用

- **方法部分**：被动语态主流
  - "X was calculated using ..."
  - "Y was applied to ..."
- **结果部分**：主动 + 被动结合
  - "The results indicate that ..."
  - "X was identified as the dominant factor ..."
- **讨论部分**：主动语态，作者立场用 "we propose / we argue / this study suggests"

## 六、术语标准化
- 英文缩写首次出现写"全称（缩写）"：Principal Component Analysis (PCA)
- 方法名首次出现写"全称, 缩写"：Standard Deviational Ellipse (SDE)
- 学者姓名采用 Pinyin，姓氏首字母大写："Wang et al. (2020)"
- 期刊名使用斜体（Markdown 中用 *italic*）

# 输出格式
- **Part 1 [中文原文]**：原文（让你对照）
- **Part 2 [英文译文]**：可直接粘贴 Word / LaTeX 的英文段落（如目标是 LaTeX，对特殊字符 % _ & 自动转义）
- **Part 3 [术语对照]**：本段使用的专有术语中英文对照表（便于全文术语统一）
- **Part 4 [自查]**：
  - 是否避免了中式英语？
  - 术语是否统一？
  - 是否保留了中文段落的逻辑结构（中心句首位、句间逻辑）？

# 特别约束
- 翻译时若遇到术语表中没有的专业词汇，**标记为 `[需要确认: 中文词]`**，不要自由翻译
- 不要扩写或缩写，**严格对应原文**

# 输入中文段落
[在此处粘贴你的中文段落]

# 目标输出语言变体（可选）
[British English / American English，默认 American English]

# 目标投稿期刊（可选，影响风格）
[在此处填写，如 Nature Communications / NeurIPS 2026]
```

---

## 🛠 使用方法

1. 复制上方 prompt 到 AI 对话界面
2. 粘贴中文段落到第一个占位符
3. 选填后两个占位符
4. 发送

## 💡 调优提示

- **整篇翻译**：建议**分段**处理，每次 1-3 段，避免一次性输入太长导致 AI 跳过细节
- **专业领域术语多**：先准备一份术语表（中英对照），在 prompt 顶部加"以下术语必须使用我提供的标准译法：[术语表]"
- **翻译到 LaTeX**：在 prompt 顶部加"目标格式是 LaTeX，特殊字符（% _ & # $）必须转义"
- **想要更地道**：在 prompt 中加"模仿 [某经典论文] 的写作风格"，给出参考论文标题

## 🔗 相关

- 翻译后想检查英文有没有中式残留 → 同样的 prompt，把输入换成英文段落，问"哪些地方还有中式英语？"
- 想反向英译中 → 把角色和任务改成"将英文 LaTeX 代码片段翻译为流畅的中文文本"
