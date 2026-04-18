---
title: 心率变异性 (Heart Rate Variability)
created: 2026-04-18
updated: 2026-04-18
type: concept
tags: [physiological-signal, heart-rate, hrv, emotion-recognition, radar-sensing, vital-signs]
sources: [raw/papers/2025利用雷达技术进行心脏健康-心率.md, raw/papers/2025毫米波雷达测心率-挺多的-包括处理算法.md, raw/papers/s41598-025-09112-w.md]
---

# 心率变异性 (Heart Rate Variability, HRV)

## 定义
心率变异性(HRV)指连续心跳之间时间间隔(IBI, Interbeat Interval)的波动。HRV反映自主神经系统对心脏的调节能力,是评估心血管健康、情绪状态、压力水平的重要指标。

## HRV关键指标
| 指标 | 全称 | 含义 |
|------|------|------|
| RMSSD | Root Mean Square of Successive Differences | 相邻RR间期差值的均方根,反映副交感神经活性 |
| SDRR | Standard Deviation of RR Intervals | RR间期标准差,总体HRV指标 |
| pNN50 | Percentage of successive IBIs differing >50ms | 相邻IBI差>50ms的比例 |
| LF/HF | Low Frequency / High Frequency ratio | 交感/副交感神经平衡指标 |

## 雷达测量HRV

### 优势
- 非接触式监测,适合智能家具/智能家居场景
- 患者无需穿戴设备,适合长期监测
- 可在日常环境(座椅、床垫)中集成

### 挑战
- 呼吸谐波干扰(呼吸频率约0.1-0.5Hz,心率约0.8-2Hz)
- 随机体动伪影
- 距离/角度导致的信号衰减
- Range bin选择(胸腔位置定位)

### 典型算法
- **VMD (Variational Mode Decomposition)** — 自适应变分模态分解,分离心跳与呼吸信号
- **A-VMD** — 自适应变分模态分解,用于FMCW雷达心跳信号提取
- **DWT (离散小波变换)** — 信号去噪与分解
- **自适应卡尔曼滤波 (AKF)** — 结合平方根归一化精确估计心率
- **STFT (短时傅里叶变换)** — 时频分析捕获心跳频率变化
- **多bin方法** — 融合多个距离门的信号

### 2025年研究进展
- FMCW毫米波雷达心率监测,平均绝对误差<4 BPM
- 结合A-VMD和加权估计(谐波关系)提取心跳
- 智能家具(座椅背后毫米波雷达)监测健康人心脏波形:两峰+一谷特征
- 可检测QTc延长(QT间期纠正后延长),预警心脏风险
- IBI最大误差30ms,心率估计平均相对误差4.8%

## HRV与情绪的关系
- RMSSD升高通常与平静/放松状态相关
- LF/HF比值升高与压力/焦虑状态相关
- 副交感神经活性(RMSSD)是情绪调节能力的重要指标
- HRV生物反馈是情绪调节训练的有效手段

## 相关概念
- [[radar-based-emotion-recognition]] — 雷达情感识别
- [[physiological-signal-based-emotion-recognition]] — 生理信号情绪识别
- [[contactless-emotion-recognition]] — 非接触式情感识别
- [[emotion-recognition]] — 情感识别
- [[wearable-sensors]] — 可穿戴传感器
