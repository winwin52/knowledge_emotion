---
title: IMU情感识别 (IMU-based Emotion Recognition)
created: 2026-04-14
updated: 2026-04-14
type: concept
tags: [emotion-recognition, physiological-signal, wearable, methodology]
sources: [raw/papers/2023-imuemotion-recognition-algorithm.md]
---

# IMU情感识别 (IMU-based Emotion Recognition)

## 定义
惯性测量单元(IMU)通过采集人体运动加速度、角速度等数据,结合算法分析来推断情感状态。

## IMU组件
- **加速度计** — 测量线性加速度,检测身体运动
- **陀螺仪** — 测量角速度,检测旋转和姿态变化
- **磁力计** — 测量地磁场方向(航向参考)

## 情感识别方法

### 预处理
1. 去噪(卡尔曼滤波、低通滤波)
2. 重力分离
3. 积分求速度和位移(可选)
4. 特征提取(时域/频域)

### 特征提取
- 时域: 均值、标准差、峰值、均方根(RMS)
- 频域: FFT提取主频、频谱熵
- 时频: 小波变换

### 分类算法
- SVM
- Random Forest
- CNN/LSTM(深度学习)
- 特征选择+分类器组合

## 优势
- 成本低、功耗小
- 可穿戴设备集成度高(手机、手表)
- 不受光照影响
- 适合日常长期监测

## 局限性
- 难以直接测量内在情感(主要反映外在行为)
- 运动状态干扰(行走vs静止)
- 个体差异大

## 相关概念
- [[emotion-recognition]] — 情感识别
- [[wearable-sensors]] — 可穿戴传感器
- [[physiological-signal-based-emotion-recognition]] — 生理信号情绪识别
- [[deep-learning]] — 深度学习
