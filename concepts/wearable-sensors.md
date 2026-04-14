---
title: 可穿戴传感器 (Wearable Sensors)
created: 2026-04-14
updated: 2026-04-14
type: concept
tags: [physiological-signal, wearable, emotion-recognition, rehabilitation]
sources: [raw/papers/2025hand-rehabilitation-remote-camera-microphone-wearablephysiological-parameters-vrgaming.md, raw/papers/2025multimodaldata-eeg-heart-rate-eda-皮肤温度-cnn-lstm-开源data集.md, raw/papers/2024三星手表-ecg-看影片与walking.md, raw/papers/2023树莓派-vision-edasweat-glandsensor.md]
---

# 可穿戴传感器 (Wearable Sensors)

## 定义
可穿戴传感器是集成于衣物、腕表、贴片等便携设备中的传感装置,用于实时采集人体生理参数。

## 常见可穿戴传感器

### 生理信号传感器
| 类型 | 信号 | 采集位置 |
|------|------|----------|
| EEG | 脑电 | 头皮/耳后 |
| ECG | 心电 | 胸部/手腕 |
| GSR/EDA | 皮肤电导 | 手指/手掌 |
| ST | 皮肤温度 | 手腕/手臂 |
| EMG | 肌电 | 肌肉表面 |
| PPG | 光电容积 | 耳垂/手腕 |

### 运动传感器
| 类型 | 用途 |
|------|------|
| IMU | 加速度、角速度、姿态 |
| 陀螺仪 | 旋转角速度 |
| 磁力计 | 方向感知 |

## 在情绪识别中的应用

### 三星手表 + ECG
- 佩戴手表观看影片和步行时采集心电
- 研究心率变异性(HRV)与情绪的关系

### 耳后脑电采集
- 轻便隐蔽的EEG采集方案
- 适合日常情绪监测

### 树莓派 + 视觉 + EDA
- 低成本开源硬件方案
- 皮肤电 + 计算机视觉融合

## 优势与局限
- **优势**: 连续监测、便携、适合日常场景
- **局限**: 佩戴舒适度、电池续航、运动伪影、个体差异

## 康复场景应用
- 远程康复中的生理参数监测
- 虚拟现实游戏中的情绪反馈
- 实时训练难度调整

## 相关概念
- [[physiological-signal-based-emotion-recognition]] — 生理信号情绪识别
- [[emotion-recognition]] — 情感识别
- [[rehabilitation]] — 康复技术
- [[wearable-ecg]] — 可穿戴心电
- [[wearable-eeg]] — 可穿戴脑电
