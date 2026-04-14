---
title: 语音情感识别 (Speech Emotion Recognition)
created: 2026-04-14
updated: 2026-04-14
type: concept
tags: [emotion-recognition, nlp, hci, multimodal]
sources: [raw/papers/2024emotion-recognitionsurvey.md, raw/papers/2023survey-affectivemodel-data集-machine-learningalgorithm-expression-speech-text.md, raw/papers/2024multimodalcontactlesssurvey.md]
---

# 语音情感识别 (Speech Emotion Recognition)

## 定义
语音情感识别(SER)通过分析语音信号中的声学特征来识别说话者的情感状态。

## 声学特征

### 韵律特征 (Prosodic Features)
- **基频(F0)** — 反映音高变化
- **语速** — 音节/秒
- **音量/能量** — 语音强度
- **共振峰** — 声道共鸣特性(F1, F2, F3)

### 频谱特征
- MFCC (梅尔频率倒谱系数)
- 谱质心、谱熵、谱通量

### 时域特征
- 过零率
- 短时能量

## 典型数据集
- IEMOCAP (Interactive Emotional Dyadic Motion Capture)
- RAVDESS (Ryerson Audio-Visual Database of Emotional Speech and Song)
- EmoDB (Berlin Emotional Database)
- CREMA-D (Crowd-sourced Emotional Multimodal Actors Dataset)

## 方法

### 传统机器学习
- GMM (高斯混合模型)
- SVM
- HMM (隐马尔可夫模型)

### 深度学习
- CNN (1D-CNN处理时序语音)
- LSTM/GRU (时序建模)
- Wav2Vec + Transformer
- 多任务学习

## 挑战
- 跨语言/跨说话者泛化
- 噪声环境鲁棒性
- 自然对话中的情感识别
- 与文本内容的解耦

## 在康复中的应用
- 临床医生远程评估患者情绪
- 多模态transformer融合音频+文本+雷达信号

## 相关概念
- [[emotion-recognition]] — 情感识别
- [[multimodal-interaction]] — 多模态交互
- [[nlp]] — 自然语言处理
- [[hci]] — 人机交互
- [[deep-learning]] — 深度学习
