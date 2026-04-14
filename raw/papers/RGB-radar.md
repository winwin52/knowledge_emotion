IEEE TRANSACTIONS ON INSTRUMENTATION AND MEASUREMENT
1
CardiacMamba: A Multimodal RGB-RF Fusion Framework with
State Space Models for Remote Physiological Measurement
Zheng Wu, Yiping Xie, Bo Zhao, Jiguang He, Fei Luo, Ning Deng, Zitong Yu
Abstract—Heart rate (HR) estimation via remote photoplethys-
mography (rPPG) offers a non-invasive solution for health moni-
toring. However, traditional single-modality approaches (RGB or
Radio Frequency (RF)) face challenges in balancing robustness
and accuracy due to lighting variations, motion artifacts, and
skin tone bias. In this paper, we propose CardiacMamba, a mul-
timodal RGB-RF fusion framework that leverages the comple-
mentary strengths of both modalities. It introduces the Temporal
Difference Mamba Module (TDMM) to capture dynamic changes
in RF signals using timing differences between frames, enhancing
the extraction of local and global features. Additionally, Cardiac-
Mamba employs a Bidirectional SSM for cross-modal alignment
and a Channel-wise Fast Fourier Transform (CFFT) to effectively
capture and refine the frequency domain characteristics of RGB
and RF signals, ultimately improving heart rate estimation
accuracy and periodicity detection. Extensive experiments on
the EquiPleth dataset demonstrate state-of-the-art performance,
achieving marked improvements in accuracy and robustness.
CardiacMamba significantly mitigates skin tone bias, reducing
performance disparities across demographic groups, and main-
tains resilience under missing-modality scenarios. By addressing
critical challenges in fairness, adaptability, and precision, the
framework advances rPPG technology toward reliable real-
world deployment in healthcare. The codes are available at:
https://github.com/WuZheng42/CardiacMamba.
Index Terms—remote photoplethysmography, multimodal fu-
sion, state space models, missing modality robustness.
I. INTRODUCTION
H
EART rate (HR) is a crucial physiological signal for as-
sessing a person’s health and emotional state. Traditional
HR measurement methods like Electrocardiography (ECG)
and Photoplethysmography (PPG) require contact sensors,
which can be uncomfortable and impractical for long-term
monitoring. To address these limitations, remote photoplethys-
mography (rPPG) has emerged as a promising solution. rPPG
uses facial videos to capture skin color changes caused by
blood flow [1–5], enabling non-contact HR estimation. This
method is gaining attention due to its potential applications
in various fields, such as healthcare, human-robot interaction,
and driver monitoring systems. Additionally, rPPG offers
advantages over traditional sensors by being non-invasive, con-
This work was supported by National Natural Science Foundation of
China (Project No. 62306061), and Guangdong Research Team for Com-
munication and Sensing Integrated with Intelligent Computing (Project No.
2024KCXTD047). Zheng Wu and Yiping Xie are co-first authors and con-
tribute equally. Corresponding author: Zitong Yu (email: zitong.yu@ieee.org).
Z. Wu, B. Zhao, J. He, F. Luo, N. Deng, and Z. Yu are with School
of Computing and Information Technology, Great Bay University, and also
with Dongguan Key Laboratory for Intelligence and Information Technology,
Dongguan, 523000, China.
Y. Xie is with Computer Vision Institute, School of Computer Science
& Software Engineering, Shenzhen University, Shenzhen, 518060, and also
with School of Computing and Information Technology, Great Bay University,
Dongguan, 523000, China.
Collect RGB  data
RGB-Only learning framework for rPPG estimation
Camera
RGB
Predictor
rPPG Signal
Feature
Extraction
(a) RGB-only Methods
Collect RF data
RF-Only learning framework for rPPG estimation
Radar
RF
Predictor
Feature
Extraction
rPPG Signal
(b) RF-only Methods
Fusion learning framework for rPPG estimation
Collect RGB and RF data
RF
RGB
Predictor
Camera
Radar
Feature
Extraction
rPPG Signal
(c) RGB-RF fusion Methods
Fig. 1: Comparison of deep learning methods for rPPG learn-
ing. (a) RGB-only Method: Training with only RGB data
collected by the camera. (b) RF-only Method: Training with
only RF data collected by the radar. (c) Training with both
RGB and RF data.
venient, and cost-effective, making it suitable for continuous
health monitoring.
Non-contact physiological systems, such as those using
cameras for remote photoplethysmography (rPPG), rely on the
movement of the skin’s RGB spectrum with the blood volume
pulse (BVP), providing insights into human vital signs. The
field of camera-based remote plethysmography has evolved
significantly, with methods based on facial skin color changes
linked to blood volume, using approaches like physics-based
models [6, 7], blind source separation [8, 9], and deep learning
based methods [10]. However, environmental factors (e.g.,
illumination variations) severely degrade performance. For
instance, under low-light conditions, darker skin tones further
amplify estimation errors due to reduced light reflectance [11].
To address the limitations of video-based methods, alter-
native non-contact solutions have emerged, offering potential
advantages in overcoming these challenges. Radio Frequency
(RF) sensors estimate heart rate by periodically emitting and
receiving electromagnetic signals to measure the radial depth
changes near the chest, which vibrates in response to the in-
arXiv:2502.13624v1  [cs.CV]  19 Feb 2025
IEEE TRANSACTIONS ON INSTRUMENTATION AND MEASUREMENT
2
dividual’s vital cycle. Unlike video-based physiological mon-
itoring methods that rely on RGB pixel intensity [12, 13], RF
sensors infer radial depth information through electromagnetic
signal transmission and reception, inherently mitigating the
influence of surrounding illumination. However, RF sensors
have their own disadvantages, such as poor angular resolution
that makes them susceptible to lateral motions, and the greater
difficulty they pose for data acquisition compared to cameras.
Consequently, most previous RF physiological approaches
have depended upon learning-free methods [14, 15]. But
in recent years, deep learning-based technologies have also
emerged [16].
The fusion of RGB and RF modalities presents a com-
pelling avenue to synergize their complementary strengths:
rPPG provides high spatial resolution for localized signal
extraction, while RF ensures robustness against lighting vari-
ations and skin tone biases. However, current multimodal
fusion strategies inadequately address three key gaps [17]: (1)
inefficient cross-modal feature alignment due to heterogeneous
temporal and spatial characteristics, (2) insufficient exploita-
tion of frequency-domain correlations for periodic HR signal
enhancement, and (3) persistent fairness disparities in under-
represented demographic groups. To address the limitations of
video-based methods, alternative non-contact solutions have
emerged, offering potential advantages in overcoming these
challenges.
In response to the above issues, this paper proposes Cardiac-
Mamba, a multi-modal RGB-RF fusion framework based on
dynamic feature enhancement and cross-modal bidirectional
interaction using a State Space Model. The framework aims
to significantly improve the performance and fairness of heart
rate estimation and other tasks by introducing innovative
module designs and frequency-domain fusion strategies. In
the Dual-level Feature Extraction and Alignment stage, we
introduce the Temporal Difference Mamba Module (TDMM)
and the Bifurcated Diff-Conv Fusion (BDCF). These modules
extract dynamic features through temporal differential convo-
lutions, and, combined with the global modeling capability of
the Mamba block, effectively enhance the rPPG features of
the RGB modality and the temporal dynamic information of
the RF modality. In the Bidirectional Feature Interaction stage,
we innovatively introduce the Bidirectional State Space Model
(Bi-SSM). This model enables the cooperative modeling of the
RGB and RF modalities by sharing state transition matrices
and input matrices. The mechanism integrates cross-modal
information under a unified dynamic framework, preserving
the unique semantics of each modality while enhancing global
context awareness through bidirectional temporal modeling
(both forward and backward). In the Bidirectional Feature
Fusion stage, we propose the Channel-wise Fast Fourier
Transform, which maps the RGB and RF features into the
frequency domain for interaction. By utilizing learnable real
and imaginary part interaction parameters, the model can adap-
tively enhance the frequency bands related to heart rate and
suppress noise, with the final reconstruction back into time-
domain features through inverse transformation. Experiments
on the EquiPleth dataset demonstrate that CardiacMamba
outperforms existing methods in scenarios involving skin tone
bias and missing modalities. Our multi-modal fusion mecha-
nism effectively alleviates the estimation bias caused by skin
reflectance differences in traditional single-modal methods.
In summary, our contributions encompass:
• We introduce Mamba into the framework for joint RGB
and RF fusion-based rPPG estimation, enhancing the
model’s ability to efficiently capture and integrate multi-
modal features. By leveraging Mamba’s advanced struc-
ture, we improve the robustness and accuracy of rPPG
estimation, enabling the model to effectively handle the
diverse and complementary information from both RGB
and RF modalities.
• We design the Temporal Difference Mamba Module
(TDMM), which improves the standard Mamba frame-
work by leveraging temporal differences between consec-
utive frames to capture dynamic changes in RF signals.
By incorporating the Mamba block, this module enhances
the extraction of both local and global temporal features,
thereby significantly improving the model’s performance
in complex dynamic scenarios.
• We designed the Channel-wise Fast Fourier Transform
(CFFT), which effectively captures the unique frequency-
domain characteristics of RGB and RF modalities. This
frequency-domain approach enhances the accuracy of
heart rate estimation by revealing cross-modal frequency
relationships and selectively enhancing or suppressing
relevant components, thereby strengthening the model’s
ability to detect heart rate periodicity.
• We have achieved state-of-the-art performance in han-
dling missing modality scenarios and eliminating skin
tone bias, demonstrating the advantages of our proposed
model in dealing with incomplete data and cross-modal
data biases. At the same time, we conducted a series
of extensive ablation experiments to thoroughly evaluate
the individual components of the model, validating the
critical role each module plays in enhancing overall
performance.
II. RELATED WORK
A. RGB Video-Based Methods
Camera-based remote photoplethysmography (rPPG) tech-
nology has undergone significant development over the past
few decades. In video-based remote physiological monitoring,
RGB cameras can be used to remotely reconstruct human
physiological information, particularly in the facial region,
because the skin’s reflectance spectrum changes with physi-
ological movements such as blood pulses. Initially, traditional
rPPG methods mainly relied on signal processing techniques
to analyze periodic signals from facial regions. These meth-
ods typically used signal decomposition techniques such as
Principal Component Analysis (PCA) [18] and Independent
Component Analysis (ICA) [19, 20] to recover physiological
signals under low signal-to-noise ratio conditions. However,
these traditional methods were limited by external factors such
as head movements and lighting changes, which interfered
with their application.
With the rise of deep learning techniques, rPPG measure-
ment tasks have seen significant improvements. Convolutional
IEEE TRANSACTIONS ON INSTRUMENTATION AND MEASUREMENT
3
Dual-level Feature Extraction and Alignment
SCFM
Bidirectional Feature Interaction
Bidirectional Feature Fusion
Vedio
Radar
BDCF
TDMM
CFFT
CFFT
predictor
Vision
Mamba 
Vision
Mamba 
Linear
Linear
RFAM
Conv
BN
Attention
DS
ReLu
Sigmoid
mask
mean
Conv
BN
rPPG Signal
Fig. 2: The overall architecture of CardiacMamba. It consists of three stages: Dual-level Feature Extraction and Alignment,
Bidirectional Feature Interaction, and Bidirectional Feature Fusion.
Neural Networks (CNNs) have been widely applied to skin
segmentation and rPPG feature extraction. Early works used
3D CNNs or 2D CNNs to capture spatio-temporal informa-
tion [10, 19, 21, 22], enabling the reconstruction of rPPG
signals. In recent years, transformers have been introduced
to rPPG tasks [23–25], enhancing quasi-periodic rPPG fea-
tures and global spatio-temporal perception, further improv-
ing accuracy. As subtle physiological movements are often
affected by external factors, new methods have introduced
techniques such as inverse attention mechanisms or temporal
shift modules to effectively suppress interference caused by
head movements [26].
B. RF radar-Based Methods
Radar-based remote photoplethysmography (rPPG) technol-
ogy has evolved significantly since its inception in the 1970s
for respiratory-rate detection [27]. Over time, radar has been
increasingly applied to monitor vital signs like heart rate,
respiratory rate, and blood pressure. Various radar systems, in-
cluding FMCW, UWB Impulse, and Continuous Wave Doppler
radars, are used to detect minute chest displacements caused
by physiological movements.
Early research showed that radar-based and camera-based
methods for heart-rate estimation performed similarly under
ideal conditions, but radar systems are more susceptible to
noise, often requiring subjects to remain still. Recent advance-
ments have integrated deep learning techniques into FMCW
radar to enhance the detection of plethysmograph signals,
improving the accuracy of heart-rate estimation [28].
In RF-based remote physiology, radar’s ability to capture
doppler information and its superior depth resolvability allows
it to track subtle oscillations in the chest, providing a precise
measurement of vital signs. Initially, most RF techniques relied
on signal decomposition methods such as frequency analysis
and wavelet decomposition. However, recent studies have
leveraged deep learning to further improve the interpretation of
radar signals. For example, [28] proposed an encoder-decoder
model for reconstructing vital signals from raw RF data, while
[29] employed variational inference.
C. Multi-modal Fusion Methods
Multi-modal
fusion
in
remote
photoplethysmography
(rPPG) enhances vital sign estimation performance by combin-
ing multiple data modalities. This process involves integrating
different modalities to achieve better results than using a
single modality. In deep learning, fusion can occur in a
middle latent space, where features from different modalities
are combined, or at a later decision stage, where predictions
from each modality are aggregated. Nevertheless, previous
studies have attempted to fuse modalities like RGB with Mid-
Infrared (thermal) and Near-Infrared (NIR) to improve rPPG
performance [30–32]. Previous studies have also combined
RGB and RF to better estimate human vital signs [17]. In the
field of depression detection, there have been studies that use
Bi-SSM as the core framework, combining audio and video
information for depression detection.
Additionally, recent research has focused on combining
RGB and radar frequency (RF) signals to enhance robustness
in challenging conditions, such as low light or adverse weather.
This is particularly important for outdoor applications like
autonomous driving, where spatial fusion of RGB and RF
signals helps with object detection.
D. Mamba
Mamba [33] was initially introduced in the field of natural
language processing to efficiently handle long sequence data.
As research progressed, many variations of mamba have
emerged [34–38], and Mamba was extended to the computer
vision domain, notably through the incorporation of Bidirec-
tional State Space Models (BSSM), resulting in Vision Mamba
(Vim) [39]. Vim processes image sequences bidirectionally
and integrates positional embeddings, effectively capturing
global visual context and enhancing the efficiency and per-
formance of high-resolution image processing. Compared to
traditional transformer models, Vim achieves a 2.8-fold in-
crease in inference speed and reduces GPU memory usage
when processing high-resolution images. This advancement
signifies a substantial breakthrough for the Mamba architecture
in visual tasks.
IEEE TRANSACTIONS ON INSTRUMENTATION AND MEASUREMENT
4
Mamba block
Time
difference
Conv
BN
Linear
Linear
Conv
Sigmoid
Sigmoid
Linear
RELU
SSM
Fig. 3: Time difference Mamba Module (TDMM) for extract-
ing RF dynamic timing features and global features.
III. METHODOLOGY
A. Preliminaries
1)
State Space Representation in the Continuous Domain:
Mamba and S4, both state space model (SSM)-based ap-
proaches in deep learning, originate from the concept of linear
time-invariant (LTI) systems in classical control theory. An LTI
system maps a one-dimensional continuous input sequence
x(t) ∈R through an intermediate hidden state h(t) ∈RN
to an output y(t) ∈R. Mathematically, such a system is
described by the following linear ordinary differential equation
(ODE):
(
h′(t) = A h(t) + B x(t),
y(t) = C h(t) + D x(t),
(1)
where A ∈RN×N is the state transition matrix, B ∈RN×1
and C ∈R1×N serve as projection matrices, and D ∈R
denotes a skip connection. While this continuous-time for-
mulation benefits from a solid foundation in control theory,
applying it directly to discrete sequence data (e.g., text or
speech) in deep learning requires discretization to align with
modern hardware computation.
2)
Zero-Order Hold (ZOH) Discretization: To bridge con-
tinuous ODEs and discrete sequence modeling, one typically
introduces a time scale parameter ∆and applies the Zero-
Order Hold (ZOH) principle to discretize the continuous
parameters A and B into their discrete counterparts A and
B. The essential transformation is captured as follows:
A = exp(∆A),
B = (∆A)−1h
exp(∆A) −I
i
∆B,
(2)
where exp(·) is the matrix exponential and I denotes the
identity matrix of compatible dimensions. Once discretization
is complete, Eq. (1) can be rewritten on discrete time steps
(or sequence indices) as
(
hk = A hk−1 + B xk,
yk = C hk + D xk,
(3)
with k indexing each discrete time step or sequence element.
This step effectively maps the continuous state dynamics into
a discrete iterative framework amenable to deep learning.
3) From RNN Form to Convolutional Form: While Eq. (3)
superficially resembles a class of RNN hidden-state updates,
it can be further recast into a one-dimensional convolutional
form. Specifically, by unrolling hk over preceding time steps
Linear
Frequency
domain
Interaction
Linear
Chnnel-Wise
Domain
Conversion
Domain
Inversion
Fig. 4: Channel-wise Fast Fourier Transform (CFFT) is used to
extract frequency domain features of RGB and RF modalities.
and collecting terms of {A
k−1 B}, one can define a struc-
tured convolutional kernel K, yielding a single convolution
operation over the sequence {x1, x2, . . . , xL}:
K =
 C B, C A B, . . . , C A
L−1 B

,
y = x ∗K,
(4)
where ∗denotes one-dimensional convolution and L is the se-
quence length. This formulation confers significant paralleliza-
tion advantages, leveraging large-scale GPU/TPU parallelism
to greatly enhance efficiency and scalability for long-sequence
modeling.
B. Overview
The proposed CardiacMamba model incorporates three fun-
damental components for the modality fusion process: Dual-
level Feature Extraction and Alignment, Bidirectional Fea-
ture Interaction, and Bidirectional Feature Fusion. As shown
in Fig. 2, the RGB modality input is denoted as IC
∈
R3×T1×H×W , while the RF modality input is represented as
If ∈RC×T2.
The initial phase, Dual-level Feature Extraction and Align-
ment, encompasses both low-level and high-level feature ex-
traction processes. In the low-level stage, we employ Temporal
Difference Mamba Module (TDMM) and Bifurcated Diff-
Conv Fusion (BDCF) to capture primary features from both
the RGB and RF modalities. The RGB modality output, Hn1
c ,
is then processed by Spatial-Channel Fusion Module (SCFM),
which extracts rPPG-related features and consolidates spatial
information into token channels. For the RF modality output,
Hn1
f , we utilize two RF Alignment Module (RFAM) modules
to extract deeper features and align the RF modality with the
RGB modality in the temporal domain.
Hn2
c
= SCFM(BDCF(IC))
(5)
Hn2
f
= RFAM(RFAM(TDMM(IC)))
(6)
In the subsequent Bidirectional Feature Interaction stage,
the outputs Hn2
c
and Hn2
f
from the RGB and RF modalities
are fed into the Vision Mamba (Vim) module, which aligns
both modalities into a shared representation space, facilitating
the interaction of information across modalities and enabling
the extraction of global features.
The aligned features are then fused by adding Hn2
c
to
V im(Hn2
c ) for the RGB modality, and similarly adding Hn2
f
IEEE TRANSACTIONS ON INSTRUMENTATION AND MEASUREMENT
5
to V im(Hn2
f ) for the RF modality. These fused features are
subsequently transformed into a new feature space through a
linear transformation, resulting in Hn4
c
and Hn4
f .
This fusion process enhances the exchange of information
between modalities, thereby producing a more comprehensive
feature representation that improves the accuracy and robust-
ness of the final predictions.
Hn4
c
= Linear(Hn2
c
+ V im(Hn2
c ))
(7)
Hn4
f
= Linear(Hn2
f
+ V im(Hn2
f ))
(8)
Subsequently, the fused outputs from the Vim module
are passed through a channel-wise Fast Fourier Transform
(CFFT) network, which further facilitates the interaction of
information across multiple channels. Finally, the aggregated
features are forwarded to the predictor to estimate the BVP
signal.
Hn5
c , Hn5
f
= CFFT(Hn4
c ), CFFT(Hn4
f )
(9)
C. Dual-level Feature Extraction and Alignment
1) Low-level Feature Extraction.: Temporal Difference
Mamba Module (TDMM): To better capture the dynamic
changes in the time series of the radio frequency (RF) modal-
ity, we propose a novel module called the Temporal Difference
Mamba Module (TDMM). As shown in Fig. 3 and Algorithm
1, This module is designed to effectively handle time dif-
ference information and extract more discriminative features
from the temporal data, thereby significantly enhancing the
temporal information in the RF signal and improving the
model’s performance in complex dynamic scenarios.
Firstly, we calculate the differences between consecutive
frames in the input RF data to help the network cap-
ture the dynamic changes of the signal. Specifically, for
each frame, we apply a temporal shift operation to obtain
Xt−2, Xt−1, Xt, Xt+1, Xt+2 (i.e., five adjacent frames). By
calculating the differences between each frame and its pre-
ceding and succeeding frames, we obtain frame differences
D−2, D−1, D1, D2, which reflect the variation characteristics
of the RF signal at different time points.
Next, we combine the differential RF signal with the
original signal, then we apply convolution operations and
batch normalization to these time-differenced maps. Given that
RF signals typically contain periodic dynamic features and
to avoid introducing excessive redundancy in the temporal
dimension, we use 7×1 convolution kernels to efficiently
extract these features. We then introduce the Mamba block
to further extract global features, and finally apply the ReLU
activation function to enhance the non-linear expression.
Bifurcated Diff-Conv Fusion (BDCF): The diff-fusion
module first integrates frame differences into the raw frames,
enhancing the perception of BVP wave variations. This ef-
fectively improves rPPG features with minimal computational
cost. Since rPPG requires both high-frequency information
across frames and low-frequency information within frames,
Algorithm 1: Temporal Difference Mamba Module
(TDMM). Notation: ‘B’ (Batch Size), ‘C’ (Number
of Channels), ‘T’ (Number Of Frames), ‘D’ (Frame
Difference)
Input: If : (B, Ci, Ti)
Output: X3 : (B, Ci, Ti)
1: Xt−2, Xt−1, Xt, Xt+1 ←Temporal Slice(If).
2: D−2, D−1, D1, D2 ←Compute difference between adjacent
slices.
3: Xdiff ←Concatenate(D−2, D−1, D1, D2).
4: for k = 1 to N do
5:
X : (B, Ci, Ti) ←Conv(Xdiff).
6:
X′ : (B, Ci, Ti) ←Batchnorm(X).
# Mamba Block.
7:
X′′ : (B, Ci, Ti) ←Linear(X′).
8:
X′′ ←Conv(X′′).
9:
X : (B, Ci, Ti) ←Linear(X′).
10:
X : (B, Ci, Ti) ←Sigmoid(X).
11:
X′′′ : (B, Ci, Ti) ←X ⊙X′′.
12:
X1 : (B, Ci, Ti) ←SSM(X′′′).
13:
X2 : (B, Ci, Ti) ←Linear(X1).
14:
X3 : (B, Ci, Ti) ←RElu(X2).
15: end for
large convolutional kernels are used to capture the low-
frequency information within frames, fully incorporating spa-
tial information into the channels.
The
process
is
as
follows:
For
an
input
video
X
∈
R3×T ×H×W ,
temporal
shifting
is
applied
to
obtain Xt−2, Xt−1, Xt, Xt+1, and Xt+2. The differences
between consecutive frames are then computed, resulting
in D−2, D−1, D1, and D2. These frame differences are
combined with the raw frames and passed through Stem1 for
feature extraction. Stem1 consists of a (7 × 7) convolution
layer, followed by batch normalization (BN), ReLU, and max
pooling. The input dimension is 3 when using single-frame
features, and 12 when concatenating frame differences.
Next, the features of the difference video and the raw video
are merged and further enhanced through Stem2, which also
includes a (7×7) convolution layer, BN, and ReLU.The fusion
formula is:
Xfu = α·Stem2(Xorigin)+β ·Stem2(α·Xorigin +β ·Xdiff)
The fusion coefficients α and β are both set to 0.5. The
output of the BDCF is a fused and enhanced feature represen-
tation.
2) High-level Feature Extraction:
Spatial-Channel Fu-
sion Module (SCFM): This module aims to effectively
capture high-level features from RGB video signals. First,
the input features undergo an initial nonlinear transformation
through the Sigmoid activation function. The use of the
Sigmoid function compresses the input signal to the range of
[0, 1], enhancing model stability and effectively suppressing
outliers. The activated features are then passed into the Atten-
tion Mask module, which uses a self-attention mechanism to
weight the input signal and capture the relationships between
different spatial locations. Specifically, the Attention Mask is
computed as follows:
IEEE TRANSACTIONS ON INSTRUMENTATION AND MEASUREMENT
6
TABLE I: Comparison of different methods on the EquiPleth dataset. The best results are marked in bold.
Method
Input
MAE
RMSE
ρ
DeepPhys [22]
RGB
5.54
18.51
0.66
PhysNet [10]
RGB
8.06
19.71
0.61
MTTS-CAN [40]
RGB
3.69
13.8
0.82
PhysFormer [23]
RGB
12.92
24.36
0.47
EfficientPhys [41]
RGB
5.47
17.04
0.71
RhythmMamba [42]
RGB
2.87
9.58
0.92
Ours (RGB-Only)
RGB
1.2
4.23
0.95
Tu et al. [43]
RF
5.5
11.68
0.64
Mercuri et al. [44]
RF
4.73
9.6
0.7
FFT-based [14]
RF
13.51
21.07
0.24
Ours (RF-Only)
RF
5.2
7.4
0.8
Vilesov et al. [17]
RGB+RF
1.12
3.42
0.95
Ours (Full model)
RGB+RF
0.96
3.06
0.97
Mask = (H/8)(W/8) · σ(Stem(Xfu))
2∥σ(Stem(Xfu))∥1
,
(10)
where σ represents the Sigmoid activation function, and Stem
is a relatively large (5×5) convolution kernel that effectively
integrates spatial information into the channel. In this way,
the Attention Mask highlights the strong signal regions in the
skin areas of the image, which is crucial for tasks like heart
rate estimation. Compared to traditional Softmax mechanisms,
L1 normalization (| · |1) is smoother and produces a sparser
mask, allowing the Attention Mask to more precisely focus on
the key signal regions, while requiring fewer computational
resources.
The generated Attention Mask is then applied to the fused
features Xfusion, resulting in an enhanced feature representa-
tion Xattn ∈RC×T/2×H/8×W/8. This enhancement process
effectively reduces unnecessary noise and strengthens the
representation of the signal in the spatial domain through L1
normalization.
Next, the features processed by the self-attention mecha-
nism undergo global average pooling to further integrate the
features. Global average pooling reduces the feature dimen-
sionality while effectively incorporating spatial information
into the channels, making the representation for each channel
more compact and representative. The pooled output features
Xstem ∈RT/2×C provide highly condensed information for
the subsequent convolution operations.
Finally, the pooled features are processed through convolu-
tion and batch normalization layers. The convolution operation
further extracts useful information from the feature space,
enhancing the model’s expressiveness, while batch normal-
ization standardizes the feature distribution across channels,
accelerating convergence and improving training stability.
RF Alignment Module (RFAM): RF Alignment Module
(RFAM) module is designed to process RF modality data
by enhancing its feature representation and ensuring tem-
poral alignment with other modalities, such as RGB. The
module consists of several critical operations: convolution,
batch normalization, channel attention, downsampling, and
ReLU activation. Initially, the RF data is passed through
convolutional layers to extract spatial features, followed by
batch normalization to standardize the feature distributions
across the mini-batch.
Next, the processed features undergo a channel attention
mechanism that adaptively highlights the most informative
channels. The attention mechanism uses both average pooling
and max pooling to capture global spatial information, which
is then passed through a fully connected network comprising
two convolutional layers. The attention weights are calculated
using a Sigmoid activation, and these weights are applied
to the input feature map, selectively amplifying the relevant
channels while suppressing less useful ones. This step allows
the model to focus on the most important features of the RF
data, which is particularly useful for handling the dynamic
nature of RF signals.
Finally, the RF data undergoes downsampling to align its
temporal dimension with that of the RGB data. This temporal
alignment ensures that both modalities are synchronized and
can be effectively fused in subsequent stages of the model.
After downsampling, the data is passed through a ReLU
activation function, which introduces non-linearity and helps
capture complex patterns in the features.
D. Bidirectional Feature Interaction
Inspired by [39, 45], we proposed Bidirectional Feature
Interaction enhances multimodal representation by collabo-
ratively modeling RF and video features. With the Vision
Mamba encoder [45], it captures temporal dependencies be-
tween the modalities and facilitates their interaction via a
shared state transition matrix, without adding parameters. This
approach allows both modalities to learn cross-modal informa-
tion while preserving their unique characteristics, improving
the model’s expressiveness and accuracy.
The Vision Mamba Encoder first applies linear projection
to transform each image patch into a sequence of tokens,
augmented with positional embeddings to maintain spatial
relationships. It then models the patch sequence bidirection-
ally through a Bidirectional State Space Model (Bi-SSM),
IEEE TRANSACTIONS ON INSTRUMENTATION AND MEASUREMENT
7
TABLE II: Comparison of the performance of various methods
on the RGB and RF fusion task, with the differences in
performance (∆) between light and dark skin tones in terms
of MAE, RMSE, and correlation coefficient (ρ).
Method
Input
∆MAE
∆RMSE
∆ρ
ICA [9]
RGB
4.42
3.15
-0.36
CHROM [6]
RGB
4.97
4.17
-0.38
BCG [18]
RGB
0.99
1.25
0.05
PhysNet [10]
RGB
2.22
4.05
-0.25
FFT-based RF [14]
RF
1.32
2.06
0.32
Vilesov et al. [17]
RGB&RF
0.67
1.44
-0.10
CardiacMamba (Ours)
RGB&RF
0.26
1.28
0.05
capturing comprehensive spatiotemporal dependencies. This
bidirectional modeling integrates both global context and local
details effectively. Convolutional operations extract local fea-
tures, helping the model identify fine-grained patterns, while
global convolution layers capture long-range dependencies.
This multi-level structure generates rich visual representations
for downstream tasks such as classification and object detec-
tion.
In multimodal tasks, the Vision Mamba Encoder excels with
both RGB video and RF radar modalities. For RGB video,
bidirectional modeling captures temporal dependencies, aiding
in dynamic information extraction like facial expressions and
pose changes. For RF radar, the low resolution and noise
typically hinder detail extraction. However, by combining RF
signals with RGB video signals, bidirectional modeling and
shared state matrices enhance the RF signal’s temporal dy-
namics, improving multimodal fusion and model performance.
Unlike traditional multimodal learning, which uses separate
state transition matrices for each modality, Bidirectional Fea-
ture Interaction introduces a shared state transition matrix. This
unified approach ensures that both RF and video modalities
evolve under the same dynamic rules, fostering closer collab-
oration. The shared matrices A and B allow both modalities to
update simultaneously, enhancing fusion and complementarity:
h(t+1)
c
= Ah(t)
c
+ Bx(t)
c
(11)
h(t+1)
f
= Ah(t)
f
+ Bx(t)
f
(12)
This shared matrix framework simplifies the model and
improves cross-modal integration, enabling more efficient
learning and better performance on multimodal tasks.
The introduction of a shared state transition matrix not
only simplifies the model structure but also significantly im-
proves the efficiency of cross-modal information integration.
By sharing matrices A and B, Bidirectional Feature Interaction
can capture the interdependencies between RF signals and
video images under the same temporal dynamics. The shared
matrices eliminate redundancy between modalities, facili-
tate information exchange and collaborative learning between
modalities, and thus effectively improve the performance of
multimodal learning tasks.
TABLE III: Testing under missing-modality conditions.
Method
Train
Test
MAE
RMSE
Base
RGB&RF
RGB
21.7
25.7
Base
RGB&RF
RF
21.4
24.3
Base
RGB&RF
RGB&RF
20.3
24.8
Vilesov et al. [17]
RGB&RF
RGB
6.82
13.32
Vilesov et al. [17]
RGB&RF
RF
7.25
9.62
Vilesov et al. [17]
RGB&RF
RGB&RF
1.12
3.42
CardiacMamba (Ours)
RGB&RF
RGB
1.2
3.41
CardiacMamba (Ours)
RGB&RF
RF
11
13
CardiacMamba (Ours)
RGB&RF
RGB&RF
0.96
3.06
E. Bidirectional Feature Fusion
In this subsection, the features of the RGB and RF modali-
ties are first fed into their respective Channel-wise Fast Fourier
Transforms (CFFT) to extract higher-order frequency-domain
features. The features from both modalities are then combined
through summation, and the fused features are passed into the
predictor for decoding to obtain the rPPG signal.
As shown in Fig. 4, the CFFT module first applies a fast
Fourier transform to map the channel-domain signals into the
frequency domain, highlighting the frequency information of
different modalities across channels. It then uses learnable
interactions between the real and imaginary parts in the fre-
quency domain to enhance or suppress specific frequency com-
ponents. Finally, by applying the inverse Fourier transform,
the processed results are restored back to the channel domain.
This process preserves the original feature representations
while effectively fusing RGB and RF signals in the frequency
domain and strengthening the model’s ability to detect heart
rate periodicity.
By performing a Fast Fourier transform along the channel
dimension rather than directly on the time dimension or other
dimensions, we can effectively extract the unique frequency
characteristics of each modality, since the RGB and RF signals
carry distinct frequency-domain information across different
channels. This channel-wise approach allows the model to
capture those distinct frequency components of both RGB and
RF signals and to uncover their cross-modal frequency rela-
tionships, thereby improving heart rate estimation accuracy.
In addition, it can enhance or suppress specific frequency
components to remove noise more effectively and highlight
those related to heart rate.
Fast Fourier Transform (FFT) along the Channel Dimen-
sion: We apply the FFT to the features along the channel
dimension, transforming the signal from the time domain into
the frequency domain:
H(fc) =
Z ∞
−∞
H(c) e−j2πfc c dc
=
Z ∞
−∞
H(c) cos
 2πfc c

dc + j
Z ∞
−∞
H(c) sin
 2πfc c

dc
= H(fc)re + j H(fc)im,
(13)
where c is the channel dimension (continuous variable in
this integral form), fc is the channel-frequency variable,
H(c) denotes the original signal in the channel domain,
IEEE TRANSACTIONS ON INSTRUMENTATION AND MEASUREMENT
8
H(fc)re, H(fc)im are the real and imaginary parts of H(fc),
and j is the imaginary unit with j2 = −1.
Frequency-domain Interaction: After transforming the fea-
tures into the frequency domain, we perform interaction op-
erations using learnable parameters. This enables the model
to focus on the most important frequency components and
suppress irrelevant ones. The interaction between the real and
imaginary parts of the frequency-domain features is modeled
as:
Hreal = ReLU
 B
X
b=0

Xreal
fre r −Ximag
fre i + rb
!
(14)
Himag = ReLU
 B
X
b=0

Ximag
fre r + Xreal
fre i + ib
!
(15)
Inverse Fourier Transform (IFFT): After the frequency-
domain interaction, the inverse Fourier Transform (IFFT) is
applied to convert the features back to the time domain:
H(c) =
Z ∞
−∞
H(fc) e j2πfc c dfc
=
Z ∞
−∞
 H(fc)re + j H(fc)im

e j2πfc c dfc.
F. Loss
Our loss includes a Negative Pearson Loss Lneg
and a Signal-to-Noise Ratio (SNR) loss LSNR
The Negative Pearson Loss is defined as follows:
Ln(y, ˆy) = 1 −
1
√a1 × a2
 N
X
i=1
yiˆyi −
N
X
i=1
yiˆyi
!
(16)
a1 =


N
X
i=1
y2
i −
 N
X
i=1
yi
!2

(17)
a2 =


N
X
i=1
ˆy2
i −
 N
X
i=1
ˆyi
!2

(18)
The SNR loss is defined as follows:
LSNR(y, ˆy) =
R f0+w
f0−w | ˆY (f)|2df
R f0−w
−∞
| ˆY (f)|2df +
R ∞
f0+w | ˆY (f)|2df
,
(19)
f0 = arg max Y (f),
(20)
where Y (f) and ˆY (f) are the respective Fourier transforms
of y and ˆy and w is the chosen window size.The overall loss
is:
L(y, ˆy) = Lneg(y, ˆy) + λLSNR(y, ˆy)
(21)
IV. EXPERIMENT
A. Datasets and Metrics
Datasets.
To conduct evaluations, we performed extensive
experiments on the EquiPleth dataset [17]. The EquiPleth
TABLE IV: Ablation experiments on different modules, in-
cluding ‘Vim’ (short for Vision Mamba), ‘CFFT’ (short for
Channel-wise Fast Fourier Transform), ‘RFAM’ (RF Align-
ment Module), and TDMM’‘(Temporal Difference Mamba
Module).
Vim
CFFT
SSM
RFAM
TDMM
MAE
RMSE
ρ
×
✓
✓
✓
✓
1.7
4.9
0.91
✓
×
✓
✓
✓
18.8
20.5
0.2
✓
✓
×
✓
✓
1.86
5.51
0.89
✓
✓
✓
×
✓
1.85
5.31
0.9
✓
✓
✓
✓
×
3.82
8.06
0.81
✓
✓
✓
✓
✓
0.96
3.06
0.97
dataset comprises The dataset contains 28 light, 49 medium,
and 14 dark skin tone volunteers. The RGB camera, set to
default factory settings at 30 fps, and the FMCW radar, set to
a starting frequency of 77 GHz, were used to record 6 sessions
per volunteer, each lasting 30 seconds and consisting of both
RGB video and radar IQ data.
Metrics.
This study adopts the evaluation metrics of mean
absolute error (MAE), root mean square error (RMSE), and
Pearson correlation coefficient (ρ).In particular, lower MAE
and RMSE values indicate smaller error margins, while ρ
values closer to 1.0 reflect reduced error. Both MAE and
RMSE are expressed in beats per minute (bpm), and for
convenience, these units will be omitted in the following tables
and analyses.
B. Experimental Setup
The inputs for the RGB branch consisted of video clips that
were processed to 128x128 crops using a MTCNN
[46] to
locate facial regions. The inputs for the RF branch consisted
of IQ data, which was processed into a range matrix, with
data related to regions of interest extracted within a 25 cm
window.The proposed Fusion-Vital model was trained using
the ADAM optimizer with a batch size of 32, a learning rate
of 0.0001, on a 4090 GPU for 30 epochs.
C. Comparison with State-of-the-Art method
As shown in TABLE I, we evaluated the performance of
the proposed model against several state-of-the-art remote
physiology models [22] [10] [40] [23] [41]
[42]), which
depend on a single modality. We also evaluate the performance
of our model with multimodal remote physiology model[17].
For heart rate estimation, our model outperforms the base-
line models by a significant margin. Compared to the best
output of the RGB model, our multimodal fusion model
reduces MAE by 67% and RMSE by 68%. It also outper-
forms the best RF model. Additionally, when compared to
the previously best-performing multimodal fusion model, our
approach reduces MAE by 15% and RMSE by 11%. While the
performance of our single-modality RGB model is comparable
to the best output of the RGB model, our single-modality RF
model surpasses the performance of the best RF model.
IEEE TRANSACTIONS ON INSTRUMENTATION AND MEASUREMENT
9
(a) Human face
(b) Feature heat map of human
face
(c) Radar spectrum diagram
(d) Feature heat map of radar
spectrum diagram
Fig. 5: Visual representations of human face and radar spectrum features. (a) The human face image used in the analysis.
(b) Feature heat map of the human face, illustrating the key regions of interest. (c) Radar spectrum diagram representing the
frequency information of the signal. (d) Feature heat map of the radar spectrum diagram, highlighting the relevant features for
analysis.
Mean Error
-50
-40
-30
-20
-10
0
10
50
60
70
80
90
100
20
+95% Confidence Interval
-95% Confidence Interval
-40
-30
-20
-10
0
10
20
Difference between rPPG HR and GT PPG HR [bpm] 
Average of rPPG HR and  GT PPG HR (bpm)
(a) CardiacMamba (Ours)
-40
-30
-20
-10
0
10
20
30
Difference between rPPG HR and GT PPG HR [bpm] 
50
60
70
80
90
100
Average of rPPG HR and  GT PPG HR (bpm)
-40
-30
-20
-10
0
10
20
Mean Error
+95% Confidence Interval
-95% Confidence Interval
(b) Vilesov et al. [17]
Fig. 6: Bland-Altman plots comparing the heart rate
estimation from different methods. (a) CardiacMamba,
showing the agreement between estimated and ground truth
(GT) heart rates. (b) Vilesov et al. [17], illustrating the
discrepancies between estimated and GT heart rates. The
color gradient represents the distribution of differences, with
confidence intervals indicated by the dashed lines.
D. Measuring Skin Tone Bias and Fairness
To address skin tone bias, this study systematically evaluates
the fairness of different models by quantifying performance
differences (Difference Value) between light and dark skin
samples. As shown in TABLE II, the proposed RGB and
RF fusion model demonstrates significant superiority across
three key metrics: MAE, RMSE, and ρ. Specifically, in terms
of MAE (measuring absolute error), our model achieves a
minimal skin tone difference of 0.26, which is 61.2% lower
than the suboptimal Vilesov et al. [17] (0.67) and outperforms
conventional methods ICA (4.42) [9], CHROM (4.97) [6], and
PhysNet (2.22) [10] by factors of approximately 17, 19, and
8.5, respectively.
Regarding RMSE, our model shows a notable improvement
with a value of 1.28, achieving 11.1% and 68.4% reductions
compared to Vilesov et al. (1.44) [17] (1.44) and PhysNet
(4.05) [10], respectively. In terms of ρ , which represents the
difference in correlation between light and dark skin samples,
0
1
2
3
4
5
6
60
70
80
90
100
Time(Seconds)
Heart Rate (BPM)
Ground Truth
Predicted HR
(a) Heart Rate
0
1
2
3
4
5
-2
-1
0
1
2
Ground Truth
Predicted PPG
Time(Seconds)
(b) PPG
Fig. 7: Comparison of ground truth and predicted continuous
heart rate and PPG signals. (a) The ground truth (red) and
predicted heart rate (blue) over time (in seconds). (b) The
ground truth (red) and predicted PPG signals (blue) over
time (in seconds).
our model achieves a minimal difference of 0.05, demonstrat-
ing a much smaller skin tone bias compared to the significantly
higher differences found in ICA (-0.36) [9], CHROM (-0.38)
[6], and PhysNet (-0.25) [10]. This indicates that our approach
ensures more consistent and fair performance across different
skin tones. These results demonstrate that by integrating
multimodal signals from RGB and radio frequency (RF),
our model effectively mitigates spectral reflectance estimation
biases caused by skin tone variations in traditional unimodal
methods, providing a more reliable technical pathway for
fairness-sensitive applications.
E. Measurement in Missing Modality Scenarios
In robustness testings under missing modalities, the pro-
posed multimodal fusion model (RGB and RF) demonstrates
exceptional adaptability. As shown in TABLE III, the model
maintains leading performance in most scenarios even when
partial modalities are missing during testing (e.g., RGB-only
or RF-only). Under full-modality testing (RGB and RF), our
model achieves optimal results outperform Vilesov et al.[17]
IEEE TRANSACTIONS ON INSTRUMENTATION AND MEASUREMENT
10
110
100
90
80
70
60
0
1
2
3
4
5
6
Ground Truth
Predicted(RGB-RF)
Predicted(RGB-Only)
Time(Seconds)
Heart Rate (BPM)
Fig. 8: Visualization of continuous HR results between RGB-
only and RGB-RF fusion Methods
by 14.3% and 10.5%, respectively, and surpassing the baseline
model by over 20-fold, thereby validating the efficacy of deep
multimodal fusion.
In RGB-only testing, our model reduces MAE by 82.4%
compared to Vilesov et al. [17], with error levels approaching
full-modality performance, highlighting the robust generaliza-
tion of RGB feature extraction. While the model underper-
forms Vilesov et al. [17] (MAE=7.25, RMSE=9.62) in RF-only
testing , its superiority under full modalities confirms that RF
signals primarily serve as complementary components within
the framework, maximizing value through multimodal synergy.
This capability not only underscores the model’s robustness
to modality incompleteness but also ensures reliable deploy-
ment in real-world complex environments.
F. Ablation Study
As shown in TABLE IV, to validate the contribution of
each module, we conducted systematic ablation studies. The
results demonstrate that the Vision Mamba and Channel-
wise Fast Fourier Transform (CFFT) are critical to model
accuracy. While excluding Vision Mamba (first row) retains
decent performance (MAE=1.7, R=0.91), removing CFFT
(second row) causes severe degradation (MAE=18.8, ρ=0.2),
indicating that cross-modal feature alignment heavily relies on
frequency-domain compensation. The spatiotemporal synchro-
nization module (SSM) and RF Alignment Module (RFAM)
provide auxiliary stabilization and detail enhancement. Their
individual absence only slightly increases MAE to 1.862 and
1.85, respectively, while maintaining ρ > 0.89, proving the
model’s tolerance to partial module failure. Notably, the ex-
clusion of the Temporal Difference Mamba Module(TDMM)
doubles MAE (3.82 vs. 1.7) and increases RMSE by 64.5%,
highlighting its essential role in temporal consistency reg-
ulation. In conclusion, Vision Mamba and CFFT form the
core framework, while SSM, channel attention, and Time
difference collaboratively refine performance through multi-
level optimization, achieving balanced metrics (MAE=1.7,
ρ=0.91), thereby validating the completeness and robustness
of our modules.
G. Visualization and Analysis
Face and Radar Spectrum Feature Visualizations: As
shown in Fig. 5, we present the visual representations of both
the RGB and RF modalities. Fig. 5a shows an image from the
EquiPleth dataset, where the human face is captured. Fig. 6b
highlights a feature heatmap of this image, illustrating the
key regions of interest for heart rate estimation. The heatmap
emphasizes areas with strong signal correlation, such as the
face’s skin regions. Moving to Fig. 5c, the radar spectrum
diagram visualizes the frequency information captured by the
radar. Finally, Fig. 5d presents the feature heatmap of the
radar spectrum, where key frequency components related to
physiological signals are emphasized. This series of images
provides a clear comparison of the spatial and frequency-
domain features from the two modalities.
Bland-Altman Plots for CardiacMamba and Other
Methods.: Fig. 6 shows the Bland-Altman plots comparing
the heart rate estimates from CardiacMamba and Vilesov et al.
[17] with the ground truth values. Fig. 6a illustrates the Bland-
Altman plot for our CardiacMamba model, demonstrating that
the heart rate estimates are more tightly clustered within the
confidence interval, signifying greater accuracy and consis-
tency. In contrast, Fig. 6b presents the results from Vilesov et
al. [17], which show a broader spread and higher variance in
heart rate predictions. This comparison highlights the superior
performance of CardiacMamba in terms of estimation stability
and accuracy.
Comparison of Ground Truth and Predicted Signals for
Heart Rate and PPG: As shown in Fig. 7, Fig. 6b compares
the ground truth (red) and predicted heart rate (blue) signals
over time (in seconds). The predicted heart rate closely follows
the ground truth, with minimal fluctuations, indicating high
prediction accuracy. The consistency between the two curves
demonstrates the robustness of the model in estimating heart
rate. Fig. 7b presents the comparison between the ground
truth (red) and predicted PPG signals (blue) over time. The
predicted PPG signal accurately mirrors the ground truth,
confirming the model’s capability in tracking the periodic
patterns of the PPG signal. This comparison underscores the
model’s effectiveness in predicting the physiological signal
Comparison of HR Results Between RGB-only and
RGB-RF Fusion Methods: Fig. 8 compares the heart rate
predictions using two methods: RGB-only (yellow) and RGB-
RF Fusion (blue), against the ground truth (red) over time (in
seconds). It is clear that the predictions from the RGB-RF
fusion model (blue) are much closer to the ground truth, with
less fluctuation and greater stability compared to the RGB-only
predictions (yellow). The RGB-RF fusion method outperforms
the RGB-only approach, demonstrating its superior accuracy,
stability, and robustness. The fusion model provides smoother
and more consistent heart rate estimation.
V. CONCLUSION
In this paper, we propose the CardiacMamba, a multi-
modal fusion framework for rPPG heart rate estimation from
RGB video and radio frequency (RF) sensors. CardiacMamba
achieves dual-level feature extraction and alignment through
IEEE TRANSACTIONS ON INSTRUMENTATION AND MEASUREMENT
11
time-differential perception and convolution alignment mod-
ules, enhancing the dynamic features of both RGB and RF
modalities, while leveraging Mamba blocks to improve fea-
ture expression. Based on a bidirectional state-space model,
it performs cross-modal collaborative modeling, preserving
the semantic information of each modality and enhancing
global context awareness. Additionally, the channel Fourier
transform adaptively enhances heart rate-related frequency
bands, suppresses noise, and reconstructs temporal features,
improving heart rate signal detection. Experimental results
demonstrate that this framework outperforms existing meth-
ods across multiple performance metrics, effectively mitigates
skin tone bias, improves accuracy for darker skin samples,
and maintains strong adaptability even in cases of missing
modalities, significantly enhancing accuracy, robustness, and
fairness.
REFERENCES
[1] M. A. R. Ahad, U. Mahbub, and T. Rahman, Contactless
Human Activity Analysis.
Springer, 2021.
[2] J. Cheng, P. Wang, R. Song, Y. Liu, C. Li, Y. Liu, and
X. Chen, “Remote heart rate measurement from near-
infrared videos based on joint blind source separation
with delay-coordinate transformation,” IEEE Transac-
tions on Instrumentation and Measurement, vol. 70, pp.
1–13, 2020.
[3] B. Liu, X. Zheng, and Y. I. Wu, “Remote heart rate
estimation in intense interference scenarios: A white-box
framework,” IEEE Transactions on Instrumentation and
Measurement, 2024.
[4] M. Hu, F. Qian, D. Guo, X. Wang, L. He, and F. Ren,
“Eta-rppgnet: Effective time-domain attention network
for remote heart rate measurement,” IEEE Transactions
on Instrumentation and Measurement, vol. 70, pp. 1–12,
2021.
[5] Z. Yu, X. Li, and G. Zhao, “Facial-video-based phys-
iological signal measurement: Recent advances and af-
fective applications,” IEEE Signal Processing Magazine,
vol. 38, no. 6, pp. 50–58, 2021.
[6] G.
D.
Haan
and
V.
Jeanne,
“Robust
pulse
rate
from chrominance-based rppg,” IEEE Transactions on
Biomedical Engineering, vol. 60, no. 10, pp. 2878–2886,
2013.
[7] W. Verkruysse, L. O. Svaasand, and J. S. Nelson, “Re-
mote plethysmographic imaging using ambient light,”
Optics Express, vol. 16, no. 26, pp. 21 434–21 445, 2008.
[8] M.
Lewandowska,
J.
Rumi´nski,
T.
Kocejko,
and
J. Nowak, “Measuring pulse rate with a webcam—a
non-contact method for evaluating cardiac activity,” in
2011 Federated Conference on Computer Science and
Information Systems (FedCSIS).
IEEE, 2011, pp. 405–
410.
[9] M.-Z. Poh, D. J. McDuff, and R. W. Picard, “Ad-
vancements in noncontact, multiparameter physiological
measurements using a webcam,” IEEE Transactions on
Biomedical Engineering, vol. 58, no. 1, pp. 7–11, 2010.
[10] Z. Yu, X. Li, and G. Zhao, “Remote photoplethys-
mograph signal measurement from facial videos using
spatio-temporal networks,” in The British Machine Vision
Conference (BMVC), 2019.
[11] E. M. Nowara, T. K. Marks, H. Mansour, and A. Veer-
araghavan, “Sparseppg: Towards driver monitoring using
camera-based vital signs estimation in near-infrared,” in
Proceedings of the IEEE Conference on Computer Vision
and Pattern Recognition Workshops.
IEEE, 2018, pp.
1272–1281.
[12] J.-K. Park, Y. Hong, H. Lee, C. Jang, G.-H. Yun, H.-J.
Lee, and J.-G. Yook, “Noncontact rf vital sign sensor for
continuous monitoring of driver status,” IEEE Transac-
tions on Biomedical Circuits and Systems, vol. 13, no. 3,
pp. 493–502, 2019.
[13] T. Zheng, Z. Chen, C. Cai, J. Luo, and X. Zhang,
“V2ifi: In-vehicle vital sign monitoring via compact rf
sensing,” Proceedings of the ACM on Interactive, Mobile,
Wearable and Ubiquitous Technologies (IMWUT), vol. 4,
no. 2, pp. 1–27, 2020.
[14] M. Alizadeh, G. Shaker, J. C. M. D. Almeida, P. P.
Morita, and S. Safavi-Naeini, “Remote monitoring of
human vital signs using mm-wave fmcw radar,” IEEE
Access, vol. 7, pp. 54 958–54 968, 2019.
[15] C. Li and J. Lin, “Random body movement cancellation
in doppler radar vital sign detection,” IEEE Transactions
on Microwave Theory and Techniques, vol. 56, no. 12,
pp. 3143–3152, 2008.
[16] S. Wu, T. Sakamoto, K. Oishi, T. Sato, K. Inoue,
T. Fukuda, K. Mizutani, and H. Sakai, “Person-specific
heart rate estimation with ultra-wideband radar using
convolutional neural networks,” IEEE Access, vol. 7, pp.
168 484–168 494, 2019.
[17] A. Vilesov, P. Chari, A. Armouti, A. B. Harish, K. Kulka-
rni, A. Deoghare, L. Jalilian, and A. Kadambi, “Blending
camera and 77 ghz radar sensing for equitable, ro-
bust plethysmography,” ACM Transactions on Graphics,
vol. 41, no. 4, pp. 1–14, 2022.
[18] G. Balakrishnan, F. Durand, and J. Guttag, “Detecting
pulse from head motions in video,” in Proceedings of
the IEEE Conference on Computer Vision and Pattern
Recognition (CVPR).
Portland, OR, USA: IEEE, 2013,
pp. 3430–3437.
[19] M.-Z. Poh, D. J. McDuff, and R. W. Picard, “Noncon-
tact, automated cardiac pulse measurements using video
imaging and blind source separation,” Optics Express,
vol. 18, no. 10, pp. 10 762–10 774, 2010.
[20] H. Monkaresi, R. A. Calvo, and H. Yan, “A machine
learning approach to improve contactless heart rate moni-
toring using a webcam,” IEEE Journal of Biomedical and
Health Informatics, vol. 18, no. 4, pp. 1153–1160, 2014.
[21] Z.-K. Wang, Y. Kao, and C.-T. Hsu, “Vision-based heart
rate estimation via a two-stream cnn,” in Proceedings of
the IEEE International Conference on Image Processing
(ICIP).
Taipei, Taiwan: IEEE, 2019, pp. 3327–3331.
[22] W. Chen and D. McDuff, “Deepphys: Video-based phys-
iological measurement using convolutional attention net-
works,” in Proceedings of the European Conference on
Computer Vision (ECCV), 2018, pp. 349–365.
[23] Z. Yu, Y. Shen, J. Shi, H. Zhao, P. H. Torr, and
IEEE TRANSACTIONS ON INSTRUMENTATION AND MEASUREMENT
12
G. Zhao, “Physformer: Facial video-based physiological
measurement with temporal difference transformer,” in
Proceedings of the IEEE/CVF Conference on Computer
Vision and Pattern Recognition, 2022, pp. 4186–4196.
[24] B. Zou, Z. Guo, J. Chen, and H. Ma, “Rhythmformer:
Extracting rppg signals based on hierarchical temporal
periodic transformer,” arXiv preprint arXiv:2402.12788,
2024.
[25] Z. Yu, Y. Shen, J. Shi, H. Zhao, Y. Cui, J. Zhang, P. Torr,
and G. Zhao, “Physformer++: Facial video-based physi-
ological measurement with slowfast temporal difference
transformer,” International Journal of Computer Vision,
vol. 131, no. 6, pp. 1307–1330, 2023.
[26] E. M. Nowara, D. McDuff, and A. Veeraraghavan, “The
benefit of distraction: Denoising camera-based physio-
logical measurements using inverse attention,” in Pro-
ceedings of the IEEE International Conference on Com-
puter Vision (ICCV), 2021, pp. 4955–4964.
[27] J. C. Lin, “Noninvasive microwave measurement of res-
piration,” Proceedings of the IEEE, vol. 63, no. 10, pp.
1530–1530, 1975.
[28] U. Ha, S. Assana, and F. Adib, “Contactless seismo-
cardiography via deep learning radars,” in Proceedings
of the ACM Annual International Conference on Mobile
Computing and Networking (MobiCom), 2020, pp. 1–14.
[29] T. Zheng, Z. Chen, S. Zhang, C. Cai, and J. Luo, “More-
fi: Motion-robust and fine-grained respiration monitoring
via deep-learning uwb radar,” in Proceedings of the ACM
Conference on Embedded Networked Sensor Systems
(SenSys), New York, NY, USA, 2021, pp. 111–124.
[30] T. Negishi, S. Abe, T. Matsui, H. Liu, M. Kurosawa,
T. Kirimoto, and G. Sun, “Contactless vital signs mea-
surement system using rgb-thermal image sensors and
its clinical screening test on patients with seasonal in-
fluenza,” Sensors, vol. 20, no. 8, p. 2171, 2020.
[31] K. Matsumura, S. Toda, and Y. Kato, “Rgb and near-
infrared light reflectance/transmittance photoplethysmog-
raphy for measuring heart rate during motion,” IEEE
Access, vol. 8, pp. 80 233–80 242, 2020.
[32] S. Park, B.-K. Kim, and S.-Y. Dong, “Self-supervised
rgb-nir fusion video vision transformer framework for
rppg estimation,” IEEE Transactions on Instrumentation
and Measurement, vol. 71, pp. 1–10, 2022.
[33] A. Gu, K. Goel, and C. R´e, “Efficiently modeling long
sequences with structured state spaces,” in Proceedings
of the Tenth International Conference on Learning Rep-
resentations (ICLR), 2022.
[34] D. Y. Fu, T. Dao, K. K. Saab, A. W. Thomas, A. Rudra,
and C. R´e, “Hungry hungry hippos: Towards language
modeling with state space models,” in Proceedings of
the Eleventh International Conference on Learning Rep-
resentations (ICLR), 2023.
[35] H. Mehta, A. Gupta, A. Cutkosky, and B. Neyshabur,
“Long range language modeling via gated state spaces,”
in Proceedings of the Eleventh International Conference
on Learning Representations (ICLR 2023), 2023.
[36] J. T. H. Smith, A. Warrington, and S. W. Linderman,
“Simplified state space layers for sequence modeling,”
in Proceedings of the Eleventh International Conference
on Learning Representations (ICLR), 2023.
[37] X. Xie, Y. Cui, T. Tan, X. Zheng, and Z. Yu, “Fusion-
mamba: Dynamic feature enhancement for multimodal
image fusion with mamba,” Visual Intelligence, vol. 2,
no. 1, p. 37, 2024.
[38] C. Luo, Y. Xie, and Z. Yu, “Physmamba: Efficient re-
mote physiological measurement with slowfast temporal
difference mamba,” in Chinese Conference on Biometric
Recognition, 2024, pp. 248–259.
[39] L. Zhu, B. Liao, Q. Zhang, X. Wang, W. Liu, and
X. Wang, “Vision mamba: Efficient visual representa-
tion learning with bidirectional state space model,” in
Proceedings of the International Conference on Machine
Learning (ICML), 2024.
[40] X. Liu, J. Fromm, S. Patel, and D. McDuff, “Multi-task
temporal shift attention networks for on-device contact-
less vitals measurement,” in Advances in Neural Infor-
mation Processing Systems (NeurIPS), Virtual, 2020, pp.
1–23.
[41] X. Liu, B. Hill, Z. Jiang, S. Patel, and D. McDuff, “Effi-
cientphys: Enabling simple, fast and accurate camera-
based cardiac measurement,” in Proceedings of the
IEEE/CVF Winter Conference on Applications of Com-
puter Vision, 2023, pp. 5008–5017.
[42] B. Zou, Z. Guo, X. Hu, and H. Ma, “Rhythmmamba: Fast
remote physiological measurement with arbitrary length
videos,” arXiv preprint arXiv:2404.06483, 2024.
[43] J. Tu, T. Hwang, and J. Lin, “Respiration rate measure-
ment under 1-d body motion using single continuous-
wave doppler radar vital sign detection system,” IEEE
Transactions on Microwave Theory and Techniques,
vol. 64, no. 6, pp. 1937–1946, 2016.
[44] M. Mercuri, I. Lorato, Y.-H. Liu, P. Wieringa, F. V.
Hoof, and T. Torfs, “Vital-sign monitoring and spatial
tracking of multiple people using a contactless radar-
based sensor,” Nature Electronics, vol. 2, pp. 252–262,
2019.
[45] J. Ye, J. Zhang, and H. Shan, “Depmamba: Progressive
fusion mamba for multimodal depression detection,”
arXiv
preprint
arXiv:2409.15936,
2024.
[Online].
Available: https://arxiv.org/abs/2409.15936
[46] K. Zhang, Z. Zhang, Z. Li, and Y. Qiao, “Joint face
detection and alignment using multitask cascaded con-
volutional networks,” IEEE Signal Processing Letters,
vol. 23, no. 10, pp. 1499–1503, 2016.
