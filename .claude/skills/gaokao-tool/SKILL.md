---
name: gaokao-tool
description: 高考志愿填报工具。输入分数智能推荐冲稳保院校，含位次估算、录取概率。
---

# 高考志愿填报工具

## 用途
搭建一个高考志愿填报辅助网站。用户输入分数 → 自动推荐冲/稳/保三类院校。

## 核心功能

| 功能 | 说明 |
|------|------|
| 🎯 冲稳保推荐 | 优志愿同款算法，分差+概率双维度 |
| 📊 位次估算 | 基于一分一段表实时计算 |
| 🏫 院校库 | 200+面向招生院校含录取线 |
| 📋 专业查询 | 200+专业含霍兰德代码 |

## 使用方式

```
"用 gaokao-tool skill 帮我建一个[省份]高考志愿填报网站"
```

## 技术要点

### 冲稳保算法
```javascript
function analyze(score, school){
  var diff = score - school.minScore;
  if(diff < -25) return null; // 差太多不显示
  if(diff < 0) return {level:'cw', prob: '1-49%'}; // 冲刺
  if(diff < 12) return {level:'wd', prob: '50-79%'}; // 稳妥
  return {level:'bd', prob: '80-99%'}; // 保底
}
```

### 位次估算
基于官方一分一段表的关键节点插值：
```javascript
var rankTable = {700:100, 680:400, 660:1200, 640:3100, ...};
```

### 数据结构
```javascript
{n:"福州大学", c:"福州", t:"理工", i985:false, i211:true,
 sc:{wl:594, ls:592}, enrl:{wl:3410, ls:309}}
```

## 参考链接
- sissc0731.github.io/gaokao-volunteer-tool（福建版示例）
- eeafj.cn（福建省教育考试院官方数据源）
