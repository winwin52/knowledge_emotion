---
title: 情感识别 (Emotion Recognition)
created: 2026-04-14
updated: 2026-04-14
type: concept
tags: [emotion-recognition, affective-computing, computer-vision, nlp, multimodal]
sources: [raw/papers/competition-proj2-motion-rehab-emotion-system-2026.md, raw/papers/2024emotion-recognitionsurvey.md, raw/papers/2023survey-affectivemodel-data集-machine-learningalgorithm-expression-speech-text.md, raw/papers/2025multimodalemotion-recognitioncomprehensivesurvey-technology-challenges与future-directions-给力-detailed-data集等都有.md, raw/papers/2025multimodaldata-eeg-heart-rate-eda-皮肤温度-cnn-lstm-开源data集.md]
---

# 情感识别 (Emotion Recognition)

## 定义
情感识别是情感计算的核心子领域,旨在从多种信息源(面部表情、语音、文本、生理信号等)中自动识别人类情感状态。

## 主要技术路线

### 1. 视觉通道
- **面部表情识别** — FACS (面部动作编码系统), CNN/Transformer模型
- **姿态识别** — 身体动作中的情感线索
- **眼神追踪** — 注视方向、瞳孔变化

### 2. 语音通道
- **语音特征** — 音调、语速、音量、共振峰
- **语音内容** — 语义分析、语气识别
- **语音情感数据库** — IEMOCAP, RAVDESS, EmoDB

### 3. 文本通道
- **文本情感分析** — 情感词典、机器学习、BERT等预训练模型
- **细粒度情感** — 情感极性(正/负)、情感类型(喜/怒/哀/惧/惊/恶)

### 4. 生理信号
- **生理参数** — 心率变异性(HRV)、皮肤电导(EDA)、肌电(EMG)、呼吸
- **优势** — 难以伪装,更真实反映内在情感状态

## 多模态融合
单模态识别存在局限性(遮挡、噪声、个体差异),多模态融合是趋势:
- **早期融合** — 特征层面拼接
- **晚期融合** — 决策层面投票/加权
- **中间融合** — 注意力机制融合

## 在康复场景中的应用
患者在康复训练中的情绪状态直接影响训练效果和依从性。通过实时情感识别:
- 调整训练难度和节奏
- 提供正向激励
- 预防负面情绪累积
- 个性化训练方案

## 相关概念
- [[affective-computing]] — 情感计算
- [[multimodal-interaction]] — 多模态交互
- [[physiological-signal-processing]] — 生理信号处理
- [[rehabilitation-technology]] — 康复技术
