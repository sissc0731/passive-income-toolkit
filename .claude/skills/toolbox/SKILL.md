---
name: toolbox
description: 在线工具箱。纯前端15+实用工具，飞书妙搭免费托管，SEO流量入口。
---

# 在线工具箱

## 用途
搭建一个多功能在线工具箱网站，15+实用工具一站式服务，飞书妙搭免费托管。

## 工具清单

| 分类 | 工具 |
|------|------|
| 📋 文本编码 | JSON格式化、Base64、URL编码、HTML实体 |
| 🔐 加密生成 | MD5/SHA哈希、UUID、二维码 |
| 🔍 开发工具 | 正则测试、文本差异对比 |
| ⏰ 时间换算 | 时间戳、单位换算 |
| 🎨 图片颜色 | 图片压缩/格式转换、颜色选择器 |
| 🌐 网络 | IP查询、手机归属地 |

## 部署方式

用 lark-apps skill 部署到飞书妙搭：
```bash
lark-cli apps +create --name "在线工具箱" --app-type HTML
lark-cli apps +html-publish --app-id <id> --path ./toolbox/
lark-cli apps +access-scope-set --app-id <id> --scope public --require-login=false
```

## 盈利方式
1. Google AdSense 广告
2. 支付宝/微信赞赏码
3. 电子书/工具合集付费

## 参考链接
- xcn6au7vv0e4.aiforce.cloud/app/app_4kcptf9pby7e4（飞书妙搭版）
