Received: 2 December 2022
-
Revised: 20 February 2023
-
Accepted: 3 March 2023
-
IET Signal Processing
DOI: 10.1049/sil2.12201
O R I G I N A L R E S E A R C H
Attention‐based sensor fusion for emotion recognition from
human motion by combining convolutional neural network and
weighted kernel support vector machine and using inertial
measurement unit signals
Yan Zhao1
|
Ming Guo1
|
Xuehan Sun2
|
Xiangyong Chen1
|
Feng Zhao1
1School of Automation and Electrical Engineering,
Linyi University, Linyi, Shandong, China
2School of Physical Education and Health, Linyi
University, Linyi, Shandong, China
Correspondence
Xuehan Sun and Ming Guo.
Email: sunxuehan@lyu.edu.cn
and guoming0537@126.com
Funding information
Natural Science Foundation of Shandong Province,
Grant/Award Numbers: ZR2019BF045,
ZR2019MF021, ZR2019QF004; National Natural
Science Foundation of China, Grant/Award
Numbers: 61877033, 61903170, 62173175; Key
Research and Development Project of Shandong
Province of China, Grant/Award Number:
2019GGX101003
Abstract
The remarkable development of human–computer interactions has created an urgent
need for machines to be able to recognise human emotions. Human motions play a key
role in emphasising and conveying emotions to meet the complexity of daily application
scenarios, such as medical rehabilitation and social education. Therefore, this paper aims
to explore hidden emotional states from human motions. Accordingly, we proposed a
novel approach for emotion recognition using multiple inertial measurement unit (IMU)
sensors worn on different body parts. First, the mapping relationship between emotion
and human motion was established through fuzzy comprehensive evaluation, and data
were collected for six emotional states: sleepy, bored, excited, tense, angry, and distressed.
Second, the preprocessed data were used as input in a lightweight convolutional neural
network to extract discriminative features. Third, an attention‐based sensor fusion
module was developed to obtain the importance scores of each IMU sensor for gener-
ating a fused feature representation. In the recognition phase, we constructed a weighted
kernel support vector machine (SVM) model with an auxiliary fuzzy function to improve
the weight calculation method of kernel functions in a multiple kernel SVM. Finally, the
results obtained are compared with those of similar state‐of‐the‐art studies, the proposed
method showed a higher accuracy (99.02%) for the six emotional states mentioned above.
These findings may promote the development of social robots with non‐verbal emotional
communication capabilities.
K E Y W O R D S
emotion recognition, fuzzy comprehensive evaluation, human motion, neural network, sensor fusion, weighted
kernel support vector machine
1
|
INTRODUCTION
Artificial intelligence and human–computer interactions are
showing a trend of rapid growth, and emotion recognition
plays an important role in improving the intelligence of
human–computer interaction [1]. However, the problem that
must be solved with respect to human–computer interaction is
emotional intelligence, which is consistent with the commu-
nication between people. The scope of artificial intelligence can
be increased only when sufficient emotional intelligence is
achieved. The application value and potential of emotion
recognition in various fields have continued to increase. For
example, in the medical rehabilitation industry, emotion
recognition provides therapeutic strategies for autism spectrum
disorder research, which can improve physicians' understand-
ing of patients' emotions and adjust the patient's experience
accordingly. Furthermore, the emotional robots invented using
emotion recognition technology can considerably relieve
This is an open access article under the terms of the Creative Commons Attribution‐NonCommercial‐NoDerivs License, which permits use and distribution in any medium, provided the
original work is properly cited, the use is non‐commercial and no modifications or adaptations are made.
© 2023 The Authors. IET Signal Processing published by John Wiley & Sons Ltd on behalf of The Institution of Engineering and Technology.
IET Signal Process. 2023;e12201.
wileyonlinelibrary.com/journal/sil2
-
1 of 12
https://doi.org/10.1049/sil2.12201
anxiety in the elderly. For example, the seal‐like robot “Paro,”
which was tested in Norwegian nursing homes, can respond
affectionately to human touch.
Emotion is a psychological response to external stimuli or
changes, and its expression can be verbal or non‐verbal. The
former is represented by known words, whereas the latter,
includes changes in facial expressions, speech, and the auto-
nomic nervous system. Human motion, as an important
component
of
body
language,
also
conveys
important
emotional information. Human motion recognition is widely
used in biomedical monitoring [2], clinical evaluation [3], and
sports competition [4]. Research has shown that human mo-
tion is an important way of expressing emotions [5]. People
perceive each other's emotional states through motions. In
reality, human–computer interaction scenarios are complex,
and emotion recognition methods based on human motion can
play a crucial role when facial expressions and speech are
invalid.
Most emotion recognition research mainly uses visual
methods [6, 7] that can provide a wealth of information and
intuitive performance. But image or video processing tech-
nology requires a large number of memory resources on high‐
specification computers. Moreover, illumination and occlusion
in monitoring scenes can reduce recognition accuracy. High‐
performance inertial measurement unit (IMU) sensors have
made a great breakthrough and have been widely used in
motion analysis [8], gait evaluation [9], and communication
positioning [10]. They are worn on one or more parts of the
body for data collection and comprise built‐in accelerometers,
gyroscopes, and magnetometers. Inertial measurement unit
sensor systems are inexpensive compared with vision‐based
systems, and they can easily collect data for extended periods
without environmental constraints.
Emotion recognition is an important part of emotion
computing, where features that can fully express emotion are
obtained from various body signals and the mapping rela-
tionship between external representations and internal states
are detected. Classical machine learning methods for emotion
recognition rely on manually extracted features as input for
classifiers, such as statistical regularities and signal distributions
[11]. These features are obtained through experience, domain
knowledge, and experimental validation. But this operation
may ignore some useful features, hence it cannot be applied to
different scenarios.
Automated feature engineering is a relatively new technique
for solving a range of scientific problems in real‐world datasets.
It can reduce time cost and generate meaningful and interpret-
able features to build predictive models. As a widely used and
effective deep
learning
technology,
convolutional
neural
network (CNN) has achieved superior performance in com-
puter vision and natural language processing. It has also received
extensive attention in the field of inertial signal processing.
Furthermore, the efficient, simple, and lightweight CNN en-
ables hardware deployment on mobile sensing terminals [12].
This paper aims to explore the hidden emotional states
from human motion and make accurate identification, which
helps to promote the development of non‐verbal behaviour in
human–computer interaction and equip machines to have
emotional communication capabilities. We consider that this is
helpful to improve the intelligence and emotionalisation of
human–computer interaction at this stage. Figure 1 shows the
overall architecture for emotion recognition from human
motion using wearable IMU sensors. This method mainly
comprises emotional data collection, feature extraction, IMU
sensor fusion, and emotion recognition. And we believe that
the use of multiple IMU sensors on different locations of the
body can improve the emotion recognition accuracy. For this
paper, the main contributions are as follows:
(1) A new emotion recognition method based on human
motion was proposed. In this method, multiple wearable
IMU sensors located in different body parts are aggregated
to better recognise emotions.
(2) A sensor‐based feature extraction module was designed. It
uses a three‐layer lightweight CNN to extract critical and
discriminative features from IMU signals, and fully con-
siders the correlation between signals.
(3) An attention‐based sensor fusion module was developed.
It automatically learns attention weights from the fused
features to assign importance scores to each IMU sensor.
F I G U R E 1
The overall process of emotion recognition from human motion using inertial measurement unit (IMU) sensors.
2 of 12
-
ZHAO ET AL.
 17519683, 2023, 4, Downloaded from https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/sil2.12201, Wiley Online Library on [19/03/2026]. See the Terms and Conditions (https://onlinelibrary.wiley.com/terms-and-conditions) on Wiley Online Library for rules of use; OA articles are governed by the applicable Creative Commons License
(4) A weighted kernel support vector machine (WK‐SVM)
model was presented. It uses a fuzzy function to assist in
calculating the weight of the kernel function in multiple
kernel SVM to realise the flexible expression of hetero-
geneous data in the IMU sensor.
2
|
RELATED WORK
Facial expressions are a form of communication that expresses
emotions directly and is one of the earliest researched topics in
the field of emotion recognition. Many scholars have conducted
in‐depth research on facial emotion recognition achieving
advanced results. Hassan et al. [13] proposed a facial emotion
recognition method based on graph mining, where the facial
regions are represented as a graph of nodes and edges. They
used the frequent subgraph mining algorithm gSpan to locate
frequent substructures in the graph datasets. Chowdary et al.
[14] adopted a transfer learning approach to study emotion
recognition using pretrained networks: ResNet50, VGG19,
Inception V3, and MobileNet. Li et al. [15] proposed an
enhanced broad Siamese network algorithm for facial emotion
recognition in robotic applications by combining a broad
learning system with a Siamese network, which reduces time and
memory costs. Zhang et al. [16] proposed two methods to
recognise the facial expressions of elderly people using a home
service robot: a double‐channel weighted mixture deep CNN
based on static images and deep CNN long short‐term memory
(LSTM) networks of the double‐channel weighted mixture
based on image sequences.
Speech is also an important way to express emotions. Most
research uses acoustic features for speech emotion recognition
and analyses the correlation between various emotions. Tao et al.
[17] used semi‐supervised learning to construct a ladder
network for speech emotion recognition with a small amount of
labelled data and achieved good recognition efficiency. Musta-
qeem et al. [18] proposed a two‐stream deep CNN for speech
emotion recognition with iterative neighbourhood component
analysis to learn the spectral features of the mutual space and
select the most discriminative optimal features. Zhao et al. [19]
designed a merged CNN consisting of a one‐dimensional (1D)
and a two‐dimensional (2D) CNN branches. Furthermore, they
used bayesian optimisation to select parameters to learn deep
features from different data for speech emotion recognition. To
extract speech emotional features, Ancilin et al. [20] improved
the extraction process of Mel frequency cepstral coefficients to
construct Mel frequency amplitude coefficients, replacing en-
ergy spectrum with amplitude spectrum and excluding discrete
cosine transform. Then, a multiclass SVM was used as a clas-
sifier for automatic recognition of speech emotion.
But in many cases, recognising emotions from facial ex-
pressions and speech is challenging, mainly because the source
may be unreliable. People can control their expressions and
speech through subjective consciousness to cover up real
emotions. Emotion recognition research based on human mo-
tion has attracted large attention in the field of human–
computer interactions, and the advancements in IMU sensors
have led to efficient and convenient information interaction
between humans and devices. Recent studies have attempted to
recognise emotions from human motion via attaching wearable
inertial devices on different parts of the body to acquire
emotional information. Hashmi et al. [21] used a smartphone
worn on the chest to record human gait signals, and used the
calculated spectro‐temporal features for each stride signal as
input of random forest and SVM for identifying six basic
emotions. Gravina et al. [22] used sensor‐level and feature‐level
fusion techniques to identify and monitor in‐seat activities to
reflect psychological and emotional states. Although the hand-
made features used in this study have good interpretability, the
feature construction is time‐consuming and laborious, and re-
quires careful design based on experience and data characteris-
tics. Hnatiuc et al. [23] aimed to analyse writing movement using
a pencil equipped with vibration, accelerometer, and gyroscope
sensors. They used the hand motion signals generated during
writing to detect emotional states, but this is not friendly to long‐
term data monitoring under different writing habits. Chang et al.
[24] used intelligent inertial sensors to identify emotions during
badminton movement, and sensors can respond to emotional
changes, such as happiness, nausea, and sadness. However, with
the increase of exercise time, the degree of physical fatigue af-
fects the recognition effect of emotion.
3
|
MATERIALS AND METHODS
3.1
|
Emotion dataset
The first step in emotion recognition is to define emotion.
Russell [25] proposed the circumplex model of emotion
(Figure 2), which is widely approved and applied in various
emotion recognition studies. Here, emotion is divided into
pleasure and arousal dimensions, and some areas in the model
space are interpreted as 28 discrete emotions. The next step
F I G U R E 2
The circumplex model of emotion.
ZHAO ET AL.
-
3 of 12
 17519683, 2023, 4, Downloaded from https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/sil2.12201, Wiley Online Library on [19/03/2026]. See the Terms and Conditions (https://onlinelibrary.wiley.com/terms-and-conditions) on Wiley Online Library for rules of use; OA articles are governed by the applicable Creative Commons License
requires the support of a public dataset. Scherer and Ellgring
[26] listed multiple types of limb movements and 14 common
emotions and obtained the correlation between them through
statistical experiments.
So this paper establishes an emotion dataset composed of
human motion labels and emotion labels based on the 14 basic
emotions mentioned by Ref. [26], some of which are not
involved. We initially used “sleepy,” “bored,” “excited,” “tense,”
“angry,” and “distressed” as emotional labels, which are marked
with triangles in Figure 2. Human motion labels include
stretching, waving hands, applauding, rubbing hands, swing fist,
and covering face with hands.
Simple reference to the datasets provided in the relevant
literature is not sufficient. Additionally, a fuzzy comprehensive
evaluation is required to further determine the mapping rela-
tionship between emotions and human motions. The initially
selected labels were sequentially evaluated by 20 experts for
correlation. Combining the supported datasets and evaluation
scores, we determined the one‐to‐one correspondence be-
tween emotions and human motions, as shown in Figure 3.
3.2
|
System platform and data collection
This paper constructs a platform for a multisensor wireless
transmission system platform composed of four wireless nine‐
axis IMU sensors and four Bluetooth signal receivers. Each
IMU sensor (WIT Inc., CHN) has a built‐in ICM‐42605
(accelerometer and gyroscope) and MMC3630 (magnetom-
eter), and are small, wearable, and low‐power consuming.
Table 1 lists the main parameters. Each inertial sensor reads
nine analog‐to‐digital conversion output values, including
three‐axis acceleration, three‐axis angular rate, and three‐axis
magnetic field. Then, the read data are transmitted to a per-
sonal computer through a USB port of a Bluetooth receiver
(HC06‐HID), which receives and processes these nine‐axis
data. The whole data transmission process is shown in
Figure 4.
Generally, the collection of human motion data for
emotion recognition is a difficult task because it requires
subjects to generate the corresponding real emotion. More-
over, this process is a spontaneous response mediated by the
nervous system. To address the problem of emotion stimula-
tions, we employed an audition stimulus modality where sub-
jects watch emotional video clips with correlated effects during
data acquisition. A total of nine healthy volunteers were
selected to participate in the data collection, which included
five males and four females aged 22–26 years. They were
screened for their physical fitness and ability to respond
emotionally to external stimuli. We chose to deploy four mo-
tion sensors to monitor the whole body movement for
emotional information and its sampling frequency was set to
50 Hz, the sensors were attached to the left wrist, right wrist,
waist and head. To adequately sample a continuous movement
of non‐momentary emotions, each subject should collect data
for each emotion for 120 consecutive seconds and the same
movement should be sampled repeatedly. And it was assumed
that all wearable sensors are firmly fixed at selected body lo-
cations throughout the recording. During this process, the
volunteers continued to repeat actions based on their own
habits and methods, but the normal data collection cannot be
disturbed. This paper collects six emotions shown in Table 2,
which are sleepy (stretching), bored (wave hand), excited
(applause), tense (rub hands), angry (swing fist), and distressed
(cover face with hands). Figure 5 shows the partial emotional
data collected by the x‐axis accelerometer of the sensor on the
right wrist of the first volunteer for six different emotions.
3.3
|
Signal preprocessing
To facilitate feature extraction from a large amount of
emotional motion data collected by IMU sensors, signals need
F I G U R E 3
Illustration of the mapping relationship between emotions
and human motions.
T A B L E 1
The main parameters of inertial measurement unit (IMU)
sensors.
Range
Resolution
Accelerometer
16 g
0.0005 (g/LSB)
Gyroscope
2000°/s
0.061 (°/s)/(LSB)
Magnetometer
2 Gauss
0.0667 mGauss/LSB
F I G U R E 4
Construction of the system platform.
4 of 12
-
ZHAO ET AL.
 17519683, 2023, 4, Downloaded from https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/sil2.12201, Wiley Online Library on [19/03/2026]. See the Terms and Conditions (https://onlinelibrary.wiley.com/terms-and-conditions) on Wiley Online Library for rules of use; OA articles are governed by the applicable Creative Commons License
to be divided into data segments using window segmentation
technology. We used a sliding window‐based data segmentation
technique, which includes two parameters: window width and
overlap rate. The overlap of adjacent windows prevents data
loss at window edges, thereby completely retaining all infor-
mation. Emotional motion data were divided according to an
overlap rate of 50% and window width of 2 s (100 sampling
points). Within this frame, a total of 6496 samples with a size
of 100  9 were obtained. The original data obtained from
accelerometers, gyroscopes, and magnetometers were also
fused using the Kalman filter algorithm.
Since the units and ranges of the emotional data collected
by the accelerometers, gyroscopes, and magnetometers were
inconsistent, Z‐score was used to standardise the input data of
the classifier. For this purpose, we used the following formula:
X∗¼ X −X
sðXÞ
ð1Þ
where X is the mean and s(X) is the standard deviation.
3.4
|
Single‐sensor feature extraction
After signal preprocessing, we need to convert the IMU sensor
data passed to the CNN into formatted tensors. Then, the size
of the input data is channel (C)  width (W)  height (H), and
their amplitude range is 0; 1
½
. For example, the size of the
inertial sensor data sample after preprocessing is 1009
(WH, two‐dimensional). Then, the input to the lightweight
CNN network needs to be represented as a formatted tensor,
so the inertial data sample size is 1  100  9 (CWH,
three‐dimensional), and the number of channels is 1. Con-
volutional neural network is composed of alternating con-
volutional layers and max‐pooling layers, whose fundamental
features include local receptive field, weight sharing, and
pooling layer. Compared with artificial neural network, CNN
has interpretability, indicating that the target features can be
designed for a certain purpose. Furthermore, CNN shares
convolution kernels, which can process high‐dimensional data
quickly and efficiently. This structure can reduce the amount of
memory occupied by the deep network, thereby effectively
reducing the number of network parameters, and alleviating
the overfitting problem.
The
input
of
CNN
is
composed
of
N
samples:
N ¼ D1; …; Dn; …; DN
½
. Each sample contains S IMU sen-
sors Dn = [d1, d2, …, dS]. The shape of each input data is
Cin; Hin; Win
½
, and features are extracted layer by layer using a
2D convolution operation. The formula for calculating the
feature map size of the lth convolutional layer is as follows:
Cl
out ¼ K
ð2Þ
Hl
out ¼ Hl−1
in −Hk þ 2Pw
Sh
þ 1
ð3Þ
W l
out ¼ W l−1
in −Wk þ 2Ph
Sw
þ 1
ð4Þ
where the shape of the feature map output by the l‐th con-
volutional layer is
Cl
out; Hl
out; W l
out
h
i
, the number and shape
of the 2D convolution kernel are K and Hk; Wk
½
, and the
stride and padding are Sh; Sw
½
 and Ph; Pw
½
, respectively. The
pooling layer also has a sliding kernel similar to the convolution
layer, which can reduce the amount of obtained data in the
feature map through convolution.
This paper designs a feature extraction module to learn the
correlation between multiple channels of a single IMU sensor
using a three‐layer lightweight CNN, as shown in Figure 6.
Additionally, the parameters of the proposed lightweight CNN
are shown in Table 3. For the first convolutional layer, there are
64 convolution kernels with a size of 1  5 and a stride length
of 1 moving across all axes of the feature map. This setting
allows us to examine the relationship among time‐series data in
a single channel of the input IMU signal sample data. The
input of the second convolutional layer is the output feature
map of the first layer. Moreover, the second layer has another
32 64  2  2 convolution kernels with a stride length of 1.
T A B L E 2
Description of emotion from human motion.
Emotion
Human motion
Average length
Sleepy
Stretching
1.91s
Bored
Wave hand
1.84s
Excited
Applause
1.65s
Tense
Rub hands
1.42s
Angry
Swing fist
1.76s
Distressed
Cover face with hands
2.08s
F I G U R E 5
Data waveform of the x‐axis accelerometer in the sensor
on the right wrist for six emotions.
ZHAO ET AL.
-
5 of 12
 17519683, 2023, 4, Downloaded from https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/sil2.12201, Wiley Online Library on [19/03/2026]. See the Terms and Conditions (https://onlinelibrary.wiley.com/terms-and-conditions) on Wiley Online Library for rules of use; OA articles are governed by the applicable Creative Commons License
This configuration allows us to investigate the important fea-
tures of the correlation between the two channels of the input
feature map. This layer is followed by a max‐pooling layer with
a pooling kernel of size 2  2, and the largest result for each
part of the input feature map is obtained. Pooling layer has a
padding of (0, 1), indicating that the paddings have dimensions
of 0 and 1 on width and height, respectively. The third con-
volutional layer has 8 32  2  2 convolution kernels with a
stride length of 1. It computes features using the interdepen-
dence of all IMU signals. It is also followed by a max‐pooling
layer with a pooling kernel of size 2  2.
Additionally, each convolutional layer is immediately fol-
lowed by an activation layer with a rectified linear unit (ReLU),
whose main role is to provide hierarchical non‐linear mapping
learning abilities to neural networks. A batch normalisation
layer was added after the ReLU and convolutional layers to
increase the training and convergence rate of the network, to
prevent exploding and vanishing gradients, and to prevent
overfitting. Then, the feature maps extracted from each IMU
sensor were expanded into 1D vectors fs s ¼ 1; 2; ⋯S
ð
Þ using a
flattening layer. These extracted fs were finally concatenated to
form a richer feature matrix F ¼ f1; f2; …; fs; …; fS
½
 contain-
ing the information of features across different channels in all
IMU sensors.
3.5
|
Attention‐based feature fusion
The IMU sensor feature matrix F extracted using the CNN
contains all the information required to recognise emotion
from human motion. However, only some sensors may be
able to represent a particular emotional state effectively and
distinguish it from other emotions. Hence, it is reasonable to
assign weights to the vector of each IMU sensor feature
depending on its importance. Therefore, we propose an
attention‐based sensor fusion module, aiming to discover IMU
sensors having major contributions for each emotional motion,
as shown in Figure 7. The feature matrix obtained through the
attention mechanism collects the most critical information,
which guarantees the correct emotion recognition.
The attention function of the attention mechanism consists
of three weight matrices: Q (query), K (key), and V (value); the
fusion matrix F corresponds to S pair Q; K; V
ð
Þ [27]. It should
be noted that Q, K, and V are learnt through network training
and are expressed as the corresponding input matrix F multi-
plied by the corresponding weight matrix W.
Q ¼ WQF ¼ q1; q2; …; qS
½

ð5Þ
K ¼ WKF ¼ k1; k2; …; kS
½

ð6Þ
V ¼ WV F ¼ v1; v2; …; vS
½

ð7Þ
ζ ¼ sof tmax QKT
ffiffiffiffiffiffi
dK
p
 
!
¼ ζ1; ζ2; …; ζS
½

ð8Þ
where WQ, WK, and WV are the weight matrices of Q, K, and
V, respectively. ζs s ¼ 1; 2; ⋯S
ð
Þ is the importance score of the
vector fs of the corresponding IMU sensor feature. In Figure 7,
the MatMul module represents the matrix product of two
tensors, and the Scale module scales the tensors to obtain a
scaling factor
ffiffiffiffiffiffi
dK
p
. Then, the attention‐based fused feature
matrix is calculated using the following formula:
bF ¼ F ⊙ζ
ð9Þ
where ⊙represents the multiplication of the corresponding
elements of two matrices. Thus, the proposed sensor‐based
attention mechanism constructs a fused sensor feature matrix
by weighting the feature vectors from individual sensors.
Fusing inputs from multiple sensors into a single representa-
tion enables the distribution of different degrees of attention
across different sensors.
3.6
|
Weighted kernel support vector
machine model
The WK‐SVM model is proposed in this paper to improve the
accuracy of emotion recognition. A new kernel function was
constructed using a linear convex combination of multiple
kernel functions and the weight of each kernel function was
determined by a fuzzy function, thereby reducing the effect of
a single kernel function selection on the recognition accuracy.
Support vector machine is a supervised machine learning
model that can be used to determine the best hyperplane for
distinguishing between the positive and negative training
F I G U R E 6
Architecture of the proposed lightweight convolutional
neural network (CNN).
T A B L E 3
Specific parameters of the proposed three‐layer lightweight
convolutional neural network (CNN).
Layer name
Kernel num
Kernel size
Stride
Padding
Conv1
64
(1, 5)
1
0
Conv2
32
2
1
0
Max‐pooling1
None
2
2
(0, 1)
Conv3
8
2
1
0
Max‐pooling2
None
2
2
1
6 of 12
-
ZHAO ET AL.
 17519683, 2023, 4, Downloaded from https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/sil2.12201, Wiley Online Library on [19/03/2026]. See the Terms and Conditions (https://onlinelibrary.wiley.com/terms-and-conditions) on Wiley Online Library for rules of use; OA articles are governed by the applicable Creative Commons License
samples. It can map the linearly inseparable problem in a high‐
dimensional space using the kernel function and convert it into
a linearly separable problem to obtain the optimal solution. For
the training sample
x1; y1
ð
Þ; x2; y2
ð
Þ; …; xN; yN
ð
Þ
f
g; xi ∈Rn;
yi ∈−1; þ1
f
g; i ¼ 1; 2; …; N can be separated using the hy-
perplane yi ωTx þ b
 
≥1; i ¼ 1; …; n.
Compared with a single kernel SVM, the multicore model
has a higher flexibility. The high‐dimensional space obtained by
mapping multiple kernel functions is a composite space
formed by combining multiple feature spaces. Different feature
components in heterogeneous data can be mapped using the
most suitable single kernel function. Finally, data can be
expressed more accurately and reasonably in the new combi-
nation space, thereby improving the prediction accuracy of the
sample data [28]. Generally, it is a linear convex combination of
multiple kernel functions as follows:
K x; z
ð
Þ ¼ a1K1 x; z
ð
Þ þ α2K2 x; z
ð
Þ þ ⋯þ αkKk x; z
ð
Þ ð10Þ
a1 þ α2 þ ⋯þ αk ¼ 1
ð11Þ
where Kk x; z
ð
Þ is the predetermined kernel function, αk is the
weight value, k is the number of kernel functions, and K x; z
ð
Þ
is the weighted kernel function.
In this paper, a fuzzy function is used as an auxiliary to
obtain the subordinate degree of the model recognition accu-
racy. Then, the accuracy of the single kernel SVM model is
used to calculate the weight of the corresponding kernel
function. Fuzzy function form is as follows, and its function
image is shown in Figure 8.
θðλÞ ¼
0
;
0 < λ < a
λ −a
1 −a

S
;
a ⩽λ
8
>
<
>
:
ð12Þ
where, θðλÞ is the membership function, λ is the accuracy of
the model, S is the number of sensors, and a is a constant.
We believe that the recognition effect of SVM model is
poor when the accuracy is lower than a. However, when the
accuracy of the model is greater than a, the classification effect
of the model meets the requirements, and the kernel function
used by the model is suitable as a member of the weighted
kernel function. The value of a is not certain, but it could be
assigned by experience. In general, the greater the number of
sensors, the better the recognition achieved. θðλÞ is the
concave function between a and 1. As t increases, the
discrimination of parts with a relatively high recognition rate
becomes more obvious. Further, the fuzzy function parameters
were set as a = 0.6 and t = 4.
A longer time is required to utilise the whole datasets to
select the kernel functions because of the relatively large
amount of emotional data, hence we selected 30% of the data
for prescreening. First, we employed a commonly used single
kernel SVM to identify emotions with kernel functions, such as
linear, polynomial, radial basis, and Gaussian kernel functions
and obtained the accuracy λ. Then, we determined the degree
of membership θðλÞ corresponding to each recognition accu-
racy according to fuzzy function, and calculated the classifi-
cation weight αi. The functional form of the classification
weight is as follows:
αi ¼
θ λi
ð Þ
P
k
i¼1
θ λi
ð Þ
; i ¼ 1; 2; …; k
ð13Þ
where k is the number of kernel functions and θ λi
ð Þ is the
subordinate degree corresponding to the accuracy of the model
using the ith kernel function.
3.7
|
Loss function and parameter
optimization
Recognising emotion from human motion is a multiclass
classification problem, and we chose the cross‐entropy loss
function [29] as the classification loss function. It can be used
to obtain maximum likelihood with consistency and statistical
efficiency and is defined as follows:
Loss ¼ −1
v
X
v
j¼1
X
z
i¼1
ylog ~y
ð Þ þ 1 −y
ð
Þlog 1 −~y
ð
ÞÞ þ χl2ðϕÞ
ð
ð14Þ
F I G U R E 7
Workflow of attention‐based feature fusion module.
F I G U R E 8
K‐th semiparabolic distribution.
ZHAO ET AL.
-
7 of 12
 17519683, 2023, 4, Downloaded from https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/sil2.12201, Wiley Online Library on [19/03/2026]. See the Terms and Conditions (https://onlinelibrary.wiley.com/terms-and-conditions) on Wiley Online Library for rules of use; OA articles are governed by the applicable Creative Commons License
where ~y is the predicted label of the model output, y is the true
label of the input sample, v is the sample size of the batch, and
z is the number of categories. The l2ðϕÞ regularisation term is
appended to the loss function as a penalty and χ is its coeffi-
cient. Then, the Adam optimiser with an initial learning rate of
0.001 is selected to design independent adaptive learning rates
for different parameters, which has the characteristics of fast
convergence speed and stable convergence process.
The weight kernel SVM implementation is based on a one‐
vs.‐all strategy and the regularisation terms C and G (in a
logarithmically spaced range from 1  10−10 to 1  1010). A
grid search method was used to optimise the parameters using
leave‐one‐out cross‐validation. 80% of the data was used as the
training set and the other 20% as the verification set of the
classification model. The process was repeated 5 times until
each sample was used as a validation set. The average accuracy
of 5 iterations was used to evaluate the performance of the
classifier. According to the highest accuracies, the weight
kernel SVM's regularisation term C was set to 1.14 and G to 3.
4
|
RESULTS
After completing the training, we evaluated the trained model
to determine the classifier quality. Commonly used evaluation
metrics are used as follows:
Accuracy ¼
TP þ TN
TP þ TN þ FP þ FN
ð15Þ
Precision ¼
TP
TP þ FP
ð16Þ
Recall ¼
TP
TP þ FN
ð17Þ
F1score ¼ 2 ⋅Precision ⋅Recall
Precision þ Recall
ð18Þ
where TP is the number of correctly classified positive exam-
ples, FP is the number of positive examples misclassified as
negative, TN is the number of correctly classified negative
examples, and FN is the number of negative examples mis-
classified as positive.
4.1
|
Evaluating the effectiveness of
weighted kernel support vector machine
model
To evaluate the performance of the WK‐SVM model, we
compared it with the classical SVM (C‐SVM), decision tree
(DT), and fully connected (FC) layers. Then, all classifiers were
trained with optimised parameters and tested for each emotion
in the test set. The performance comparison results of the
classifiers are shown in Table 4.
Figure 9 shows the performance of each classifier on the
four evaluation indexes. Based on the comparison results, the
WK‐SVM outperforms the C‐SVM by 4.71%, 3.90%, 4.64%,
and 4.26% in terms of accuracy, precision, recall, and F1 score,
respectively. The reason is that the WK‐SVM can find the
optimal segmentation hyperplane. Simultaneously, the flexi-
bility of the weighted kernel is fully reflected in the mapping
process of the existing data from the original space to the high‐
dimensional space. The complexity of the DT model depends
on the depth of the tree generated in the recursive process for
classifying datasets according to data characteristics. Addi-
tionally, its performance in terms of accuracy, precision, recall,
and F1 score is 95.09%, 95.94%, 95.93%, and 95.93%,
respectively. The performance of a FC layer is affected by the
complexity of the parameters and the expressiveness of the
spatial structure, whose accuracy, precision, recall, and F1 score
are 97.58%, 98.05%, 97.99%, and 98.02%, respectively.
4.2
|
Evaluating the effectiveness of
attention‐based sensor fusion module
In terms of feature fusion, the attention mechanism focuses on
the crucial parts of the fused multi‐IMU sensor feature matrix.
Attention‐based sensor fusion was achieved by multiplying the
T A B L E 4
Performance (%) evaluation of the effectiveness of the
proposed weighted kernel SVM (WK‐SVM) model.
Classifier
Accuracy
Precision
Recall
F1 score
C‐SVM
94.31
95.20
94.42
94.81
DT
95.09
95.94
95.93
95.93
FC
97.58
98.05
97.99
98.02
WK‐SVM
99.02
99.10
99.06
99.07
Note: Bold means the best indicator in the table.
F I G U R E 9
Performance comparison between four classifiers.
8 of 12
-
ZHAO ET AL.
 17519683, 2023, 4, Downloaded from https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/sil2.12201, Wiley Online Library on [19/03/2026]. See the Terms and Conditions (https://onlinelibrary.wiley.com/terms-and-conditions) on Wiley Online Library for rules of use; OA articles are governed by the applicable Creative Commons License
sensor feature vectors with the importance scores. To verify
the effectiveness of the proposed fusion method, we compared
it with a fusion method without the attention function, the
fused feature matrix was directly expanded through the flatten
layer. The comparison results in Table 5 show that the
attention‐based feature fusion has better performance. In
addition, the accuracy, precision, recall, and F1 score of the
fusion method without attention mechanism are 98.44%,
98.51%, 98.49%, and 98.48%, respectively. This shows that the
attention mechanism effectively learns the importance of each
IMU sensor and that the constructed emotion features are
more suitable as input of the classifier to recognise different
emotional states.
Furthermore, we analysed and visualised the learnt atten-
tion scores from the fused feature matrix, that is, the impor-
tance of each inertial sensor. Each row of the fusion feature
matrix represents the feature of each inertial sensor. After the
attention mechanism, each fusion feature matrix can obtain the
corresponding weight matrix, that is, the importance score of
each sensor. The final sensor importance score is the average
of the weight matrix, and the importance score of each inertial
sensor in the six emotions is shown in Figure 10. For example,
for the emotion “bored,” the swing of the right hand is the
most important indication for the IMU sensor worn on the
right wrist. But other sensors are not useless as they provide
additional supplementary information for the recognition of
emotional states.
4.3
|
Comparing the performance of
different data fusion methods
Data fusion methods that can improve the performance of
emotion recognition models are divided into input‐level,
decision‐level, and feature‐level methods. We compared the
attention‐based sensor fusion method with two other fusion
methods, as shown in Figure 11. For input‐level fusion, as
shown in Figure 11a, the input signals of all S IMU sensors are
concatenated to generate a single input of size H  S
ð
Þ  W.
Then, the fused input is passed into the lightweight CNN.
Decision‐level fusion fuses prediction information at a later
stage. As shown in Figure 11b, the inputs of all S IMU sensors
are individually learnt by different lightweight CNNs. Then, the
output predicted labels are fused through the majority voting
mechanism to generate the final output label.
Table 6 compares the performance of different IMU sensor
fusion methods. The accuracy, precision, recall, and F1 score of
input‐level fusion are 97.85%, 97.88%, 97.83%, and 97.85%,
respectively. The reason is a lack of analysis on each individual
IMU signal and an increase in the amount of data. Decision‐level
fusion relies on the specificity of an individual IMU sensor to
predict results, but it cannot focus on the correlations between
T A B L E 5
Performance (%) evaluation of the effectiveness of the
proposed sensor fusion module.
Method
Accuracy
Precision
Recall
F1 score
Without attention
98.44
98.51
98.49
98.48
With attention
99.02
99.10
99.06
99.07
Note: The best indicators in the table were highlighted in bold.
F I G U R E 1 0
Examples of the importance score of each inertial sensor
in the six emotions.
T A B L E 6
Performance (%) evaluation of different data fusion
methods.
Method
Accuracy
Precision
Recall
F1 score
Input‐level fusion
97.85
97.88
97.83
97.85
Decision‐level fusion
90.04
90.29
88.97
89.47
Feature‐level fusion
99.02
99.10
99.06
99.07
Note: The best indicators in the table were highlighted in bold.
F I G U R E 1 1
Architecture of two data fusion methods: (a) input‐level
fusion and (b) decision‐level fusion.
ZHAO ET AL.
-
9 of 12
 17519683, 2023, 4, Downloaded from https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/sil2.12201, Wiley Online Library on [19/03/2026]. See the Terms and Conditions (https://onlinelibrary.wiley.com/terms-and-conditions) on Wiley Online Library for rules of use; OA articles are governed by the applicable Creative Commons License
different sensors like an attention‐based feature fusion. Its ac-
curacy, precision, recall, and F1 score are 90.04%, 90.29%,
88.97%, and 89.47%, respectively. Figure 12 shows the confu-
sion matrix of three data fusion methods, where each row rep-
resents the real emotion category, each column represents the
prediction category, and each element represents the proportion
of the amount of data belonging to a certain location to the total
amount of data in the row. Overall, the attention‐based IMU
sensor fusion method proposed herein achieved better results.
4.4
|
Comparison with state‐of‐the‐art
methods
In this section, the performance of our method was compared
with that of the current state‐of‐the‐art methods proposed in
other works, as shown in Table 7. The comparison with these
works is completely fair on the premise of using the dataset
developed herein. Asad Khattak et al. [30] proposed an effi-
cient deep learning technique using CNN model for classifying
emotions from facial images. Two convolutional layers were
applied in the proposed CNN model, which can sequentially
extract low‐level features and high‐level features from images.
Arjun et al. [31] proposed a novel deep learning framework
capable of subject‐independent emotion recognition. Among
them, a CNN with an attention framework is used to perform
a topic‐independent emotion recognition task on encoded low‐
dimensional latent space representations obtained from LSTM
with channel attention autoencoders. Muzaffer Aslan [32] used
electroencephalogram (EEG) signals to automatically detect
human emotions. The EEG signal was transformed into an
image using continuous wavelet transform, and then, the fea-
tures extracted using the pretrained GoogLeNet were used as
input for k‐nearest neighbour, SVM, and extreme learning
machine classifiers. In general, the proposed method out-
performed them by at least 0.62% and 0.66% in terms of ac-
curacy
and
precision,
respectively.
And
the
emotion
recognition method proposed herein has higher performance,
which is attributed to two aspects. One is that the IMU sensor
fusion based on the attention mechanism can calculate the
importance score of the IMU sensors to fuse all the emotional
information and the other is that the WK‐SVM model im-
proves the emotion recognition performance.
This paper also evaluated the generalisation ability of the
proposed method and other methods on the same indepen-
dent test set. The activity recognition dataset [33] was con-
structed based on the records of 30 subjects who carried a
waist‐mounted smartphone with an embedded six‐axis iner-
tial sensor (three‐axis accelerometer and three‐axis gyroscope)
while performing basic activities and posture conversion. Ta-
ble 8 shows the performance metrics of different trained
models. On the independent test set, the accuracy, precision,
recall, and F1 score of the proposed are 75.26%, 72.64%,
75.91%, and 74.24%, respectively, indicating that the proposed
method has the best generalisation ability than other methods.
5
|
CONCLUSION
In this paper, an emotion recognition method based on human
motion was proposed. Subjects wore four IMU sensors on their
left wrists, right wrists, waists, and heads. We collected data on
F I G U R E 1 2
Confusion matrix of three data fusion methods: (a) input‐level fusion, (b) feature‐level fusion, and (c) decision‐level fusion.
T A B L E 7
Performance (%) comparison with state‐of‐the‐art
methods.
Method
Accuracy
Precision
Recall
F1 score
Asad Khattak et al.
98.40
98.44
98.39
98.41
Arjun et al.
92.11
92.48
91.95
92.21
Muzaffer Aslan
94.31
95.20
94.42
94.81
The proposed method
99.02
99.10
99.06
99.07
Note: The best indicators in the table were highlighted in bold.
T A B L E 8
Performance (%) comparison with state‐of‐the‐art
methods on the same independent test set.
Method
Accuracy
Precision
Recall
F1 score
Asad Khattak et al.
72.97
73.26
92.57
72.91
Arjun et al.
71.05
71.61
70.62
71.11
Muzaffer Aslan
70.89
68.74
71.73
70.20
The proposed method
75.26
72.64
75.91
74.24
Note: Bold means the best indicator in the table.
10 of 12
-
ZHAO ET AL.
 17519683, 2023, 4, Downloaded from https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/sil2.12201, Wiley Online Library on [19/03/2026]. See the Terms and Conditions (https://onlinelibrary.wiley.com/terms-and-conditions) on Wiley Online Library for rules of use; OA articles are governed by the applicable Creative Commons License
six emotions: sleepy, bored, excited, tense, angry, and distressed.
Among them, the mapping relationship between human motion
and emotion is established through fuzzy comprehensive
evaluation. Lightweight CNNs extract discriminative features
from single and multiple IMU sensors. Then, the attention‐
based feature fusion module learns the importance scores at
the IMU sensors integrated at different body locations to better
perceive emotional information. Finally, the obtained feature
representation was used as the input of the WK‐SVM model,
and a recognition accuracy of 99.02% was obtained. This helps
to improve the emotional communication ability in intelligent
human–computer interaction.
It is worth noting that the limitations of this study need to
be pointed out. This study recruited nine volunteers to collect
emotional data, and the number of sample sets was limited. We
can increase the number of volunteers and increase the dataset
capacity. The data in this study can be tested as a test set to
verify the effectiveness of the proposed method. And the range
of real‐time development, applicability, and usability of its
application phase is also a direction worthy of attention. In
addition, as multimodality‐based research has been of wide-
spread concern and achieved good sentiment classification
results, this study presents the direction for future work. We
plan to fuse multimodal information including images, inertial
signals, and physiological signals to improve the accuracy and
robustness of emotion recognition.
AUTHOR CONTRIBUTION
Yan Zhao: Conceptualisation, Data curation, Formal analysis,
Investigation, Methodology, Project administration, Resources,
Software,
Supervision,
Validation,
Visualisation,
Writing‐
original draft, Writing‐review and editing. Ming Guo: Con-
ceptualisation, Data curation, Formal analysis, Funding acqui-
sition, Methodology, Validation, Writing‐review and editing.
Xuehan Sun: Data curation, Funding acquisition, Project
administration, Resources, Supervision, Validation, Writing‐
review and editing. Xiangyong Chen: Data curation, Fund-
ing
acquisition,
Methodology,
Validation,
Visualisation,
Writing‐review and editing. Feng Zhao: Data curation, Formal
analysis, Funding acquisition, Project administration, Supervi-
sion, Validation, Writing‐review and editing.
ACKNOWLEDGEMENTS
This research was funded by National Natural Science Foun-
dation of China under (Grant Nos. 61903170, 62173175,
61877033), and by the Natural Science Foundation of Shandong
Province under grants Nos. ZR2019BF045, ZR2019MF021,
ZR2019QF004, and by the Key Research and Development
Project of Shandong Province of China, No.2019GGX101003.
CONFLICT OF INTEREST
The authors declare no conflict of interest.
DATA AVAILABILITY STATEMENT
The data that support the findings of this study are available
from the corresponding author upon reasonable request.
ORCID
Ming Guo
https://orcid.org/0000-0003-3274-1201
Xuehan Sun
https://orcid.org/0009-0000-7077-6996
REFERENCES
1.
Nayak, S., et al.: A Human–Computer Interaction framework for
emotion recognition through time‐series thermal video sequences.
Comput. Electr. Eng. 93, 107280 (2021). https://doi.org/10.1016/j.
compeleceng.2021.107280
2.
Hao, Y., et al.: An end‐to‐end human abnormal behavior recognition
framework for crowds with mentally disordered individuals. IEEE
Journal of Biomedical and Health Informatics 26(8), 3618–3625 (2021).
https://doi.org/10.1109/JBHI.2021.3122463
3.
Zhang, Y., et al.: Application of skeleton data and long short‐term
memory in action recognition of children with autism spectrum disor-
der. Sensors 21(2), 411 (2021). https://doi.org/10.3390/s21020411
4.
Guo, M., et al.: A multisensor multiclassifier hierarchical fusion model
based on entropy weight for human activity recognition using wearable
inertial sensors. IEEE Transactions on Human‐Machine Systems 49(1),
105–111 (2019). https://doi.org/10.1109/THMS.2018.2884717
5.
Rida, F., et al.: From motion to emotion prediction: a hidden biometrics
approach. In: Hidden Biometrics. Series in BioEngineering. Spring-
erSingapore (2020). https://doi.org/10.1007/978‐981‐13‐0956‐4_11
6.
Saurav, S., Saini, R., Singh, S.: EmNet: a deep integrated convolutional
neural network for facial emotion recognition in the wild. Appl. Intell.
51(8), 5543–5570 (2021). https://doi.org/10.1007/s10489‐020‐02125‐0
7.
Kulkarni, P., Rajesh, T. M.: Video based sub‐categorized facial emotion
detection using LBP and edge computing. Rev. d’Intelligence Artif. 35(1),
55–61 (2021). https://doi.org/10.18280/ria.350106
8.
Wang, Z., et al.: Motion analysis of deadlift for trainers with different
levels based on body sensor network. IEEE Trans. Instrum. Meas. 70,
1–12 (2021). https://doi.org/10.1109/TIM.2021.3062162
9.
Ader, L.G.M., et al.: Reliability of inertial sensor based spatiotemporal
gait parameters for short walking bouts in community dwelling older
adults. Gait Posture 85, 1–6 (2021). https://doi.org/10.1016/j.gaitpost.
2021.01.010
10.
Liu, R., et al.: A wearable gait analysis and recognition method for Par-
kinson’s disease based on error state Kalman filter. IEEE Journal of
Biomedical and Health Informatics 26(8), 4165–4175 (2022). https://doi.
org/10.1109/JBHI.2022.3174249
11.
Subasi, A., et al.: EEG‐based emotion recognition using tunable Q wavelet
transform and rotation forest ensemble classifier. Biomed. Signal Process
Control 68, 102648 (2021). https://doi.org/10.1016/j.bspc.2021.102648
12.
Alemayoh, T.T., Lee, J.H., Okamoto, S.: New sensor data structuring for
deeper feature extraction in human activity recognition. Sensors 21(8),
2814 (2021). https://doi.org/10.3390/s21082814
13.
Hassan, A.K., Mohammed, S.N.: A novel facial emotion recognition
scheme based on graph mining. Defence Technology 16(5), 1062–1072
(2020). https://doi.org/10.1016/j.dt.2019.12.006
14.
Chowdary, M.K., Nguyen, T.N., Hemanth, D.J.: Deep learning‐based facial
emotion recognition for human–computer interaction applications. Neural
Comput. Appl. (2021). https://doi.org/10.1007/s00521‐021‐06012‐8
15.
Li, Y., Zhang, T., Chen, C.P.: Enhanced broad siamese network for facial
emotion recognition in human–robot interaction. IEEE Transactions on
Artificial Intelligence 2(5), 413–423 (2021). https://doi.org/10.1109/
TAI.2021.3105621
16.
Zhang, H., Huang, B., Tian, G.: Facial expression recognition based on
deep convolution long short‐term memory networks of double‐channel
weighted mixture. Pattern Recogn. Lett. 131, 128–134 (2020). https://
doi.org/10.1016/j.patrec.2019.12.013
17.
Tao, J.H., et al.: Semi‐supervised ladder networks for speech emotion
recognition. Int. J. Autom. Comput. 16(4), 437–448 (2019). https://doi.
org/10.1007/s11633‐019‐1175‐x
18.
MustaqeemKwon, S.: Optimal feature selection based speech emotion
recognition using two‐stream deep convolutional neural network. Int. J.
Intell. Syst. 36(9), 5116–5135 (2021). https://doi.org/10.1002/int.22505
ZHAO ET AL.
-
11 of 12
 17519683, 2023, 4, Downloaded from https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/sil2.12201, Wiley Online Library on [19/03/2026]. See the Terms and Conditions (https://onlinelibrary.wiley.com/terms-and-conditions) on Wiley Online Library for rules of use; OA articles are governed by the applicable Creative Commons License
19.
Zhao, J., Mao, X., Chen, L.: Learning deep features to recognise speech
emotion using merged deep CNN. IET Signal Process. 12(6), 713–721
(2018). https://doi.org/10.1049/iet‐spr.2017.0320
20.
Ancilin, J., Milton, A.: Improved speech emotion recognition with Mel
frequency magnitude coefficient. Appl. Acoust. 179, 108046 (2021).
https://doi.org/10.1016/j.apacoust.2021.108046
21.
Hashmi, M.A., et al.: Motion reveal emotions: identifying emotions from
human walk using chest mounted smartphone. IEEE Sensor. J. 20(22),
13511–13522 (2020). https://doi.org/10.1109/JSEN.2020.3004399
22.
Gravina, R., Li, Q.: Emotion‐relevant activity recognition based on smart
cushion using multi‐sensor fusion. Inf. Fusion 48, 1–10 (2019). https://
doi.org/10.1016/j.inffus.2018.08.001
23.
Hnatiuc, M., Iov, C., Savin, B.: Emotion identification using writing
system. In: IEEE International Symposium for Design and Technology
in Electronic Packaging (SIITME), pp. 9–12 (2018). https://doi.org/10.
1109/SIITME.2018.8599278
24.
Chang, C., et al.: Analyzing the effect of badminton on physical health
and emotion recognition on the account of smart sensors. Appl. Bionics
Biomech. 2022, 1–13 (2022). https://doi.org/10.1155/2022/8349448
25.
Russell, J.A.: A circumplex model of affect. J. Personality Soc. Psychol.
39(6), 1161–1178 (1980). https://doi.org/10.1037/h0077714
26.
Scherer, K.R., Ellgring, H.: Multimodal expression of emotion: affect
programs or componential appraisal patterns? Emotion 7(1), 158–171
(2007). https://doi.org/10.1037/1528‐3542.7.1.158
27.
Vaswani, A., et al.: Attention is all you need. Adv. Neural Inf. Process.
Syst. 30 (2017)
28.
Shah, F., et al.: Sign language recognition using multiple kernel learning: a
case study of Pakistan sign language. IEEE Access 9, 67548–67558 (2021).
https://doi.org/10.1109/access.2021.3077386
29.
Sun, F., Sun, J., Zhao, Q.: A deep learning method for predicting
metabolite–disease associations via graph neural network. Briefings
Bioinf. 23(4), 1–11 (2022). https://doi.org/10.1093/bib/bbac266
30.
Khattak, A., et al.: An efficient deep learning technique for facial emotion
recognition. Multimed. Tool. Appl. 81(2), 1649–1683 (2022). https://doi.
org/10.1007/s11042‐021‐11298‐w
31.
Rajpoot, A.S., Panicker, M.R.: Subject independent emotion recognition
using EEG signals employing attention driven neural networks. Biomed.
Signal Process Control 75, 103547 (2022). https://doi.org/10.1016/j.
bspc.2022.103547
32.
Aslan, M.: CNN based efficient approach for emotion recognition.
Journal of King Saud University‐Computer and Information Sciences
34(9), 7335–7346 (2022). https://doi.org/10.1016/j.jksuci.2021.08.021
33.
Reyes‐Ortiz, J.L., et al.: Transition‐aware human activity recognition us-
ing smartphones. Neurocomputing 171, 754–767 (2016). https://doi.
org/10.1016/j.neucom.2015.07.085
How to cite this article: Zhao, Y., et al.: Attention‐
based sensor fusion for emotion recognition from
human motion by combining convolutional neural
network and weighted kernel support vector machine
and using inertial measurement unit signals. IET Signal
Process. e12201 (2023). https://doi.org/10.1049/sil2.
12201
12 of 12
-
ZHAO ET AL.
 17519683, 2023, 4, Downloaded from https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/sil2.12201, Wiley Online Library on [19/03/2026]. See the Terms and Conditions (https://onlinelibrary.wiley.com/terms-and-conditions) on Wiley Online Library for rules of use; OA articles are governed by the applicable Creative Commons License
