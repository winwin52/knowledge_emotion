# Wiki Schema

## Domain
生物医学工程创新设计竞赛 — 面向运动康复的智能情感交互系统设计

涵盖: 情感计算、人机交互、运动康复、生物医学工程、竞赛备赛

## Conventions
- 文件名: 小写,中划线分隔,无空格 (例如: `emotion-recognition.md`)
- 每个 wiki 页面以 YAML frontmatter 开头
- 使用 `[[wikilinks]]` 进行页面间交叉链接,每个页面至少2个出站链接
- 更新页面时必须更新 `updated` 日期
- 新页面必须添加到 `index.md` 正确板块下
- 每个操作必须追加到 `log.md`

## Frontmatter
```yaml
---
title: 页面标题
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: entity | concept | comparison | query | summary
tags: [from taxonomy below]
sources: [raw/articles/source-name.md]
---
```

## Tag Taxonomy
定义10-20个顶层标签,在使用新标签前先在此添加:

- 竞赛: competition, 生物医学工程, 康复赛道
- 技术: emotion-recognition, hci, physiological-signal, computer-vision, nlp, multimodal
- 领域: rehabilitation, sports-medicine, affective-computing, human-factors
- 研究: literature-review, methodology, experiment, dataset
- 产出: prototype, design-doc, ppt, report
- 记录: journal, reflection, progress
- 人物/组织: person, company, lab, open-source
- 技巧: optimization, fine-tuning, inference, alignment

## Page Thresholds
- **创建页面** — 实体/概念在2+来源中出现 OR 集中于一个核心来源
- **添加到已有页面** — 来源提到已有页面覆盖的内容
- **不创建页面** — 一次性提及、微不足道的细节或超出领域的内容
- **拆分页面** — 超过200行时拆分,用交叉链接
- **归档页面** — 内容完全被取代时移至 `_archive/`,从 index 移除

## Entity Pages
每个重要实体一页,包含:
- 概述/是什么
- 关键事实和日期
- 与其他实体的关系 ([[wikilinks]])
- 来源引用

## Concept Pages
每个概念或主题一页,包含:
- 定义/解释
- 当前认知状态
- 开放问题或争议
- 相关概念 ([[wikilinks]])

## Comparison Pages
并排分析,包含:
- 比较的对象及原因
- 比较维度 (建议表格格式)
- 结论或综合
- 来源

## Update Policy
新信息与现有内容冲突时:
1. 检查日期 — 新来源通常取代旧来源
2. 确有矛盾时,双方都要注明日期和来源
3. 在 frontmatter 标记矛盾: `contradictions: [page-name]`
4. 在 lint 报告中标记供用户审核

## log.md 轮换规则
当 log.md 超过500条条目时,重命名为 `log-YYYY.md`,重新开始。
