# paper-toolkits

中文学术写作工具集。覆盖论文写作、图表生成、参考文献处理、审稿回复 4 件事。

每件事都做了**两份**：一份是 **agent skill**（装到 Claude Code / ChatGPT Codex 等支持 SKILL.md 的工具，用 `/` 命令触发），一份是独立 **prompt 文件**（复制粘贴到 ChatGPT / 豆包 / DeepSeek / Kimi / 任何对话式 AI 都能用）。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/Agent_Skills-4-blue.svg)]()
[![Prompts](https://img.shields.io/badge/Standalone_Prompts-38-orange.svg)]()
[![中文](https://img.shields.io/badge/Language-中文-red.svg)]()

---

## 📂 目录长这样

```
paper-toolkits/
│
├── skills/                    给 Claude Code / ChatGPT Codex 等 agent 用
│   ├── academic-writing/      论文写作（草稿/润色/去AI/检查/分析/审稿/翻译）
│   ├── academic-figure/       图表（推荐/绘图/架构图/流程图/图形摘要/caption）
│   ├── academic-citation/     参考文献（格式/检查/BibTeX/转换/DOI/正文核对）
│   └── academic-response/     审稿回复（拆解/起草/润色/审查/cover letter）
│
└── prompts/                   给任何 AI 用，复制粘贴即可
    ├── writing/               7 个文件
    ├── figure/                21 个文件
    │   ├── chart-recommendation.md
    │   ├── flowchart/         流程图 6 种（线性/分支/并行/循环/嵌套/泳道）
    │   ├── architecture/      架构图 6 种（main/pipeline/对比/分镜/数据流/总览）
    │   ├── graphical-abstract/ 图形摘要 5 种（叙事/环形/金字塔/生物/对比）
    │   └── caption/           图标题 + 表标题
    ├── citation/              6 个文件
    └── response/              5 个文件
```

---

## 🔧 用法一：装成 agent skill

支持任何能加载 `SKILL.md` 的 agent，包括：

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) — 路径 `~/.claude/skills/`
- [ChatGPT Codex](https://github.com/openai/codex) — 路径 `~/.codex/skills/`
- 其他遵循 SKILL.md 规范的 agent

### 装到 Claude Code

**Windows PowerShell**：

```powershell
git clone https://github.com/XYD-GIS/paper-toolkits.git
Copy-Item "paper-toolkits/skills/academic-*" "$env:USERPROFILE\.claude\skills\" -Recurse -Force
```

**macOS / Linux**：

```bash
git clone https://github.com/XYD-GIS/paper-toolkits.git
mkdir -p ~/.claude/skills
cp -R paper-toolkits/skills/academic-* ~/.claude/skills/
```

### 装到 ChatGPT Codex

**Windows PowerShell**：

```powershell
git clone https://github.com/XYD-GIS/paper-toolkits.git
Copy-Item "paper-toolkits/skills/academic-*" "$env:USERPROFILE\.codex\skills\" -Recurse -Force
```

**macOS / Linux**：

```bash
git clone https://github.com/XYD-GIS/paper-toolkits.git
mkdir -p ~/.codex/skills
cp -R paper-toolkits/skills/academic-* ~/.codex/skills/
```

### 验证

重启 agent。在对话里输入 `/`，会看到 4 个新命令：

```
/academic-writing
/academic-figure
/academic-citation
/academic-response
```

用的时候直接说要做什么，比如：

```
/academic-writing draft

把下面这段笔记重写成正式段落：
[粘贴你的草稿]
```

```
/academic-figure flowchart

画训练循环的流程图：前向传播 → 损失 → 反向传播 → 更新参数 → 收敛判断 → 否则回到第一步
```

---

## 📋 用法二：复制 prompt 到任何 AI

如果不想装任何 agent 工具，直接打开 `prompts/` 里对应主题的文件，比如想去 AI 味就打开 [prompts/writing/03-deai.md](prompts/writing/03-deai.md)。

每个文件都长这样：

- 写明什么场景用
- 给出**预期输出的样子**（图类带 ASCII 预览，让你提前知道生成的图大概什么样）
- 一段可整段复制的完整 prompt
- 真实输入输出对照
- 调优提示
- 指向相关的其他 prompt

直接把 prompt 复制到 ChatGPT、Claude.ai、豆包、DeepSeek、Kimi、文心一言、Gemini——任何对话式 AI 都能用。

---

## 📊 4 个主题各自做了什么

| 主题 | 触发场景 | 模式（参数）|
|---|---|---|
| **writing** | 笔记零散想写成段落；段落想润色；像 AI 写的想去 AI 味；终稿挑致命错；数据想写成结果段；模拟审稿挑刺；中文段落要译成英文 | draft / polish / deai / check / analyze / review / translate |
| **figure** | 不知道用什么图；要画流程图 / 架构图 / 图形摘要；要写英文 figure caption / table caption；现有图不符合规范要 polish | plot / recommend / caption / architecture / flowchart / abstract / polish / design |
| **citation** | 参考文献格式混乱要统一；终稿想挑错；要生成 BibTeX；想转 RIS / EndNote；要验 DOI；要核对正文引用对得上文献列表 | format / check / bibtex / convert / verify / inline |
| **response** | 收到审稿意见要拆解分类；起草 point-by-point；既有草稿要润色；投稿前真实性审查；只起草 cover letter | classify / draft / polish / audit / cover |

---

## ✨ 有几处细节值得说一下

**figure 类 prompt 有 ASCII 预览图**。送给 AI 之前能先看到大概长什么样，避免反复重试。例如循环流程图的预览：

```
        Initialize Param  ← 蓝色椭圆
              ↓
         Forward Pass    ← 灰色矩形
              ↓
         Compute Loss
              ↓
              ...
              ↓
          Converged?     ← 橙色菱形
           yes ↓  ╲ no
               ↓   ╲
         Final Model    ╲── 红色粗弧线，反馈回 Forward Pass
```

**所有占位符用 `{}` 标记**。比如 `{阶段数量}`、`{论文标题}`，眼睛一扫就知道哪里要填，不用读完整段才发现。

**Skill 拆成入口 + references 子文件**。SKILL.md 只 100 行左右，agent 按需读 references。避免一上来就吃几千 token 的上下文。

**writing 主题内置 12 条具体写作准则**。比如禁用"明显差异 / 重要意义"等模糊词、"因此"前后必须真因果、方法命名必须统一、改进要落到具体指标、朗读卡顿处即不通顺处。每个 prompt 都嵌了这 12 条，让 AI 输出自动按准则自查。

---

## 🙏 致谢

本仓库借鉴了几个开源项目。

**直接借鉴**：

| 项目 | 作者 | 借鉴了什么 |
|---|---|---|
| [awesome-ai-research-writing](https://github.com/Leey21/awesome-ai-research-writing) | [@Leey21](https://github.com/Leey21) | writing 主题的模式划分（中转英、润色、去 AI、缩写扩写、Reviewer 审视）|
| [nature-skills](https://github.com/Yuan1z0825/nature-skills) | [@Yuan1z0825](https://github.com/Yuan1z0825) | `SKILL.md + references/` 的多文件结构；nature-figure / polishing / citation / response 的模块拆分思路 |
| [awesome-gpt-image-2-API-and-Prompts](https://github.com/EvoLinkAI/awesome-gpt-image-2-API-and-Prompts) | [@EvoLinkAI](https://github.com/EvoLinkAI) | figure 主题的 prompt 工程套路——参数化语法 `{argument name="X" default="Y"}`、空间定位词汇、构图结构语、否定约束清单 |

**间接参考**：

- [Anthropic 官方 skills](https://github.com/anthropics/skills) — SKILL.md 的写法规范
- [zechenzhangAGI/AI-research-SKILLs](https://github.com/zechenzhangAGI/AI-research-SKILLs) — ML 论文写作 skill
- [numman-ali/openskills](https://github.com/numman-ali/openskills) — OpenSkills 装载机制
- [ChenLiu-1996/figures4papers](https://github.com/ChenLiu-1996/figures4papers) — matplotlib 论文级图表脚本
- [Leey21/arxiv-translator](https://github.com/Leey21/arxiv-translator) — arXiv 翻译 skill

**期刊与会议规范**参考：GB/T 7714-2015、APA 7、IEEE、Nature Portfolio、Cell Press、Elsevier Graphical Abstract 规范、ISO 5807。

---

## 🤝 欢迎贡献

提 Issue 或 PR 都行。

新增 skill：放 `skills/academic-<topic>/` 下，含 `SKILL.md`（≤ 120 行入口）+ `references/`。

新增 prompt：放 `prompts/<topic>/` 下，一个 `.md` 文件，按现有文件的样子写——开头说何时用 + 预期输出（图类带 ASCII 预览），中间是可整段复制的 prompt，末尾给调优提示和相关 prompt。

---

## 📜 License

MIT。详见 [LICENSE](LICENSE)。

---

⭐ 用得上的话点个 Star，让更多人看到。
