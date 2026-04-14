---
title: 脑电信号处理 (EEG Signal Processing)
created: 2026-04-14
updated: 2026-04-14
type: concept
tags: [physiological-signal, emotion-recognition, methodology, rehabilitation]
sources: [raw/papers/2023耳后脑电采集+模型分析.md, raw/papers/2025多模态数据（脑电，心率，皮肤电，皮肤温度）+CNN+LSTM+开源数据集.md, raw/papers/2023survey-sensor-preprocessing-algorithm.md]
---

# 脑电信号处理 (EEG Signal Processing)

## 定义
脑电信号处理是采集、预处理、特征提取和分类脑电信号(EEG)的技术,是实现脑机接口和生理信号情感识别的核心环节。

## EEG频段

| 频段 | 频率范围 | 与情感关联 |
|------|----------|------------|
| δ | 0.5-4 Hz | 深度睡眠、放松 |
| θ | 4-8 Hz | 浅睡眠、冥想、愉悦 |
| α | 8-13 Hz | 闭眼放松、平静 |
| β | 13-30 Hz | 警觉、主动思考、焦虑 |
| γ | 30-100 Hz | 认知加工、高阶情感 |

## 采集方式

### 实验室高密度采集
- 32/64/128导联标准10-20系统
- 高空间分辨率
- 需要导电凝胶

### 消费级便携采集
- 耳后EEG(如ear-EEG)
- 干电极技术
- 适合日常监测

## 预处理流程

### 滤波
- 带通滤波(0.5-50Hz)
- 陷波滤波(50/60Hz工频)
- 去基线漂移

### 伪迹去除
- 眼动伪迹(EOG)去除
- 肌电伪迹(EMG)去除
- 运动伪迹去除
- 独立成分分析(ICA)

### 分段与重参考
- 按刺激材料分段
- 平均参考/乳突参考

## 特征提取

### 时域
- ERP (事件相关电位)
- 幅值、潜伏期

### 频域
- 功率谱密度(PSD)
- 频段功率比(θ/β, α/β)

### 空域
- 共空间模式(CSP)
- LORETA

## 在情感识别中的应用
- 额叶α不对称性 → 情绪效价(正/负)
- θ频段功率 → 情感唤醒度
- γ频段活动 → 认知情感加工

## 相关概念
- [[physiological-signal-based-emotion-recognition]] — 生理信号情绪识别
- [[emotion-recognition]] — 情感识别
- [[deep-learning]] — 深度学习
- [[signal-processing]] — 信号处理
