# 核心图表规范

---

## 1. 字体与渲染（matplotlib 必备）

任何 Python 绘图脚本必须以下面三行 rcParams 开头：

```python
plt.rcParams['font.family'] = 'sans-serif'
plt.rcParams['font.sans-serif'] = ['Arial', 'DejaVu Sans', 'Liberation Sans']
plt.rcParams['svg.fonttype'] = 'none'   # 保持 SVG 文字为 <text> 节点，不转路径
```

对 PDF 输出还要加：
```python
plt.rcParams['pdf.fonttype'] = 42
plt.rcParams['ps.fonttype'] = 42
```

## 2. 输出格式

- **主输出**：`.svg`（矢量、可编辑、文字可选中）
- **备份**：`.png` 300 dpi（用于初稿预览）
- **永远不直接输出 jpg**（光栅压缩 + 颜色失真）

保存惯例：
```python
fig.savefig('figure.svg', bbox_inches='tight')
fig.savefig('figure.png', dpi=300, bbox_inches='tight')
```

## 3. 配色

- **严格使用淡色系或柔和色调**
- 严禁过于鲜艳饱和的颜色（大红大绿）
- 严禁过于暗淡沉重的颜色
- 利用颜色深浅变化区分模块类型
- 色盲友好：优先 ColorBrewer、Viridis、Cividis 调色板

推荐调色板：
```python
# 类别型
palette_categorical = ['#4C72B0', '#DD8452', '#55A467', '#C44E52', '#8172B3']
# 连续型（顺序）
palette_sequential = 'Blues'
# 连续型（发散）
palette_diverging = 'RdBu_r'
```

## 4. 多面板信息层级

- 三级层次：**overview → deviation → relationship**
- **没有任何两个面板可以回答同一个科学问题**——否则其中一个必须删除
- 子图编号使用 (a)、(b)、(c)，左上角，加粗
- GridSpec 控制比例，避免错位

## 5. 文字规范

- 图中所有文字使用英文
- 必须为关键模块或方程式添加清晰易读的文本标签
- 严禁在图中出现长句子、描述性段落或复杂的公式
- 文字用来标识身份，不解释原理

## 6. 禁忌清单

- ❌ 逼真照片感
- ❌ 杂乱草图线条
- ❌ 难以辨认文本
- ❌ 廉价 3D 阴影瑕疵
- ❌ 在论文正文中使用动图、emoji、卡通元素

---

# 图表规范检查清单（12 项）

提交前自查：

**字体与渲染**
1. rcParams 是否设置了 sans-serif 字体？
2. SVG 文字是否保留为 `<text>` 节点（svg.fonttype='none'）？
3. PDF 输出 fonttype 是否设为 42（避免栅格化）？

**配色**
4. 是否避开了过饱和（大红大绿）和暗淡色调？
5. 是否色盲友好（避免红绿对比 + 仅用色相区分）？

**布局**
6. 多面板时，每个子图是否回答**不同**的科学问题？
7. 子图编号 (a)(b)(c) 是否清晰可见？

**文字**
8. 图中所有文字是否为英文？
9. 是否避免了长句子和复杂公式？
10. 字号是否在所有子图中一致？

**正文引用**
11. 图表是否在正文中被显式引用（如 "见图 3"、"as shown in Figure 3"）？
12. 图标题是否符合 Title Case 或 Sentence case？
