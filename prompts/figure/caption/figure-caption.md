# 图标题生成 · Figure Caption

> **何时用**：你做好了图，要写英文 caption（投稿用）

## 🎨 预期输出长什么样

输入一段中文描述，输出一行符合学术规范的英文标题：

| 输入（中文描述）| 输出（英文 caption）|
|---|---|
| 描述我们的模型架构和数据流向 | `Architecture of the proposed model and data flow.` |
| 三种方法在 5 个 benchmark 上的性能对比 | `Performance Comparison of Three Methods on Five Benchmarks` |
| 学习率从 1e-4 减小到 1e-6 时损失曲线的变化 | `Loss curves as the learning rate decreases from 1e-4 to 1e-6.` |

---

## 📋 完整 Prompt（复制下方代码块全部内容）

```text
# 角色
你是经验丰富的学术编辑，擅长撰写精准、规范的论文插图标题。

# 任务
请将我提供的【中文图描述】转化为符合顶级会议/期刊规范的英文图标题。

# 格式规则

## 1. 大小写
- **名词性短语** → 使用 Title Case（所有实词首字母大写，末尾**不加**句号）
  - 示例：`Architecture of the Proposed Model`
  - 示例：`Performance Comparison on Five Benchmarks`
- **完整句子** → 使用 Sentence case（仅第一个单词首字母大写，专有名词除外，末尾**必须加**句号）
  - 示例：`The proposed model outperforms baselines across all datasets.`
  - 示例：`Loss curves decrease as the learning rate is reduced.`

## 2. 极简原则
- **去除冗余开头**：不要用 "The figure shows..."、"This diagram illustrates..."、"Visualization of..."
- 直接以核心名词开头：Architecture / Performance comparison / Visualization / Distribution / Workflow

## 3. 去 AI 味（必须遵守）
- **禁用**：showcase, depict, delve into, unveil, intricate, paramount, comprehensive, novel（除非确实是 novelty 才用）
- **推荐**：show, compare, present, report, illustrate, demonstrate

## 4. 输出格式
- **只输出**翻译后的英文标题文本
- **不要**包含 `Figure 1:` / `Fig. 1.` 这样的前缀，只输出内容本身
- 必须对特殊字符进行转义：`%` → `\%`、`_` → `\_`、`&` → `\&`（如果输出格式是 LaTeX）
- 保持数学公式原样（保留 `$` 符号）

# 输入（中文图描述）
[在此处粘贴你的中文图描述]
```

---

## 🛠 使用方法

1. 复制上方 prompt 到 AI 对话界面
2. 替换最后的占位符
3. 发送

## ✏️ 几个真实输入输出对照

**输入**：
> 模型在三个不同数据集（CIFAR-100、ImageNet、TinyImageNet）上的精度随训练 epoch 变化曲线

**输出**：
```
Accuracy curves over training epochs on three datasets (CIFAR-100, ImageNet, TinyImageNet).
```

---

**输入**：
> 我们方法的整体框架

**输出**：
```
Overview of the Proposed Framework
```

---

**输入**：
> 通过对比实验展示了不同注意力机制的效率差异

**输出**：
```
Efficiency comparison across different attention mechanisms.
```

## 💡 调优提示

- **想要更短的 caption**：在 prompt 中加 "max 8 words"
- **要包含数据集名称**：在 prompt 中加 "Include dataset names if mentioned in description"
- **多面板图（含子图 a/b/c）**：在 prompt 中加 "For multi-panel figures, write a main caption + sub-captions for each panel"

## 🔗 相关

- 表格的 caption → [table-caption.md](table-caption.md)
- 推荐什么类型的图 → [../chart-recommendation.md](../chart-recommendation.md)
