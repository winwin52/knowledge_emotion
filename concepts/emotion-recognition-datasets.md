---
title: 情感识别数据集 (Emotion Recognition Datasets)
created: 2026-04-14
updated: 2026-04-14
type: concept
tags: [emotion-recognition, dataset, experiment]
sources: [raw/papers/2024emotion-recognitionsurvey.md, raw/papers/2025多模态数据（脑电，心率，皮肤电，皮肤温度）+CNN+LSTM+开源数据集.md, raw/papers/2023survey-affectivemodel-data集-machine-learningalgorithm-expression-speech-text.md, raw/papers/2025multimodalemotion-recognitioncomprehensivesurvey-technology-challenges与future-directions-给力-detailed-data集等都有.md, raw/papers/2011DEEP-一个利用生理信号进行情绪分析的数据库.md]
---

# 情感识别数据集 (Emotion Recognition Datasets)

## 定义
情感识别数据集是经过标注的音频、视频、生理信号等样本集合,用于训练和评估情感识别模型。

## 常用数据集

### 视觉数据集
| 数据集 | 样本数 | 模态 | 备注 |
|--------|--------|------|------|
| CK+ | 593序列 | 图像/视频 | 8种基本表情 |
| AffectNet | 100万+ | 图像 | 11种表情+效价/唤醒度 |
| FER2013 | 35887 | 图像 | 7种基本表情 |
| RAF-DB | 30000+ | 图像 | 7种基本表情+12种复合表情 |
| Affect-In-Wild | 100万+ | 视频 | 自然场景 |

### 语音数据集
| 数据集 | 样本数 | 语言 | 模态 |
|--------|--------|------|------|
| IEMOCAP | 10000段 | 英文 | 音频+视频+文本 |
| RAVDESS | 7356段 | 英文 | 音频+视频 |
| EmoDB | 535段 | 德语 | 音频 |
| CREMA-D | 7442段 | 英文 | 音频+视频 |

### 生理信号数据集
| 数据集 | 样本数 | 信号类型 | 备注 |
|--------|--------|----------|------|
| **DEAP** | 32被试,1280 trials | EEG, GSR, EMG, ECG, 呼吸, 皮肤温度 | 音乐视频诱发;效价/唤醒度/喜好度/支配度标注;2012年IEEE情感计算顶刊 |
| MAHNOB-HCI | 27被试 | EEG, ECG, GSR, 眼动 | 视频诱发 |
| DREAMER | 23被试 | EEG, ECG | 视频诱发 |
| AMIGOS | 40被试 | EEG, ECG, GSR | 视频+孤独评估 |

### 多模态数据集
- **CMU-MOSI** — 语音+文字+视频
- **MELD** — 对话多模态
- **MUGE** — 中文多模态

## 数据集构建要素
- 诱发材料(视频、图片、音乐、任务)
- 标注方案(离散类别/连续维度)
- 被试信息(年龄、性别、文化背景)
- 实验协议(实验室/自然场景)

## 挑战
- 数据规模vs隐私
- 标注主观性
- 跨文化泛化
- 自然vsposed表情差异
- 康复专用数据集稀缺

## 相关概念
- [[emotion-recognition]] — 情感识别
- [[multimodal-interaction]] — 多模态交互
- [[experiment-design]] — 实验设计
- [[deep-learning]] — 深度学习
