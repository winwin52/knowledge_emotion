---
title: 非接触式情感识别 (Contactless Emotion Recognition)
created: 2026-04-14
updated: 2026-04-14
type: concept
tags: [emotion-recognition, contactless-sensing, computer-vision, hci]
sources: [raw/papers/2024multimodalcontactlesssurvey.md, raw/papers/2024三星手表-ecg-看影片与walking.md, raw/papers/2025radar-multimodal.md, raw/papers/2024detailedradardetection情绪mdpi.md, raw/papers/RGB-radar.md]
---

# 非接触式情感识别 (Contactless Emotion Recognition)

## 定义
非接触式情感识别(Contactless Emotion Recognition, CER)通过雷达、摄像头、麦克风等非接触设备远距离采集人体信号来实现情感识别,避免了接触式设备的佩戴负担和侵入性问题。

## 非接触式传感技术

### 摄像头 (Vision-based)
- 面部表情识别(webcam)
- 眼神追踪(eye-tracking)
- 姿态估计
- 工具: MediaPipe, OpenCV

### 雷达 (Radar-based)
- 毫米波雷达检测呼吸和心跳
- 微多普勒特征提取
- 非接触式生命体征监测

### 麦克风 (Audio-based)
- 语音情感识别
- 非接触、远距离采集

### 组合方案
- RGB + 雷达融合
- 音频 + 文本 + 雷达多模态

## 优势
- 无需佩戴设备,依从性高
- 适合ICU、隔离环境
- 保护隐私(相比视频监控)
- 适合长期持续监测

## 挑战
- 信噪比随距离下降
- 环境干扰(光照、噪声)
- 多人场景中的目标分离
- 与接触式传感器相比精度较低

## 典型应用
- 车内驾驶员状态监测
- 远程医疗评估
- 智能家居健康监测
- 康复训练中的情绪跟踪

## 相关概念
- [[radar-based-emotion-recognition]] — 雷达情感识别
- [[facial-expression-recognition]] — 面部表情识别
- [[speech-emotion-recognition]] — 语音情感识别
- [[contactless-sensing]] — 非接触式传感
- [[multimodal-interaction]] — 多模态交互
