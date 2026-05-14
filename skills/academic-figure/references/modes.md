# 8 种工作模式详细步骤

根据 $ARGUMENTS 选择模式。未指定时根据输入内容自动判断。

---

## 模式 1：plot（绘图）

输入：数据（CSV/表格/JSON）+ 图表类型 + 想表达的核心结论

执行步骤：
1. 确认图表类型（必要时切换到 recommend 模式）
2. 选择合适的调色板（见 `specs.md`）
3. 生成 matplotlib 脚本（带必备 rcParams，参考 `matplotlib.md`）
4. 同时输出 .svg 和 .png 300dpi
5. 给出建议的图标题（参考 `caption.md`）

输出：
- Part 1：Python 脚本（完整可运行）
- Part 2：英文图标题（Title Case 或 Sentence case）
- Part 3：自查报告（按 `specs.md` 12 项检查清单）

---

## 模式 2：recommend（图表类型推荐）

输入：实验数据（最好附 Excel/CSV 原表）+ 想强调的核心结论

执行步骤：
1. 分析数据结构（维度、样本数、是否多次实验）
2. 从 `chart-types.md` 的 19 种类型中匹配 1-2 种最佳方案
3. 按下述格式输出

输出：
1. **推荐方案**：图表名称
2. **核心理由**：结合数据逻辑，解释为什么这张图最符合学术叙事
3. **视觉设计规范**：
   - 坐标轴：X/Y 轴的物理含义及单位
   - 尺度处理：是否需要断裂轴/对数坐标/归一化
   - 统计要素：误差线/拟合曲线/显著性标记
   - 配色与样式：具体配色策略与线型建议

---

## 模式 3：caption（生成图/表标题）

输入：中文图/表描述 + 图/表类型（figure / table）

执行步骤：
1. 提炼核心内容
2. 决定 Title Case 还是 Sentence case（看是名词短语还是句子）
3. 应用去 AI 味词汇过滤（详见 `caption.md`）

输出：英文标题文本（不带前缀编号）

---

## 模式 4：architecture（架构图 prompt）

> ⚠️ 在 architecture 与 flowchart 之间选模式的判断：
> - **强调"系统由什么模块组成"** → 用 architecture（本模式）
> - **强调"按时间/逻辑顺序怎么走"**（含判断、循环、分支）→ 用 flowchart（模式 8）
> 模糊时优先 flowchart——它的形状语义更标准化，AI 生成质量更稳定。

输入：论文摘要 + 方法部分描述（可附图的具体目标：main figure / 对比 / storyboard / 数据流 / 系统总览）

执行步骤：
1. **判断架构图类型**：阅读 `architecture.md`，从 6 类场景中选最贴合的：
   - 模板 1：通用论文架构图（main figure，泛用）
   - 模板 2：算法 pipeline 流程图（≥ 3 阶段方法 — 若强调顺序，转模式 8 flowchart 更合适）
   - 模板 3：A vs B 模块对比图（消融 / 方法对比）
   - 模板 4：多阶段方法分镜（4/6/9 panel grid）
   - 模板 5：数据流向图（强调信息流转）
   - 模板 6：系统总览图（多组件复杂系统）
2. **提取核心元素**：从论文中提取核心模块名、数据流、关键公式、模块间关系
3. **套用 + 填充**：将 `{argument name="X" default="Y"}` 形式的占位符按论文内容替换
4. **加 prompt 工程优化**（参考 `prompt-engineering.md`）：
   - 关键英文标签用双引号围住
   - 末尾加标准否定约束清单
   - 必要时显式控制模块比例、箭头流向、配色

输出：
- Part 1：可直接送入 nano banana / DALL-E / GPT-Image-2 / Imagen 的 prompt 文本（含填好的参数化变量）
- Part 2：模块清单（让用户核对是否漏关键模块）
- Part 3：选用的模板编号 + 建议的图模型 + 调优提示（用户初次生成不理想时怎么改）

---

## 模式 5：polish（图表规范检查）

输入：已有图表（图片或脚本）

执行步骤：
1. 按 `specs.md` 12 项清单逐项检查
2. 指出违反项，给出具体修改建议
3. 必要时重写关键代码片段

输出：
- 通过：`[检测通过，符合学术图表规范]`
- 有问题：分点列出违反项 + 修改方案

---

## 模式 6：design（概念图/示意图设计）

输入：想表达的概念或对比

执行步骤：
1. 先输出 design philosophy（设计哲学，文字版）
2. 列出建议的模块、布局、配色（参考 `prompt-engineering.md` 的词汇表）
3. 给出可执行的 Python 代码 或 用于 AI 图像生成的 prompt

输出：
- Part 1：design philosophy（.md）
- Part 2：实现方案（matplotlib 脚本 或 图像生成 prompt）

---

## 模式 7：abstract（图形摘要 prompt）

适用：Cell / Nature / Elsevier 等期刊要求的 Graphical Abstract（GA），一张图讲完 "问题 → 方法 → 结果"。

输入：论文核心三段——研究问题 / 提出方法 / 关键结果 + 目标期刊（决定比例）

执行步骤：
1. **判断 GA 类型**：阅读 `graphical-abstract.md`，从 5 类场景中选最贴合的：
   - 模板 1：三段式叙事 GA（最经典，问题 → 方法 → 结果）
   - 模板 2：环形 GA（适合闭环系统 / RL / 反馈循环）
   - 模板 3：金字塔 / 层级 GA（理论框架 / 多尺度模型）
   - 模板 4：分子/细胞/生物 GA（生命科学专用）
   - 模板 5：对比型 GA（with vs without 方法）
2. **提取叙事元素**：
   - 问题：1 句话说清 + 1 个视觉比喻
   - 方法：核心模块 / 流程 + 1 个比喻
   - 结果：1 个量化指标 + 1 个视觉比喻
3. **选目标期刊比例**：查 `graphical-abstract.md` § 期刊提交规格速查
4. **套用模板填空**：填 `{argument name="X" default="Y"}` 形式的占位符
5. **应用 prompt 工程优化**（参考 `prompt-engineering.md`）

输出：
- Part 1：完整 prompt 文本（送入图像生成模型）
- Part 2：选用的模板编号 + 目标期刊比例 + 叙事弧线确认
- Part 3：提交清单（按 `graphical-abstract.md` 末尾的"提交前必查"清单）

---

## 模式 8：flowchart（流程图 prompt）

> 流程图与架构图的边界：
> - **强调"按顺序怎么走"、含判断/循环/分支** → 用 flowchart（本模式）
> - **强调"系统由什么模块组成"** → 用 architecture（模式 4）
> 不确定时优先 flowchart，它的 ISO 5807 形状语义更标准化，AI 输出质量更稳。

适用：算法流程、训练循环、决策树、实验步骤、人机交互、多 agent 协同、跨模块协作流程等。

输入：用户描述的流程内容（步骤列表 / 判断条件 / 循环条件 / 分支条件 / 角色或模块 / 期望布局方向）。

执行步骤：
1. **判断流程图类型**：阅读 `flowchart.md`，从 6 类中选最贴合的：
   - 模板 1：线性流程图（≥ 3 个无判断的顺序步骤）
   - 模板 2：分支流程图（含 if-then-else 判断）
   - 模板 3：并行流程图（多支路并行最后汇合）
   - 模板 4：循环流程图（含闭环 / 迭代 / 训练 loop）
   - 模板 5：嵌套 / 层级流程图（某节点展开为子流程）
   - 模板 6：泳道流程图（多角色 / 多模块跨界协作）
2. **应用形状语义**（`flowchart.md` § 二，ISO 5807 标准）：
   - 起止 → 圆角椭圆（oval）
   - 过程 → 圆角矩形
   - 判断 → 菱形（diamond）
   - 数据 → 平行四边形
   - 子流程 → 虚线矩形
3. **应用颜色语义**（`flowchart.md` § 七）：
   - 输入 / 起点：soft 蓝
   - 正确路径 / 成功：soft 绿
   - 错误路径 / 失败：soft 红
   - 判断 / 警告：soft 橙
   - 主流向：solid 实线
   - 反馈 / 循环：颜色不同 + 显式标签（"iterate", "loop back"）
4. **套用 8 段式骨架**（`flowchart.md` § 四）填空
5. **加标准否定约束**（`flowchart.md` § 八）：
   - NO crossing arrows
   - NO unlabeled decision branches
   - NO inconsistent shape semantics
   - NO bidirectional arrows where unidirectional is intended
6. **如适用，建议代码工具协同**（`flowchart.md` § 十）：
   - 若用户要矢量、可编辑、要进 LaTeX：建议 Mermaid / TikZ
   - 若用户要快速试错、要美感：用本 prompt + 图像模型
   - 若用户节点数 > 20：建议 Graphviz/DOT

输出：
- Part 1：完整 prompt 文本（可直接送入图像生成模型）
- Part 2：选用的模板编号 + 形状语义清单 + 颜色映射
- Part 3：可选的代码版本（如适用，给一份 Mermaid 等价代码作为备选）
- Part 4：调优提示（参考 `flowchart.md` § 九调试常见问题）
