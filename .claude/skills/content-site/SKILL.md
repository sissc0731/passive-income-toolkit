---
name: content-site
description: 自动生成内容网站，GitHub Pages + Actions 每日更新，零成本 SEO 流量。
---

# 自动内容站生成器

## 用途
搭建一个每天自动更新的内容网站，托管在 GitHub Pages（免费），用 GitHub Actions 每天生成新文章。

## 架构
```
GitHub Actions (每天触发)
    ↓
node scripts/generate.js (生成文章)
    ↓
GitHub Pages (自动部署)
    ↓
搜索引擎收录 → 流量 → 广告收入
```

## 使用方式

```
"用 content-site 帮我建一个 [行业] 网站，每天自动更新"
```

### 示例
- "建一个家常菜谱网站"
- "建一个宠物养护知识站"
- "建一个手机使用技巧站"

## 技术要点

1. 创建 GitHub 仓库 → 启用 Pages
2. 创建 `scripts/generate.js` 含内容池
3. 创建 `.github/workflows/daily.yml` 定时触发
4. 创建 `feed.json` 存储文章索引
5. 创建 `index.html` 展示文章列表

### 内容池格式
```javascript
const pool = [
  {t:'标题', tag:'标签', d:'描述内容', img:'建议配图'},
  // 每组3条，8组=24天不重复
];
```

### Workflow 模板
```yaml
name: Daily
on:
  schedule: [{cron: '30 6 * * *'}]
  workflow_dispatch:
permissions: {contents: write, pages: write}
jobs:
  update:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: {node-version: '20'}
      - run: node scripts/generate.js
      - run: |
          git config user.name "Bot"
          git config user.email "bot@x.com"
          git add feed.json posts/
          git diff --staged --quiet || (git commit -m "Daily: $(date +%Y-%m-%d)" && git push)
```

## 盈利方式
- Google AdSense（满$100起付）
- 联盟营销链接
- 微信/支付宝赞赏码

## 参考项目
- sissc0731.github.io/easy-home-recipes（菜谱）
- sissc0731.github.io/pet-care-guide（宠物）
- sissc0731.github.io/slim-down-guide（减肥）
