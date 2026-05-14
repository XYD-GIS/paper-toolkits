# 表标题生成 · Table Caption

> **何时用**：你做好了表格（baseline 对比 / 消融 / 数据集统计），要写英文 caption

## 🎨 预期输出长什么样

| 输入（中文描述）| 输出（英文 caption）|
|---|---|
| 与三个 baseline 在 ImageNet 上的对比 | `Comparison with Three Baselines on ImageNet` |
| 各模块消融实验结果 | `Ablation Study on Each Module` |
| 数据集统计：样本量、类别数、平均长度 | `Statistics of the Datasets Used` |

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
# 角色
你是经验丰富的学术编辑，擅长撰写精准、规范的论文表格标题。

# 任务
请将我提供的【中文表描述】转化为符合顶级会议/期刊规范的英文表标题。

# 格式规则

## 1. 大小写（与图标题相同规则）
- **名词性短语** → Title Case（所有实词首字母大写，末尾**不加**句号）
- **完整句子** → Sentence case（首字母大写，末尾**加**句号）

## 2. 表格常用句式（按场景选）
- 对比类：`Comparison with X` / `Comparison of A, B, and C on Y`
- 消融类：`Ablation Study on X` / `Ablation Study of Each Component`
- 结果类：`Results on X` / `Performance on X across Different Settings`
- 统计类：`Statistics of X Dataset` / `Statistics of the Datasets Used`
- 参数表：`Hyperparameters Used in the Experiments` / `Default Parameter Settings`
- 时间/速度：`Inference Time per Sample` / `Training Time Comparison`
- 资源：`Memory Usage Comparison` / `Parameter Count of Different Models`

## 3. 去 AI 味（必须遵守）
- **禁用**：showcase, depict, unveil, comprehensive
- **推荐**：show, compare, present, report, summarize

## 4. 输出格式
- 只输出翻译后的英文标题文本
- **不要**包含 `Table 1:` 前缀，只输出内容本身
- 必须对特殊字符转义（如 LaTeX 中 `%` → `\%`）
- 保持数学公式原样（保留 `$` 符号）

# 输入（中文表描述）
[在此处粘贴你的中文表描述]
```

---

## 🛠 使用方法

复制 → 替换占位符 → 发送

## ✏️ 几个真实输入输出对照

**输入**：
> 我们方法与现有的 5 种 SOTA 方法在 COCO 数据集上的 mAP 对比

**输出**：
```
Comparison with State-of-the-Art Methods on COCO (mAP)
```

---

**输入**：
> 消融实验：分别去掉 module A / module B / module C 后的性能下降

**输出**：
```
Ablation Study Showing Performance Drop after Removing Each Module
```

---

**输入**：
> 我们用到的 3 个数据集的样本量、类别数和平均序列长度

**输出**：
```
Statistics of the Three Datasets Used in This Study
```

## 💡 调优提示

- **强调"我们 vs 别人"**：用 "Comparison with X" 句式（注意 with 不是 vs，学术习惯）
- **多列表格**：caption 中提到主要列（如 "Table 3: Results on three datasets, including accuracy, F1, and AUC."）
- **数字加在 caption 中**：在 prompt 中加 "Include key numbers if mentioned, e.g., 'Comparison with 5 baselines on 3 datasets.'"

## 🔗 相关

- 图的 caption → [figure-caption.md](figure-caption.md)
- 推荐什么类型的图表（表 vs 图）→ [../chart-recommendation.md](../chart-recommendation.md)
