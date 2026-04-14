---
title: 情感识别技术对比 (Emotion Recognition Technology Comparison)
created: 2026-04-14
updated: 2026-04-14
type: comparison
tags: [emotion-recognition, methodology, dataset, comparison]
sources: [raw/papers/2024emotion-recognitionsurvey.md, raw/papers/2023survey-sensor-preprocessing-algorithm.md, raw/papers/2024multimodalcontactlesssurvey.md, raw/papers/2025multimodalemotion-recognitioncomprehensivesurvey-technology-challenges与future-directions-给力-detailed-data集等都有.md]
---

# 情感识别技术对比 (Emotion Recognition Technology Comparison)

## 模态对比

| 模态 | 优势 | 局限 | 典型应用 |
|------|------|------|----------|
| 面部表情 |直观、非侵入、成熟 |遮挡、个体差异、自发vsposed |人机交互、远程康复 |
| 语音 |远距离、自然语言 |噪声敏感、跨语言 |客服、临床评估 |
| 文本 |内容丰富、易获取 |隐含情感难检测 |社交媒体分析 |
| EEG |直接反映大脑活动 |设备复杂、佩戴不便 |临床诊断、BCI |
| ECG/HRV |可穿戴集成 |运动伪影 |健康监测 |
| EDA |设备简单 |个体差异大 |测谎、情绪唤起 |
| 雷达 |非接触、隐私保护 |精度有限 |远程监测 |
| IMU |成本低、功耗小 |间接反映情感 |日常监测 |

## 传感器类型对比

### 接触式 vs 非接触式

| 维度 | 接触式 | 非接触式 |
|------|--------|----------|
| 精度 | 较高 | 相对较低 |
| 舒适度 | 佩戴负担 | 无需佩戴 |
| 连续监测 | 困难(设备限制) | 容易 |
| 隐私 | 较少顾虑 | 需考虑隐私 |
| 成本 | 传感器成本高 | 设备成本多样 |
| 适用场景 | 临床、实验室 | 日常、远程 |

## 融合策略对比

| 策略 | 层次 | 优势 | 挑战 |
|------|------|------|------|
| 早期融合 | 特征层 | 可学习跨模态关联 | 需特征对齐 |
| 晚期融合 | 决策层 | 模态独立灵活 | 丢失交互信息 |
| 中期融合 | 中间层 | 平衡两者 | 架构复杂 |

## 数据集对比

| 类型 | 规模 | 模态 | 代表数据集 |
|------|------|------|----------|
| 视觉 | 大规模 | 图像/视频 | AffectNet, FER2013 |
| 语音 | 中等 | 音频 | IEMOCAP, RAVDESS |
| 生理 | 小规模 | EEG/ECG/GSR | DEAP, MAHNOB-HCI |
| 多模态 | 中等 | 混合 | CMU-MOSI, MELD |

## 在康复领域的选型建议

| 场景 | 推荐方案 |
|------|----------|
| 手部康复(VR游戏) | 面部表情(CNN) + 生理信号(ECG/EDA) |
| 远程康复 | 摄像头表情 + 雷达心率 |
| 日常监测 | 可穿戴(IMU + PPG) |
| 临床评估 | 多模态Transformer |

## 相关概念
- [[emotion-recognition]] — 情感识别
- [[multimodal-fusion]] — 多模态融合
- [[contactless-emotion-recognition]] — 非接触式情感识别
- [[physiological-signal-based-emotion-recognition]] — 生理信号情绪识别
- [[emotion-recognition-datasets]] — 情感识别数据集
