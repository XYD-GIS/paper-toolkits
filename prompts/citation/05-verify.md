# DOI 验证 · Verify

> **何时用**：投稿前确认每条引用的 DOI 是否真实存在、元数据是否匹配
> **预期输出**：验证通过 ✓ / 失败 ✗（带修正建议）

⚠️ 单纯让 AI 验证 DOI **不靠谱**（AI 可能编造）。**推荐用 Crossref API 自动化验证**。下方 prompt 仅适合快速人工核对少量 DOI。

---

## 📋 完整 Prompt（适合少量 DOI 人工核对）

```text
# 角色
你是熟悉 Crossref / DataCite / PubMed 等学术元数据库的资深编辑。

# 任务
对我提供的【DOI 列表 + 对应的引用信息】，**根据你认知中已发表的论文**，核对每条 DOI 是否匹配引用信息。

# 检查内容
对每条 DOI：
1. **格式合法性**：DOI 是否符合 `10.xxxx/xxxx` 格式？是否含非法字符？
2. **DOI 真实性**（基于你的认知）：这个 DOI 是否对应一个真实发表的论文？
3. **元数据一致性**：标题、作者、年份、期刊、卷期是否与你认知中该 DOI 对应的论文一致？

# 输出格式

| DOI | 状态 | 详细说明 |
|---|---|---|
| 10.1038/s41467-024-12345-6 | ✓ | 与引用信息一致 |
| 10.1109/INVALID-FORMAT | ✗ | 格式错误：缺少分隔符斜杠 |
| 10.5555/3666999.3667174 | ⚠️ | 我无法确认该 DOI 是否存在，建议手动到 https://doi.org/{DOI} 验证 |

# 重要约束
- ⚠️ 你的训练数据有截止日期，对于较新的论文（最近 1-2 年内）你可能不熟悉，**这种情况标 ⚠️ 而不是 ✗**
- ⚠️ **绝不编造**论文信息。如果你不确定，明确说"无法确认"
- ⚠️ 建议用户对所有 ⚠️ 条目手动到 `https://doi.org/{DOI}` 验证

# 输入

## DOI + 引用信息列表
[在此处粘贴，每行格式：DOI + 标题 + 作者 + 年份]
例：
10.1038/s41467-024-12345-6 | A Novel Framework for Spatial Analysis | Zhang et al. | 2024
10.1109/CVPR52729.2023.01234 | Deep Vision Method | He et al. | 2023
```

---

## 🛠 使用方法

1. 复制 prompt
2. 把 DOI + 引用信息按格式粘到最后
3. 发送

## ⚙️ 推荐自动化（更可靠）

让 AI 验证 DOI 有不确定性，**强烈建议用脚本调 Crossref API**：

### Bash 一键验证

```bash
#!/bin/bash
# verify_dois.sh
while IFS= read -r doi; do
  response=$(curl -s -o /dev/null -w "%{http_code}" "https://api.crossref.org/works/$doi")
  if [ "$response" == "200" ]; then
    title=$(curl -s "https://api.crossref.org/works/$doi" | jq -r '.message.title[0]')
    echo "✓ $doi → $title"
  else
    echo "✗ $doi → HTTP $response (NOT FOUND)"
  fi
done < dois.txt
```

### Python 批量验证

```python
import requests
import json

with open('dois.txt') as f:
    dois = [line.strip() for line in f if line.strip()]

for doi in dois:
    r = requests.get(f"https://api.crossref.org/works/{doi}")
    if r.status_code == 200:
        data = r.json()['message']
        title = data.get('title', ['(no title)'])[0]
        year = data.get('published-print', {}).get('date-parts', [[None]])[0][0] or \
               data.get('published-online', {}).get('date-parts', [[None]])[0][0]
        print(f"✓ {doi} | {title} ({year})")
    else:
        print(f"✗ {doi} | HTTP {r.status_code}")
```

### 浏览器手动核验（最稳）

复制 DOI 到浏览器：`https://doi.org/10.1038/s41467-024-12345-6`

- 跳转成功且是你引用的论文 → ✓
- 跳转到 404 / 错误页 → ✗
- 跳转到其它论文 → ⚠️ DOI 错误，需要修正

## 💡 调优提示

- **DOI 数量很多**：用 Python/bash 脚本，不要用 AI
- **要核验非 DOI 标识符**：PMID 用 PubMed API，arXiv ID 用 arXiv API
- **DOI 格式合法但 Crossref 404**：可能是 DataCite 注册的（数据集 / 软件），改用 `https://api.datacite.org/dois/{DOI}`

## 🔗 相关

- 生成 BibTeX（含 DOI）→ [03-bibtex.md](03-bibtex.md)
- 检查格式整体问题 → [02-check.md](02-check.md)
