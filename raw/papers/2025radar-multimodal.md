Received 24 March 2025, accepted 29 April 2025, date of publication 26 May 2025, date of current version 13 June 2025.
Digital Object Identifier 10.1109/ACCESS.2025.3573648
Framework for Emotion Recognition Using
Cross-Modal Transformers With Non-Contact
Multimodal Signals Aiming Clinical
Service Support
HOMURA KAWAMURA
1, TOMOFUMI MIURA
2, YUKA MAEDA
3, (Member, IEEE),
YUKIHIKO OKADA
3,4, AND KEIICHI ZEMPO
3, (Member, IEEE)
1Graduate School of Science and Technology, University of Tsukuba, Tsukuba 305-8573, Japan
2Department of Palliative Medicine, National Cancer Center Hospital East, Kashiwa 277-8577, Japan
3Institute of Systems and Information Engineering, University of Tsukuba, Tsukuba 305-8573, Japan
4Center for Artificial Intelligence Research, Tsukuba Institute for Advanced Research (TIAR), University of Tsukuba, Tsukuba 305-8577, Japan
Corresponding author: Keiichi Zempo (zempo@iit.tsukuba.ac.jp)
This work was supported by JSPS KAKENHI under Grant 22H03693 and Grant 23K24948, and in part by Tsukuba Simulated Patient
Association.
This work involved human subjects or animals in its research. Approval of all ethical and experimental procedures and protocols was
granted by the National Cancer Center Institutional Review Board under Application No. 2022-91, and performed in line with the
Declaration of Helsinki.
ABSTRACT
In clinical communication, it is believed that accurately understanding and appropriately
responding to patients’ emotions contributes to treatment effectiveness and patient satisfaction. Recently,
multimodal approaches that integrate various modalities such as speech, text, and physiological signals have
gained attention for emotion estimation. However, the application of emotion recognition (ER) technology in
clinical settings has not been thoroughly explored, particularly in terms of utilizing non-contact measurement
techniques to reduce patient burden. Furthermore, there is limited research on quantitatively evaluating
physicians’ ER abilities and comparing them with existing ER methods. This study aims to propose a
multimodal ER framework using non-contact measurement techniques and validate its effectiveness by
comparing it with the emotion prediction accuracy of experienced physicians. The results demonstrated that
the proposed non-contact multimodal approach outperformed physicians in ER accuracy. While physicians’
empathetic abilities have traditionally been considered high, integrating multiple modalities was shown to
surpass the recognition accuracy of unimodal approaches and human physicians. Moreover, the ability to
obtain emotion-related data non-invasively enables advanced emotion estimation while reducing physical
and psychological burdens on patients, highlighting the potential for clinical applications. These findings
suggest a new method for supporting physicians’ ER in clinical settings, offering a means to reduce the risk
of fatigue associated with empathy.
INDEX TERMS
Human–computer interaction (HCI), multimodal emotion recognition, doctor-patient
relations, physiological signals.
I. INTRODUCTION
A. BACKGROUND
The advancements in medical technology have extended
the average life expectancy and increased the time patients
The associate editor coordinating the review of this manuscript and
approving it for publication was Orazio Gambino
.
spend interacting with physicians [1]. Consequently, the
doctor-patient relationship has garnered growing atten-
tion as a critical factor in assessing the quality of
healthcare [2]. As the aging population continues to
grow, there is a corresponding rise in patients with
chronic diseases, necessitating the development of long-
term, close relationships between physicians and patients [3].
99490
 2025 The Authors. This work is licensed under a Creative Commons Attribution 4.0 License.
For more information, see https://creativecommons.org/licenses/by/4.0/
VOLUME 13, 2025
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
FIGURE 1. A framework for non-contact ER for clinical practice.
To achieve high-quality healthcare, it is imperative not
only to provide accurate diagnoses and appropriate treat-
ments but also to establish a trusting and reassuring
relationship that enables patients to undergo treatment with
confidence [2], [3].
In high-stress contexts such as oncology care, patients
often perceive physicians as one of the most critical
sources of psychological support [4], and psychological care
emerges as a pivotal component influencing the quality
of medical care [5], [6]. Creating a medical environ-
ment where patients can openly share their emotions and
symptoms allows physicians to gather more comprehen-
sive clinical information, improving diagnostic accuracy
and treatment efficacy [7]. Furthermore, a strong doctor-
patient relationship has been shown to enhance patient
adherence to medical instructions, increase satisfaction
with treatment, and contribute to improved therapeutic
outcomes [5], [8].
Given these circumstances, the ability of physicians to
accurately recognize patient emotions and respond empa-
thetically has become increasingly important [9], [10].
Empathy, defined as the capacity to understand and share
another’s emotional and affective states, has long been
recognized as essential in clinical practice, with substantial
evidence supporting its therapeutic value [11], [12], [13].
This ability not only enhances patient satisfaction but
also contributes to better compliance with recommended
treatments [5].
In light of these considerations, we focused on the
application of ER technology to support physician empathy
in clinical practice. ER technology provides a foundation
for accurately capturing patients’ emotional cues, enabling
physicians to respond more appropriately [14], [15]. Recent
advancements have driven the development of tools utilizing
computer vision and machine learning for ER [16], [17], [18].
Particularly noteworthy is the emergence of multimodal ER
techniques, which integrate non-verbal cues such as facial
expressions, vocal tones, and physiological signals [19].
These techniques offer a comprehensive understanding of
subtle emotional changes and psychological states that
traditional doctor-centered communication methods might
overlook [20], [21].
However, the clinical application of multimodal ER tech-
nology presents significant ethical challenges [7], [22], [23],
[24]. Evidence supporting the benefits of such technologies
in high-stress environments like oncology remains limited.
In clinical ER, it is crucial to address patient privacy
concerns, ensure transparency in data usage, and consider
the psychological burden that measurement methods may
impose on patients. Contact-based measurement approaches
risk increasing both physical and mental stress for patients,
rendering them unsuitable during medical consultations [25].
In an ideal measurement environment, subjects would not
be overly conscious of the measurement process itself,
mitigating psychological factors that could influence the
measurement. Therefore, non-contact measurement methods
have the potential to become invaluable tools in clinical
healthcare systems [26]. The framework proposed in this
study introduces non-contact measurement technology to
avoid placing excessive burden on patients, thereby maintain-
ing their natural state while acquiring necessary peripheral
and physiological signal data for ER technology.
B. NOVELTY AND CONTRIBUTIONS
This study proposes a framework for multimodal ER based
on non-contact measurement data to support patient care
in clinical settings (FIGURE1). The proposed framework
integrates multiple modalities, such as speech, text, and
physiological signals, to achieve higher accuracy compared
to conventional unimodal ER approaches. By employing
non-contact measurement methods for data acquisition, the
framework aims to offer a practical ER approach while
considering the realities of clinical environments. The novelty
of this research can be summarized in the following two key
aspects.
The first point of novelty lies in the quantitative evaluation
of practicing physicians’ ER abilities in clinical settings.
Previous clinical studies assessing physicians’ skills have
primarily focused on areas such as the effectiveness of
communication skills training [27] and emotional response
evaluation [28]. Even recent studies examining empathy
skills [29] have targeted medical students, leaving the
precision of ER abilities among experienced physicians
VOLUME 13, 2025
99491
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
largely unexplored. Particularly in oncology care, prior
research has highlighted the challenges of measuring
physicians’ skills during actual consultations [30], [31],
[32], [33]. Consequently, the accuracy and limitations of
ER by physicians in clinical oncology contexts have not
been sufficiently investigated. The quantitative evaluation
of seasoned physicians’ ER abilities presented in this study
provides valuable data that can serve as foundational evidence
for integrating ER technologies into clinical practice, paving
the way for the development of advanced clinical support
systems.
Specifically, rather than relying solely on surveys or semi-
qualitative methods, we adopt widely recognized metrics
from machine learning–such as Accuracy, Precision, Recall,
and F1 scores–to measure physicians’ emotion recognition
error rates. We asked both simulated patients and physicians
to annotate emotional states during recorded consultations,
treating the simulated patients’ annotations as ground truth
for rigorous comparison. This approach offers a more
objective and transparent quantification of physicians’ ER
performance, marking a significant departure from prior
clinical research predominantly reliant on subjective or semi-
quantitative evaluations.
The second point of novelty is the proposal of an
ER framework that minimizes physical and psychological
burdens on patients while enhancing applicability in clinical
environments, particularly in oncology care. Conventional
methods for acquiring physiological signal data for ER rely
on contact-based sensors. Previous studies that performed
ER using data acquired in clinical contexts [34], [35], [36]
often depended on contact-based measurements without ade-
quately addressing clinical applicability. In contrast, recent
research employing non-contact measurement methods for
ER [37] has utilized facial and ocular data. However,
capturing such data through cameras may prove challenging
in high-stress clinical environments, such as oncology,
making direct application in clinical settings potentially
problematic.
This study adopts a non-invasive, non-contact measure-
ment approach to collect data, thereby reducing the burden on
patients during data acquisition. By leveraging a multimodal
ER approach that integrates text, speech, and physiological
signals, the framework seeks to overcome the challenges
of reduced accuracy commonly associated with non-contact
measurements. The integration of multiple modalities aims
to complement the information provided by each modality,
enhancing the overall precision of ER.
The primary contributions of this research are as follows:
1) Quantitatively evaluated the accuracy of physicians’
ER abilities, providing foundational data for ER in
clinical settings.
2) Calculated the accuracy of multimodal ER by inte-
grating text, speech, and physiological signals, and
demonstrated its effectiveness by comparing it with
physicians’ ER abilities.
3) Proposed a non-contact measurement-based ER frame-
work that aligns with the practical requirements of
clinical environments.
II. RELATED WORKS
A. ER IN CLINICAL SETTINGS
ER in the medical field has recently attracted attention as a
means of improving the quality of patient psychological care.
It is believed that by accurately grasping patients’ emotions,
healthcare professionals can provide more individualized
care, contributing to patients’ peace of mind and improved
treatment outcomes [38].
In ER research in the medical field, there has been an
increase in application examples using datasets acquired
in clinical environments. For example, the MODMA
dataset [39], which includes electroencephalogram (EEG)
signals and voice data from patients with depression,
is divided into training data and test data with 971 segments
and 350 segments, respectively, for the purpose of depression
detection. The data is processed to learn features according
to the mental state of the subjects [40]. Chollet achieved
93 % accuracy in depression detection using the depthwise
separable convolution method of the Xception model [41]
on this MODMA dataset [42]. In addition, by dynamically
integrating features between multiple modalities and com-
bining EEG and voice data, they achieved 98.9 % accuracy
in multimodal classification [43] and 92 % accuracy in
depression detection [42]. Recently, by extracting features
from multiple modalities (voice, EEG, and text) and learning
the relationships between different tasks, they achieved the
highest accuracy of 99 % in depression detection [42].
Furthermore, research on multi-class classification of emo-
tions has also progressed. Zitouni et al. used discussion data
from pairs of participants to perform 4-class emotion clas-
sification based on arousal and valence, achieving 93.65 %
accuracy with a BiLSTM-based ER model [44]. Livingstone
and Russo used the public dataset RAVDESS [45] to classify
eight different emotion classes using an LSTM-Transformer
model, showing 69.61 % accuracy [46].
Although these studies have shown that ER using machine
learning is useful as a tool for detecting specific mental states
and emotions, there is still a lack of clear empirical data on ER
in clinical settings. Considering the use of ER technology in
clinical practice, it is reasonable to examine it in comparison
to the accuracy of physicians’ ER. However, it remains
unclear how advantageous or limited ER technology is
compared to the perception of healthcare professionals.
Therefore, it is necessary to evaluate how accurately ER
technology can recognize patients’ emotions and verify its
practical feasibility by comparing it with the accuracy of
physicians.
B. UNIMODAL/MULTIMODAL ER
In ER, conventional approaches have typically relied on uni-
modal methods based on a single modality such as emotional
99492
VOLUME 13, 2025
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
FIGURE 2. mmWave radar signal processing.
expressions in text, voice, or physiological signals [20], [47].
In unimodal approaches, since each modality has unique
emotional characteristics, text, voice, and physiological
signals are analyzed independently to infer emotional states.
In text-based unimodal ER, Li et al. proposed SENN,
a hybrid approach combining CNN-based emotion encoding
and BiLSTM-based semantic encoding. Using 10 datasets
including DailyDialogs [48], they performed 6-class classi-
fication of Ekman’s six basic emotions (joy, fear, sadness,
surprise, anger, and disgust), achieving an F1-score of up to
98.8 % [16].
In voice-based unimodal emotion recognition (UER), Mel-
Frequency Cepstral Coefficients (MFCCs) are widely used
in speech-based ER [17], [49]. For example, Er used a
hybrid approach combining acoustic features such as MFCCs
and zero-crossing rate with deep features extracted from
pre-trained CNN models such as VGG16 and ResNet,
achieving 79.41 % accuracy on the RAVDESS dataset [50].
Furthermore, in physiological signal-based unimodal ER,
Galvanic Skin Response (GSR) signals, Electromyography
(EMG) signals, Electroencephalogram (EEG) signals, heart
rate, and respiration are often used. Physiological signals are
considered to reflect an individual’s emotional state relatively
objectively. For example, Miranda-Correa et al. employed
a hybrid approach using 1DCNN and Vision Transformer,
achieving 98.2 % accuracy in 4-class emotion classification
(HALA, LAHV, LALV, HAHV) based on the AMIGOS [51]
and DEAP datasets [52] by using an ensemble classifier with
MAML [53].
With a single modality, there are limitations in capturing
subtle changes in emotions and complex psychological
states. In recent years, multimodal approaches that integrate
information obtained from multiple modalities to capture
various aspects of emotion have become widely used.
In Multimodal Emotion Recognition (MER), Xie et al.
proposed a model that extracts features from three modalities:
text, voice, and video, using the MELD dataset. Specifically,
they extracted features from each modality using the GPT
language model for text, WaveRNN for voice, and Deep CNN
for facial embeddings from video, and learned the temporal
relationships of image sequences with an RNN-based model.
This model achieved 63.1 % accuracy by integrating the three
modalities [54].
However, many of these unimodal and multimodal
ER studies rely on datasets obtained in natural dialogue
environments, and there are very few studies that utilize
data collected in clinical environments. In particular, there
are no studies that have evaluated the performance of
ER using multimodal data including physiological indica-
tors in high-stress clinical environments such as cancer
treatment.
III. METHODOLOGY
A. NON-CONTACT DATA MEASUREMENT
In this study, we used a non-contact method of measuring
physiological signals via millimeter-wave radar, aiming to
minimize patient burden in high-stress oncology settings.
Specifically, we adopted the 24 GHz miRadar 8 [55],
developed by Sakura Tech Corporation, which has also
been utilized in previous research [56].The non-contact
measurement method for physiological signals consists of
two steps: Signal Conditioning and Digital Signal Processing
(DSP).
1) SIGNAL CONDITIONING
First, Signal Conditioning (FIGURE 2, a) is the pro-
cess of conditioning the analog signal acquired by the
millimeter-wave radar system into a form suitable for
subsequent digital processing. This stage includes signal
generation, transmission, reception, and Analog-to-Digital
Conversion (ADC). A Frequency Modulated Continuous
Wave (FMCW) chirp signal is generated by a synthesizer,
which serves as the basic signal for the radar system. This
signal is emitted through the transmit antenna (Tx Antennas)
and transmitted as a high-frequency electromagnetic wave
towards the target.
VOLUME 13, 2025
99493
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
Next, the echo signal reflected from the target is acquired
by the receive antenna (Rx Antennas). The transmitted signal
and the received signal are mixed by a Mixer to generate an
Intermediate Frequency (IF) signal (beat signal) containing
information about distance and speed. This beat signal is then
digitized by an Analog-to-Digital Converter (ADC) and input
to the DSP module.
2) DSP
DSP (FIGURE 2, b) is the stage where the digitized signal is
analyzed to extract the target’s physical parameters (distance,
speed, angle, and physiological signals). First, a Fast Fourier
Transform (FFT) is applied to the beat signal to analyze
the frequency spectrum and determine the beat frequency,
which is used to estimate the target’s distance. Furthermore,
the Angle of Arrival (AoA) is estimated using a Multiple-
Input Multiple-Output (MIMO) array with multiple receive
antennas.
Next, physiological signals such as heart rate (HR),
respiration rate (RR), and R-R interval (RRI) are measured
non-contactly by analyzing minute fluctuations in the dis-
tance data. Time-domain and frequency-domain analyses
are used to extract these physiological signals. Finally, the
target is detected and tracked by integrating distance and
angle data to generate a 2D map and applying a clustering
algorithm. Through these processes, the millimeter-wave
radar transforms raw data into practical information.
B. CROSS-MODAL TRANSFORMER
1) FEATURE EXTRACTION
Features were extracted using multiple models for each
modality (audio, text, and physiological signals). The text
corresponding to a single utterance was treated as one
sequence, and feature values for each modality were extracted
for each sequence. Then, the ER accuracy of each feature
extraction model was compared, and the features from the
model with the highest accuracy were adopted for the cross-
modal transformer.
a: AUDIO MODALITY
For feature extraction from the audio modality, we used
the self-supervised learning models wav2vec2.0 [57], [58]
and HuBERT [59]. As a comparison method, we built a
model using MFCCs [60], which is a traditional method in
speech ER, and Spectrogram features [61], and compared
their performance as a baseline.
In fine-tuning, we applied Partial Fine-Tuning (PF) [62] to
the wav2vec 2.0 and HuBERT models. In partial fine-tuning,
the CNN encoder part of the pre-trained model is frozen, and
only the Transformer-based context encoder is trained. This
allows us to retain the low-level acoustic features obtained
in pre-training while optimizing the high-level contextual
features for the specific task. For the learning settings, we set
the learning rate to 10−5 for the encoder and 10−4 for the
linear classifier, and adopted the Adam optimizer [63] as the
optimization method.
b: TEXT MODALITY
We used XLNet [64], GPT [65], and BERT [66] based models
for emotion prediction from the text modality. For BERT-
based models, domain-specific pre-trained models such as
Sci-BERT [67], Bio-BERT [67], and Clinical-BERT [68]
for English text have been released in the clinical field.
However, since there are few effective models for Japanese
text, especially for clinical medicine text [69], we translated
the text dataset obtained in the experiment of this study and
applied Clinical-BERT for English.
As for the fine-tuning method, we adjusted the model
with the same settings as in the previous study [54] based
on Wolf et al. [70]. Specifically, we generated sentence-
level embeddings by providing each utterance as a separate
sequence. The sequence input was designed to efficiently
learn contextual information by introducing special tokens
and segment distinctions. Multi-task learning was adopted for
optimization in fine-tuning, combining three loss functions:
next sentence prediction loss Ls, language modeling loss Ll,
and emotion classification loss Le.
The next sentence prediction loss Ls was set as a task
to classify the correct response sentence and a random
distracting sentence using the special token [CLS] added
to the end of the input sequence. The language modeling
loss Ll is a task to predict the next token in the sequence,
and the language model was optimized based on contextual
information. For the emotion classification loss Le, we set
a task to predict multi-class emotion labels by inputting
the output vector of the final hidden layer to a multi-layer
classifier.
The final total loss function Ltotal is defined as the sum of
the three loss functions as follows:
Ltotal = Ls + Ll + Le
(1)
c: PHYSIOLOGICAL SIGNAL MODALITY
In this study, for ER using the physiological signal modality,
we calculated time and frequency domain (TFD) features
and used a total of 37 features by utilizing respiration
signals in addition to heart rate signals. These features
are based on previous studies that used autonomic nervous
system indicators [71], [72], [72]. As for time-domain
features in TFD, we calculated the root mean square of
successive differences (RMSSD) of the R-R intervals (RRI),
the percentage of RRI exceeding 20 ms and 50 ms (pNN20
and pNN50), two Poincaré coefficients [73], and statistics
related to heart rate (HR), respiration rate, and heart rate
variability (HRV) such as mean, standard deviation, kurtosis,
skewness, and the number of times the signal value exceeds
or falls below the mean ± 1 standard deviation. We adopted
a total of 23 features.
As for frequency-domain features, we used a total of
14 features corresponding to spectral power in each band
99494
VOLUME 13, 2025
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
FIGURE 3. Cross-modal transformer fusion.
of high frequency (HF), middle frequency (MF), low
frequency (LF), and very low frequency (VLF) of the heart
rate and respiration signals, LF/HF ratio, power spectral
entropy, sample entropy, and Shannon entropy [74]. Since
extracting features only in these time and frequency domains
is insufficient to capture the variability of signals during
changes in emotional state [75], we adopted Empirical Mode
Decomposition (EMD) [76] and Wavelet Transform (WT)
[77] as representative methods [78] to extract more complex
features and conducted comparisons using the following two
feature extraction models. The effectiveness of EMD and
WT for feature extraction has been shown in numerous
papers [79], [80], [81], [82].
First, in the method using EMD [78], an approach is
adopted to decompose nonlinear and non-stationary signals
into multiple Intrinsic Mode Functions (IMFs). IMFs are
decomposed components of a signal into simpler waveforms,
each with a certain frequency range, reflecting the amplitude
and frequency modulation of the original signal. These IMFs
are considered to be the basic elements for capturing the fine
fluctuations of the original signal and are useful for analyzing
the complex structure of the signal step by step. To obtain
IMFs, a sifting process is used, which involves repeatedly
detecting the maxima and minima of the signal to construct
an envelope and subtracting its mean from the signal. The
Hilbert transform is applied to the obtained IMFs to calculate
instantaneous amplitude and frequency, and then the discrete
Fourier transform is used to calculate spectral power and
spectral entropy [78].
Next, we used Wavelet Scattering (WS) as an approach
using WT [75]. In this method, the signal is first divided
into multiple small time intervals (scattering windows).
Then, features are extracted through a three-step process of
wavelet convolution (convolving the signal with a wavelet
function), modulation (applying a non-linear transformation
to the signal), and filtering (smoothing the signal to extract
features). The scattering coefficients obtained through these
processes have the characteristic of suppressing variations
within a class and highlighting differences between classes.
WS is robust to temporal shifts in the input signal and has the
property of capturing changes at multiple scales [83], [84].
In this study, rather than adopting a deep neural network
(DNN) for physiological feature extraction, we opted for a
domain-driven approach. The primary reason for this choice
is the limited availability of large-scale labeled datasets for
physiological signals, which makes it difficult to train com-
plex DNNs without incurring the risk of overfitting [85], [86].
Furthermore, time-domain and frequency-domain features,
as well as feature extraction methods such as EMD and
WT, have been extensively validated and widely adopted in
previous research.
2) CONTEXT-AWARE MODULE
a: PROBLEM DEFINITION
In this module, we adopt an approach based on Bi-LSTM
to capture the continuous dependencies between adjacent
utterances, following the methodology of prior research [87].
A conversation is defined as a sequence of utterances
{um}M
m=1, where M represents the number of utterances. Each
utterance um is spoken by a speaker sm, with sm ∈{s1, s2}.
Here, s1 represents the service provider, and s2 represents the
service receiver. In this study, s1 corresponds to the physician,
and s2 corresponds to the patient.
Each utterance um consists of tokens {xm,1, xm,2, . . .,
xm,Km}, where Km denotes the number of tokens in um. The
feature vector vm for each utterance corresponds to audio
modality vA
m, text modality vT
m, and physiological signals vP
m,
and is expressed as:
vm = (vA
m, vT
m, vP
m),
vA
m ∈RdA, vT
m ∈RdT, vP
m ∈RdP. (2)
Here, dA, dT, dP denote the dimensionality of features for
audio, text, and physiological signal modalities, respectively.
Based on the conversational context {vm}M
m=1, the objective is
to predict the emotion label ym ∈C of utterance um, where C
represents the set of emotion labels.
VOLUME 13, 2025
99495
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
b: A/T/P-LSTM MODULE
To effectively extract modality-specific information from the
conversational context, LSTMs are applied to each of the
audio, text, and physiological modalities. For each modality,
features are computed using Bi-LSTM as follows, based on
the procedure described in Zou et al. [87]:
Hk
m, hk
m = LSTMk(vk
m, hk
m−1),
k ∈{A, T, P}.
(3)
Here, k represents the modality (audio modality, text
modality, or physiological signals), hA
m, hT
m, hP
m denote the
hidden states of the m-th utterance for the audio, text, and
physiological signal modalities, respectively, and HA
m
∈
R2dA, HT
m ∈R2dT, HP
m ∈R2dP represent the contextual
feature representations at time step m for each modality.
Finally, the modality-specific features obtained from the
M utterances within the conversation are concatenated and
aligned to a dimension of dT via a linear layer:
Hk = Linear
M
m=1Hk
m

,
k ∈{A, T, P}.
(4)
Here, ∥denotes the concatenation operation, and Hk
∈
RLT×dT represents the aligned feature representation for each
modality. LT indicates the sequence length of the time-series
data.
3) CROSS-MODAL TRANSFORMER FUSION
a: CROSS-MODAL ATTENTION
Cross-modal attention is used to achieve interaction of infor-
mation between different modalities. This method effectively
integrates the flow of information from the source modality
to the target modality within the utterance context.
By learning the feature representation of the source modal-
ity, the representation of the target modality is enhanced. For
example, when learning the feature representation from text
to audio, the query, key, and value are defined as follows:
QA = HAWQ,
KT = HTWK,
VT = HTWV.
(5)
Here, WQ, WK, WV represent learnable weight matrices.
Next, the information fusion from the source modality (text)
to the target modality (audio) is expressed as cross-modal
attention by the following equation:
YTA = CMAT→A(HA, HT) = softmax
QAKT
√dT

VT. (6)
Here, →represents the information fusion from T to A, CMA
represents the cross-modal attention module, and YTA ∈
RLT×dT is the fusion result.
b: CROSS-MODAL TRANSFORMER
We designed a Cross-Modal Transformer (CMT) based
on previous research [87] to enhance information trans-
fer between different modalities and promote interaction
between modalities. CMT plays a role in improving the
expressive power of modalities with relatively weak expres-
sive power by using features learned from other modalities.
In the following, we will explain using information transfer
from text (T) to audio (A) (T →A) as an example:
Z(0)
T→A = H(0)
T .
(7)
Z(m)
T→A = fθ(m)
T→A

Norm

eZ(m)
T→A

+ eZ(m)
T→A.
(8)
eZ(m)
T→A = CA(m),mul
T→A

Norm

Z(m−1)
T→A

, Norm

H(0)
T

+ Norm

Z(m−1)
T→A

.
(9)
Here, CMA(m),mul
T→A
represents the multi-head cross-modal
attention block, and Norm(·) represents the normalization
operation. fθ(m)
T→A is a sublayer that considers positional infor-
mation and is configured using the parameter θ(m). In this
process, each modality sequentially updates its expressive
power while utilizing low-level external information. In each
layer of the attention block, the features of the source
modality, text (T), are transformed into different sets of
key-value pairs to interact with the audio (A) modality.
c: SELF-ATTENTION
The outputs of CMT are integrated in a way that shares the
same target modality. This output is calculated as XA ∈
RLT×dT.
Then, self-attention is applied to extract sequence informa-
tion and obtain modality features corresponding to the current
utterance.
XA = ZT→A ⊕ZP→A.
(10)
ZA = Attention(XA).
(11)
Here, ⊕represents the element-wise concatenation operation,
and Attention(·) refers to the attention mechanism. Self-
attention integrates information about each position in the
sequence and emphasizes the features of the target modality.
4) MULTIMODAL FUSION
In the ER task, to enhance the robustness when integrating
information between modalities, we applied the EmbraceNet
architecture [88], referring to Xie et al. [54]. This approach
aims to efficiently integrate features obtained from multiple
modalities and minimize the impact of data loss and noise.
EmbraceNet consists of two components: the docking layer
and the Embracement Layer.
The output of each modality obtained by CMT is trans-
formed into a unified dimension through the docking layer.
Using the ReLU activation function, the features of each
modality are unified to the same dimension and summarized
as follows:
d(k) = [d(k)
1 , d(k)
2 , . . . , d(k)
N ]⊤,
k ∈{A, T, P}.
(12)
Here, N represents the dimension of the vector. In this study,
N=256. The output of the docking layer obtained in this way
functions as a process to enable processing in the subsequent
Embracement Layer.
The features of each modality aligned in the docking
layer are integrated through the Embracement Layer. In this
99496
VOLUME 13, 2025
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
layer, different modality features are efficiently combined by
using a stochastic sampling method. Specifically, a vector
r(k) obtained from a multinomial distribution is defined as
follows:
r(k) = [r(k)
1 , r(k)
2 , . . . , r(k)
N ],
k ∈{A, T, P}.
(13)
r(k) ∼Multinomial(1, p).
(14)
Here, p = [p1, p2, . . . , pF]⊤represents the probability of
each modality being selected, satisfying P
f pf = 1. Also,
within r(k), one component r(k)
i
= 1 is selected, and the
remaining components are r(k)
j
= 0 (j ̸= i). This r(k) is
applied to the output d(k) from the docking layer, and the
Hadamard product is calculated by the following equation:
d′(k) = r(k) ⊙d(k),
k ∈{A, T, P}.
(15)
ei =
X
k
d′(k).
(16)
Here, ⊙represents the element-wise product. Through this
process, only the features of the sampled modality are
selected. Then, ei is an embedding vector that integrates
the features of all modalities and is represented by e =
[e1, e2, . . . , eN]⊤. This Embracement Layer plays a role in
preventing over-reliance on a specific modality by randomly
selecting modalities. At the same time, it has a regularization
effect and improves the model’s ability to learn diverse
modality information [54], [88].
C. EVALUATION
1) LOSS FUNCTION
In this study, we adopted a loss function that combines
cross-entropy and L2 regularization, similar to previous
research [87]. This loss function is defined as follows:
J = −
1
PS
t=1 v(t)
S
X
i=1
v(i)
X
j=1
log Qi,j

ˆzi,j

+ µ∥φ∥2.
(17)
Here, S represents the number of sessions, v(i) represents the
number of utterances in session i, Qi,j represents the predicted
probability distribution of the emotion label of utterance
j, ˆzi,j represents its correct label, µ represents the weight
of regularization, and φ represents the model parameters,
respectively.
The first term of the loss function evaluates the prediction
accuracy based on cross-entropy, and the second term plays
a role in preventing overfitting of the model through L2
regularization. We use Adam [63] for optimization.
2) EVALUATION METRICS
To evaluate the performance of the model, we used the
following metrics, similar to previous research [54], [87]:
Accuracy =
TP + TN
TP + FP + TN + FN,
(18)
F1 = 2 · Precision · Recall
Precision + Recall,
(19)
where TP, TN, FP, and FN represent True Positive, True
Negative, False Positive, and False Negative, respectively,
which are calculated for each sequence. Precision and Recall
are calculated by the following equations:
Precision =
TP
TP + FP,
Recall =
TP
TP + FN.
(20)
3) VALIDATION SETTING
To evaluate the performance of the ER model, we used two
types of validation settings: Speaker-Dependent (SD) and
Speaker-Independent (SI). In the SD setting, we performed
10-fold cross-validation on each subject’s data, dividing the
data into 10 equal parts and using one as the test set and the
rest as training and validation data. This process is repeated
10 times for each subject, and the average performance
of all subjects is calculated. The SD setting evaluates the
model’s performance on individual emotional expressions
for each subject and is suitable for measuring optimization
performance adapted to a specific individual.
In the SI setting, one subject’s data is used as the test
set, and the other subjects’ data is used as training and
validation data. This process is repeated for all subjects, and
the average value of the evaluation metrics obtained for each
test set is calculated. This method evaluates the generalization
performance of the model for unknown subjects and is
suitable for measuring applicability in realistic scenarios.
IV. EXPERIMENT
A. EXPERIMENTAL DESIGN
In this study, we conducted simulated consultations to
evaluate the ER task in cancer consultations. Conducting
research with actual cancer patients poses ethical and prac-
tical constraints considering the psychological and physical
burden on the patients, and it is particularly challenging
with terminal patients. The difficulties of this kind of
intervention research are explained in previous studies [30],
[31], [32], [33], and to address this, Fujimori et al. conducted
an experiment using simulated patients for their baseline
experiment [89]. In this study, we also employed simulated
cancer patients to ensure the validity of the experiment while
approximating actual clinical situations.
For the simulated consultations, we employed trained
professional simulated patients. These simulated patients
specialize in replicating the emotions and psychological
responses during medical consultations, following the cancer
consultation scenarios used in previous research on cancer
patients [30], [31]. This allows for a faithful simulation of the
emotional exchange between physicians and patients. A total
of 36 simulated consultations were conducted.
1) PARTICIPANTS
a: PHYSICIANS
Three physicians conducted the simulated consultations.
They were certified palliative care physicians in the National
Cancer Center Hospital East (NCCE), had completed
VOLUME 13, 2025
99497
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
FIGURE 4. Emotional annotation methods.
Communication Skills Training (CST), and were familiar
with the SHARE model [89], the Communication Skills
Model (CSM) adopted in this study.
b: SIMULATED CANCER PATIENTS
The experimental participants cooperated with the experi-
ment after receiving an explanation through an explanatory
consent document beforehand. Six simulated patients (three
males and three females) who provided consent participated
in the study, each undergoing six consultations, resulting in a
total of 36 consultations.
The simulated patients have also been employed as
patient actors in previous clinical research on cancer [89].
In this study, we asked for the cooperation of members
of the Tsukuba Simulated Patient Association, who have
extensive experience as simulated patients in CST in cancer
care. The Tsukuba Simulated Patient Association consists
of members who have undergone specialized training to
participate as simulated patients in CST aimed at improving
communication in medical settings, and they possess the
understanding of cancer consultation scenarios and the skills
to fulfill their roles.
2) ETHICS DECLARATION
All participants provided written informed consent prior to
the experiment for the use of data, including text, audio, and
physiological signals, collected during the experiment. The
data recording methods and the experiment were approved
by the ethics committee of NCC.
B. EXPERIMENTAL PROCEDURE
The experimental procedure consisted of two steps: Simu-
lated Consultation and Emotional Annotation. Each experi-
ment took approximately 15 minutes.
1) SIMULATED CONSULTATION
The Simulated Consultations (FIGURE 1) were conducted
over five days starting from 2022/12/13, simulating actual
cancer consultations. As a preventive measure against
COVID-19 infection, the physician and the simulated patient
wore masks and maintained a distance of about one meter.
Data collection was performed using non-invasive methods.
For non-contact data measurement, equipment placed
about 1.5 meters away from the simulated patient was used to
record physiological signals such as heart rate and respiration
in real-time. In the simulated consultations, considering the
psychological burden on the patient and to mimic actual
consultations, three scenarios were set. These scenarios were
set with consideration for the cancer progression process,
referring to previous research on Japanese cancer patients’
preferences regarding the announcement of bad news [30],
[31], [33]. The Simulated Consultations were conducted in
the following order for each simulated patient (FIGURE 1):
#1 Diagnosis of advanced cancer
#2 Recurrence of cancer
#3 Cessation of anticancer treatment
Consultations were conducted for each scenario with six
simulated cancer patients. For each scenario, the physician
conducted consultations with and without the use of a
conceptual CSM, resulting in a total of 36 consultations
throughout the experiment. As the CSM, we adopted the
SHARE model in this study. The SHARE model is a model
for physicians to provide empathetic attitudes and mental
support to patients, and its validity has been guaranteed using
the Delphi method [90] in previous research. The components
of the model are as follows [31]:
S Setting up supportive environment for interview
H Considering how to deliver bad news
A Discussing additional information that patient would
like to know
RE Providing reassurance and addressing patient’s emo-
tions with empathic responses
2) EMOTIONAL ANNOTATION
After the Simulated Consultation, the physician and the sim-
ulated patient reviewed the video of the consultation. They
then annotated their emotional states during the consultation
on a unit circle created based on the two-dimensional model
of emotion [91] (Figure 4).
While watching the video displayed on the monitor, the
physician and the simulated patient plotted their emotions
using a controller. The physician plotted the predicted emo-
tional state of the simulated patient during the consultation,
and the simulated patient plotted the emotions they actually
experienced.
C. EXPERIMENTAL DATASET
1) AUDIO MODALITY
The audio modality data was recorded using unidirectional
lapel microphones attached to the chest of the physician and
the patient during the Simulated Consultations. The recording
environment was similar to a typical hospital examination
room, approximately 15 m2 to 20 m2 in size, with walls
made of standard sound-absorbing materials to suppress
reverberation.
99498
VOLUME 13, 2025
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
As the first step in preprocessing the audio modality
data, bandpass filtering was applied to the audio signals
using a Butterworth filter, limiting the frequency range
to 300 Hz to 3400 Hz, which primarily contains the human
voice. Next, we used the Demucs-Denoiser model [92],
a speech enhancement technique. This model has excellent
enhancement performance with a signal-to-interference ratio
of 20 dB or more even for very small windows of about
64 ms, and has been shown to be superior in terms of
speech enhancement compared to other methods [93]. Only
the speaker’s speech was emphasized from the audio signal
containing a mixture of noise and speaker’s voice, and
ultimately, clean speech was used as input for the audio
modality.
2) TEXT MODALITY
The text modality data was obtained by transcribing the
audio data recorded during the Simulated Consultation
experiments. The transcription was done manually by the
authors themselves, carefully recording the spoken words
as Japanese text while listening to the recorded audio. The
transcribed Japanese text was then translated into English
using GPT4-o. For quality assurance, the transcription and
translation were independently checked by three graduate
students and manually corrected as needed.
As for the statistical features of the dataset, the average
utterance length overall was 19.60 words (standard deviation:
16.89), and the average number of utterances per session
was approximately 77.22 (standard deviation: 19.88). These
values indicate that the text modality data is rich in content,
and it was utilized as input data for the ER model.
3) PHYSIOLOGICAL SIGNAL MODALITY
Physiological signal data was acquired using non-contact
millimeter-wave radar during the Simulated Consultations.
In this experiment, we employed specially trained simulated
cancer patients, and it is necessary to be aware of the
differences in autonomic nervous system indicators between
simulated patients and actual cancer patients when interpret-
ing the data.
Comparing the autonomic nervous system indicators of
the simulated cancer patients acquired in this study with
those of actual cancer patients in existing research [94]
(Table 1), although the respective indicators are generally
similar, the simulated cancer patients show larger values
than the actual cancer patients in RMSSD and pNN50,
which reflect parasympathetic nervous system activity.
Moreover, the standard deviation of RRI is considerably
larger (178.89 compared to 93.18), indicating a greater
heterogeneity among simulated patients. This result indicates
that there are some differences in some of the autonomic
nervous system indicators of simulated cancer patients.
Alternatively, it may be due to the accuracy of the non-contact
measurement approach used in this study. Although the
results of the ER model using physiological signals in
TABLE 1. Comparison of physiological indicators between actual cancer
patients [94] and simulated cancer patients (this study).
FIGURE 5. Percentage of labels in the sentiment data set.
this study show the effectiveness of the research targeting
simulated cancer patients, careful interpretation is necessary
considering the differences from actual patient data.
4) EMOTION
Emotion labels were annotated by the physician and the
patient plotting their emotions on a two-dimensional model
of Arousal and Valence [91] while reviewing the consultation
video after the Simulated Consultation. Emotions were
classified based on the two-dimensional model and defined
according to the following four criteria. First, for the 3-class
classification, emotions were divided into Valence (LV: Low
Valence, HV: High Valence, Neutral) and Arousal (LA: Low
Arousal, HA: High Arousal, Neutral). Next, for the 5-class
classification, emotions were categorized into five classes
based on the combination of Arousal and Valence levels: Low
Arousal Low Valence (LALV), Low Arousal High Valence
(LAHV), High Arousal Low Valence (HALV), High Arousal
High Valence (HAHV), and Neutral. Furthermore, for the 8-
class classification, specific emotion categories were defined
as ‘‘Happy’’, ‘‘Surprised’’, ‘‘Fearful’’, ‘‘Angry’’, ‘‘Sad’’,
VOLUME 13, 2025
99499
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
TABLE 2. Baseline performance evaluation of er by physician using
SHARE model.
‘‘Disgusted’’, ‘‘Calm’’, and ‘‘Neutral’’. The classification
method and the number of samples for each class are shown
in FIGURE 5.
In the 8-class classification, ‘‘Neutral’’ accounts for
35.88% (494 samples) and ‘‘Disgusted’’ accounts for 22.66%
(312 samples) of the total. For example, in a previous
study (multimodal emotion dataset: MELD) [95], ‘‘Neutral’’
accounted for 46.95% and ‘‘Disgusted’’ accounted for 2.63%.
In this study, the negative scenario of a cancer consultation
has an impact, with ‘‘Disgusted’’ accounting for a larger
proportion.
Additionally, we conducted an intraclass correlation (ICC)
analysis to evaluate the stability of the continuous Arousal
and Valence annotations both within and across subjects.
In this study, we used each simulated patient’s utterance
interval as a time window for analyzing the Arousal-Valence
data, consistent with the window size adopted in our proposed
framework. This approach yielded a total of 1377 labeled
samples of emotional states. For the within-subject analysis,
we computed the ICC individually for each of the six
participants to assess how consistently they labeled their
own emotional states over the course of the consultation.
For the across-subject analysis, we considered six patterns
that combined the presence or absence of the SHARE
model with the three scenarios (1)-3 in Fig. 1), and then
calculated the ICC among those participants who experienced
the same scenario and condition. This procedure allowed
us to measure how closely different individuals agreed in
their Arousal-Valence ratings under comparable consultation
conditions. As a result, the within-subject ICC was 0.52 for
Arousal and 0.57 for Valence, whereas the across-subject ICC
was 0.43 for Arousal and 0.51 for Valence. Although these
values may appear modest, they likely reflect the dynamic
nature of our consultation sessions, in which toggling the
TABLE 3. Comparison of prediction accuracy in audio modality models.
SHARE model can lead to rapid changes in emotional
responses.
D. BASELINE PERFORMANCE: PHYSICIAN ER
1) RESULTS
This section presents the baseline results of the ER accuracy
of active physicians with and without the intervention of
the SHARE Model (Table 2). In Table 2, ‘‘V’’ represents
Valence, and ‘‘A’’ represents Arousal, reflecting the two
main dimensions of emotion. The ‘‘With’’ and ‘‘Without’’
conditions indicate the presence or absence of the SHARE
Model intervention, respectively.
In the Valence-based 3-class classification, the without
SHARE condition outperformed the with SHARE condition
in all metrics. On the other hand, in the Arousal-based 3-class
classification, the with SHARE condition showed a slightly
higher score in Acc (with SHARE: 0.5432, without SHARE:
0.5388), but the without SHARE condition was superior in
Precision, Recall, and F1. In the 5-class classification of
Valence-Arousal, the with SHARE condition showed higher
scores than the without SHARE condition in all metrics
except Precision, but the difference was not significant. In the
8-class classification of typical emotions, the with SHARE
condition was higher in all metrics, with a particularly
noticeable difference in the F1 score (with SHARE: 0.3091,
without SHARE: 0.2638). These results suggest that while
the SHARE Model has a certain effect on improving Acc
in the 3-class classification, the without SHARE condition
may be superior in Precision and Recall. In more complex
classification criteria, the with SHARE condition showed
overall superior results.
The Total results in Table 2 show the overall trend for the
baseline of physicians’ ER accuracy. In the Valence-based
99500
VOLUME 13, 2025
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
TABLE 4. Comparison of prediction accuracy in text modality models.
TABLE 5. Comparison of prediction accuracy in physiological signal
modality models.
3-class classification, all metrics showed relatively high
values, with an F1 score of 0.5124. On the other hand, in the
Arousal-based 3-class classification, the scores were lower
overall compared to Valence, with an F1 score of 0.4793.
In the 5-class classification combining Valence-Arousal,
the accuracy was further reduced compared to the 3-class
classification due to the more complex classification criteria,
with an F1 score of 0.4043. In the 8-class classification, Acc
was 0.3826, Precision was 0.3121, Recall was 0.2940, and F1
was 0.2864, indicating even lower accuracy than the 5-class
classification.
2) DISCUSSIONS
These results are partially similar to the reports of previous
research on cancer patients [89]. Specifically, previous
research has shown that the use of the SHARE Model makes
physicians more empathetic, and this study also showed
a trend of the SHARE Model improving ER accuracy in
complex classification criteria. This suggests that the SHARE
Model may be effective in tasks dealing with more diverse
and subdivided emotions.
On the other hand, simple tasks such as 3-class classi-
fication may have a smaller effect of the SHARE Model
in terms of ER. The results of this study suggest that the
effect of the SHARE Model is limited in simple classification
criteria.
E. UER PERFORMANCE
1) RESULTS
This section presents the results of UER using audio, text, and
physiological signals (Tables 3, 4, and 5). The evaluation was
based on 3, 5, and 8-class classification criteria, comparing
Acc and F1 scores in Speaker-Dependent (SD) and Speaker-
Independent (SI) settings.
In the audio modality, wav2vec2.0 showed generally
superior performance, particularly in the SD setting, where
the F1 score reached 0.6881 and 0.7241 for the 3-class
classification of Valence and Arousal, respectively, achieving
performance equivalent to or better than HuBERT. Even in
the 8-class classification, it consistently outperformed other
methods with SD: 0.6326 and SI: 0.5396. Its effectiveness
was particularly confirmed in the SI setting, but the accuracy
difference between SD and SI remains a challenge.
In the text modality, Clinical BERT performed the best in
all tasks. In the 3-class classification of Valence and Arousal,
the F1 score reached 0.6946 and 0.6678, respectively, in the
SD setting, and it also showed high performance in the
more complex 5-class and 8-class classifications (5)-class:
0.6088, 8-class: 0.4915). Its effectiveness was particularly
pronounced in the SD setting and complex tasks, and its
accuracy stability surpassed other methods.
In the physiological signal modality, in Valence and
Arousal, using EMD or WT as feature extraction methods
showed higher performance than the method using time and
frequency domain features directly (TFD). In the 5-class
and 8-class classifications, WT performed better, showing
the highest values in the F1 score for both SD and SI
settings. However, the decrease in accuracy in the SI setting
compared to the SD setting is a common challenge with other
modalities.
Based on these results, in the UER, the text modality
had the highest predictive performance in the 3-class
classification, while the audio modality had the highest
predictive performance in the more complex 5 and 8-class
classifications. The physiological signal modality had the
lowest predictive performance in all classification criteria
compared to the other two methods.
VOLUME 13, 2025
99501
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
2) DISCUSSIONS
The results obtained in this study indicate that audio,
text, and physiological signal modalities have different
characteristics in ER, and several factors contribute to
the performance differences between them. In the audio
modality models, HuBERT and Wav2vec2.0-based models
showed the highest performance. This is attributed to their
excellent feature extraction capabilities due to large-scale
pre-training, consistent with numerous research results [96],
[97], [98], [99]. For example, Kim and Kang showed that
wav2vec2.0 has higher accuracy than other feature extraction
methods (such as MFCC) [96], and similarly, wav2vec2.0 has
the highest accuracy in this study.
On the other hand, the superiority of Clinical BERT in the
text modality is due to the fact that pre-training specialized
in the medical field makes it easier to understand medical
contexts. The domain of the corpus used for pre-training is
preferably the same as the domain of the target task [69], and
it has been shown that using BERT for the clinical domain can
improve performance in Natural Language Processing (NLP)
tasks in the clinical domain [67], [68]. The results of this
study also suggest that using Clinical-BERT, its adaptability
surpassed other methods in the specific data of patient-
physician dialogue, and this result is similar to previous
research [68].
In the physiological signal modality, EMD and WT showed
high performance. The effectiveness of EMD and WT has
also been shown in previous research [79], [80], [81], [82],
and in this study, they are more effective than ordinary TFD
features for extracting features of physiological signals.
Comparing the results of UER, the audio modality
showed the highest performance and the physiological signal
modality showed the lowest performance in this study. This
difference is attributed to the amount of information provided
by each modality and the measurement method. Nonverbal
elements play a major role in emotional communication, and
there is a research result that linguistic messages account for
only 8% of the whole, while voice tone accounts for 38%
and facial expressions account for 55% [100], indicating the
importance of the audio modality for ER. In fact, in a recent
ER study [101], the audio modality had the highest accuracy
with an Acc of 0.6606, while the text modality, for example,
had an accuracy of 0.5874. On the other hand, the reason
for the low performance of the physiological signal modality
is that the data was measured non-contactly. Non-contact
measurement is susceptible to noise and makes it difficult
to accurately capture signal fluctuations, which may result in
insufficient extraction of features necessary for ER.
Also, the reason why the SD setting showed higher per-
formance than the SI setting is that the SD setting allows for
learning based on a single speaker, enabling more appropriate
modeling of speaker-specific characteristics. On the other
hand, the SI setting requires generalization across different
speakers, making learning more difficult. In particular,
in modalities such as audio and text where emotional
expression is susceptible to speaker-specific influences, the
TABLE 6. Performance evaluation of emotion classification using
cross-modal transformer fusion.
performance difference between SD and SI is prominent, and
this trend is similar to other research results [44], [62].
F. MER PERFORMANCE
1) RESULTS
In the MER, we first compared multiple feature extraction
methods for each modality in the preceding UER experi-
ments, then adopted the approach that achieved the highest
accuracy (Acc) and F1 scores (Tables 3, 4, and 5). As a
result, we chose wav2vec2.0 for the audio modality (A),
Clinical-BERT for the text modality (T), and WT for the
physiological signal modality (P). The results of emotion
classification using multimodal fusion are shown in Table 6.
In the 3-class classification based on Valence and Arousal,
A+T+P (integration of Audio, Text, and Physiological
Signal) showed the highest accuracy, with F1 scores of
0.8105 for Valence and 0.8163 for Arousal in the SD setting,
and 0.7607 and 0.7403, respectively, in the SI setting. On the
other hand, although the scores generally decrease in the 5-
class and 8-class classifications, A+T+P still outperforms
other modality combinations, with F1 scores of 0.7341 for
5-class and 0.6614 for 8-class in the SD setting, indicating
the effectiveness of integrating multimodal information even
in complex tasks.
The confusion matrix of emotions in Figure 6 shows
the prediction accuracy for each label in each classification
task. In the Valence-based 3-class classification (Figure 6,
a), LV showed the highest recognition accuracy, and
in the Arousal-based 3-class classification (Figure 6, b),
LA showed the highest recognition accuracy (Figure 6, b),
99502
VOLUME 13, 2025
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
FIGURE 6. Confusion matrix of emotions in 8-Class classification.
with accuracies of 0.85 and 0.83, respectively. In the 5-
class classification (Figure 6, c), HALV showed relatively
high accuracy, and in the 8-class classification (Figure 6,
d), Disgusted showed relatively high accuracy, but there is
a tendency for a high rate of misclassification as Neutral
emotion in all classification tasks.
2) DISCUSSIONS
Figure 7 shows the performance of the training and validation
sets for the most complex 8-class classification in multimodal
fusion emotion classification. The loss values (Figure 7: a,
b) decrease steadily as the training epochs progress, and
convergence is confirmed in both the SD and SI settings.
Since poor prediction on untrained sample data is caused by
overfitting [102], we overcome overfitting by early stopping
FIGURE 7. Loss value and accuracy performance in SD and SI settings for
8-Class classification.
FIGURE 8. t-SNE visualization of the CMT in the eight-class classification.
in this study. Early stopping is a common method to overcome
overfitting [103]. Also, the Acc of the training and validation
sets (Figure 7: c, d) steadily improves as learning progresses
and converges around 50 epochs. The fact that the accuracy
of both sets almost matches indicates that an appropriate
learning rate was selected and overfitting was suppressed.
Furthermore, we examined how the extracted features clus-
ter across different emotional states. As shown in Figure 8,
we applied t-SNE visualization to the learned representations
for the eight-class classification [104]. Although partial
clustering is observed for each labeled emotion, there is
considerable overlap between adjacent emotions such as
Sad and Disgusted, indicating that some emotional states
share similar feature patterns and are therefore difficult to
distinguish precisely. In particular, the Neutral class displays
relatively large dispersion, aligning with previous findings
VOLUME 13, 2025
99503
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
suggesting that neutral expressions may resemble multiple
other emotions depending on the context [54].
In the results of the emotion confusion matrix (Figure 6),
one reason for the large number of misclassifications into
Neutral emotion is that the number of data samples with
the Neutral label is excessive compared to other emotion
labels. In a study on ER targeting general dialogue [54], 47%
of the data was classified as Neutral emotion, the highest
percentage, and as a result, a tendency for a large number of
misclassifications into the Neutral label was reported. In this
study, Neutral emotion accounts for about 36% of all data,
which is a large proportion overall, so a similar tendency is
observed. Also, while there are many misclassifications into
the Neutral label, the proportion of correctly classified cases
is also relatively high. Regarding this point, a study on ER in
clinical settings [105] also observed a large number of Neutral
emotions, confirming similar results.
V. GENERAL DISCUSSION
A. CAN NON-CONTACT ER (PROPOSED METHOD)
OUTPERFORM THE PREDICTION ACCURACY OF
PHYSICIANS?
The non-contact MER approach proposed in this study
has the potential to assist physicians in recognizing emo-
tions during medical examinations. Empathetic behavior by
physicians involves a considerable expenditure of mental
energy in the process of empathizing with patients. It has
been reported that, especially when deeply empathizing with
patients suffering from trauma or pain, the physician’s own
mental vulnerability may increase [106], [107], [108]. Such
excessive immersion in empathy can be a risk factor that
impairs the physician’s mental health, like a ‘‘double-edged
sword’’ [28]. Therefore, in clinical practice, there is a need to
develop effective support processes for objectively assessing
and appropriately adjusting emotions.
The results of this study showed that in the most complex
8-class classification task, the proposed non-contact multi-
modal integration (A+T+P: audio, text, and physiological
signals) achieved high performance with Acc = 0.6548 and
F1 = 0.6088, exceeding the prediction accuracy of physicians
(Acc = 0.3826, F1 = 0.2864) (Table 7). This result suggests
that the proposed method may effectively complement
physicians’ ER in clinical examinations. On the other hand,
the reason for the low prediction accuracy of physicians in
this study may be due to their habituation to patients’ pain.
Related research has reported a tendency for physicians to
have a suppressed response at the EEG level to patients’
pain and discomfort, suggesting that medical expertise and
experience may reduce sensitivity to patients’ pain [28].
This method is expected to not only reinforce physicians’
recognition ability but also reduce the burden of ER and
suppress compassion fatigue. By assisting physicians in
quickly and accurately grasping patients’ emotions, it may
improve the efficiency of clinical examinations and the
quality of patient care. Furthermore, by using this technology
TABLE 7. 8-Class (SI) performance summary across models.
complementarily, it may be possible to prevent physicians
from being excessively emotionally burdened and maintain
a stable empathetic response to patients.
B. DOES MER OUTPERFORM UER ?
This study compared the performance of UER and MER
methods and demonstrated that MER significantly outper-
forms UER (Table 7). First, in UER, the audio modality
(A) showed particularly excellent performance, surpassing
the text modality (T) and physiological signal modality (P)
in terms of emotion classification accuracy. This trend was
prominent in complex classification tasks such as 5-class and
8-class.
Next, in MER, the combinations including the audio
modality (A+T, A+P) showed higher accuracy than the
combination of text modality and physiological signal modal-
ity (T+P). Furthermore, the combination of audio modality
and text modality (A+T) achieved the best performance.
This result is consistent with the report by Li et al. [101],
suggesting that audio information significantly contributes
to improving the accuracy of ER. Audio information
contains various features that reflect emotional states, such
as intonation, tempo, and emphasis. By integrating audio
information with text information and physiological signals,
the features of each modality can complement each other,
leading to improved accuracy in emotion classification.
Previous studies have also reported that MER approaches
integrating multiple modalities such as acoustic informa-
tion, facial expressions, and body movements show higher
performance than UER [109], [110], [111], [112]. The
results of this study are consistent with these findings.In
addition, Kawamura et al. reported that an approach using
physiological signals achieved high accuracy in ER [113].
In this study, further improvement in accuracy was observed
by integrating the physiological signal modality in addition
to the audio modality and text modality (A+T+P). This
suggests that physiological signals can be effectively utilized
for ER as objective indicators reflecting emotional states.
C. LIMITATIONS AND FUTURE WORKS
Although the results of this study suggest the usefulness
of non-contact ER in clinical settings, there are some
99504
VOLUME 13, 2025
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
limitations. First, considering the ethical and practical
challenges of collecting data from patients who may be facing
highly sensitive situations (e.g., terminal cancer diagnoses),
we conducted experiments using trained professional simu-
lated patients. Although these simulated patients are educated
to approximate the emotional expressions of real patients,
they may still differ from individuals truly experiencing
severe physical and psychological distress. Consequently,
there is a concern that they may not fully capture the
high-stress emotional states and complex interactions typical
of terminal cancer care. Nevertheless, using simulated
patients is recognized as a practical step in medical education:
physicians themselves often practice communication skills
with such simulations. Thus, building a training dataset
with simulated patients and gradually verifying its utility
is a realistic approach for eventual deployment in clinical
settings, even if it does not immediately substitute for data
from actual patients.
In addition, this study primarily focused on enhancing ER
accuracy and did not examine other psychological and social
factors that influence the physician-patient relationship, such
as patient satisfaction, treatment motivation, or trust in
the physician. Therefore, when applying this framework
to real-world medical contexts, it is crucial to consider
not only ER performance but also broader patient-centered
outcome indicators (e.g., satisfaction, trust). Further verifi-
cation, including data collection from actual patients under
appropriate ethical guidelines, will be essential to confirm the
value of this framework in actual clinical practice.
In the experiments conducted for this study, we anno-
tated emotions in each consultation video by continuously
plotting them on a two-dimensional model using a game
controller. This method was employed to maintain a high
sampling rate of emotional data and to ensure a sufficient
number of samples for analysis. However, adopting and
validating a more standardized annotation approach–such
as the Self-Assessment Manikin (SAM)–could yield more
robust and reliable evaluation [114]. Additionally, comparing
the non-contact physiological signals acquired during the
experiments with gold-standard sensors (e.g., ECG, PPG)
would help solidify the reliability of our approach in actual
clinical settings.
Furthermore, while we employed standard feature extrac-
tion methods widely used in previous research, this does
not necessarily guarantee that the selected features are
optimal. Indeed, more recent or specialized techniques may
further improve performance or robustness in certain clinical
contexts.
VI. CONCLUSION
In this study, we proposed a MER framework using
non-contact measurement for clinical settings and verified
its effectiveness. We showed that by integrating multiple
modalities (audio, text, and physiological signals), emotion
classification accuracy is significantly improved compared
to UER. Also, this study is the first report to quantitatively
evaluate the ER accuracy of active physicians, and the
proposed framework showed performance exceeding the
prediction accuracy of physicians. This suggests that while
complex decision-making in medical settings is supported by
multifaceted factors, at least in terms of ER, the non-contact
multimodal approach can complement the judgment of
physicians.
The results of this study suggest the potential of a system
that supports physicians in recognizing patients’ distress
while preventing excessive empathic stress. Furthermore,
they are significant in encouraging the development of
medical support technologies that contribute to improving
the quality of communication with cancer patients. However,
this study is still at the stage of initial validation through
experiments using simulated patients, and additional verifica-
tion is essential, considering the differences in physiological
responses in actual patient populations. The findings obtained
in this study may also be applicable to other clinical fields
where emotional care is required and are expected to serve
as fundamental data for the advancement of future medical
support technologies.
ACKNOWLEDGMENT
The authors would like to thank Assoc. Prof. Mamoru
Amemiya and Asst. Prof. Hiroki Takahashi of the Institute
for Systems and Information Engineering with the University
of Tsukuba for their advice throughout this study. They also
express their gratitude to Dr. Emi Kubo and Dr. Kazuhiro
Kosugi of the Department of Palliative Medicine, National
Cancer Center Hospital East, for conducting the simulated
consultations. Additionally, they acknowledge the use of
two AI systems (ChatGPT O1 Pro and Gemini 1.5 Pro) for
proofreading this article.
REFERENCES
[1] R. Berger, B. Bulmash, N. Drori, O. Ben-Assuli, and R. Herstein,
‘‘The patient–physician relationship: An account of the physician’s
perspective,’’ Isr. J. health policy Res., vol. 9, no. 1, pp. 1–16, Jun. 2020.
[2] B. D. Silverman, ‘‘Physician behavior and bedside manners: The
influence of William Osler and the Johns Hopkins school of medicine,’’
Baylor Univ. Med. Center Proc., vol. 25, no. 1, pp. 58–61, Jan. 2012.
[3] A. Maitra, M. R. Kamdar, D. M. Zulman, M. C. Haverfield, C. Brown-
Johnson, R. Schwartz, S. T. Israni, A. Verghese, and M. A. Musen, ‘‘Using
ethnographic methods to classify the human experience in medicine:
A case study of the presence ontology,’’ J. Amer. Med. Inform. Assoc.,
vol. 28, no. 9, pp. 1900–1909, Aug. 2021.
[4] E. Molleman, P. J. Krabbendam, A. A. Annyas, H. S. Koops, D. T. Sleijfer,
and A. Vermey, ‘‘The significance of the doctor-patient relationship in
coping with cancer,’’ Social Sci. Med., vol. 18, no. 6, pp. 475–480,
Jan. 1984.
[5] H. Riess, ‘‘Empathy matters: Study shows that teaching empathy can
improve patient satisfaction,’’ Iowa Med., J. Iowa Med. Soc., vol. 106,
no. 1, p. 13, 2016.
[6] M. Borghi and M. M. Mariani, ‘‘The role of emotions in the consumer
meaning-making of interactions with social robots,’’ Technolog. Forecast-
ing Social Change, vol. 182, Sep. 2022, Art. no. 121844.
[7] J. Decety and A. Fotopoulou, ‘‘Why empathy has a beneficial impact on
others in medicine: Unifying theories,’’ Frontiers Behav. Neurosci., vol. 8,
p. 457, Jan. 2015.
[8] S. S. Kim, S. Kaplowitz, and M. V. Johnston, ‘‘The effects of
physician empathy on patient satisfaction and compliance,’’ Eval. Health
Professions, vol. 27, no. 3, pp. 237–251, Sep. 2004.
VOLUME 13, 2025
99505
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
[9] J. Roche and D. Harmon, ‘‘Exploring the facets of empathy and pain in
clinical practice: A review,’’ Pain Pract., vol. 17, no. 8, pp. 1089–1096,
Nov. 2017.
[10] P. Burnard, ‘‘Empathy: The key to understanding,’’ Prof. Nurse (London,
England), vol. 3, no. 10, pp. 388–391, Jul. 1988.
[11] D. A. Matthews, A. L. Suchman, and W. T. Branch Jr., ‘‘Making
connexions: Enhancing the therapeutic potential of PatientClinician
relationships,’’ Ann. Internal Med., vol. 118, no. 12, pp. 973–977,
Jun. 1993.
[12] D. H. Novack, ‘‘Therapeutic aspects of the clinical encounter,’’ J. Gen.
Internal Med., vol. 2, no. 5, pp. 346–355, Sep. 1987.
[13] A. L. Suchman, ‘‘A model of empathic communication in the medical
interview,’’ aJ. Amer. Med. Assoc., vol. 277, no. 8, p. 678, Feb. 1997.
[14] M. Maithri, U. Raghavendra, A. Gudigar, J. Samanth, P. D. Barua,
M. Murugappan, Y. Chakole, and U. R. Acharya, ‘‘Automated emotion
recognition: Current trends and future perspectives,’’ Comput. Methods
Programs Biomed., vol. 215, Mar. 2022, Art. no. 106646.
[15] T. Bänziger, D. Grandjean, and K. R. Scherer, ‘‘Emotion recognition from
expressions in face, voice, and body: The multimodal emotion recognition
test (MERT),’’ Emotion, vol. 9, no. 5, pp. 691–704, 2009.
[16] E. Batbaatar, M. Li, and K. H. Ryu, ‘‘Semantic-emotion neural
network for emotion recognition from text,’’ IEEE Access, vol. 7,
pp. 111866–111878, 2019.
[17] K.-C. Chin, T.-C. Hsieh, W.-C. Chiang, Y.-C. Chien, J.-T. Sun, H.-
Y. Lin, M.-J. Hsieh, C.-W. Yang, A. Y. Chen, and M. H.-M. Ma,
‘‘Early recognition of a caller’s emotion in out-of-hospital cardiac arrest
dispatching: An artificial intelligence approach,’’ Resuscitation, vol. 167,
pp. 144–150, Oct. 2021.
[18] N. Samadiani, G. Huang, W. Luo, C.-H. Chi, Y. Shu, R. Wang, and
T. Kocaturk, ‘‘A multiple feature fusion framework for video emotion
recognition in the wild,’’ Concurrency Comput., Pract. Exper., vol. 34,
no. 8, Apr. 2022, Art. no. e5764.
[19] T. H. Zhou, W. L. Liang, H. Y. Liu, W. Pu, and L. Wang, ‘‘Wavelet-based
emotion recognition using single channel EEG device,’’ in Proc. 16th Int.
Conf. Intell. Comput., Bari, Italy. Cham, Switzerland: Springer, Jan. 2020,
pp. 510–519.
[20] S. G. Koolagudi and K. S. Rao, ‘‘Emotion recognition from speech: A
review,’’ Int. J. Speech Technol., vol. 15, no. 2, pp. 99–117, Jun. 2012.
[21] N. Samadiani, G. Huang, B. Cai, W. Luo, C.-H. Chi, Y. Xiang, and J. He,
‘‘A review on automatic facial expression recognition systems assisted
by multimodal sensor data,’’ Sensors, vol. 19, no. 8, p. 1863, Apr. 2019.
[Online]. Available: https://www.mdpi.com/1424-8220/19/8/1863
[22] M. Fässler, K. Meissner, A. Schneider, and K. Linde, ‘‘Frequency and
circumstances of placebo use in clinical practice—A systematic review
of empirical studies,’’ BMC Med., vol. 8, no. 1, pp. 1–10, Dec. 2010.
[23] S. K. B. Sangeetha, R. R. Immanuel, S. K. Mathivanan, J. Cho,
and S. V. Easwaramoorthy, ‘‘An empirical analysis of multimodal
affective computing approaches for advancing emotional intelligence
in artificial intelligence for healthcare,’’ IEEE Access, vol. 12,
pp. 114416–114434, 2024.
[24] M. E. Hurley, A. Sonig, J. Herrington, E. A. Storch, G. Lázaro-Muñoz,
J. Blumenthal-Barby, and K. Kostick-Quenet, ‘‘Ethical considerations
for integrating multimodal computer perception and neurotechnology,’’
Frontiers Hum. Neurosci., vol. 18, Feb. 2024, Art. no. 1332451.
[25] G. Zieff, L. C. Bates-Fraser, P. Pagan Lassalle, C. Paterson, K. Heffernan,
and L. Stoner, ‘‘Editorial: Non-invasive physiological measurements:
From discovery to implementation,’’ Frontiers Physiol., vol. 14,
Jan. 2024, Art. no. 1356664, doi: 10.3389/fphys.2023.1356664.
[26] J. Kranjec, S. Beguš, G. Geršak, and J. Drnovšek, ‘‘Non-contact heart
rate and heart rate variability measurements: A review,’’ Biomed. Signal
Process. Control, vol. 13, pp. 102–112, Sep. 2014.
[27] B. Newton and Z. Vaskalis, ‘‘Empathic divergence: Partially blunting an
affective empathic response while maintaining cognitive empathy is an
important skill for medical students to acquire,’’ Med. Res. Arch., vol. 12,
no. 1, 2024.
[28] J. Decety, C.-Y. Yang, and Y. Cheng, ‘‘Physicians down-regulate
their pain empathy response: An event-related brain potential study,’’
NeuroImage, vol. 50, no. 4, pp. 1676–1682, May 2010.
[29] A. Dinoff, S. Lynch, A. S. Hameed, J. Koestler, S. J. Ferrando, and
L. Klepacz, ‘‘When did the empathy die: Examining the correlation
between length of medical training and level of empathy,’’ Med. Sci.
Educator, vol. 33, no. 2, pp. 489–497, Mar. 2023.
[30] M. Fujimori, T. Akechi, N. Akizuki, M. Okamura, A. Oba, Y. Sakano,
and Y. Uchitomi, ‘‘Good communication with patients receiving bad
news about cancer in Japan,’’ Psycho-Oncology, vol. 14, no. 12,
pp. 1043–1051, 2005.
[31] M. Fujimori, T. Akechi, T. Morita, M. Inagaki, N. Akizuki, Y. Sakano, and
Y. Uchitomi, ‘‘Preferences of cancer patients regarding the disclosure of
bad news,’’ Psycho-Oncology, vol. 16, no. 6, pp. 573–581, Jun. 2007.
[32] M. Fujimori, P. A. Parker, T. Akechi, Y. Sakano, W. F. Baile, and
Y. Uchitomi, ‘‘Japanese cancer patients’ communication style prefer-
ences when receiving bad news,’’ Psycho-Oncology, vol. 16, no. 7,
pp. 617–625, Jul. 2007.
[33] M. Fujimori and Y. Uchitomi, ‘‘Preferences of cancer patients regarding
communication of bad news: A systematic literature review,’’ Jpn. J. Clin.
Oncol., vol. 39, no. 4, pp. 201–216, Feb. 2009.
[34] P. D. Purnamasari, A. A. P. Ratna, and B. Kusumoputro, ‘‘EEG based
patient emotion monitoring using relative wavelet energy feature and back
propagation neural network,’’ in Proc. 37th Annu. Int. Conf. IEEE Eng.
Med. Biol. Soc. (EMBC), Aug. 2015, pp. 2820–2823.
[35] C. Gentili, G. Valenza, M. Nardelli, A. Lanatà, G. Bertschy, L. Weiner,
M. Mauri, E. P. Scilingo, and P. Pietrini, ‘‘Longitudinal monitoring of
heartbeat dynamics predicts mood changes in bipolar patients: A pilot
study,’’ J. Affect. Disorders, vol. 209, pp. 30–38, Feb. 2017.
[36] A. Verma, A. Dogra, K. Malik, and M. Talwar, ‘‘Emotion recognition
system for patients with behavioral disorders,’’ in Intelligent Communi-
cation, Control and Devices, R. Singh, S. Choudhury, and A. Gehlot, Eds.,
Singapore: Springer, 2018, pp. 139–145.
[37] J. Zhang, K. Zheng, S. Mazhar, X. Fu, and J. Kong, ‘‘Trusted emotion
recognition based on multiple signals captured from video,’’ Expert Syst.
Appl., vol. 233, Dec. 2023, Art. no. 120948.
[38] P. Saha, A. K. A. Kunju, M. E. Majid, S. B. A. Kashem, M. Nashbat,
A. Ashraf, M. Hasan, A. Khandakar, M. S. Hossain, A. Alqahtani,
and M. E. H. Chowdhury, ‘‘Novel multimodal emotion detection method
using electroencephalogram and electrocardiogram signals,’’ Biomed.
Signal Process. Control, vol. 92, Jun. 2024, Art. no. 106002.
[39] H. Cai, ‘‘A multi-modal open dataset for mental-disorder analysis,’’ Sci.
Data, vol. 9, no. 1, p. 178, Apr. 2022.
[40] Y. Zhao, Z. Liang, J. Du, L. Zhang, C. Liu, and L. Zhao, ‘‘Multi-head
attention-based long short-term memory for depression detection from
speech,’’ Frontiers Neurorobotics, vol. 15, Aug. 2021, Art. no. 684037.
[41] F. Chollet, ‘‘Xception: Deep learning with depthwise separable convo-
lutions,’’ in Proc. IEEE Conf. Comput. Vis. Pattern Recognit. (CVPR),
Jul. 2017, pp. 1800–1807.
[42] W. Zheng, L. Yan, and F.-Y. Wang, ‘‘Two birds with one stone:
Knowledge-embedded temporal convolutional transformer for depression
detection and emotion recognition,’’ IEEE Trans. Affect. Comput.,
pp. 1–18, 2023.
[43] Y. Wang, X. Chen, L. Cao, W. Huang, F. Sun, and Y. Wang, ‘‘Multimodal
token fusion for vision transformers,’’ in Proc. IEEE/CVF Conf. Comput.
Vis. Pattern Recognit. (CVPR), Jun. 2022, pp. 12176–12185.
[44] M. S. Zitouni, C. Y. Park, U. Lee, L. J. Hadjileontiadis, and A. Khandoker,
‘‘LSTM-modeling of emotion recognition using peripheral physiological
signals in naturalistic conversations,’’ IEEE J. Biomed. Health Informat.,
vol. 27, no. 2, pp. 912–923, Feb. 2023.
[45] S. R. Livingstone and F. A. Russo, ‘‘The ryerson audio-visual database
of emotional speech and song (RAVDESS): A dynamic, multimodal
set of facial and vocal expressions in North American English,’’
PLoS ONE, vol. 13, no. 5, May 2018, Art. no. e0196391, doi:
10.1371/journal.pone.0196391.
[46] F. Andayani, L. B. Theng, M. T. Tsun, and C. Chua, ‘‘Hybrid LSTM-
transformer model for emotion recognition from speech audio files,’’
IEEE Access, vol. 10, pp. 36018–36027, 2022.
[47] L. Zhu, L. Chen, D. Zhao, J. Zhou, and W. Zhang, ‘‘Emotion recognition
from Chinese speech for smart affective services using a combination of
SVM and DBN,’’ Sensors, vol. 17, no. 7, p. 1694, Jul. 2017.
[48] Y. Li, H. Su, X. Shen, W. Li, Z. Cao, and S. Niu, ‘‘DailyDialog: A
manually labelled multi-turn dialogue dataset,’’ 2017, arXiv:1710.03957.
[49] E. Rejaibi, A. Komaty, F. Meriaudeau, S. Agrebi, and A. Othmani,
‘‘MFCC-based recurrent neural network for automatic clinical depression
recognition and assessment from speech,’’ Biomed. Signal Process.
Control, vol. 71, Jan. 2022, Art. no. 103107.
[50] M. B. Er, ‘‘A novel approach for classification of speech emo-
tions based on deep and acoustic features,’’ IEEE Access, vol. 8,
pp. 221640–221653, 2020.
99506
VOLUME 13, 2025
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
[51] J. A. Miranda-Correa, M. K. Abadi, N. Sebe, and I. Patras, ‘‘AMIGOS:
A dataset for affect, personality and mood research on individuals and
groups,’’ IEEE Trans. Affect. Comput., vol. 12, no. 2, pp. 479–493,
Apr. 2021.
[52] S. Koelstra, C. Muhl, M. Soleymani, J.-S. Lee, A. Yazdani, T. Ebrahimi,
T. Pun, A. Nijholt, and I. Patras, ‘‘DEAP: A database for emotion analysis
;Using physiological signals,’’ IEEE Trans. Affect. Comput., vol. 3, no. 1,
pp. 18–31, Jan. 2012.
[53] A. Waheed Awan, I. Taj, S. Khalid, S. M. Usman, A. S. Imran,
and M. U. Akram, ‘‘Advancing emotional health assessments: A hybrid
deep learning approach using physiological signals for robust emotion
recognition,’’ IEEE Access, vol. 12, pp. 141890–141904, 2024.
[54] B. Xie, M. Sidulova, and C. H. Park, ‘‘Robust multimodal emotion
recognition from conversation with transformer-based crossmodality
fusion,’’ Sensors, vol. 21, no. 14, p. 4913, Jul. 2021. [Online]. Available:
https://www.mdpi.com/1424-8220/21/14/4913
[55] Sakura
Tech
Co.,
Ltd.
(2021).
Miradar;8
High
Performance
24GHz
FMCW
MIMO
Radar
Platform.
[Online].
Available:
https://sakuratech.jp/miradar-8/
[56] Y. Miyashita, ‘‘Multi-criteria design analysis of sensor systems for
railway level crossings,’’ Ph.D. dissertation, Massachusetts Inst. Technol.,
2020.
[57] S. Schneider, A. Baevski, R. Collobert, and M. Auli, ‘‘Wav2vec: Unsu-
pervised pre-training for speech recognition,’’ 2019, arXiv:1904.05862.
[58] A. Baevski, H. Zhou, A. Mohamed, and M. Auli, ‘‘Wav2vec 2.0: A
framework for self-supervised learning of speech representations,’’ in
Proc. Adv. Neural Inf. Process. Syst., Jan. 2020, pp. 12449–12460.
[59] W.-N. Hsu, B. Bolte, Y. H. Tsai, K. Lakhotia, R. Salakhutdinov, and
A. Mohamed, ‘‘HuBERT: Self-supervised speech representation learning
by masked prediction of hidden units,’’ IEEE/ACM Trans. Audio, Speech,
Language Process., vol. 29, pp. 3451–3460, 2021.
[60] H. S. Kumbhar and S. U. Bhandari, ‘‘Speech emotion recognition using
MFCC features and LSTM network,’’ in Proc. 5th Int. Conf. Comput.,
Commun., Control Autom. (ICCUBEA), Sep. 2019, pp. 1–3.
[61] M. Sajjad and S. Kwon, ‘‘Clustering-based speech emotion recognition
by incorporating learned features and deep BiLSTM,’’ IEEE Access,
vol. 8, pp. 79861–79875, 2020.
[62] Y. Wang, A. Boumadane, and A. Heba, ‘‘A fine-tuned Wav2vec
2.0/HuBERT benchmark for speech emotion recognition, speaker veri-
fication and spoken language understanding,’’ 2021, arXiv:2111.02735.
[63] D. P. Kingma and J. Ba, ‘‘Adam: A method for stochastic optimization
3rd international conference on learning representations,’’ in Proc. ICLR
Conf. Track, vol. 1, 2015.
[64] Z. Yang, Z. Dai, Y. Yang, J. Carbonell, R. Salakhutdinov, and
Q. V. Le, ‘‘XLNet: Generalized autoregressive pretraining for language
understanding,’’ 2019, arXiv:1906.08237.
[65] A. Radford, K. Narasimhan, T. Salimans, and I. Sutskever. (2018).
Improving
Language
Understanding
By
Generative
Pre-training.
[Online]. Available: https://www.mikecaptain.com/resources/pdf/GPT-
1.pdf
[66] J. Devlin, M.-W. Chang, K. Lee, and K. Toutanova, ‘‘BERT: Pre-training
of deep bidirectional transformers for language understanding,’’ 2018,
arXiv:1810.04805.
[67] I. Beltagy, K. Lo, and A. Cohan, ‘‘SciBERT: A pretrained language model
for scientific text,’’ 2019, arXiv:1903.10676.
[68] E. Alsentzer, J. R. Murphy, W. Boag, W.-H. Weng, D. Jin, T.
Naumann, and M. B. A. McDermott, ‘‘Publicly available clinical BERT
embeddings,’’ 2019, arXiv:1904.03323.
[69] Y. Kawazoe, D. Shibata, E. Shinohara, E. Aramaki, and K. Ohe, ‘‘A
clinical specific BERT developed using a huge Japanese clinical text
corpus,’’ PLoS ONE, vol. 16, no. 11, Nov. 2021, Art. no. e0259763.
[70] T. Wolf, V. Sanh, J. Chaumond, and C. Delangue, ‘‘TransferTransfo:
A transfer learning approach for neural network based conversational
agents,’’ 2019, arXiv:1901.08149.
[71] G. K. Verma and U. S. Tiwary, ‘‘Multimodal fusion framework: A
multiresolution approach for emotion classification and recognition from
physiological signals,’’ NeuroImage, vol. 102, pp. 162–172, Nov. 2014.
[72] Z. Yin, Y. Wang, L. Liu, W. Zhang, and J. Zhang, ‘‘Cross-subject EEG
feature selection for emotion recognition using transfer recursive feature
elimination,’’ Frontiers Neurorobotics, vol. 11, p. 19, Apr. 2017.
[73] J. Piskorski and P. Guzik, ‘‘Filtering Poincare plots,’’ Comput. Methods
Sci. Technol., vol. 11, no. 1, pp. 39–48, 2005.
[74] K. Tung, P.-K. Liu, Y.-C. Chuang, S.-H. Wang, and A. A. Wu,
‘‘Entropy-assisted multi-modal emotion recognition framework based on
physiological signals,’’ in Proc. IEEE-EMBS Conf. Biomed. Eng. Sci.
(IECBES), Dec. 2018, pp. 22–26.
[75] A. Sepúlveda, F. Castillo, C. Palma, and M. Rodriguez-Fernandez,
‘‘Emotion recognition from ECG signals using wavelet scattering and
machine learning,’’ Appl. Sci., vol. 11, no. 11, p. 4945, May 2021.
[Online]. Available: https://www.mdpi.com/2076-3417/11/11/4945
[76] N. E. Huang, Z. Shen, S. R. Long, M. C. Wu, H. H. Shih, Q.
Zheng, N.-C. Yen, C. C. Tung, and H. H. Liu, ‘‘The empirical mode
decomposition and the Hilbert spectrum for nonlinear and non-stationary
time series analysis,’’ Proc. Roy. Soc. London. Ser. A, Math., Phys. Eng.
Sci., vol. 454, no. 1971, pp. 903–995, Mar. 1998.
[77] I. Daubechies, ‘‘Ten lectures on wavelets,’’ Soc. Ind. Appl. Math., 1992.
[78] M. A. Hasnul, N. A. A. Aziz, S. Alelyani, M. Mohana, and A. A. Aziz,
‘‘Electrocardiogram-based emotion recognition systems and their appli-
cations in healthcare—A review,’’ Sensors, vol. 21, no. 15, p. 5015,
Jul. 2021.
[79] Z. Guendil, Z. Lachiri, C. Maaoui, and A. Pruski, ‘‘Emotion recognition
from physiological signals using fusion of wavelet based features,’’ in
Proc. 7th Int. Conf. Model., Identificat. Control (ICMIC), Dec. 2015,
pp. 1–6.
[80] G. Chen, Y. Zhu, Z. Hong, and Z. Yang, ‘‘EmotionalGAN: Generating
ECG to enhance emotion state classification,’’ in Proc. Int. Conf. Artif.
Intell. Comput. Sci., Jul. 2019, pp. 309–313.
[81] T. Dissanayake, Y. Rajapaksha, R. Ragel, and I. Nawinne, ‘‘An ensemble
learning approach for electrocardiogram sensor based human emotion
recognition,’’ Sensors, vol. 19, no. 20, p. 4495, Oct. 2019.
[82] C. Zong and M. Chetouani, ‘‘Hilbert–Huang transform based physiolog-
ical signals analysis for emotion recognition,’’ in Proc. IEEE Int. Symp.
Signal Process. Inf. Technol. (ISSPIT), Dec. 2009, pp. 334–339.
[83] S. G. Mallat, ‘‘A theory for multiresolution signal decomposition: The
wavelet representation,’’ IEEE Trans. Pattern Anal. Mach. Intell., vol. 11,
no. 7, pp. 674–693, Jul. 1989.
[84] J. Bruna and S. Mallat, ‘‘Invariant scattering convolution networks,’’
IEEE Trans. Pattern Anal. Mach. Intell., vol. 35, no. 8, pp. 1872–1886,
Aug. 2013.
[85] A. Li, H. Li, and G. Yuan, ‘‘Continual learning with deep neural networks
in physiological signal data: A survey,’’ Healthcare, vol. 12, no. 2,
p. 155, Jan. 2024. [Online]. Available: https://www.mdpi.com/2227-
9032/12/2/155
[86] A. Bizzego, G. Gabrieli, and G. Esposito, ‘‘Deep neural networks
and transfer learning on a multivariate physiological signal dataset,’’
Bioengineering, vol. 8, no. 3, p. 35, Mar. 2021.
[87] S. Zou, X. Huang, X. Shen, and H. Liu, ‘‘Improving multimodal fusion
with main modal transformer for emotion recognition in conversation,’’
Knowl.-Based Syst., vol. 258, Dec. 2022, Art. no. 109978.
[88] J.-H. Choi and J.-S. Lee, ‘‘EmbraceNet: A robust deep learning archi-
tecture for multimodal classification,’’ Inf. Fusion, vol. 51, pp. 259–270,
Nov. 2019.
[89] M. Fujimori, Y. Shirai, M. Asai, K. Kubota, N. Katsumata, and
Y. Uchitomi, ‘‘Effect of communication skills training program for
oncologists based on patient preferences for communication when
receiving bad news: A randomized controlled trial,’’ J. Clin. Oncol.,
vol. 32, no. 20, pp. 2166–2172, Jul. 2014.
[90] S. Keeney, H. A. McKenna, and F. Hasson, The Delphi Technique in
Nursing and Health Research. Hoboken, NJ, USA: Wiley, 2011.
[91] J. A. Russell, ‘‘A circumplex model of affect,’’ J. Personality social
Psychol., vol. 39, no. 6, pp. 1161–1178, Dec. 1980.
[92] A. Defossez, G. Synnaeve, and Y. Adi, ‘‘Real time speech enhancement
in the waveform domain,’’ 2020, arXiv:2006.12847.
[93] C.
Rascon,
‘‘Characterization
of
deep
learning-based
speech-
enhancement techniques in online audio processing applications,’’
Sensors, vol. 23, no. 9, p. 4394, Apr. 2023.
[94] M. Vigier, B. Vigier, E. Andritsch, and A. R. Schwerdtfeger, ‘‘Cancer
classification using machine learning and HRV analysis: Preliminary
evidence from a pilot study,’’ Sci. Rep., vol. 11, no. 1, p. 22292, Nov. 2021.
[95] S. Poria, D. Hazarika, N. Majumder, G. Naik, E. Cambria, and R.
Mihalcea, ‘‘MELD: A multimodal multi-party dataset for emotion
recognition in conversations,’’ 2018, arXiv:1810.02508.
[96] D. Kim and P. Kang, ‘‘Cross-modal distillation with audio–text fusion
for fine-grained emotion classification using BERT and Wav2vec 2.0,’’
Neurocomputing, vol. 506, pp. 168–183, Sep. 2022.
VOLUME 13, 2025
99507
H. Kawamura et al.: Framework for ER Using Cross-Modal Transformers
[97] L. Pepino, P. Riera, and L. Ferrer, ‘‘Emotion recognition from speech
using Wav2vec 2.0 embeddings,’’ 2021, arXiv:2104.03502.
[98] K. Dabbabi and A. Mars, ‘‘Self-supervised learning for speech emotion
recognition task using audio-visual features and distil Hubert model on
BAVED and RAVDESS databases,’’ J. Syst. Sci. Syst. Eng., vol. 33, no. 5,
pp. 576–606, Oct. 2024.
[99] A. B. Matraf and A. Elnagar, ‘‘WESER: Wav2 Vec 2.0 enhanced speech
emotion recognizer,’’ in Proc. Doctoral Symp. Comput. Intell. Cham,
Switzerland: Springer, Jan. 2024, pp. 451–461.
[100] A. Mehrabian, Nonverbal Communication. Evanston, IL, USA: Rout-
ledge, 2017.
[101] F. Li, J. Luo, and W. Xia, ‘‘WavFusion: Towards wav2vec 2.0 multimodal
speech emotion recognition,’’ 2024, arXiv:2412.05558.
[102] A. A. Abdelhamid, E. M. El-Kenawy, B. Alotaibi, G. M. Amer,
M. Y. Abdelkader, A. Ibrahim, and M. M. Eid, ‘‘Robust speech emotion
recognition using CNN+LSTM based on stochastic fractal search
optimization algorithm,’’ IEEE Access, vol. 10, pp. 49265–49284, 2022.
[103] J. Loughrey and P. Cunningham, ‘‘Using early-stopping to avoid
overfitting in wrapper-based feature selection employing stochastic
search,’’ Dept. Comput. Sci., Trinity College Dublin, Tech. Rep., 2005.
[104] L. Van der Maaten and G. E. Hinton, ‘‘Visualizing data using t-SNE,’’ J.
Mach. Learn. Res., vol. 9, no. 86, pp. 2579–2605, Jan. 2008.
[105] H.-C. Li, T. Pan, M.-H. Lee, and H.-W. Chiu, ‘‘Make patient consul-
tation warmer: A clinical application for speech emotion recognition,’’
Appl. Sci., vol. 11, no. 11, p. 4782, May 2021. [Online]. Available:
https://www.mdpi.com/2076-3417/11/11/4782
[106] S. D. Hodges and R. Biswas-Diener, ‘‘Balancing the empathy expense
account: Strategies for regulating empathic response,’’ Empathy Mental
Illness, pp. 389–407, Mar. 2007.
[107] C. R. Figley, ‘‘Compassion fatigue: Psychotherapists’ chronic lack of self
care,’’ J. Clin. Psychol., vol. 58, no. 11, pp. 1433–1441, Nov. 2002.
[108] B. M. Sabo, ‘‘Compassion fatigue and nursing work: Can we accurately
capture the consequences of caring work?’’ Int. J. Nursing Pract., vol. 12,
no. 3, pp. 136–142, Jun. 2006.
[109] S. Siriwardhana, T. Kaluarachchi, M. Billinghurst, and S. Nanayakkara,
‘‘Multimodal emotion recognition with transformer-based self supervised
feature fusion,’’ IEEE Access, vol. 8, pp. 176274–176285, 2020.
[110] S. Poria, E. Cambria, D. Hazarika, N. Mazumder, A. Zadeh, and
L.-P. Morency, ‘‘Multi-level multiple attentions for contextual multi-
modal sentiment analysis,’’ in Proc. IEEE Int. Conf. Data Mining
(ICDM), Nov. 2017, pp. 1033–1038.
[111] A. Zadeh, P. P. Liang, N. Mazumder, S. Poria, E. Cambria, and
L. Morency, ‘‘Memory fusion network for multi-view sequential learn-
ing,’’ in Proc. AAAI Conf. Artif. Intell., Apr. 2018, vol. 32, no. 1.
[112] N. Majumder, D. Hazarika, A. Gelbukh, E. Cambria, and S. Poria,
‘‘Multimodal sentiment analysis using hierarchical fusion with context
modeling,’’ Knowl.-Based Syst., vol. 161, pp. 124–133, Dec. 2018.
[113] H. Kawamura, Z. Wang, K. Harima, T. Yamanishi, T. Miura, Y.
Maeda, Y. Okada, and K. Zempo, ‘‘PSCOUTER: Time-series emotion
classification using contactless measured multimodal biosignals in
medical diagnosis,’’ in Proc. Companion ACM Int. Joint Conf. Pervasive
Ubiquitous Comput., Oct. 2024, pp. 46–50.
[114] M. M. Bradley and P. J. Lang, ‘‘Measuring emotion: The self-assessment
manikin and the semantic differential,’’ J. Behav. Therapy Experim.
Psychiatry, vol. 25, no. 1, pp. 49–59, Mar. 1994.
HOMURA
KAWAMURA
received the B.E.
degree from the University of Tsukuba, in 2023.
He is currently enrolled in the Graduate School of
Systems and Information Engineering, University
of Tsukuba. His research interests include data
science and human–computer interaction.
TOMOFUMI MIURA received the M.D. degree
from the School of Medicine, Niigata Univer-
sity, in 2004, and the Ph.D. degree from the
Graduate School of Medicine, Chiba University,
in 2017. He was with Nagaoka Red Cross Hospital,
from 2004 to 2011. Since 2011, he has been work-
ing with the Department of Palliative Medicine,
National Cancer Center Hospital East, where he is
currently the Chief of the Department of Palliative
Medicine. His research interests include palliative
medicine, clinical trials, and the medical applications of technology.
YUKA MAEDA (Member, IEEE) received the
Ph.D. degree from Chiba University, Japan,
in 2012. She was a Postdoctoral Fellow with
Osaka Electro-Communication University and the
Spaulding Rehabilitation Hospital, in 2012. She is
currently an Assistant Professor with the Institute
of Systems and Information Engineering, Univer-
sity of Tsukuba. Her research interests include
biomedical instrumentation, wearable devices, and
unobtrusive measurement techniques.
YUKIHIKO OKADA received the Ph.D. degree
in commerce and management from Hitotsubashi
University, in 2006. Since 2006, he has been
with the University of Tsukuba, where he is
currently an Associate Professor. Since 2010,
he has been a Visiting Associate Professor with
the Institute of Statistical Mathematics. Since
2017, he has also been a Chief Scientist with
the Department of Service Engineering, Center
for Artificial Intelligence Research, University of
Tsukuba. In 2010, he was awarded Japan Accounting Association Award by
Japan Accounting Association for his research of Service Target Costing.
In 2021, he was awarded the Engineering Education Award by Japanese
Society for Engineering Education for his achievement in establishing and
managing the ‘‘Master’s Program in Service Engineering.’’
KEIICHI ZEMPO (Member, IEEE) received the
B.Sc. degree in physics and the M.B.A. degree
and the Ph.D. degree in engineering from the
University of Tsukuba, in 2013. Following a
postdoctoral fellowship with the National Institute
of Advanced Industrial Science and Technology,
he joined the Institute of Systems and Information
Engineering, University of Tsukuba, in 2014,
and became an Associate Professor, in 2023.
He also serves as Head Investigator under the JSPS
Transformative Research Areas (B), since 2024, a PRESTO Researcher
with JST, since 2022, and CEO of Xtrans Tech, Inc., since 2018. His
research interests include smart sensing, human–machine interfaces (human
augmentation, 3D audio, XR), service measurement, and telepresence,
under the overarching theme of ‘‘eXtending Umwelt and Self: Harmonizing
Chimera in Virtual Service Realms Beyond Physics.’’
99508
VOLUME 13, 2025
