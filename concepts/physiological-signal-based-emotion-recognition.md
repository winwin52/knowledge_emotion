---
title: 生理信号情绪识别 (Physiological Signal Emotion Recognition)
created: 2026-04-14
updated: 2026-04-14
type: concept
tags: [emotion-recognition, physiological-signal, affective-computing, multimodal, rehabilitation]
sources: [raw/papers/2025multimodaldata-eeg-heart-rate-eda-皮肤温度-cnn-lstm-开源data集.md, raw/papers/2023survey-sensor-preprocessing-algorithm.md, raw/papers/2023耳后eeg采集+模型分析.md, raw/papers/基于生理信号emotion-recognition的hand-rehabilitation人机交互设备research_huang-xiansheng.md, raw/papers/2025hand-rehabilitation-remote-camera-microphone-wearablephysiological-parameters-vrgaming.md, raw/papers/2011DEEP-一个利用生理信号进行情绪分析的数据库.md]
---

# 生理信号情绪识别 (Physiological Signal Emotion Recognition)

## 定义
通过采集和分析人体生理信号来识别情感状态的技术。与表情、语音等行为信号不同，生理信号难以自主伪装，因此能更真实地反映内心情感状态。

## 主要生理信号模态

### 1. 脑电信号 (EEG)
- 采集方式: 头皮电极、耳后电极
- 频段特征: δ(0.5-4Hz), θ(4-8Hz), α(8-13Hz), β(13-30Hz), γ(30-100Hz)
- 优势: 直接反映大脑皮层活动,时间分辨率高
- 典型设备: 32/64/128导联EEG采集系统,耳后便携式EEG

### 2. 心电信号 (ECG) / 心率变异性 (HRV)
- 采集方式: 胸带、手表心电传感器、雷达非接触式
- 关键指标: HRV、RR间期、心率
- 优势: 可穿戴设备兼容性好,三星手表等已集成

### 3. 皮肤电活动 (EDA/GSR)
- 采集方式: 皮肤表面电极
- 原理: 情绪激动时汗腺分泌增加,皮肤电导率上升
- 优势: 设备简单,成本低

### 4. 皮肤温度
- 末梢皮肤温度随情绪变化
- 常与其他生理信号多模态融合

### 5. 呼吸信号
- 呼吸频率、深度、节律
- 可通过胸带或雷达非接触式采集

## 典型算法框架

### CNN + LSTM 混合模型
- CNN用于空间特征提取(各通道生理信号)
- LSTM用于时序建模
- 软投票集成进一步提升准确率至96.21%(7类情绪)

### 预处理流程
1. 信号滤波(去基线漂移、去工频干扰)
2. 降采样(统一采样率)
3. 分段(按刺激材料划分)
4. 标准化(Z-score)

## 在康复场景中的应用
- 手部康复训练中的情绪监测
- 虚拟现实康复游戏中的情感反馈
- 远程康复中的实时情绪跟踪
- 康复机器人的人机情感交互

## 相关概念
- [[emotion-recognition]] — 情感识别
- [[affective-computing]] — 情感计算
- [[multimodal-interaction]] — 多模态交互
- [[sports-rehabilitation]] — 运动康复
- [[virtual-rehabilitation]] — 虚拟康复
- [[wearable-sensors]] — 可穿戴传感器
- [[heart-rate-variability]] — 心率变异性(HRV)
