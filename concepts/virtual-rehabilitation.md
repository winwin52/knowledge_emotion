---
title: 虚拟康复 (Virtual Rehabilitation)
created: 2026-04-14
updated: 2026-04-14
type: concept
tags: [rehabilitation, virtual-reality, affective-computing, emotion-recognition, sports-medicine]
sources: [raw/papers/2026affective计算driven的虚拟rehabilitation-系统性survey.md, raw/papers/2025hand-rehabilitation-remote-camera-microphone-wearablephysiological-parameters-vrgaming.md, raw/papers/2024facialexpression-remoterehabilitation.md]
---

# 虚拟康复 (Virtual Rehabilitation)

## 定义
虚拟康复(Virtual Rehabilitation, VRe)是一种基于虚拟现实(VR)技术的康复训练方法,通过虚拟环境优化患者身体功能、减轻残疾程度,并增强与环境的互动能力。

## VRe 分类

### 按沉浸程度
- **非沉浸式** — 桌面VR,通过屏幕和摄像头交互(如T-Rehab系统)
- **半沉浸式** — 投影或大屏幕+交互设备
- **完全沉浸式** — 头戴式VR(HMD),完全沉浸虚拟环境

### 按康复目标
- 肢体运动康复(手部、上下肢)
- 认知康复
- 心理康复(PTSD、焦虑、ASD社交认知)
- 慢性疼痛管理

## 情感计算在VRe中的作用

### 情感-循环闭环 (Emotion-in-the-loop)
VRe的治疗"剂量"受患者即时情绪(如投入度、挫败感、焦虑)强烈影响:
- 高投入度 → 康复效果提升
- 挫败感累积 → 训练效果下降,依从性降低

### AdVRe框架 (Affective-driven Virtual Rehabilitation)
六层架构:
1. 情感建模与数据集
2. 信号采集(生理+行为+交互)
3. 多模态融合算法
4. 情感识别与适应
5. 内容自适应调整
6. 用户体验优化

## 典型系统: T-Rehab
- 半沉浸式远程康复系统
- 集成面部表情分析(MediaPipe)
- 非接触式心率监测
- VR游戏+摄像头手部追踪
- 情感状态监测 → 游戏难度自适应

## 挑战
- 情绪识别在临床变异性下的不稳定性
- 缺乏康复专用数据集
- 实时处理的计算约束
- 数据隐私问题

## 相关概念
- [[affective-computing]] — 情感计算
- [[emotion-recognition]] — 情感识别
- [[sports-rehabilitation]] — 运动康复
- [[virtual-reality]] — 虚拟现实
- [[multimodal-interaction]] — 多模态交互
- [[hand-rehabilitation]] — 手部康复
