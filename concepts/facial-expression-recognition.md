---
title: 面部表情识别 (Facial Expression Recognition)
created: 2026-04-14
updated: 2026-04-14
type: concept
tags: [emotion-recognition, computer-vision, hci, multimodal]
sources: [raw/papers/2024facialexpression-remoterehabilitation.md, raw/papers/2024emotion-recognitionsurvey.md, raw/papers/2023survey-affectivemodel-data集-machine-learningalgorithm-expression-speech-text.md, raw/papers/2024multimodalcontactlesssurvey.md]
---

# 面部表情识别 (Facial Expression Recognition)

## 定义
面部表情识别(FER)是通过分析面部肌肉动作来推断情感状态的技术,是情感识别的重要通道之一。

## 技术基础

### FACS (面部动作编码系统)
- Ekman等开发
- 将面部动作分解为动作单元(AUs)
- 44种独立动作单元,组合产生10300种表情配置

### 传统方法
- Gabor特征 + SVM
- LBP (局部二值模式)
- Active Shape Models / Active Appearance Models

### 深度学习方法
- CNN (卷积神经网络)
- VGG、ResNet等骨干网络
- 注意力机制(Expression Recognition Attention)
- Transformer架构

## 挑战
- 表情的个体差异(文化、年龄、性别)
- 遮挡问题
- 微妙表情(subtle expression)识别
- 动态表情序列建模
- 自发 vs.  posed 表情

## 远程康复中的应用
- T-Rehab系统: MediaPipe + CNN
- 非接触式采集(webcam)
- 实时情绪监测

## 数据集
- CK+ (extended Cohn-Kanade)
- AffectNet
- FER2013
- RAF-DB (Real-world Affective Faces Database)
- Affect-In-Wild

## 相关概念
- [[emotion-recognition]] — 情感识别
- [[computer-vision]] — 计算机视觉
- [[affective-computing]] — 情感计算
- [[multimodal-interaction]] — 多模态交互
- [[mediaPipe]] — MediaPipe
