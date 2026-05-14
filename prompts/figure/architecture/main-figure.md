# 论文主架构图 · Main Figure

> **何时用**：你要画论文的**总览图 / Main Figure**——读者一眼看懂方法做什么、模块如何连接、数据流向

## 🎨 预期输出长什么样

类似 DeepMind / OpenAI 论文的扁平化矢量插画，纯白底，模块清晰，数据流箭头明确。没有 3D 阴影，没有照片质感，没有装饰。

参考视觉：transformer 论文的 Figure 1、ResNet 论文的 Figure 2、CLIP 论文的 Figure 1。

---

## 📋 完整 Prompt（中文版，复制下方代码块全部内容）

```text
# Role
你是世界顶尖的学术插画专家，专注于为 CV/AI/科学领域的顶级会议（CVPR、NeurIPS、ICLR、ICML、Nature）绘制高质量、直观且美观的论文架构图。

# Task
请阅读我提供的【论文方法描述】，深刻理解其核心机制、模块组成和数据流向。基于你的理解，设计并绘制一张专业的学术架构图。

# Visual Constraints
1. 风格基调：扁平化矢量插画，参考 DeepMind 或 OpenAI 论文的图表美学；纯白色背景；拒绝卡通感、3D 阴影、过度艺术化。
2. 色彩体系：严格使用淡色系或柔和色调；颜色深浅区分模块类型；色盲友好。
3. 内容与布局：模块清晰、数据流箭头明确；适当使用简洁矢量图标增强直观性；布局采用 {布局方向，如 Left-to-Right}。
4. 文字规范：图中所有文字使用英文；关键模块用清晰标签；不出现长句和复杂公式。
5. 禁止事项：不允许逼真照片感、杂乱草图、难辨文本、3D 阴影、卡通元素、廉价 emoji、水印 logo。

# Input Methodology
[在此处粘贴你的论文摘要 + 方法部分描述]
```

---

## 📋 完整 Prompt（英文版，对 nano banana / DALL-E 效果更好）

```text
You are an expert Scientific Illustrator for top-tier AI conferences (NeurIPS / CVPR / ICML / ICLR).
Your task is to generate a professional "Illustration" (main figure for the paper) based on a research paper abstract and methodology.

**Abstract:**
{Paste your abstract here}

**Methodology:**
{Paste your methodology description here}

**Visual Style Requirements:**
1.  **Style:** Flat vector illustration, clean lines, academic aesthetic. Similar to figures in DeepMind or OpenAI papers.
2.  **Layout:** Organized flow (Left-to-Right / Top-to-Bottom / Circular). Group related components logically.
3.  **Color Palette:** Professional pastel tones. White background.
4.  **Text Rendering:** You MUST include legible text labels for key modules or equations mentioned in the methodology (e.g., "Encoder", "Loss", "Transformer").
5.  **Negative Constraints:** NO photorealistic photos, NO messy sketches, NO unreadable text, NO 3D shading artifacts.

**Generation Instruction:**
Highlight the core novelty. Ensure the connection logic makes sense.
```

---

## 🛠 使用方法

1. 选择中文版或英文版（**英文版对图像生成模型效果通常更好**）
2. 替换 `{}` 占位符 / `[在此处粘贴...]` 处
3. 复制到图像生成模型：
   - **首选**：GPT-Image-2 / DALL-E 3
   - **次选**：Imagen 3 / nano banana
4. 多生成 2-3 张，选最佳

## 💡 调优提示

- **生成的图太密**：在 prompt 中加 "with generous whitespace, sparse layout"
- **模块比例不对**：加 "all rounded rectangles have the same height unless specified"
- **箭头太乱**：加 "arrows do not cross each other; route around modules with right-angle turns"
- **缺少某个模块**：在 Input Methodology 中显式列出"该方法必须包含的关键模块：A, B, C, D"
- **颜色太花**：把所有色彩描述都加 "muted" 或 "soft" 前缀

## 🆚 何时该选 main figure 而不是其他模板

| 你的需求 | 推荐模板 |
|---|---|
| 一张图讲清楚整个方法 | **main figure（本模板）**|
| 方法有 ≥ 3 个清晰阶段，强调"顺序" | [pipeline.md](pipeline.md) |
| 想对比新旧方法 | [comparison.md](comparison.md) |
| 多个阶段都有可视化输出 | [storyboard.md](storyboard.md) |
| 强调"数据怎么流动" | [dataflow.md](dataflow.md) |
| 系统复杂、多组件 | [system-overview.md](system-overview.md) |

## 🔗 相关

- 含判断 / 循环的算法 → [../flowchart/](../flowchart/)
- 投稿用图形摘要（一张图讲完 problem-method-result）→ [../graphical-abstract/](../graphical-abstract/)
