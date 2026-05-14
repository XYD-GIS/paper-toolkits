# matplotlib 多面板示例模板

```python
import matplotlib.pyplot as plt
from matplotlib.gridspec import GridSpec

# 必备 rcParams
plt.rcParams['font.family'] = 'sans-serif'
plt.rcParams['font.sans-serif'] = ['Arial', 'DejaVu Sans', 'Liberation Sans']
plt.rcParams['svg.fonttype'] = 'none'
plt.rcParams['pdf.fonttype'] = 42

# 调色板
PALETTE = ['#4C72B0', '#DD8452', '#55A467', '#C44E52', '#8172B3']

fig = plt.figure(figsize=(8, 5), constrained_layout=True)
gs = GridSpec(2, 3, figure=fig)

ax_a = fig.add_subplot(gs[0, :2])    # 大图：overview
ax_b = fig.add_subplot(gs[0, 2])     # 小图：deviation
ax_c = fig.add_subplot(gs[1, 0])     # relationship 1
ax_d = fig.add_subplot(gs[1, 1])     # relationship 2
ax_e = fig.add_subplot(gs[1, 2])     # relationship 3

# 子图编号
for ax, label in zip([ax_a, ax_b, ax_c, ax_d, ax_e], 'abcde'):
    ax.text(-0.1, 1.05, f'({label})', transform=ax.transAxes,
            fontsize=12, fontweight='bold', va='bottom', ha='right')

# ...绘图代码...

fig.savefig('figure.svg', bbox_inches='tight')
fig.savefig('figure.png', dpi=300, bbox_inches='tight')
```

---

# 关键决策点

1. **figsize**：单栏期刊约 3.5 × 2.5 英寸；双栏期刊约 7 × 3.5 英寸
2. **constrained_layout=True**：自动调整子图间距，避免标签重叠
3. **GridSpec**：用 `gs[0, :2]` 控制不同子图占据的网格数
4. **子图编号位置**：`transform=ax.transAxes` 用坐标系归一化坐标 [0, 1]，不受数据范围影响
5. **保存顺序**：先 .svg（永久编辑用），后 .png（投稿初稿快速预览）
