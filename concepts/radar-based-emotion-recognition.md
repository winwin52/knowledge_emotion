---
title: 雷达感知的情感识别 (Radar-based Emotion Recognition)
created: 2026-04-14
updated: 2026-04-14
type: concept
tags: [emotion-recognition, physiological-signal, contactless-sensing, multimodal]
sources: [raw/papers/2024详细雷达检测情绪mdpi.md, raw/papers/2025radar-multimodal.md, raw/papers/2025cliniciancomparison-音频-text-radar-multimodaltransformer.md, raw/papers/2021呼吸+雷达详细.md, raw/papers/2016权威validation射频信号detection心跳的accuracy-证明detection情绪的possibility.md, raw/papers/RGB-radar.md, raw/papers/s41598-025-09112-w.md, raw/papers/2025毫米波雷达测心率-挺多的-包括处理算法.md, raw/papers/2025利用雷达技术进行心脏健康-心率.md]
---

# 雷达感知的情感识别 (Radar-based Emotion Recognition)

## 定义
利用雷达传感器非接触式采集人体生理信号(如呼吸、心跳、微动作)来实现情感识别。相比接触式传感器,雷达具有非侵入、无隐私顾虑、可持续监测等优势。

## 雷达类型

### 射频雷达 (RF Radar)
- 2016年研究已验证射频信号检测心跳的准确性
- 通过胸腔运动检测呼吸和心跳
- 毫米波雷达可在衣服外检测

### 毫米波雷达 (mmWave Radar)
- 60GHz / 77GHz频段
- 高分辨率,可检测细微胸腔运动
- 广泛应用于车内驾驶员状态监测

### 调频连续波雷达 (FMCW)
- 可同时估计距离和微多普勒特征
- 适合远程生命体征监测

## 生理信号提取

### 心冲击图 ( BCG ) 原理
心跳时胸腔位置微小变化(~mm级) → 雷达检测微多普勒相位变化

### 呼吸信号
- 呼吸频率: 0.1-0.5Hz
- 呼吸幅度: 胸腔运动约4-12mm

### 心率提取
- 从BCG信号中提取心率
- 需滤波去除呼吸干扰和随机体动

## 在康复中的应用
- 非接触式远程情绪监测
- 患者无需佩戴设备,依从性更高
- 可用于ICU或隔离环境

## 多模态融合
- 雷达 + RGB摄像头 → RGB-radar融合
- 雷达 + 语音 + 文本 → 多模态临床评估
- 临床医生对比: 音频、文本、雷达 + 多模态Transformer

## 挑战
- 多人场景中的目标分离
- 远距离时的信噪比下降
- 与其他模态的时间同步
- 个体差异的标准化

## 相关概念
- [[emotion-recognition]] — 情感识别
- [[physiological-signal-based-emotion-recognition]] — 生理信号情绪识别
- [[multimodal-interaction]] — 多模态交互
- [[contactless-emotion-recognition]] — 非接触式情感识别
- [[heart-rate-variability]] — 心率变异性(HRV)
- [[radar-signal-processing]] — 雷达信号处理
