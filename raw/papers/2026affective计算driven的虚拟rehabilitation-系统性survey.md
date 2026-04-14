Vol.:(0123456789)
Journal of King Saud University Computer and Information Sciences (2026) 38:71 
https://doi.org/10.1007/s44443-025-00442-3
REVIEW PAPER
Affective computing–driven virtual rehabilitation: a systematic survey
Liang Zhao1,2 · Dan Liu3   · Hanli Zhang1,2 · Guanci Yang3 · Donghua Zheng4 · Jing Yan4 · Ling He3
Received: 13 August 2025 / Accepted: 21 December 2025 / Published online: 29 January 2026 
© The Author(s) 2026
Abstract
This systematic survey comprehensively examines the integration of multimodal affective computing (MAC) with virtual 
rehabilitation (VRe) and proposes an Affective-driven Virtual Rehabilitation (AdVRe) framework. AdVRe dynamically 
adapts rehabilitation content by real-time monitoring of patients' emotional states via physiological, behavioral, and interac-
tion signals. The review addresses key research questions, including emotion model selection, signal acquisition methods, 
multimodal fusion algorithms, applications, and datasets. Technical foundations emphasize MAC's superiority over unimodal 
approaches in accuracy and robustness, enabling closed-loop 'emotion-in-the-loop' adjustments to optimize engagement and 
outcomes. Applications span limb motor training, PTSD/anxiety therapy, ASD social cognition, and chronic pain manage-
ment across non-, semi-, and immersive VR platforms. Challenges include (i) emotion recognition instability under clinical 
variability, (ii) scarce rehabilitation-specific datasets, (iii) computational constraints for real-time processing, and (iv) data 
privacy concerns. Opportunities lie in contactless sensing, edge computing, federated learning, and personalized emotional 
modeling. The study concludes that MAC-enhanced VRe significantly improves rehabilitation personalization and efficacy, 
though interdisciplinary efforts are needed to advance clinical translation by optimizing algorithms, making sensors acces-
sible, and establishing standardized ethical frameworks.
Keywords  Affective computing · Virtual rehabilitation · Affective-driven Virtual Rehabilitation · Multimodal fusion
1  Introduction
Virtual Rehabilitation (VRe) is a rehabilitation training 
methodology grounded in Virtual Reality (VR) technology. 
It was designed to optimize patients' physical function, alle-
viate disabilities, and enhance their interaction with the envi-
ronment through virtual settings. Furthermore, the gamified 
design of VRe effectively boosts patient engagement and 
motivation, thereby optimizing rehabilitation outcomes. 
Quan et al.(Quan et al. 2024) investigated the application 
of virtual reality in cognitive rehabilitation for patients with 
neurological disorders, demonstrating its efficacy in improv-
ing memory, attention, and motor functions. Additionally, 
Lukacs et al.(Lukacs et al. 2022) conducted a narrative 
review and critical reflection on virtual reality in physical 
rehabilitation, outlining its implementation benefits and 
challenges. Collectively, these studies demonstrate the broad 
applicability of virtual rehabilitation applications. Never-
theless, the therapeutic “dose” that VRe ultimately delivers 
is strongly mediated by patients’ moment‑to‑moment affect 
(e.g., engagement, frustration, anxiety), which can acceler-
ate or derail training even when task mechanics are well 
designed.
Emotion is lauded as the hidden language of social life, 
representing a comprehensive response to input signals such 
as experiences, external interactions, and personal thoughts 
(Lange et al. 2021). Mastery of emotional states is not 
only crucial for individual mental and physical well‑being 
but also holds strategic significance across fields such as 
human‑computer interaction (HCI), medical rehabilitation, 
and education. Since the mid‑twentieth century, with the 
 *	 Dan Liu 
	
dliu@gzu.edu.cn
1	
School of Mechanical Engineering, Guizhou University, 
Huaxi District, Guiyang City 550025, Guizhou Province, 
China
2	
North Alabama International College of Engineering 
and Technology, Guizhou University, Huaxi District, 
Guiyang City 550025, Guizhou Province, China
3	
Key Laboratory of Advanced Manufacturing Technology, 
Ministry of Education, Guizhou University, Huaxi District, 
Guiyang City 550025, Guizhou, China
4	
Guizhou Provincial Staff Hospital, Huaxi District, 
Guiyang City 550025, Guizhou Province, China
	
Journal of King Saud University Computer and Information Sciences (2026) 38:71
71 
Page 2 of 25
emergence of artificial intelligence (AI), affective comput-
ing (AC) has become a vital subfield and has rapidly evolved 
into an interdisciplinary research area encompassing com-
puter science, brain and psychological sciences, and social 
sciences (Bota et al. 2019). Its core objective is to develop 
computational systems capable of perceiving, recogniz-
ing, understanding, and intelligently responding to human 
emotions (Alharbi and Huang 2020), thereby establishing 
the technical foundation for natural and anthropomorphic 
human‑computer interaction. Recently, AC technology has 
transitioned from unimodal affective computing (UAC) to 
multimodal affective computing (MAC). Breakthroughs in 
convolutional neural networks (CNNs), machine learning 
(ML), and sensor technologies have enabled high‑precision 
emotion recognition, as summarized by recent reviews. For 
example, Pei et al. (Pei et al. 2024a) conducted a quantita-
tive analysis of 33,448 articles published in the period from 
1997 to 2023, identifying key research hotspots and future 
trends. Similarly, Wang et al. (Wang et al. 2022) provided a 
systematic review of emotional models, databases, and the 
latest advancements in the field, emphasizing the importance 
of multimodal approaches in emotion recognition.
Advances in wearable sensors, non-contact sensing, and 
embodied intelligence are accelerating the shift toward intel-
ligent, dynamic medical rehabilitation ((Antoniou et al. 
2020; Imran et al. 2024)). Emotion, as a direct reflection 
of physical condition, provides critical evidence for per-
sonalized treatment in medical rehabilitation. By analyzing 
patients' emotional fluctuations, therapists can dynamically 
adjust rehabilitation plans to enhance efficacy. However, the 
limited availability of medical personnel makes it challeng-
ing to provide comprehensive care to each patient. Through 
AC, we can assess patients' states during rehabilitation train-
ing and make timely adjustments (Maj et al. 2024). Within 
this landscape, VRe driven by AC has emerged as a prom-
ising new field where emotions and medical rehabilitation 
are deeply integrated. However, translating general AC 
into VR‑based rehabilitation introduces domain constraints 
that make multimodality essential: head‑mounted displays 
partially occlude the face and microphone placement var-
ies; physical exertion, pain, and motion artifacts confound 
physiological arousal; and patient heterogeneity demands 
robust, personalized inference. In this condition, MAC is not 
merely a performance upgrade over UAC but a prerequisite 
for reliable emotion inference that VRe can safely act upon 
in real time.
Literature review indicates that substantial theoretical 
research has been conducted on virtual rehabilitation and 
affective computing technologies, with a growing number 
of scholars exploring applications of affective computing 
in virtual rehabilitation—including high-quality, influential 
studies. However, this innovative interdisciplinary field lacks 
systematic reviews, impeding researchers' ability to rapidly 
comprehend its holistic progress. Furthermore, existing 
reviews on multimodal affective computing predominantly 
focus on technical summaries (e.g., sensors, data types, or 
algorithms)(((Bota et al. 2019; Wang et al. 2022; Khare et al. 
2024))) and a few studies analyze applicability for domain-
specific applications(Pepa et al. 2021). To advance both 
theoretical investigation and practical implementation of AC 
in rehabilitation, this paper proposes an affective computing-
driven virtual rehabilitation (AdVRe) framework. Centering 
on core technologies bridging affective computing and vir-
tual rehabilitation, it aims to address the following research 
questions methodically:
RQ1: How can the innovative model of AdVRe be defined 
from conceptual and technical perspectives?
RQ2: For patients recovering from a specific ailment, 
which emotional model should be chosen?
RQ3: What methods are used to collect data for AC, and 
how should they be selected for VRe scenarios?
RQ4: What multimodal fusion algorithms can be 
employed to recognize the emotions of rehabilitation 
patients?
RQ5: For which demand scenarios is AdVRe effective?
RQ6: What publicly available multimodal datasets are 
suitable for training the emotion recognition model?
RQ7: What challenges and opportunities will the AdVRe 
face?
As shown in Fig. 1, in Sect. 2, to contextualize the need 
for affect-aware adaptation, we first outline canonical VRe 
task forms and the adaptation gaps they face. Then, we pro-
vide a detailed introduction to the theory of affective com-
puting-driven virtual rehabilitation and the methodology of 
our research. Section 3 reviews the technical foundations 
of multimodal AdVRe. Section 4 summarizes the scenarios 
in which affective computing and virtual rehabilitation are 
effectively combined. Section 5 discusses relevant datasets, 
the challenges, and opportunities.
2  Survey Methodology
VRe encompasses task families whose therapeutic aims 
differ across domains. In motor rehabilitation, restorative 
tasks seek to regain lost function through high‑repetition, 
task‑oriented practice, whereas compensatory tasks culti-
vate alternative strategies and environmental aids to off-
set persistent impairments (e.g., cueing, assistive devices) 
((Shih et al. 2024; Feitosa et al. 2022)). In mental health, 
virtual reality exposure therapy (VRET) systematically 
presents fear‑relevant stimuli within controlled virtual 
scenarios to promote habituation and cognitive change 
(Carl et al. 2019). Despite demonstrated benefits, many 
VRe implementations still follow predefined progressions 
and rely on intermittent self‑reports, making them slow to 
Journal of King Saud University Computer and Information Sciences (2026) 38:71	
Page 3 of 25 
71
respond to moment‑to‑moment fluctuations in engagement, 
fatigue, or anxiety that strongly modulate dose delivery and 
adherence—sessions may oscillate between boredom and 
overload.
Against this backdrop, drawing from a synthesis of exist-
ing literature, we formally propose the concept of "Affec-
tive Computing-driven Virtual Rehabilitation" (AdVRe) and 
define it as:
"An innovative rehabilitation modality that integrates 
affective computing techniques with virtual reality/
augmented reality (VR/AR) rehabilitation platforms."
The core of AdVRe lies in the real-time perception, 
identification, and understanding of the dynamic emotional 
states reflected by multimodal signals during patients' reha-
bilitation training. Based on this affective feedback, AdVRe 
dynamically adjusts the content, difficulty, and interaction 
methods of the virtual rehabilitation environment or pro-
vides personalized emotional support and guidance, thereby 
optimizing the rehabilitation process, enhancing patient 
engagement and compliance, and ultimately improving treat-
ment outcomes. AdVRe aims to identify, understand, and 
respond to patients' emotional states during rehabilitation 
through technological means to optimize intervention strate-
gies. From a technical perspective, the essence of AC is the 
real-time monitoring and feedback of patients' emotions, At 
the same time, VR technology effectively enhances patient 
motivation, improves motor and cognitive functions, and 
supports emotional well-being by creating highly interac-
tive, immersive, and gamified environments. The integration 
of these two aims to personalize treatment plans, ultimately 
enhancing efficacy, compliance, and rehabilitation experi-
ence. The key feature of this modality is its construction of a 
highly dynamic and responsive closed-loop system, encom-
passing four stages: initial rehabilitation plan, signal acquisi-
tion, affective computing, and adaptive dynamic response, 
forming an ‘emotion-in-the-loop’ adaptive mechanism (as 
shown in Fig. 2). This mechanism enables the rehabilitation 
process to more closely align with the real-time needs and 
psychological states of individual patients, truly realizing 
patient-centered intelligent rehabilitation intervention.
*The process begins with the (1) Initial Rehabilitation 
Plan & Emotional Induction, where a default therapy proto-
col is set within a VR environment designed to elicit specific 
emotional responses. During training, (2) Multimodal Sig-
nal Acquisition occurs, capturing physiological, behavioral 
(e.g., facial, vocal, kinematic), and interaction data. These 
signals are processed in the (3) Affective Computing Engine, 
where features are extracted, fused, and classified to recog-
nize the patient's real-time emotional state. Finally, this emo-
tional insight drives the (4) Adaptive Dynamic Response, 
where the system automatically adjusts the VR rehabilitation 
Fig. 1   Article structure and 
methods‑to‑sections mapping
	
Journal of King Saud University Computer and Information Sciences (2026) 38:71
71 
Page 4 of 25
content to optimize engagement and efficacy. This creates a 
continuous ‘emotion-in-the-loop’ feedback cycle, personal-
izing the therapy in real-time.
This systematic review employed the Preferred Report-
ing Items for Systematic Reviews and Meta-Analyses 
(PRISMA) guidelines to align with the objectives of evalu-
ating virtual rehabilitation systems grounded in multimodal 
affective computing (Marzal et al. 2020). The methodol-
ogy encompassed four sequential phases—identification, 
screening, eligibility assessment, and inclusion—and was 
executed between January 2015 and June 2025 to capture 
advancements in multimodal fusion, emotion recognition, 
and rehabilitation applications. The details are shown in 
Supplementary Material.
3  Technical Pillars of AdVRe
3.1  Emotional Models for Rehabilitation
Since the 1960 s, various emotional models have been pro-
posed in psychological literature, with discrete emotion 
theory and dimensional emotion theory being the two dom-
inant frameworks. In affective computing, the selection of 
an emotional model directly affects the system's capacity 
to represent emotional states and its clinical applicability, 
necessitating a trade-off between discrete and dimensional 
representations.
a)	 Discrete Emotion Models: Rooted in Darwinian evo-
lutionary perspectives, discrete emotion models con-
ceptualize emotions as biologically adaptive entities. In 
1890, William James proposed four fundamental emo-
tions based on somatic involvement: fear, grief, love, 
and rage. Shaver et al. (Shaver et al. 1987) introduced a 
tree-structured emotion list, identifying six basic emo-
tions—love, joy, surprise, fear, sadness, and anger—
and complex emotions derived from these foundational 
states. As shown in Fig. 3(a), Ekman's cross-cultural 
research identified six basic emotions (happiness, sad-
ness, anger, disgust, surprise, and fear) (Ekman 1992). It 
aligns more closely with everyday human cognition and 
expression, and remains widely utilized in contemporary 
affective research.
Fig. 2   The affective-driven closed-loop adaptation mechanism in AdVRe
Journal of King Saud University Computer and Information Sciences (2026) 38:71	
Page 5 of 25 
71
b)	 Dimensional Emotion Models: Dimensional emotion 
models effectively address the limitations of discrete 
frameworks by acknowledging the complexity of emo-
tions through continuous spatial positioning of dynamic 
characteristics. The most prominent example is Russell 
James' Circumplex Model of Affect (CMA) (Russell 
1980). As shown in Fig. 3(b), emotions are represented 
along two dimensions: valence (from positive to nega-
tive) and arousal (from low to high). Dimensional mod-
els excel in monitoring emotional valence and intensity 
without being restricted to specific emotion categories.
*(a) Discrete Emotion Model: Categorizes emotions into 
a set of fundamental, universal classes. This model is intui-
tive and aligns well with explicit emotion labels, making it 
suitable for scenarios requiring clear emotional categoriza-
tion. (b) Dimensional Emotion Model: Represents emotions 
in a continuous space defined by core dimensions, typically 
Valence and Arousal. This model is better suited for captur-
ing subtle, mixed, or dynamically changing emotional states, 
which is often the case in rehabilitation settings.
The emotional model serves as the perceptual foundation 
of the "emotion–intervention closed loop," determining how 
multimodal signals are translated into executable regulatory 
commands, thereby influencing the effectiveness of rehabili-
tation dose control, intensity matching, and emotional sup-
port. Discrete models represent emotions using basic emo-
tional categories, offering advantages in intuitiveness and 
high interpretability; whereas dimensional models charac-
terize emotions within a continuous valence–arousal space, 
making them more suitable for capturing gradual or mixed 
emotional states. Therefore, the selection of an emotional 
model must primarily consider the specific goals of the 
rehabilitation training: when the goal involves event trigger-
ing, safety threshold monitoring, or adherence maintenance 
(e.g., immediately adjusting tasks upon detecting significant 
negative emotions such as "frustration" or "fear"), discrete 
models are preferred due to their ability to provide clear 
emotional classifications and triggering rules; when the goal 
involves continuous dose adjustment or state tracking (e.g., 
dynamically monitoring pain intensity), dimensional models 
are chosen for their sensitivity to changes in emotional inten-
sity; if the goal encompasses both aspects, a hybrid approach 
tends to be adopted, utilizing discrete labels to identify key 
emotional events while leveraging dimensional indicators 
for dynamic fine-tuning at the intensity level.
Table 1 summarizes existing research on emotional model 
selections for different pathologies. Among these, studies 
on stroke and limb motor rehabilitation have employed both 
discrete emotion models and hybrid models (((Izountar et al. 
2022; Rivas et al. 2019; Wen Yean et al. 2020))), whereas 
gait rehabilitation and pain–anxiety management often 
rely on the valence–arousal dimension to achieve continu-
ous emotion tracking ((Prabhu et al. 2019; Rodriguez et al. 
2022)). In psychological management, to maintain patients 
within the "therapeutic window of arousal," the system 
adaptively adjusts the intensity of virtual stimuli based on 
real-time physiological arousal levels, reflecting a typical 
dimensional control logic.
On the other hand, pathological characteristics also sig-
nificantly influence model selection. For instance, facial 
paralysis, dysarthria, or motor spasms may alter the channels 
and identifiable features of emotional expression, necessi-
tating the co-personalization of models and sensing strat-
egies to enhance system robustness. Device and scenario 
constraints (such as facial occlusion and motion artifacts 
Fig. 3   Dominant emotion models used in AC
	
Journal of King Saud University Computer and Information Sciences (2026) 38:71
71 
Page 6 of 25
caused by head-mounted displays) further necessitate the 
adoption of more adaptive multimodal representation strate-
gies under well-defined objectives.
3.2  Signal Acquisition and Modalities
3.2.1  Single‑Modal and Multimodal Signals
In clinical rehabilitation, AC provides critical support 
for personalized treatment by perceiving and understand-
ing patients' emotional states. The selection and fusion of 
signals are central to achieving precise emotion recogni-
tion, encompassing both single-modal and multimodal 
approaches. Single-modal signals refer to emotional infor-
mation captured through a single data source, commonly 
including facial expressions, speech, physiological signals 
(e.g., EEG, ECG, EDA), and action patterns. However, 
single-modal signals exhibit significant limitations, such as 
(i) Facial expressions may be distorted due to cultural dif-
ferences or intentional concealment, (ii) speech analysis is 
susceptible to environmental noise, (iii) physiological signal 
interpretation requires complex algorithms, and (iv) action 
data may be challenging to standardize due to individual 
variability. These factors result in insufficient accuracy and 
robustness of single-modal methods in complex emotion rec-
ognition, making them inadequate for the dynamic monitor-
ing demands of virtual rehabilitation.
To overcome the limitations of single-modal signals, mul-
timodal fusion significantly enhances emotion recognition 
performance by integrating multiple signal sources. Mul-
timodal methods reduce the impact of noise or bias across 
individual modalities by cross-validating information from 
different sources, thereby providing a more comprehensive 
emotional profile. Prabhu et al.(Prabhu et al. 2019) dem-
onstrated the effectiveness of this approach by monitoring 
heart rate variability and electrodermal activity to adaptively 
adjust virtual reality experiences, successfully reducing 
preoperative anxiety and postoperative pain levels. Salas-
Cáceres et al. (Salas-Cáceres et al. 2024) designed single-
modal and multimodal fusion emotion recognition strategies 
by collecting visual and auditory information from users, 
with results confirming the hypothesis that multimodal 
methods outperform single-modal approaches in perfor-
mance. These studies highlight that multimodal fusion not 
only improves the accuracy of emotion recognition but also 
enhances system robustness, making it more suitable for the 
complex scenarios of VRe.
3.2.2  Multimodal Signal Processing in VRe
In the field of VRe, patients engage in rehabilitation training 
through interactions with virtual reality devices. The selec-
tion of signals is the critical starting point for building an 
effective affective computing system, directly influencing 
the precision of emotion recognition, the personalization of 
treatment, and the effectiveness of rehabilitation. To ensure 
that AC technologies seamlessly integrate into clinical prac-
tice and genuinely benefit patients, signal selection must 
carefully consider multiple practical constraints: (i) clinical 
feasibility requires devices to be easy to deploy, operate, 
and maintain, avoiding interference with routine treatment 
processes; (ii) non-invasiveness is crucial for patient com-
fort and adherence, especially in long-term rehabilitation; 
(iii) compatibility with VRe devices determines whether 
data acquisition can be conducted efficiently and naturally, 
avoiding additional burdens or disruptions to the training 
experience. Therefore, identifying and integrating signal 
sources that meet these core requirements while accurately 
reflecting patients' emotional states is the primary challenge 
in advancing the clinical translation of affective computing 
in virtual rehabilitation.
Table 1   Application of emotion models in different research scenarios
Ref
Year
Clinical application
Emotion categories
Emotion model
 Izountar et al. 2022)
2021
Upper or lower limb motor 
rehabilitation
Neutral, angry, disgusted, fear, happy, sadness, sur-
prised
Discrete model
 Rivas et al. 2019)
2019
Stroke rehabilitation
Fatigue, anxiety, engagement
Mixed model
 Prabhu et al. 2019)
2019
Managing Pain and Anxiety Valence and Arousal
Dimensional model
 Rodriguez et al. 2022) 2022
Gait rehabilitation
Valence and Arousal
Dimensional model
 Aranha et al. 2023)
(Aranha et al. 2017)
2017&2022 Rehabilitation of exercise
Neutral, angry, disgusted, fear, happy, sadness, sur-
prised
Discrete model
 Lima et al. 2024)
2024
Mental Health monitoring
Valence and Arousal
Dimensional model
 Heyse et al. 2020)
2020
Stress relief
Stress, fear& arousal
Mixed model
 Smith et al. 2021)
2021
Alzheimer’s disease
Valence and Arousal
Dimensional model
 Wen Yean et al. 2020) 2020
Stroke rehabilitation
Angry, disgusted, fear, happy, sad, surprised
Discrete model
 Guo et al. 2021)
2021
ASD children
Angry, disgusted, afraid, happy, sad, surprised
Discrete model
Journal of King Saud University Computer and Information Sciences (2026) 38:71	
Page 7 of 25 
71
a)	 Physiological Signals: EEG, ECG, and EDA are the 
primary signals collected in VRe, monitored in real-time 
through wearable devices. EEG captures brain activity, 
reflecting the neural basis of emotions; ECG and EDA 
provide heart rate variability and skin conductance level 
data, indicating arousal and stress levels. Herumurti 
et al. (Herumurti et al. 2019) adjusted virtual audience 
behavior based on real-time ECG data to help individu-
als overcome public speaking anxiety, demonstrating the 
potential of ECG in psychological rehabilitation. The 
non-invasive nature of these signals makes them suitable 
for long-term monitoring, particularly in motor rehabili-
tation, pain management, and psychological rehabilita-
tion.
b)	 Behavioral Signals: Facial expressions, speech, and 
action patterns are critical behavioral signals. Modern 
VR headsets (e.g., Meta Quest Pro) are equipped with 
facial expression recognition sensors, enabling partial 
capture of facial data even when worn (Zhang et al. 
2023a). Speech is collected through built-in micro-
phones on VR devices, suitable for analyzing emotional 
tone. Action patterns, such as hand movements and pos-
tures, are recorded using VR controllers, motion track-
ing systems, or force sensors. Rivas et al. (Rivas et al. 
2015) classified states like fatigue, tension, pain, and 
satisfaction using 3D hand movements and finger pres-
sure data. Chua et al. (Chua et al. 2024) detected emo-
tions and cognitive load through hand-head movement 
data, achieving a classification accuracy of up to 91%, 
indicating that movement data can serve as an indirect 
indicator of emotional states.
c)	 Human–Computer Interaction Data: Interaction 
data, such as task performance, reaction time, and error 
rates during patient-device interactions, can also serve 
as indirect indicators of emotional states. For example, 
Hibbeln et al. (Hibbeln et al. 2017) investigated how 
human–computer interaction input devices could infer 
emotions, finding that mouse cursor distance and speed 
could indicate the presence of negative emotions, with 
an overall accuracy of 81.7%. These data are automati-
cally recorded by interaction systems and combined with 
physiological and behavioral signals to further enrich 
emotional analysis.
d)	 User Self-Assessment Scales: User self-assessment 
scales, using structured questionnaires or graphical 
tools, allow patients to report their emotional states, 
typically including valence, arousal, or specific emo-
tions (e.g., happiness, anxiety). As a non-invasive and 
easily implementable tool, they capture patients' sub-
jective emotional experiences, providing critical data 
for researchers and clinicians. Romero-Ramos et al. 
(Romero-Ramos et al. 2024) classified the valence of 
emotions through head and hand movement data while 
incorporating an improved self-assessment model to col-
lect multimodal behavioral data from 30 students. The 
results showed an accuracy of up to 71% in distinguish-
ing positive and negative emotional states.
Multimodal fusion in VRe is exemplified by combina-
tions such as EEG with facial expressions, EEG with eye-
tracking, physiological signals with action data, or action 
patterns with assessment scales. For instance, Rivas et al. 
(Rivas et al. 2021) developed a multi-label classification 
model by integrating finger pressure, hand movements, and 
facial expressions, significantly improving emotion recogni-
tion accuracy. Amini Gougeh and Falk (Amini Gougeh and 
Falk 2022) highlighted the application of electroencepha-
lography (EEG), electromyography (EMG), and inertial 
measurement units (IMUs) in immersive virtual rehabilita-
tion, emphasizing the role of physiological computing in 
providing real-time feedback and enhancing patient engage-
ment. The choice of emotional model and signal modality 
in AdVRe is often influenced by VRe task characteristics: 
compensatory training may prioritize monitoring frustration 
and engagement through behavioral cues, while restorative 
training may benefit from continuous arousal monitoring 
via physiological signals. Similarly, exposure therapy relies 
heavily on real-time arousal feedback to adjust stimulus 
intensity.
3.3  Multimodal Fusion Algorithms 
and Classification
Multimodal emotion recognition algorithms are fundamental 
technologies in the field of affective computing. These algo-
rithms identify human emotional states by integrating data 
from various sources. In virtual rehabilitation, they facili-
tate personalized treatment planning by monitoring patients' 
emotions, ultimately improving rehabilitation outcomes.
Table 2 summarizes the multimodal fusion strategies 
and emotion classifiers used in current affective comput-
ing research. As shown, there is significant diversity in the 
design of algorithm frameworks across studies. This vari-
ability primarily unfolds in two interconnected components: 
Multimodal Fusion Strategies and Emotion Classification 
Methods. Researchers have investigated fusion strategies at 
different levels, incorporating a variety of classifiers. These 
methodologies have been tested on multiple public multi-
modal emotion datasets. This chapter will systematically 
review and analyze these core algorithmic components.
3.3.1  Feature Extraction Strategies
Feature extraction is the primary and critical step in the 
MAC process, aiming to precisely extract information clues 
from raw heterogeneous data that effectively represent 
	
Journal of King Saud University Computer and Information Sciences (2026) 38:71
71 
Page 8 of 25
emotional states. Recently, DL techniques, with their pow-
erful feature learning capabilities, have gradually surpassed 
traditional manual feature engineering reliant on domain 
knowledge, becoming the mainstream paradigm. Through 
architectures such as CNNs, recurrent neural networks 
(RNNs/LSTMs), and Transformer-based models (e.g., 
BERT), they automatically capture complex, deep-seated 
emotional association patterns in data. Simultaneously, 
hybrid methods combining deep learning with the advan-
tages of traditional features of specific modalities have also 
shown significant potential. This section will detail the fea-
ture extraction of three major modalities—video/image, 
Table 2   An Overview of Representative Methods for Multimodal Sentiment Analysis
*T: Text, A: Audio, V: Video, B: Physiological/Biological Signals
Ref
Year
Modality
Fusion Strategy
Classifier
Dataset
 Mamieva et al. 2023)
2023 A + V
Feature-level (Attention-based 
feature fusion)
SoftMax
IEMOCAP
CMU-MOSEI
Zadeh et al. 2018)
2018 T + V + A Model-based
Graph Memory Fusion 
Network, Graph-MFN 
(Improved LSTM)
CMU-MOSEI
 Liu et al. 2021b)
2021 A + V
Hybrid-level (Feature-
level + Model-based)
LIBSVM
MOSI, MELD
 Islam et al. 2024)
2024 V + B
Model-based fusion (Soft 
attention mechanism)
Softmax
Bio Vid Emo DB
 Xie et al. 2023)
2023 T + A + V Model-level
Multitask Learning + Bi-
Attention Mech
CMU-MOSI
CMU-MOSEI
Zadeh et al. 2017)
2017 A + V + T Model-level (Tensor Fusion 
Layer)
DNN (Sentiment Inference 
Subnetwork)
CMU-MOSI
 Yan et al. 2022)
2022 A + V + T Feature-level: MTFN-CMM
Sigmoid
CMU-MOSI
CMU-MOSEI
 Zhang et al. 2023b)
2023 A + V + T Hybrid-level (Feature-
level + Decision-level)
GRU + Softmax
MUSIARD
Tsai et al. 2019)
2019 A + V + T Model-level: Cross-modal 
attention blocks
Crossmodal Trans-
former + Self-attention 
Transformer + FC layers
CMU-MOSI
CMU-MOSEI
IEMOCAP
 Song et al. 2018)
A + V
Decision-level
Artificial Neural Network or 
k-Nearest Neighbor
eNTERFACE'05
Gkoumas et al. 2021)
2021 A + V + T Decision-level
Quantum cognitively moti-
vated fusion
CMU-MOSI
 Zhang et al. 2017)
2018 A, V
Model-level: DBN fusion
Linear SVM
RML
 Zheng et al. 2018)
2019 A + V + T Hybrid-level
SVM/Naive Bayes
DEAP
 Ma et al. 2019)
2019 A + V
Feature-level: deep belief 
network
CNN
RML, Enterface05, BAUM-1 s
Ref
Year Modality Fusion Strategy
Classifier
Dataset
 Middya et al. 2022)
2022 A + V
Model-level
Softmax
SAVEE, RAVDESS
 Razzaq et al. 2023)
2020 B
BiLSTM
UnSkEm
 Tan et al. 2020)
2020 V + B
Feature-level fusion, Decision-
level fusion
NeuCube (evolving SNN 
framework)
MAHNOB-HCI
 Zhong et al. 2017)
2017 V + B
Hybrid-level
AdaBoost (physio), SVM-
Gaussian (facial)
MAHNOB-HCI
 Huang et al. 2019)
2019 V + B
Decision-level
SVM
DEAP, MAHNOB-HCI
 Chen and Li 2020)
2020 A + T
Model-level (Stacking ensem-
ble)
Multifeature combined net-
work classifier
Million Song Dataset
 Pandeya et al. 2021)
2021 A + V
Decision-level
1D-CNN (raw audio), 
2D-CNN (spectrogram), 
C3D/I3D (video)
Custom dataset
 Noroozi et al. 2017)
2019 A + V
Decision-level (Stacking)
First-level: SVM/RF
Second-level: RF (stacking)
SAVEE, RML
eNTERFACE'05
 Al Roken and Barlas 2023) 2023 A + V
Decision-level
• Audio: 3-layer CNN
• Visual: VGG-16
Custom Arabic Natural Audio-
Visual Dataset
Journal of King Saud University Computer and Information Sciences (2026) 38:71	
Page 9 of 25 
71
audio, and physiological signals—in VRe scenarios, laying 
the foundation for subsequent fusion and classification.
a)	 Video/image: They contain numerous features that 
clearly reveal visual emotional cues of positive or nega-
tive emotions, including facial expressions and body 
movements. For facial expressions, traditional feature 
extraction methods include facial landmarks, local 
binary patterns (LBP), histogram of oriented gradients 
(HOG), and optical flow, which capture facial muscle 
movements and dynamic changes. However, these fea-
tures require domain experts' knowledge and may fail 
to fully capture the diversity of emotions in complex 
scenarios. The introduction of deep learning technol-
ogy has completely transformed this field. CNNs, par-
ticularly pre-trained models like VGGNet and ResNet, 
are widely used due to their exceptional performance 
in capturing complex visual patterns (Mamieva et al. 
2023). Additionally, CNN models incorporating atten-
tion mechanisms can better focus on emotionally rel-
evant regions in images, further improving the accuracy 
of feature extraction (Liu et al. 2021a). Hybrid meth-
ods also show promise by combining manual and deep 
learning features to leverage their respective strengths. 
For example, Tsalera et al. (Tsalera et al. 2022) fused 
geometric features of facial landmarks with appearance 
features extracted by CNNs, enhancing classification 
performance. Body movements are also critical carriers 
of emotional expression, with relevant features including 
velocity, acceleration, joint angles, quantity of motion 
(QoM), and silhouette motion images (SMI) (Liu 2024). 
These features can effectively capture emotional infor-
mation even at a distance or from non-frontal perspec-
tives, compensating for the limitations of facial expres-
sion analysis.
b)	 Audio: Audio features are primarily categorized into 
prosodic, phonatory, and spectral features (Zvarevashe 
and Olugbara 2020). Prosodic features include funda-
mental frequency, energy, and speech rate. Phonatory 
features such as formants and jitter analyze speech clar-
ity and fluctuation, suitable for distinguishing subtle 
emotions. Spectral features like mel-frequency ceps-
tral coefficients (MFCCs) and linear predictive coding 
(LPC) capture the spectral characteristics of speech, 
widely applied in speech emotion recognition. RNNs 
and their variants, such as long short-term memory net-
works (LSTMs), are highly regarded for their ability to 
process time-series data, capturing long-term depend-
encies in speech signals. CNNs are frequently used to 
process two-dimensional representations like mel-spec-
trograms, extracting high-level features. For instance, 
Issa et al. (2020) (Issa et al. 2020) employed two CNNs 
and an LSTM (CNN-LSTM) to learn local and global 
emotion-related features from speech and log-mel spec-
trograms, enhancing emotion recognition performance.
c)	 Physiological signals: Physiological features are 
extracted from bodily responses. EEG features include 
time-domain statistical features (e.g., mean, variance), 
frequency-domain band power (e.g., α, β waves), and 
time–frequency domain wavelet coefficients, suitable 
for capturing brain responses to emotions (Chen et al. 
2025). ECG features encompass heart rate and heart rate 
variability (HRV), reflecting autonomic nervous system 
changes induced by emotions (Sepúlveda et al. 2021). 
EDA features such as skin conductance level (SCL) and 
response (SCR) quantify arousal levels, ideal for detect-
ing intense emotions (Kumar et al. 2024). Other signals 
such as respiratory rate and surface electromyography 
(sEMG) are increasingly used alongside EEG and other 
biosignals to enhance emotion recognition systems.
In MACs, designing targeted feature extraction methods 
based on the characteristics of each modality effectively 
enhances the accuracy of emotion classification. For exam-
ple, Zadeh et al. (Zadeh et al. 2018) designed independ-
ent feature extraction networks for text, audio, and video 
modalities, emphasizing the importance of modality-specific 
feature extraction. Liu et al. (Liu et al. 2021b) established 
corresponding feature extraction methods for different sin-
gle modalities, where the speech modality adopted a CNN-
LSTM network to capture temporal features and emotional 
cues in speech signals; facial expressions in videos were 
extracted using the Inception-ResNet-v2 network, fully lev-
eraging the advantages of deep learning in image process-
ing. Additionally, Islam et al. (Islam et al. 2024) designed 
deep separable convolutional neural networks (DSCNNs) 
for facial videos and bidirectional long short-term memory 
(Bi-LSTM) networks for physiological signals to extract 
features, thereby improving the performance of multimodal 
emotion recognition. While the feature extraction tech-
niques described above are suitable for most applications 
of multimodal affective computing, their application in vir-
tual rehabilitation introduces unique challenges that require 
specialized considerations. For instance, facial paralysis or 
asymmetry may limit the reliability of facial action units; 
dysarthria can distort prosodic and spectral speech features; 
and spasticity or reduced range of motion can alter kinematic 
descriptors. These pathological manifestations may overlap 
with or mask genuine emotional expressions, leading to 
distributions of features that differ significantly from those 
of healthy individuals. Therefore, rehabilitation-specific 
feature engineering or model fine-tuning is often required. 
This may involve personalizing feature sets to account for 
individual motor capabilities, incorporating compensatory 
movement metrics, or employing domain adaptation tech-
niques to bridge the gap between general affective models 
	
Journal of King Saud University Computer and Information Sciences (2026) 38:71
71 
Page 10 of 25
and patient-specific expressions. Failure to address these 
nuances can compromise the validity of emotion recognition 
and, consequently, the adaptive logic of the AdVRe system.
3.3.2  Multimodal Fusion Strategies for AdVRe
Multimodal fusion strategies are a core component of emo-
tion recognition algorithm frameworks. They determine how 
to effectively integrate information from different perceptual 
channels (modalities). This integration aims to create a more 
comprehensive and accurate representation of emotional 
states. The choice of fusion strategy directly impacts the 
model's ability to utilize the complementarity and redun-
dancy within multimodal data. It helps overcome limitations 
inherent to single modalities, such as noise and incomplete 
information. Consequently, this choice significantly influ-
ences overall recognition performance. Based on the stage 
where information integration occurs, fusion strategies pri-
marily fall into three main paradigms: Feature-Level Fusion, 
Model-Level Fusion, and Decision-Level Fusion. Hybrid 
fusion, combining multiple paradigms, is also employed, as 
illustrated in Fig. 4.
a)	 Feature-Level Fusion
Feature-level fusion (also known as early fusion) inte-
grates information from different modalities during feature 
extraction. This process generates a joint feature vector, 
which is then fed into an emotion classifier (as shown in 
Fig. 4a). Traditional strategies include feature concatena-
tion, feature addition, and weighted summation. These 
methods are widely used due to their computational effi-
ciency. However, they often fail to fully leverage the poten-
tial of multimodal data, primarily because they cannot 
model complex inter-modal relationships. To overcome 
these limitations, researchers have developed advanced 
feature-level fusion techniques using deep learning. Atten-
tion mechanisms have emerged as a key research direction. 
Attention-weighted fusion dynamically assigns modality 
weights, enabling models to focus on features most rel-
evant to emotion classification. Zhou et al. (Zhou et al. 
2021) proposed a multimodal fusion attention network. It 
combines adaptive, multi-level factorized bilinear pool-
ing (FBP) with an attention-guided strategy (AG-FBP) for 
dynamic fusion-weight calculation. This approach achieved 
significant performance gains in audio-visual emotion rec-
ognition. Similarly, Mamieva et al. (Mamieva et al. 2023) 
developed an attention-based method. It uses independent 
encoders for facial and speech features, applies attention 
to compute feature weights, and generates a multimodal 
feature vector. This method achieved a weighted accuracy 
of 74.6% on IEMOCAP and 80.7% on CMU-MOSEI. To 
capture complex inter-modal interactions, Yan et al. (Yan 
et al. 2022) introduced a multi-tensor fusion network. It 
enhances relational representations of emotion by modeling 
cross-modal interactions. The network extracts modality 
features, models bi-modal and multimodal interactions via 
tensor operations, and produces a fused feature vector. This 
improved classification accuracy by approximately 3–5% on 
the CMU-MOSI and CMU-MOSEI datasets. Furthermore, 
their proposed non-concatenative multi-level cross-modal 
fusion demonstrates the potential of tensor methods for han-
dling modality heterogeneity.
Despite significant progress, feature-level fusion faces 
several challenges. First, concatenating high-dimensional 
feature vectors can cause overfitting, especially with 
limited training data. To mitigate this, researchers often 
employ dimensionality reduction techniques like Principal 
Component Analysis (PCA) or feature selection. Second, 
capturing long-term inter-modal relationships and address-
ing modality alignment remain challenging, particularly 
for time-series data such as audio and video. Khan et al. 
(Khan et al. 2025) innovatively proposed a Cross-Modal 
Transformer (CMT) which effectively analyzes local and 
global features of speech and its corresponding text. This 
suggests future development requires more intelligent and 
adaptive fusion methods for efficient emotion recognition 
across diverse scenarios.
Fig. 4   Feature fusion strategy
Journal of King Saud University Computer and Information Sciences (2026) 38:71	
Page 11 of 25 
71
b)	 Model-Level Fusion
Model-level fusion, also termed intermediate fusion, 
integrates information from different modalities within 
a model's architecture. This strategy typically occurs 
at intermediate layers to learn joint representations 
capturing inter-modal interactions. As shown in Fig. 4(b), 
model-level fusion enables features from different 
modalities to be fed into distinct model structures. This 
leverages the model's learning capacity to discover and 
exploit cross-modal relationships, thereby achieving 
higher accuracy and robustness in complex emotion 
recognition tasks. In recent years, numerous researchers 
have adopted model-level fusion to enhance multimodal 
emotion recognition performance. DBNs represent one 
such technique. Zhang et al. (Zhang et al. 2017) designed 
a multimodal deep fusion model aiming to bridge the 
affective gap. This model first generates audio-visual 
segment features using CNNs and 3D-CNNs, then fuses 
them within a DBN. Experimental results demonstrated 
the effectiveness of this approach on several public 
audio-visual emotion databases (RML, eNTERFACE05, 
BAUM-1 s), validating model-level fusion for emotion 
recognition. Zheng et al. (Zheng et al. 2018) proposed 
a multimodal emotion recognition framework called 
EmotionMeter. It used DBNs for model-level fusion, 
combining EEG and eye movement features to improve 
emotion recognition. To capture high-order inter-modal 
interactions, tensor fusion and attention mechanisms 
have also been applied to multimodal model-level 
fusion. Xie et al. (Xie et al. 2023) presented a method 
called MTL-BAM, based on multi-task learning and 
attention mechanisms. It fuses affective interactions 
across modalities at intermediate layers via cross-
modal attention, combined with a multi-task framework 
that shares underlying representations, leading to 
significant performance gains. Zadeh et al. (Zadeh et al. 
2017) introduced the Tensor Fusion Network (TFN). 
It explicitly models unimodal, bimodal, and trimodal 
interactions via a tensor fusion layer at an intermediate 
model level, significantly boosting performance for 
multimodal sentiment analysis. Tsai et al. (Tsai et al. 
2019) proposed the Multimodal Transformer (MulT). 
It dynamically fuses unaligned multimodal language 
sequences using cross-modal attention at intermediate 
layers, substantially improving performance in sentiment 
analysis and emotion recognition tasks. Researchers have 
also explored other innovative approaches. Zhang et al. 
(Zhang et al. 2023b) proposed an encoder-decoder-based 
multimodal multi-task learning model. It dynamically 
fuses text, audio, and visual modalities at intermediate 
layers using attention mechanisms to recognize sarcasm, 
sentiment, and emotion in conversations simultaneously.
c)	 Decision-Level Fusion
Decision-level fusion, also known as late fusion, inte-
grates the outputs of individual modality classifiers to pro-
duce the final emotion classification result. As shown in 
Fig. 4(c), its implementation typically involves extracting 
specific features, classifying emotions per modality, and then 
fusing the classification results to determine the final emo-
tion category. The key advantages of decision-level fusion 
are its modular design and robustness to missing modalities. 
Since each modality is processed independently, the system 
can flexibly choose the optimal model for each modality. It 
can also continue functioning even when data from some 
modalities is unavailable. For example, Song et al. (Song 
et al. 2018) proposed a decision-level fusion method that 
significantly improved emotion analysis performance on 
the IEMOCAP dataset by integrating emotional information 
from multiple modalities. Similarly, Gkoumas et al. (Gkou-
mas et al. 2021) introduced a quantum-inspired cognitive 
multimodal decision-level fusion strategy, which enhanced 
emotion recognition accuracy by combining modalities to 
resolve inter-modal ambiguities. In practical applications 
such as virtual rehabilitation, patients may be unable to pro-
vide facial expression data due to limitations in posture or 
equipment constraints. The system can still perform emotion 
recognition using audio or physiological signals.
Additionally, decision-level fusion is relatively simple 
to implement, debug, and maintain. It also offers higher 
interpretability, as the contribution of each modality to 
the final decision can be traced. However, a limitation of 
decision-level fusion is that its late integration may fail to 
capture complex inter-modal interactions fully. For instance, 
dynamic associations between vocal tone and facial expres-
sions might be lost during independent processing, poten-
tially leading to lower performance compared to feature-
level or model-level fusion methods. Future research 
directions include developing more advanced fusion mecha-
nisms. Examples include deep learning-based meta-classifi-
ers designed to integrate decision-level information across 
modalities better.
d)	 Hybrid Fusion
Hybrid fusion is a comprehensive strategy that combines 
multiple fusion techniques at different stages. For instance, 
Nemati et al. (Nemati et al. 2019) employed a linear map-
ping in the latent space to fuse audio and visual modalities 
at the feature level. They then integrated text modality fea-
tures at the decision level using an evidence fusion method 
based on Dempster-Shafer theory. Evaluation on the DEAP 
dataset showed that this approach outperformed single deci-
sion-level fusion and non-latent-space fusion methods. It 
effectively captured complementary information between 
	
Journal of King Saud University Computer and Information Sciences (2026) 38:71
71 
Page 12 of 25
modalities, particularly for multimodal data. Similarly, 
Cimtay et al. (Cimtay et al. 2020) proposed a hybrid fusion 
strategy combining feature-level and decision-level fusion 
for emotion recognition. They used facial expressions, GSR, 
and EEG. Features from multiple physiological signals were 
first fused at the feature level. Classification results from 
individual modalities were then integrated at the decision 
level. On their custom LUMED-2 dataset, they achieved a 
maximum single-subject accuracy of 81.2% and an average 
accuracy of 74.2% across three emotion categories: sadness, 
neutrality, and happiness. The method also achieved 91.5 
percent maximum single-subject accuracy on the DEAP 
dataset, demonstrating the effectiveness of hybrid fusion 
for multimodal emotion data.
The advantage of hybrid fusion lies in its ability to lever-
age the strengths of different fusion strategies. However, it 
faces several challenges. First, its high computational com-
plexity may limit use on resource-constrained virtual reha-
bilitation devices. Second, heterogeneity between modalities 
can affect fusion performance, necessitating more sophisti-
cated preprocessing techniques. Third, hybrid fusion typi-
cally requires large amounts of annotated data for model 
training, which can be scarce in specific domains like vir-
tual rehabilitation. To address these challenges, researchers 
have proposed improvements. Razzaq et al. (Razzaq et al. 
2023) introduced a hybrid multimodal emotion recogni-
tion framework accounting for inter-modal differences. It 
dynamically assigns modality weights using Generalized 
Mixture Functions to optimize the fusion process. Wang 
et al. (Wang et al. 2023) proposed a method called "mul-
timodal transformer-enhanced fusion," utilizing a hybrid 
strategy combining feature-level and model-level fusion. 
This enables fine-grained intra- and inter-modal information 
interaction. Future research could explore semi-supervised 
or unsupervised learning to reduce reliance on annotated 
data. Simultaneously, improved preprocessing techniques 
are needed to handle modal heterogeneity.
e)	 Analysis of Multimodal Fusion Strategies in AdVRe
Decision-level fusion excels in real-time performance 
and robustness to modality missingness, making it suit-
able for typical AdVRe scenarios like emotion recogni-
tion under HMD occlusion. Feature-level and model-level 
fusion offer higher accuracy when resources permit, ideal 
for scenarios requiring complex modality interactions. 
However, the selection of a fusion strategy in clinical 
settings is a trade-off governed by practical constraints. 
Feature-level fusion, while potentially offering high accu-
racy, demands stringent temporal alignment of modalities. 
Its susceptibility to noisy or missing data from any single 
modality can destabilize the entire system, limiting its 
reliability in real-world rehabilitation. Model-level fusion 
excels at learning complex cross-modal relationships and 
is highly suitable for mental health applications where 
nuanced emotional cues from voice, face, and physiology 
interact. However, its "black-box" nature reduces inter-
pretability, making it difficult for clinicians to trust and 
understand the system's decisions. Decision-level fusion 
offers the highest robustness to missing modalities and 
aligns well with modular clinical system design. Its sim-
plicity facilitates interpretability, as clinicians can see the 
contribution of each modality to the final decision.
In addition to the technical considerations previously 
outlined, adopting these multimodal fusion strategies 
in real-world clinical rehabilitation faces significant 
non-technical barriers that are equally critical to their 
practical implementation. A primary obstacle lies in the 
economic and infrastructural costs associated with each 
approach. Feature-level and model-level fusion typically 
demand higher computational resources and more sophis-
ticated, often expensive, sensor arrays to ensure high-
quality, synchronous data streams. This can render them 
prohibitively costly for standard clinics, whereas deci-
sion-level fusion, with its lower computational footprint 
and tolerance for simpler, more modular hardware, pre-
sents a more financially viable pathway for widespread 
deployment. Furthermore, therapist acceptance is a piv-
otal human factor. The "black-box" nature of advanced 
model-level fusion can create a barrier of mistrust, as 
clinicians are understandably reluctant to base critical 
therapeutic decisions on systems whose reasoning is not 
transparent. In contrast, the inherent interpretability of 
decision-level fusion, where the contribution of each 
modality is more discernible, aligns better with clinical 
workflows and fosters greater trust and agency among 
healthcare professionals.
In summary, no single fusion strategy is universally 
superior; their effectiveness in a given clinical applica-
tion depends on which performance aspects are prioritized, 
and the choice must be carefully calibrated. Mental health 
interventions often emphasize interpretable and trustwor-
thy decisions, which may favor feature-level or decision-
level fusion so that the model’s reasoning is transparent 
to clinicians. In contrast, motor rehabilitation training 
prioritizes sensing precision and timely feedback. Here, 
deeply fusing multiple data sources can offer more fine-
grained state recognition. For remote monitoring and 
therapy, the complexity of environments demands high 
robustness, and decision-level fusion can maintain stable 
outputs even when some data streams are incomplete. The 
optimal solution is not to rigidly commit to one fusion 
level, but rather to design a hybrid fusion architecture tai-
lored to the application’s needs, guided by evidence in the 
literature, in order to strike an appropriate balance among 
these dimensions.
Journal of King Saud University Computer and Information Sciences (2026) 38:71	
Page 13 of 25 
71
3.3.3  Emotion Classification Methods
Emotion classification strategies map fused features to spe-
cific emotional categories (e.g., happiness, sadness, positive/
negative valence). Based on the techniques employed, these 
strategies are broadly divided into traditional machine learn-
ing classifiers and deep learning classifiers.
a)	 Traditional Machine Learning Classifiers
Traditional classifiers rely on manually designed fea-
ture extraction processes, learning mappings between fea-
tures and emotional categories through statistical or rule-
based methods. These include Support Vector Machines 
(SVM), Naive Bayes (NB), k-Nearest Neighbors (k-NN), 
and Random Forests (RF). These methods typically offer 
good interpretability and low computational demands, suit-
able for scenarios with small data volumes or low feature 
dimensions. For example, Zhang et al. (Zhang et al. 2017) 
used SVMs for audio-visual emotion classification, achiev-
ing stable classification performance. Similarly, Huang et al. 
(Huang et al. 2019) applied linear SVM to text and audio 
data, demonstrating efficiency in simple tasks. Zheng et al. 
(Zheng et al. 2018) validated the applicability of linear SVM 
in similar scenarios. NB and k-NN are often used in prelimi-
nary experiments or benchmark tests due to their simplicity, 
while RF excels in robustness for certain multimodal tasks. 
However, traditional methods face limitations when data 
scales increase or feature complexity rises, as their com-
putational efficiency and generalization capabilities may 
decline. For instance, in handling high-dimensional video 
data or dynamic physiological signals, traditional methods 
may fail to capture complex nonlinear relationships, leading 
to performance degradation.
b)	 Deep Learning Classifiers
Deep learning classifiers automatically learn feature 
representations through multi-layer neural networks, 
reducing dependence on manual feature engineering. 
Common models include DNNs, CNNs, RNNs and their 
variants (e.g., LSTM, Gated Recurrent Units (GRUs)), 
and Transformer architectures. These models excel in pro-
cessing high-dimensional, sequential, or multimodal data. 
For example, Zadeh et al. (Zadeh et al. 2017) proposed 
a DNN-based emotion classification method that signifi-
cantly improved accuracy by fusing text, audio, and video 
features. Ma et al. (Ma et al. 2019) utilized CNNs to cap-
ture spatial features in video data, successfully identifying 
changes in facial expressions. Tsai et al. (Tsai et al. 2019) 
adopted the Transformer architecture, effectively mode-
ling complex relationships between text, audio, and video 
modalities through attention mechanisms. Some studies 
have explored hybrid deep learning models to enhance per-
formance further. For instance, Chen and Li (Chen and Li 
2020) proposed a CNN-LSTM hybrid model that combines 
CNNs' spatial feature extraction with LSTM's temporal 
modeling, suitable for dynamic multimodal data. Xie et al. 
(Song et al. 2018) optimized classification performance 
through multi-task learning and attention mechanisms. 
These researches indicate that deep learning methods often 
outperform traditional approaches on complex datasets. 
However, deep learning methods face challenges such as 
the high demand for annotated data, significant compu-
tational resource requirements, and poor interpretability.
c)	 Hybrid Classification Strategies
Recent studies have explored hybrid classification strat-
egies that integrate traditional machine learning and deep 
learning methods to leverage their respective strengths. 
These strategies often employ different techniques across 
modalities or classification stages, enhancing overall per-
formance through integration. For example, Noroozi et al. 
(Noroozi et al. 2017) designed a two-tier classification 
framework for audio-visual emotion tasks: the first tier used 
SVM and RF for audio and geometric features, while CNNs 
classified visual features; the second tier combined decisions 
via RF. This approach achieved 90% accuracy across multi-
ple datasets, demonstrating the potential of hybrid strategies 
in improving classification performance. The advantages of 
hybrid methods include combining the simplicity of tradi-
tional machine learning with the robust feature extraction 
capabilities of deep learning, while integrating techniques 
to compensate for the shortcomings of each method. How-
ever, implementing hybrid strategies is typically complex, 
requiring careful design of classifier combinations and 
fusion mechanisms to avoid overfitting or computational 
inefficiency.
4  Applications and Case Studies
Virtual rehabilitation platforms augmented with AC have 
been explored across various therapeutic domains. These 
systems span the full range of VR immersion—from non-
immersive (desktop or screen-based interfaces) to semi-
immersive (mixed or augmented reality setups) to fully 
immersive (head-mounted displays and motion capture), as 
shown in Table 3. In the following subsections, we exam-
ine representative case studies in four key application areas 
(motor rehabilitation, mental health, developmental disor-
ders, and chronic pain), highlighting how integrating uni-
modal or multimodal emotion recognition into VR therapy 
enhances adaptation and outcomes.
	
Journal of King Saud University Computer and Information Sciences (2026) 38:71
71 
Page 14 of 25
4.1  Motor Rehabilitation
Motor rehabilitation (e.g., post-stroke or Parkinson’s dis-
ease therapy) often involves repetitive limb exercises to pro-
mote neuroplasticity and functional recovery. Early virtual 
rehabilitation systems for motor recovery (e.g., post-stroke 
therapy) focused on improving movement through game-like 
exercises; however, they did not account for patients' emo-
tional states. This often led to problems such as boredom, 
frustration, or fatigue, which can reduce engagement and 
even cause patients to abandon training. Affective comput-
ing (AC) has been introduced to address these challenges 
by monitoring the user's emotional signals and adapting 
therapy in real time. For example, Rivas et al. (Rivas et al. 
2018) developed a post-stroke upper-limb rehabilitation 
system that adjusts task complexity in real time based on 
the patient's emotional feedback. In their study, the sys-
tem inferred states such as frustration or low enthusiasm 
(using motion and pressure sensors as proxies for affect) 
and dynamically adjusted the exercise difficulty to keep the 
patient optimally motivated. This effect-responsive adapta-
tion led to greater training enthusiasm and better functional 
recovery outcomes than a one-size-fits-all training protocol. 
Similarly, Tadayon et al.(Tadayon et al. 2018) incorporated 
affective computing into personalized stroke rehabilitation 
games, using physiological and kinematic cues to monitor 
patient mood and fatigue. They reported that emotion-aware 
task adjustments improved patients' motor performance and 
adherence compared to conventional static training regi-
mens. These systems illustrate that by preventing negative 
emotional states (e.g., frustration or learned helplessness) 
through timely adaptations, AC-enhanced motor VR can 
sustain patient engagement.
The ideal AdVRe system would unobtrusively meas-
ure emotions (e.g., via cameras or lightweight wearables) 
without encumbering the patient’s movement. Advance-
ments in computer vision and remote photoplethysmog-
raphy could eventually eliminate the need for multiple 
contact sensors, making the technology more practical 
for real clinics. In summary, motor rehabilitation stands 
to gain significantly from AC-driven adaptivity, which 
can increase patient motivation and potentially acceler-
ate recovery. Despite these advantages, there are notable 
limitations to current AC-integrated motor rehabilitation. 
A key concern is reliability, as well as the added com-
plexity. Emotion recognition for individuals performing 
intensive physical tasks remains prone to error – facial 
expressions may be obscured by effort, and heart rate 
changes may reflect exertion rather than emotion. There-
fore, future work must refine the fidelity and ease of use 
of emotion sensing, ensuring that adaptive algorithms 
augment (rather than complicate) standard physiotherapy 
practices.
4.2  Mental Health Intervention
VR has become a powerful tool in mental health treat-
ments such as phobia exposure therapy, post-traumatic 
stress disorder (PTSD) therapy, and anxiety management. 
A prominent VRe paradigm in this domain is exposure 
therapy, where patients confront feared stimuli in a con-
trolled virtual environment. The success of exposure 
therapy hinges on maintaining an optimal anxiety level—
high enough to facilitate habituation but not so high as 
to cause distress. This makes continuous monitoring of 
arousal particularly relevant, explaining the prevalence of 
Table 3   Representative studies on the integrated application of affective computing and virtual rehabilitation
Ref
Rehabilitation Purpose
Target Emotions/States
Immersion Level Device
 Tadayon et al. 2018)
At-home motor learning
Anger, disgust, fear, happy, sadness, 
surprised
Non-immersion
Screen
 Bălan et al. 2020)
Fear classification
Relaxation, low fear, medium fear, high fear Immersion
Headset
 i Badia et al. 2018)
Emotion regulation
anger, happy, sad, and fear
Immersion
Headset
 Razzak et al. 2025)
Cognitive and Social Training for ASD Negative, positive, and neutral
Immersion
Headset
 Bugeja 2023)
Pain Conditioning
Engaged, anxious, or bored
Immersion
Headset
 Pérez et al. 2022)
Lower limb rehabilitation training
-
Immersion
Headset
 Izountar et al. 2022)
Upper limb rehabilitation training
Negative: sad, angry, fear, and disgust, 
Neutral
Positive: happy, surprised
Semi-immersion
Screen
 Meekes and Stanmore 2017) Improve seniors' physical function
-
Non-immersion
Screen
 Afyouni et al. 2017)
Hand training
-
Semi-immersion
Screen
 Rivas et al. 2018)
Hand training for stroke patients
Tiredness, anxiety, pain, and engagement
Non-immersion
Screen
 Aranha et al. 2023)
Upper limb rehabilitation training
Anger, contempt, disgust, fear, happy, sad, 
and surprised
Non-immersion
Screen
 Prabhu et al. 2019)
Pain conditioning
Valence and Arousal
Immersion
Headset
Journal of King Saud University Computer and Information Sciences (2026) 38:71	
Page 15 of 25 
71
dimensional emotion models in such applications. Tradi-
tional VR exposure therapy (VRET) systems typically fol-
low a scripted intensity progression, relying on therapist 
input or the patient's self-reports to adjust anxiety levels. 
Affective computing now enables objective, automated 
monitoring of the user's emotional arousal and the modu-
lation of the virtual environment, making therapy safer 
and more effective than static protocols.
Entirely immersive VR platforms are ubiquitous in this 
domain, as high presence can elicit authentic emotional 
responses that AC systems can measure and respond to. 
Bălan et al. (Bălan et al. 2020) developed an EEG-based 
VRET system for fear conditioning that continuously 
monitored the user's anxiety level (via brainwave and 
heart rate signals) and adjusted the exposure intensity in 
real time. By keeping the patient's physiological arousal 
within an optimal "therapeutic window," this system pre-
vented overwhelming anxiety while still challenging the 
patient, an approach that improved treatment safety and 
maintained engagement more effectively than standard 
VR exposure with fixed stimulus intensity (braininfor-
matics.springeropen.com). In another representative 
study, i Badia et al. (i Badia et al. 2018) introduced the 
"Affective Maze" – a multimodal biofeedback VR sys-
tem that reacted to the user's emotional state during a 
stress management task. Their platform captured signals 
including ECG, respiration, EDA, and even facial elec-
tromyography, building a real-time model of the user's 
affect. The virtual environment (a maze) would then 
transform dynamically, if signs of anger or frustration 
were detected, visual metaphors such as flames would 
intensify, whereas signs of calm would make the maze 
more straightforward to navigate. Such adaptive feedback 
loops ensured that the therapy remained within person-
alized emotional bounds, thereby enhancing the effec-
tiveness of emotional regulation training compared to 
non-adaptive VR setups. Rahman et al. (Rahman et al. 
2023) demonstrated a biofeedback-enhanced VRET for 
public speaking anxiety, wherein the system monitored 
EEG indices of cortical arousal and heart rate changes 
to trigger relaxation guidance when the user's anxiety 
became too high. Participants reported better anxiety 
management and coping in this multimodal VR program 
than in a similar exposure exercise without real-time 
biofeedback.
In summary, affective computing enables mental health 
VR applications – often delivered on fully immersive 
platforms for maximum realism – to fine-tune therapeu-
tic stimuli to the user's emotional state. This closed-loop 
adaptation yields more responsive and engaging therapy, 
improving outcomes like reduced phobic fear and anxiety 
symptom severity relative to conventional VR interven-
tions that lack emotion-sensing capabilities.
4.3  Cognitive and Social Training 
for Developmental Disorders
Children and adults with developmental disorders (such 
as autism spectrum disorder, ASD, or ADHD) have ben-
efited from VR-based training programs targeting social 
skills, communication, and cognitive control. VR provides 
a safe, controlled environment for practicing real-life sce-
narios, such as social conversations or attention-focused 
tasks, which can be especially useful for individuals with 
ASD. However, keeping users engaged and appropriately 
challenged is a known difficulty in this population, as many 
with ASD have atypical responses to sensory stimuli and 
can become anxious or disengaged easily. Integrating affec-
tive computing into VR for individuals with developmental 
disorders aims to monitor their engagement and emotional 
state, enabling the system to adapt interactions in real-time.
A key example is the physiology-sensitive VR platform 
developed by Kuriakose and Lahiri (Kuriakose and Lahiri 
2016) for children with autism. Their system tracked real-
time biomarkers of anxiety as a child engaged in virtual 
social scenarios, like greeting an avatar or maintaining a 
conversation. If the child showed signs of rising anxiety or 
distraction, the VR environment adaptively responded—for 
instance, by simplifying the social task or providing sup-
portive prompts—to help the child remain calm and focused. 
In a preliminary evaluation, this anxiety-adaptive VR train-
ing led to improved social communication performance in 
children with ASD compared to a non-adaptive version of 
the same training. Another study by Li et al. (Li et al. 2021) 
employed eye-tracking and gesture analysis in an educational 
VR game for ASD, detecting when a child's attention drifted 
or when confusion was likely, and then adjusting the task or 
giving feedback to re-engage the child (e.g., highlighting a 
social cue the child missed). Such affect-aware modifications 
significantly personalized the learning experience. Indeed, 
a 2024 systematic review found that VR interventions for 
ASD that dynamically adapt to implicit bio-signals (such 
as gaze, motion, or physiology) have been more effective at 
fostering social and communication skills than those that do 
not adapt (Maddalon et al. 2024). For example, Razzak et al. 
(Razzak et al. 2025) observed in an immersive attention-
training game that children with ASD exhibited distinctive 
physiological responses—heart rate and skin conductance 
spikes—when they lost focus, and the system used these 
signals to trigger refocusing strategies. This led to measur-
able improvements in sustained attention relative to a control 
condition without adaptive cues.
Compared with conventional VR or computer-based 
training for developmental disorders, AdVRe systems offer 
a clear advantage: they can "sense" when the user is bored, 
overwhelmed, or not understanding the task and intervene 
immediately. Thus, for cognitive and social rehabilitation in 
	
Journal of King Saud University Computer and Information Sciences (2026) 38:71
71 
Page 16 of 25
developmental disorders, incorporating affective computing 
into VR yields a more personalized and robust interven-
tion, bridging the gap between individual needs and therapy 
dynamics that conventional VR systems alone cannot fully 
address.
4.4  Chronic Pain Management
Chronic pain patients often use VR applications as a form 
of distraction therapy or skills training (e.g., virtual mind-
fulness or physical exercise) to manage pain symptoms. 
Conventional VR pain management experiences – such 
as relaxing virtual environments or game-based exercises 
– have shown moderate success in reducing pain percep-
tion by diverting patients' attention away from it. However, 
the efficacy of VR can vary widely between individuals and 
over time. If a patient becomes anxious, frustrated, or simply 
less engaged during the VR session, the analgesic benefit 
may diminish. Affective computing can play a pivotal role 
by personalizing VR content in response to the patient's 
real-time emotional and physiological state. This approach 
has been explored in recent studies that utilize biofeedback-
integrated VR for pain management. For example, Bugeja 
et al. (Bugeja 2023) reported on a personalized VR pain 
management framework that utilizes machine learning to 
interpret physiological signals and maintain patients in an 
optimal "flow state" during VR distraction. In their study, 
patients' heart rate patterns were used to train an algorithm 
that estimated when the patient was fully engaged versus 
when pain was capturing their attention. The VR content 
(and an accompanying wearable vibration stimulus) was 
then adapted in real time to maximize periods of engage-
ment. Likewise, Prabhu et al. (Pérez et al. 2022) developed 
a VR-based chronic pain rehabilitation game that adjusts 
in-game stimuli in response to the user's stress signals. Their 
system monitored indicators such as heart rate and muscle 
tension. If a patient's pain-related distress increased (e.g., 
heart rate spiking or a grimace detected via the headset 
camera), the game would automatically switch to a more 
soothing activity or provide coaching on using a relaxation 
technique. Conversely, if the patient's engagement dropped 
(suggesting boredom or low arousal), the system could intro-
duce slightly more interactive distraction. In evaluations, 
this AdVRe approach led to better pain coping and a larger 
drop in self-reported pain scores compared to a similar VR 
game without adaptive features. Such findings underscore 
the promise of affective computing in boosting the efficacy 
of VR analgesia through tailored experiences.
Compared with conventional VR pain management, 
which may involve a generic relaxing VR video or game 
that remains the same for all users, AdVRe offers a dynamic, 
patient-specific therapy. A conventional VR distraction can 
indeed reduce pain for a while, but if a patient's pain flares 
up or if they become anxious (common in chronic pain epi-
sodes), a static program cannot adjust to help them cope. An 
AdVRe system, on the other hand, can detect those changes 
(for instance, via facial expression of pain or changes in 
autonomic signals) and modify the experience accordingly. 
This might mean guiding the patient through a breathing 
exercise when high pain is detected, or intensifying the level 
of immersive distraction when the patient shows signs of 
discomfort. The emerging consensus is that AC imbues VR 
pain therapy with a form of "intelligence" – the ability to 
sense and respond to the patient's hidden subjective state 
– which substantially improves personalization and out-
comes. As immersive VR hardware becomes more acces-
sible, integrating biosensors (such as heart rate, EDA, and 
facial cameras) and affective algorithms into chronic pain 
therapy is a logical next step to achieve durable, self-adjust-
ing pain management interventions.
5  Datasets, Challenges, and Opportunities
5.1  Datasets
Datasets provide the necessary data samples for algorithm 
and model training, validation and testing. The data source 
and annotation quality of the datasets are crucial for training 
and validating sentiment computing models and assessing 
their accuracy. Multimodal affective computing datasets 
typically encompass multiple signal types to capture the 
multidimensional aspects of emotional states. These datasets 
are usually collected through experimental tasks or natu-
ral interactions, covering a broad range of emotional states 
from basic emotions (e.g., happiness, sadness) to complex 
emotions (e.g., anxiety, frustration). Depending on their data 
sources and target applications, these datasets can be cat-
egorized into general-purpose datasets (GPDs) and domain-
specific datasets (DSDs) (as shown in Table 4).
a)	 General-Purpose Datasets
General-purpose datasets are not tailored for specific 
populations, scenarios, or application goals. Their data col-
lection aims to achieve broad coverage and diversity in sub-
ject populations, contextual settings, and induced emotional 
states. As summarized in Table 4, general-purpose datasets, 
due to their design objectives of covering a wider range of 
emotions and contexts, often exhibit greater diversity in 
modalities (signal types) and annotated emotional categories 
compared to domain-specific datasets. The DEAP(Koelstra 
et al. 2011) dataset induces emotions through music videos, 
recording EEG, ECG, GSR, and facial expressions, suitable 
for studying dimensional emotion models (valence, arousal). 
The AMIGOS(Miranda-Correa et al. 2018) dataset extends 
Journal of King Saud University Computer and Information Sciences (2026) 38:71	
Page 17 of 25 
71
Table 4   General datasets and specialized datasets
Dataset
Modality
Subjects
Data
Emotions
Online link
General-purpose datasets
DEAP(Koelstra et al. 2011)
A + V + T + B 32
Facial, text, EEG,
and PPS signals
Arousal, valence, and like/dislike
https://​github.​com/​DEAP/​deap
AMIGOS(Miranda-Correa et al. 
2018)
V + B
40
Facial, EEG, ECR.and GSR signals
Valence, arousal, control, familiarity, 
liking and basic emotions
https://​www.​eecs.​qmul.​ac.​uk/​mmv/​
datas​ets/​amigos/
RECOLA(Ringeval et al. 2013)
A + V + B
46
Audio, video, ECG, and EDA signals
Arousal, valence
https://​diuf.​unifr.​ch/​main/​diva/​recola/
CMMA(Zhang et al. 2023c)
A + T
-
3,000 multi-party conversations and 
21,795 multi-modal utterances
Sentiment, emotion, sarcasm and 
humor,
https://​github.​com/​annoy​mity2​022/​
Chine​se-​Datas​et
IEMOCAP(Busso et al. 2008)
A + V + T
10
Facial, motion, text
Happiness, anger, sadness, frustration 
and neutral state
https://​github.​com/​flavi​orain​hoavi​la/​
IEMOC​APspe​echEm​otion​Recog​
nition
CMU-MOSEI(Zadeh et al. 2018)
A + V
1000
Words, expressions
Angry, disgust, fear, happy, sad, and 
surprise
https://​github.​com/​pakor​omilas/​Multi​
modal​SDK_​loader
Domain-specific datasets
WESAD
(stress)(Choi KiSeon et al. 2014)
V + B
15
Blood volume pulse, electrocar-
diogram, electrodermal activity, 
electromyogram, respiration, body 
temperature, and three-axis accel-
eration
Neutral, stress, amusement
https://​github.​com/​WJMat​thew/​
WESAD
CALMED
(ASD children)(Sousa et al. 2023)
A + V
57,012 examples Facial, motion, audio
Calm (green), agitation (yellow), 
upset (red), sad (blue)
https://​github.​com/​annan​da/​calmed_​
datas​et_​stati​stics
MULTICOLLAB(Ekman and Friesen 
2003; Peechatt et al. 2024)
A + V + B
48
Eye gaze, facial action units, and 
galvanic skin response
Frustration
https://​github.​com/​mp6510/​MULTI​
COLLAB
FUSE(Al-Azani and El-Alfy 2025; 
Titung and Alm 2024)
A + V + B
19
Facial, GSR, text, audio
Frustration and Surprise
MODMA(Douglas-Cowie et al. 2003; 
Tasci et al. 2023)
(Mental disorder analysis)
A + B
55
Facial, EEG, audio, eye-movement 
tracking
https://​modma.​lzu.​edu.​cn/​data/​index/
DAIC-WOZ(Peechatt et al. 2024;  
Liu et al. 2024)
(Depression)
A + V + T
189 samples
Facial, GSR, text, audio
https://​dcaps​woz.​ict.​usc.​edu/
THE-POSSD(Titung and Alm 2024; 
Zhu et al. 2025)
(Stroke)
A + V + B
136
Facial, EGG, acoustic signal and 
glottal signal
Happy, sad, angry, and neutral
-
	
Journal of King Saud University Computer and Information Sciences (2026) 38:71
71 
Page 18 of 25
this approach by collecting EEG, ECG, GSR, and facial 
expressions during individual and group video watching, 
making it ideal for analyzing emotions in social interac-
tions. The RECOLA(Ringeval et al. 2013) dataset focuses 
on natural interactions, recording facial expressions, speech, 
and physiological signals during remote collaborative tasks, 
suitable for studying dynamic emotional changes. In terms 
of language, these datasets are predominantly in English. 
However, Zhang et al.(Zhang et al. 2023c) constructed the 
first Chinese multimodal multi-emotion dialogue dataset 
(CMMA), containing 21,795 multimodal utterances and 
3,000 multi-party dialogues, annotated with emotional, 
affective, sarcastic, and humorous labels. The study explored 
the impact of different data modalities and dialogue con-
texts on affective analysis tasks, demonstrating that CMMA 
exhibits significant advantages in multitask learning models 
and highlights the potential benefits of correlations between 
emotional-affective and sarcastic-humorous dimensions for 
joint detection. These general-purpose datasets require con-
textual adjustments when applied to pathologically relevant 
emotions.
b)	 Domain-Specific Datasets
Domain-specific datasets focus on specific fields or needs, 
with data collection potentially restricted to particular popu-
lations (e.g., individuals with autism spectrum disorder or 
depression) or serving explicit application goals (e.g., stress 
detection, driver fatigue monitoring). While these datasets 
may prioritize breadth in modalities and emotional catego-
ries, their strength lies in deep characterization and targeted 
modeling of specific emotional states. Multimodal datasets 
tailored for specific pathologies are relatively scarce, but 
recent research has actively addressed this gap. In men-
tal health, the WESAD(Choi KiSeon et al. 2014) dataset 
collects ECG, GSR, respiration, and motion data through 
stress-inducing tasks, suitable for stress-related pathological 
studies. Peechatt et al. (Ekman and Friesen 2003; Peechatt 
et al. 2024) introduced a novel multimodal dialogue corpus 
called MULTICOLLAB for studying collaborative and frus-
tration emotions, achieving significant improvements in clas-
sifying teachers' frustration through sensor data and speech 
transcriptions. Titung et al. (Al-Azani and El-Alfy 2025; 
Titung et al. 2024) introduced the FUSE dataset, focusing on 
capturing natural language expressions under frustration and 
surprise emotions. Data were collected through three tasks, 
with detailed annotations and affective inference analysis 
revealing emotional expression patterns in individual and 
dyadic interactions. In autism spectrum disorder (ASD) 
research, the CALMED(Sousa et al. 2023) dataset is a criti-
cal resource, containing audio and video features extracted 
from ASD children's meetings, annotated with emotional 
and social behavior cues. This dataset captures emotional 
expressions in social interactions among ASD children, 
supporting research on emotion recognition and social skill 
training.
c)	 Limitations of Existing Datasets
While the availability of datasets is a primary concern, 
several deeper limitations hinder the development and clini-
cal translation of AdVRe systems, extending beyond mere 
scarcity.
The most prominent limitation lies in the challenge of 
dataset availability. First of all, most general-purpose data-
sets (e.g., DEAP, AMIGOS) induce emotions in healthy 
participants using standardized stimuli like music videos. 
These elicited states often lack the intensity, complexity, and 
contextual relevance of emotions experienced by patients 
during physically demanding or psychologically challeng-
ing rehabilitation tasks. The resulting models may fail to 
generalize to the frustration of a stroke patient struggling 
with a motor task or the anxiety of a PTSD patient during 
exposure therapy. Additionally, Domain-specific datasets 
are a step forward, but they often remain small-scale and 
may not capture the full heterogeneity of patient populations. 
Factors such as age, severity of condition, comorbidities, 
and cultural background significantly influence emotional 
expression. Models trained on limited, non-representative 
samples risk biased performance against underrepresented 
patient groups. Last but not least, many datasets provide 
emotion labels but lack detailed, frame-level or event-level 
annotations linking specific physiological or behavioral 
changes to clinical events (e.g., onset of fatigue, pain spikes, 
or moments of task failure). This sparse annotation limits 
the ability to train models for fine-grained, causal analysis 
of emotional dynamics during rehabilitation.
Beyond of the above reasons, an equally critical issue 
is the ecological validity and representativeness of cur-
rent emotion datasets. According to the research conducted 
by Exxon and Frissen, the expression of true emotions is 
inseparable from the triggering of natural stimuli (Ekman 
and Friesen 2003). However, many publicly used emotion 
corpora are collected under constrained lab conditions or 
rely on acted emotional displays, which fail to capture the 
spontaneity and richness of patient emotional expression 
in real clinical contexts. Such datasets often lack diversity 
across key dimensions: participants tend to come from lim-
ited demographic groups (e.g. narrow age ranges or cultural 
backgrounds) and recordings use uniform settings, leading to 
a narrow portrayal of affective behavior. This lack of diver-
sity means that important variations in how different patients 
express emotion – for example, due to culture, age, or health 
status – are not represented, potentially introducing biases 
and reducing the model’s ability to generalize to new popu-
lations (Al-Azani and El-Alfy 2025). Moreover, the limited 
Journal of King Saud University Computer and Information Sciences (2026) 38:71	
Page 19 of 25 
71
ecological validity (i.e. the gap between contrived laboratory 
emotions and genuine clinical emotions) directly hampers 
model generalizability. Studies have observed that models 
trained on acted or highly controlled emotional data often 
suffer significant drops in accuracy when applied to authen-
tic patient emotions in natural settings (Douglas-Cowie et al. 
2003). In other words, because current datasets do not reflect 
the full diversity and realism of patient emotional expres-
sions, models lack robustness and fail to generalize reliably 
across real-world clinical scenarios.
These limitations collectively constrain the ecological 
validity, generalizability, and clinical applicability of AdVRe 
systems, underscoring the urgent need for more representa-
tive, richly annotated, and clinically relevant multimodal 
datasets.
5.2  Challenges
Multimodal affective computing dynamically adjusts the dif-
ficulty of virtual rehabilitation training by real-time monitor-
ing and analyzing users' emotional states, thereby enhancing 
rehabilitation outcomes and user experience. However, this 
technology faces multiple challenges in practical applica-
tions, including emotional recognition accuracy, insufficient 
clinical datasets, computational resource constraints, and 
privacy-ethics issues.
a)	 Interference in Accurate Emotion Recognition and Sys-
tem Stability.
Accurate detection and interpretation of users' emotional 
states (e.g., anxiety, frustration, pleasure) are core to affec-
tive computing. Current technologies may face noise inter-
ference in complex scenarios, leading to misidentification. 
Additionally, cultural differences or individual expression 
habits may affect the interpretation of emotional signals. For 
example, cultural variations in emotional expression pose 
challenges for generalizable affective models, such as some 
cultures favoring reserved expressions and others being more 
overt. Individual differences in expression habits also com-
plicate the development of universal models. For instance, 
some users may exhibit higher motivation during high-
difficulty rehabilitation tasks, while others may abandon 
them due to frustration. Incorrect identification could lead 
to improper difficulty adjustments, exacerbating user frus-
tration or reducing rehabilitation efficacy. Models designed 
to achieve higher accuracy may exhibit increased sensitiv-
ity to data noise or lack sufficient interpretability in clinical 
settings, which can compromise the stability and credibility 
of the system. Therefore, current technologies still require 
supervision and refinement by therapists to maintain opti-
mal system performance. Personalized training datasets for 
patients can also enhance autonomous adjustment accuracy.
b)	 Insufficient Clinical Datasets.
Although general-purpose multimodal affective datasets 
such as DEAP, AMIGOS, and RECOLA exist, as well as 
domain-specific clinical datasets like WESAD, CALMED, 
MULTICOLLAB, FUSE, and MODMA, large-scale, high-
quality, multimodal, and well-annotated public datasets 
specifically tailored for rehabilitation patients in virtual 
rehabilitation scenarios remain scarce, limiting algorithm 
training, validation, and generalization capabilities. In addi-
tion to limitations in data quantity, existing datasets exhibit 
fundamental shortcomings in ecological validity, population 
representativeness, and annotation density. These limitations 
hinder the ability of trained models to accurately capture the 
nuanced and dynamic emotional states of patients during 
rehabilitation, thereby constraining the generalizability and 
clinical efficacy of the resulting algorithms.
c)	 Data Privacy and Ethical Issues.
Data privacy and ethical concerns are critical challenges 
for affective computing in virtual rehabilitation. Affective 
computing involves collecting and analyzing highly sensitive 
personal data, such as physiological signals (heart rate, GSR, 
EEG), facial expressions, speech, and movement data. This 
multimodal data not only reveals users' immediate emotional 
states but can also infer underlying health conditions, cog-
nitive load, and even predispositions to certain psychologi-
cal states, raising significant privacy and ethical concerns. 
The creation of detailed emotional profiles poses risks of 
misuse, such as discrimination in insurance or employment, 
if such data were inadequately protected or accessed with-
out authorization. Furthermore, the continuous monitoring 
inherent in AdVRe systems blurs the line between thera-
peutic intervention and surveillance, potentially impacting 
patient autonomy and trust.
Users may justifiably worry about data storage, access 
permissions, and whether data will be used beyond the 
immediate rehabilitation purposes. For vulnerable popula-
tions, such as children with ASD or individuals with cogni-
tive impairments, obtaining truly informed consent for such 
pervasive data collection is particularly challenging (Price 
and Cohen 2019). Additionally, data breaches or unauthor-
ized access could lead to severe infringements on privacy 
and personal dignity. Beyond external threats, the internal 
use of data for purposes such as training AI models without 
explicit patient understanding or agreement also constitutes 
an ethical pitfall (Acosta et al. 2022).
d)	 Lack of real-world clinical validation.
Over the past five years, AdVRe systems have been 
explored across motor, mental‑health, chronic‑pain, and 
	
Journal of King Saud University Computer and Information Sciences (2026) 38:71
71 
Page 20 of 25
autism interventions; yet most implementations remain at 
the prototype or small pilot‑testing stage rather than being 
validated in rigorous, real‑world clinical trials (e.g., Rivas 
et al. ((Rivas et al. 2015, 2021)); Amini Gougeh & Falk 
(Amini Gougeh and Falk 2022)). Large multicenter or prag-
matic evaluations are still uncommon.
The shortfall in large‑scale validation is multifactorial: 
(i) recruitment and sample‑size constraints, compounded 
by limited, non‑representative affective datasets with poor 
ecological validity and sparse annotations, which hin-
der generalizability; (ii) high equipment and deployment 
costs—especially for multimodal sensing arrays and syn-
chronized pipelines—together with site infrastructure needs; 
(iii) real‑time performance bottlenecks (latency/compute on 
edge devices) that complicate second‑to‑second adaptation; 
and (iv) workflow integration barriers, including clinician 
trust, explainability, and regulatory alignment, which slow 
adoption even when technical performance is promising. 
Additional cross‑cutting constraints—privacy/ethics for 
continuous emotion and physiology capture—further com-
plicate study approval and scaling; in practice, lower‑burden, 
non‑immersive configurations often show better near‑term 
feasibility than fully immersive setups. Bridging the gap 
between clinical and experimental will require multicenter, 
pragmatic trials with standardized outcome measures, 
low‑burden sensing, and privacy‑preserving edge- and feder-
ated analytics to support real‑time inference in routine care.
While general data protection regulations like GDPR 
(General Data Protection Regulation) in Europe or HIPAA 
(Health Insurance Portability and Accountability Act) in the 
U.S. apply to personal health data, specific guidelines for 
affective computing in healthcare are still lacking. Existing 
regulations often do not fully address the unique nature of 
affective data, which can be ambiguous, context-depend-
ent, and capable of revealing information beyond what an 
individual might intend to share. However, comprehensive 
standards for the ethical collection, annotation, security, and 
privacy protection of multimodal affective data in clinical 
settings remain incomplete and are urgently needed.
5.3  Opportunities
The challenges facing AdVRe, while significant, are not 
insurmountable. They instead delineate a clear and promis-
ing roadmap for future research, highlighting specific tech-
nological and methodological opportunities to accelerate the 
clinical translation of affect-aware rehabilitation systems.
A primary opportunity lies in advancing algorithmic 
robustness and personalization to overcome the instability 
of emotion recognition in clinical populations. The inherent 
variability in patient expression due to motor impairments or 
pathological states necessitates models that are both adaptive 
and resilient. Future work should pivot towards multimodal 
disentanglement techniques, which aim to separate core, 
pathology-invariant emotional features from task-specific 
artifacts or impairment-related signals (Pei et al. 2024b). 
This can enhance the ecological validity of models trained 
on general-purpose datasets. Furthermore, paradigms such 
as continual and meta-learning offer a pathway to highly 
personalized emotional models that can efficiently fine-tune 
themselves to a patient's unique and evolving expressive pat-
terns over time, directly addressing issues of individual and 
cultural differences.
Even with improved algorithms and sensors, data scarcity 
remains a formidable barrier to building generalizable affec-
tive models. The scarcity of large, richly annotated clinical 
datasets for affect in rehabilitation limits the training and 
validation of the sophisticated models described above. A 
significant opportunity, therefore, lies in cultivating multi-
center data collaborations to amass diverse and representa-
tive emotional data from rehabilitation patients. By partner-
ing with hospitals and clinics, researchers can curate shared 
databases of multimodal signals (with appropriate consent 
and anonymization) that capture a wide range of patient 
demographics, diagnoses, and emotional responses. Estab-
lishing such repositories demands robust governance—trans-
parent data use agreements, patient involvement, and clear 
ethical safeguards—but would yield high-quality corpora on 
which to hone AdVRe algorithms. In the interim, advanced 
machine learning techniques offer complementary solutions 
to leverage the limited data available. Transfer learning can 
adapt emotion recognition models pretrained on general 
population affective datasets to the nuances of rehabilitation 
contexts (Ma et al. 2023). In contrast, semi-supervised and 
few-shot learning methods can leverage unlabeled patient 
data to improve models without requiring prohibitively large 
labelled datasets (Jing et al. 2025). These strategies effec-
tively bootstrap learning from scarce clinical data, ensuring 
that affective models become more accurate and culturally 
attuned as new information is gradually incorporated.
Crucially, any solution to data scarcity must be pursued 
in tandem with rigorous privacy protections and ethical 
safeguards. Federated Learning (FL) offers a transforma-
tive paradigm by enabling model training across multiple 
hospitals or clinics without requiring the pooling of sensi-
tive patient data into a central repository (Brauneck et al. 
2023). This "bring the code to the data" approach enables the 
creation of more robust, generalizable models from diverse, 
real-world data sources while inherently aligning with data 
protection regulations. Alongside FL, researchers are also 
integrating advanced cryptographic techniques to bolster pri-
vacy. Approaches such as differential privacy – which injects 
statistical noise into data or model gradients – can math-
ematically guarantee that no individual's emotion data can 
be inferred from a trained model, even by malicious actors. 
Likewise, homomorphic encryption allows computation on 
Journal of King Saud University Computer and Information Sciences (2026) 38:71	
Page 21 of 25 
71
encrypted physiological signals or video features, ensuring 
that raw sensitive data is never exposed in plain form dur-
ing analysis. These innovations, combined with robust data 
governance and anonymization protocols, create a forward-
looking framework for developing large-scale affective 
computing models for rehabilitation without compromising 
patient confidentiality. By resolving the ethical and legal 
barriers, privacy-preserving model training approaches will 
enable broader clinical collaborations and dataset sharing, 
ultimately improving the robustness of affective models 
trained on previously siloed multi-center data.
Finally, for the successful deployment of AdVRe in real-
world clinical and home settings, a differentiated strategy 
is required. The challenges inherent in these environments 
differ significantly. Clinical settings demand robust, multi-
patient systems capable of seamless integration into pro-
fessional workflows, while home-use systems prioritize 
intuitive operation, minimal setup, and sustainable patient 
adherence without professional oversight. The convergence 
of edge computing and contactless sensing is critical for 
both. Deploying optimized algorithms on local edge devices 
addresses latency and reliability concerns, enabling real-
time adaptation even with intermittent internet connectivity, 
which is particularly crucial for home-based tele-rehabili-
tation. To enhance usability and patient comfort, Contact-
less Multimodal Emotion Recognition (CMER) methods 
should be prioritized (Khan et al. 2024). In clinical settings, 
CMER (e.g., using remote photoplethysmography (rPPG) 
from headset-mounted cameras) reduces sensor setup time 
and cross-contamination risks. In-home environments 
remove the burden of correctly placing wearable sensors and 
increase adherence. The future lies in developing context-
aware systems that can automatically configure their sens-
ing and processing strategies—perhaps leveraging a com-
bination of built-in VR headset sensors for high-immersion 
clinical sessions and smartphone cameras for low-burden, 
daily check-ins at home. Additionally, the critical shortfall 
in clinical validation and the imperative to foster therapist 
trust must be addressed by prioritizing system transparency 
and integration. A pivotal strategy is the development of 
Explainable AI (XAI) techniques, which are essential for 
clarifying the affective reasoning of the "black-box" model 
for clinicians ((Zhang et al. 2025; Gambetti et al. 2025)). 
In XAI systems, the AdVRe platform conducts continuous 
monitoring and proposes adaptations, all while the thera-
pist maintains final authority and oversight. This synergistic 
model capitalizes on the respective strengths of computa-
tional consistency and human clinical judgment, factors that 
are undoubtedly prerequisites for widespread adoption and 
successful regulatory approval.
The integration of affective computing with virtual reality 
also opens new possibilities for remote rehabilitation (Had-
jar et al. 2025). In remote modes, patients can train using 
VR/AR devices at home, while affective computing tech-
nologies monitor their emotional states in real time, trans-
mitting data to remote rehabilitation specialists. Rehabilita-
tion specialists can then adjust treatment plans based on this 
feedback, offering personalized guidance and support. This 
model not only enhances the convenience of rehabilitation 
but also alleviates feelings of loneliness or isolation experi-
enced by patients due to limited mobility through continuous 
emotional care. Furthermore, emotional data provides reha-
bilitation specialists with tools to deeply understand patient 
needs. By analyzing emotional responses to different tasks, 
specialists can identify the most challenging or satisfying 
tasks, optimizing rehabilitation plans to maximize therapeu-
tic outcomes.
6  Conclusion
This paper systematically reviews the application of multi-
modal affective computing in virtual rehabilitation, explor-
ing its theoretical framework, technical implementation, and 
clinical translation potential. By addressing five key research 
questions (RQ1-RQ7), we clarify the applicable conditions, 
emotional model selection, signal fusion strategies, dataset 
resources, algorithmic frameworks, and specific applica-
tion scenarios of affective computing in virtual rehabilita-
tion. Affective computing, by perceiving and responding to 
patients' emotional states, significantly enhances the person-
alization and therapeutic effectiveness of virtual rehabili-
tation, particularly in the fields of neurological disorders, 
mental health conditions, chronic pain, and developmental 
disabilities.
From a technical perspective, multimodal approaches 
overcome the limitations of single-modal methods by inte-
grating physiological signals (e.g., EEG, ECG), behav-
ioral data (e.g., facial expressions, action patterns), and 
human–computer interaction data, significantly improving 
the accuracy and robustness of emotion recognition. The 
combination of discrete and dimensional emotion models 
provides flexible emotional representation schemes for 
diverse clinical scenarios, while the hybrid application of 
feature-level, model-level, and decision-level fusion strate-
gies further optimizes multimodal algorithm performance. 
Additionally, public datasets (e.g., DEAP, AMIGOS, 
CALMED) offer critical support for algorithm development, 
while domain-specific datasets (e.g., WESAD, MULTICOL-
LAB) provide new opportunities for precise modeling. In 
application scenarios, virtual rehabilitation leverages gami-
fied design and immersive environments to enhance patient 
engagement, while real-time feedback mechanisms inte-
grated with affective computing achieve dynamic optimiza-
tion of motor rehabilitation, pain management, and psycho-
logical treatment. Non-immersive systems, due to their low 
	
Journal of King Saud University Computer and Information Sciences (2026) 38:71
71 
Page 22 of 25
cost and ease of deployment, demonstrate higher clinical 
feasibility, whereas immersive systems showcase unique 
advantages in complex functional recovery and psychologi-
cal intervention.
However, the clinical translation of affective computing in 
virtual rehabilitation still faces multiple challenges, includ-
ing scene stability of emotion recognition, device computa-
tional constraints, data privacy protection, and the construc-
tion of personalized models. Future advancements, driven 
by improvements in wearable devices, sensor technologies, 
and artificial intelligence algorithms, will further enhance the 
real-time performance and accuracy of multimodal affective 
computing. Cross-disciplinary collaboration will promote the 
development of novel algorithms, low-cost sensors, and stand-
ardized datasets, laying the foundation for the widespread 
application of affective computing in virtual rehabilitation.
Acknowledgements  Not applicable.
Authors' contributions  All authors contributed to the study conception 
and design. Specific contributions:
Liang Zhao: Conceptualization, Investigation, Writing—Original 
Draft
Hanli Zhang: Data Curation, Visualization, Writing—Review & 
Editing
Dan Liu: Conceptualization, Supervision, Funding Acquisition, 
Writing—Review & Editing
Guanci Yang: Conceptualization, Supervision, Review & Editing
Donghua Zheng: Conceptualization, Investigation, Review & 
Editing
Jing Yan: Investigation, Review & Editing
Ling He: Review & Editing
All authors reviewed and approved the final manuscript.
Funding  This work was supported by: The National Natural Sci-
ence Foundation of China (NSFC) under Grant No.62566009 and the 
Guizhou Provincial Science and Technology Plan Projects under 
grant QKHZC [2023] 117,QKHZC[2023] 124 and QKHZC [2023]118.
Data availability  All data generated or analysed during this study are 
included in this published article.
Declarations 
Ethics approval  Not applicable.
Consent to participate  Not applicable.
Consent for publication  Not applicable.
Competing interests  The authors declare that they have no known 
competing financial interests or personal relationships that could have 
appeared to influence the work reported in this paper.
Open Access   This article is licensed under a Creative Commons 
Attribution-NonCommercial-NoDerivatives 4.0 International License, 
which permits any non-commercial use, sharing, distribution and repro-
duction in any medium or format, as long as you give appropriate credit 
to the original author(s) and the source, provide a link to the Creative 
Commons licence, and indicate if you modified the licensed material. 
You do not have permission under this licence to share adapted material 
derived from this article or parts of it. The images or other third party 
material in this article are included in the article’s Creative Commons 
licence, unless indicated otherwise in a credit line to the material. If 
material is not included in the article’s Creative Commons licence and 
your intended use is not permitted by statutory regulation or exceeds 
the permitted use, you will need to obtain permission directly from the 
copyright holder. To view a copy of this licence, visit http://​creat​iveco​
mmons.​org/​licen​ses/​by-​nc-​nd/4.​0/.
References
Acosta JN, Falcone GJ, Rajpurkar P, Topol EJ (2022) Multimodal bio-
medical AI. Nat Med 28(9):1773–1784
Afyouni I, Rehman FU, Qamar AM, Ghani S, Hussain SO, Sadiq 
B, Basalamah S (2017) A therapy-driven gamification frame-
work for hand rehabilitation. User Model User-Adapt Interact 
27:215–265
Al Roken N, Barlas G (2023) Multimodal Arabic emotion recognition 
using deep learning. Speech Commun 155:103005
Al-Azani S, El-Alfy ESM (2025) A review and critical analysis of mul-
timodal datasets for emotional AI. Artif Intell Rev 58(10):334
Alharbi M, Huang S (2020) A survey of incorporating affective com-
puting for human-system co-adaptation. In Proceedings of the 
2nd World Symposium on Software Engineering. pp 72–79
Amini Gougeh R, Falk TH (2022) Head-mounted display-based virtual 
reality and physiological computing for stroke rehabilitation: a 
systematic review. Front Virtual Real 3:889271
Antoniou PE, Arfaras G, Pandria N, Athanasiou A, Ntakakis G, Babat-
sikos E, Bamidis P (2020) Biosensor real-time affective analytics 
in virtual and mixed reality medical education serious games: 
cohort study. JMIR Serious Games 8(3):e17823
Aranha RV, Chaim ML, Monteiro CB, Silva TD, Guerreiro FA, Silva 
WS, Nunes FL (2023) Easyaffecta: a framework to develop seri-
ous games for virtual rehabilitation with affective adaptation. 
Multimedia Tools Appl 82(2):2303–2328
Aranha RV, Silva LS, Chaim ML, dos Santos Nunes FDL (2017) 
Using affective computing to automatically adapt serious games 
for rehabilitation. 2017 IEEE 30th International Symposium 
on Computer-Based Medical Systems (CBMS), Thessaloniki, 
Greece 2017:55–60. https://​doi.​org/​10.​1109/​CBMS.​2017.​89
Bălan O, Moise G, Moldoveanu A, Leordeanu M, Moldoveanu F 
(2020) An investigation of various machine and deep learning 
techniques applied in automatic fear level detection and acropho-
bia virtual therapy. Sensors 20(2):496
Bota PJ, Wang C, Fred AL, Da Silva HP (2019) A review, current 
challenges, and future possibilities on emotion recognition 
using machine learning and physiological signals. IEEE Access 
7:140990–141020
Brauneck A, Schmalhorst L, Kazemi Majdabadi MM, Bakhtiari M, 
Völker U, Baumbach J, ... , Buchholtz G (2023) Federated 
machine learning, privacy-enhancing technologies, and data pro-
tection laws in medical research: scoping review. J Med Internet 
Res 25 e41588
Bugeja A (2023) Personalised Pain Conditioning through Affective 
Computing and Virtual Reality (Master's thesis, University of 
Malta)
Busso C, Bulut M, Lee CC, Kazemzadeh A, Mower E, Kim S, Naray-
anan SS (2008) IEMOCAP: interactive emotional dyadic motion 
capture database. Lang Resour Eval 42:335–359
Carl E, Stein AT, Levihn-Coon A, Pogue JR, Rothbaum B, Emmelkamp 
P, Asmundson GJG, Carlbring P, Powers MB (2019) Virtual 
reality exposure therapy for anxiety and related disorders: a 
meta-analysis of randomized controlled trials. J Anxiety Disord 
61:27–36
Journal of King Saud University Computer and Information Sciences (2026) 38:71	
Page 23 of 25 
71
Chen C, Li Q (2020) A multimodal music emotion classification 
method based on multifeature combined network classifier. Math 
Probl Eng 2020(1):4606027
Chen Q, Mao X, Song Y, Wang K (2025) An EEG-based emotion 
recognition method by fusing multi-frequency-spatial features 
under multi-frequency bands. J Neurosci Methods 415:110360
Choi KiSeon CK, Kang SungDae KS, Kim HaeDong KH (2014) Mul-
tiple linear regression model for the prediction of Changma onset 
date in Korea
Chua P, Sasikumar P, Weerasinghe Y, Nanayakkara S (2024) Motion as 
Emotion: Detecting Affect and Cognitive Load from Free-Hand 
Gestures in VR. arXiv preprint arXiv:​2409.​12921
Cimtay Y, Ekmekcioglu E, Caglar-Ozhan S (2020) Cross-subject multi-
modal emotion recognition based on hybrid fusion. IEEE Access 
8:168865–168878
Douglas-Cowie E, Campbell N, Cowie R et al (2003) Emotional 
speech: towards a new generation of databases. Speech Com-
mun 40(1–2):33–60
Ekman P (1992) Are there basic emotions?https://​doi.​org/​10.​1037/​
0033-​295X.​99.3.​550
Ekman P Friesen WV (2003) Unmasking the face: A guide to recogniz-
ing emotions from facial clues[M]. Ishk, 2003
Feitosa JA, Fernandes CA, Casseb RF, Castellano G (2022) Effects of 
virtual reality-based motor rehabilitation: a systematic review of 
fMRI studies. J Neural Eng 19(1):011002
Gambetti A, Han Q, Shen H, Soares C (2025) A Survey on Human-
Centered Evaluation of Explainable AI Methods in Clinical Deci-
sion Support Systems. arxiv preprint arxiv:2502.09849
Gkoumas D, Li Q, Dehdashti S, Melucci M, Yu Y, Song D (2021) 
Quantum cognitively motivated decision fusion for video senti-
ment analysis. In Proceedings of the AAAI Conference on Arti-
ficial Intelligence (Vol. 35, No. 1, pp. 827-835)
Guo C, Zhang K, Chen J, Xu R, Gao L (2021) Design and application 
of facial expression analysis system in empathy ability of chil-
dren with autism spectrum disorder. In 2021 16th Conference 
on Computer Science and Intelligence Systems (FedCSIS) (pp. 
319–325). IEEE
Hadjar H, Vu B, Hemmje M (2025) Empowering recovery: the T-rehab 
system’s semi-immersive approach to emotional and physical 
well-being in tele-rehabilitation. Electronics 14(5):852
Herumurti D, Yuniarti A, Rimawan P, Yunanto AA (2019). Overcom-
ing glossophobia based on virtual reality and heart rate sensors. 
In 2019 IEEE International Conference on Industry 4.0, Artifi-
cial Intelligence, and Communications Technology (IAICT) (pp. 
139–144). IEEE
Heyse J, Torres Vega M, De Jonge T, De Backere F, De Turck F (2020) 
A personalised emotion-based model for relaxation in virtual 
reality. Appl Sci 10(17):6124
Hibbeln M, Jenkins JL, Schneider C, Valacich JS, Weinmann M (2017) 
How is your user feeling? Inferring emotion through human–
computer interaction devices. MIS Q 41(1):1–22
Huang Y, Yang J, Liu S, Pan J (2019) Combining facial expressions and 
electroencephalography to enhance emotion recognition. Future 
Internet 11(5):105
i Badia SB, Quintero LV, Cameirao MS, Chirico A, Triberti S, Cipresso 
P, Gaggioli A (2018) Toward emotionally adaptive virtual reality 
for mental health applications. IEEE J Biomed Health Inform 
23(5):1877–1887
Imran N, Zhang J, Ali J, Hameed S, Younas M, Alenazi MJ, Niaz 
F (2024) mm-HrtEMO: Non-Invasive Emotion Recognition 
via Heart Rate Using mm-Wave Sensing in Diverse Scenarios. 
IEEE J Biomed Health Inform. https://​doi.​org/​10.​1109/​JBHI.​
2024.​35223​16
Islam MM, Nooruddin S, Karray F, Muhammad G (2024) Enhanced 
multimodal emotion recognition in healthcare analytics: a deep 
learning based model-level fusion approach. Biomed Signal Pro-
cess Control 94:106241
Issa D, Demirci MF, Yazici A (2020) Speech emotion recognition with 
deep convolutional neural networks. Biomed Signal Process Con-
trol 59:101894
Izountar Y, Benbelkacem S, Otmane S, Khababa A, Masmoudi M, 
Zenati N (2022) VR-PEER: A personalized exer-game platform 
based on emotion recognition. Electronics 11(3):455
Jing K, Ma H, Zhang C, Wen L, Zhang Z (2025) Recursive confidence 
training for pseudo-labeling calibration in semi-supervised few-
shot learning. IEEE Trans Image Process 34:3194–3208
Khan UA, Xu Q, Liu Y, Lagstedt A, Alamäki A, Kauttonen J (2024) 
Exploring contactless techniques in multimodal emotion recogni-
tion: insights into diverse applications, challenges, solutions, and 
prospects. Multimedia Syst 30(3):115
Khan M, Tran PN, Pham NT, El Saddik A, Othmani A (2025) 
Memocmt: multimodal emotion recognition using cross-modal 
transformer-based feature fusion. Sci Rep 15(1):5473
Khare SK, Blanes-Vidal V, Nadimi ES, Acharya UR (2024) Emotion 
recognition and artificial intelligence: a systematic review (2014–
2023) and research recommendations. Inf Fusion 102:102019
Koelstra S, Muhl C, Soleymani M, Lee JS, Yazdani A, Ebrahimi T, 
Patras I (2011) Deap: a database for emotion analysis, using 
physiological signals. IEEE Trans Affect Comput 3(1):18–31
Kumar PS, Govarthan PK, Gadda AAS, Ganapathy N, Ronickom 
JFA (2024) Deep learning-based automated emotion recogni-
tion using multimodal physiological signals and time-frequency 
methods. IEEE Trans Instrum Meas 73:1–12
Kuriakose S, Lahiri U (2016) Design of a physiology-sensitive VR-
based social communication platform for children with autism. 
IEEE Trans Neural Syst Rehabil Eng 25(8):1180–1191
Lange J, Heerdink M, Van Kleef G (2021) Reading emotions, reading 
people: emotion perception and inferences drawn from perceived 
emotions. Curr Opin Psychol 43:85–90
Li, Y., Sokhadze EM, Luo H, El-Baz AS, Elmaghraby AS (2021) 
Affective virtual reality gaming for autism. Modern Approaches 
to Augmentation of Brain Function, 575–606
Lima R, Chirico A, Varandas R, Gamboa H, Gaggioli A, i Badia SB 
(2024) Multimodal emotion classification using machine learning 
in immersive and non-immersive virtual reality. Virtual Reality 
28(2):107
Liu X, Li S, Wang M (2021a) Hierarchical attention-based multimodal 
fusion network for video emotion recognition. Comput Intell 
Neurosci 2021(1):5585041
Liu D, Wang Z, Wang L, Chen L (2021b) Multi-modal fusion emotion 
recognition method of speech expression based on deep learning. 
Front Neurorobot 15:697634
Liu L, Liu L, Wafa HA, Tydeman F, Xie W, Wang Y (2024) Diagnostic 
accuracy of deep learning using speech samples in depression: 
a systematic review and meta-analysis. J Am Med Inform Assoc 
31(10):2394–2404
Liu H (2024) Emotion Detection through Body Gesture and Face. 
arXiv preprint arXiv:​2407.​09913
Lukacs MJ, Salim S, Katchabaw MJ, Yeung E, Walton DM (2022) 
Virtual reality in physical rehabilitation: a narrative review and 
critical reflection. Phys Ther Rev 27(4):281–289
Ma Y, Hao Y, Chen M, Chen J, Lu P, Košir A (2019) Audio-visual 
emotion fusion (AVEF): a deep efficient weighted approach. Inf 
Fusion 46:184–192
Ma Y, Zhao W, Meng M, Zhang Q, She Q, Zhang J (2023) Cross-
subject emotion recognition based on domain similarity of EEG 
signal transfer learning. IEEE Trans Neural Syst Rehabil Eng 
31:936–943
Maddalon L, Minissi ME, Parsons T, Hervas A, Alcaniz M (2024) 
Exploring adaptive virtual reality systems used in interventions 
	
Journal of King Saud University Computer and Information Sciences (2026) 38:71
71 
Page 24 of 25
for children with autism spectrum disorder: systematic review. J 
Med Internet Res 26:e57093
Maj M, Gnat M, Pliszczuk D, Kowalski M, Łukasiewicz J (2024) An 
intelligent support system and emotional state tests for people 
who are sick or recovering. J Modern Sci 57:371
Mamieva D, Abdusalomov AB, Kutlimuratov A, Muminov B, 
Whangbo TK (2023) Multimodal emotion detection via atten-
tion-based fusion of extracted facial and speech features. Sensors 
23(12):5475
Marzal A, Martínez-Rico G, González-García RJ, Cañadas M (2020) 
An updated guideline for reporting systematic reviews. PLoS 
Med 18(3):1–15
Meekes W, Stanmore EK (2017) Motivational determinants of exer-
game participation for older people in assisted living facilities: 
mixed-methods study. J Med Internet Res 19(7):e238
Middya AI, Nag B, Roy S (2022) Deep learning based multimodal 
emotion recognition using model-level fusion of audio–visual 
modalities. Knowl-Based Syst 244:108580
Miranda-Correa JA, Abadi MK, Sebe N, Patras I (2018) Amigos: a 
dataset for affect, personality, and mood research on individuals 
and groups. IEEE Trans Affect Comput 12(2):479–493
Nemati S, Rohani R, Basiri ME, Abdar M, Yen NY, Makarenkov V 
(2019) A hybrid latent space data fusion method for multimodal 
emotion recognition. IEEE Access 7:172948–172964
Noroozi F, Marjanovic M, Njegus A, Escalera S, Anbarjafari G (2017) 
Audio-visual emotion recognition in video clips. IEEE Trans 
Affect Comput 10(1):60–75
Pandeya YR, Bhattarai B, Lee J (2021) Deep-learning-based mul-
timodal emotion classification for music videos. Sensors 
21(14):4927
Peechatt M, Alm CO, Bailey R (2024) MULTICOLLAB: A multimodal 
corpus of dialogues for analyzing collaboration and frustration 
in language. In Proceedings of the 2024 Joint International Con-
ference on Computational Linguistics, Language Resources and 
Evaluation (LREC-COLING 2024). pp 11713–11722. https://​
aclan​tholo​gy.​org/​2024.​lrec-​main.​1023/
Pei G, Li H, Lu Y et al (2024a) Affective computing: recent advances, 
challenges, and future trends. Intelligent Computing 3:0076
Pei G, Li H, Lu Y, Wang Y, Hua S, Li T (2024b) Affective comput-
ing: recent advances, challenges, and future trends. Intelligent 
Computing 3:0076
Pepa L, Spalazzi L, Capecci M, Ceravolo MG (2021) Automatic emo-
tion recognition in clinical scenario: a systematic review of meth-
ods. IEEE Trans Affect Comput 14(2):1675–1695
Pérez VZ, Yepes JC, Vargas JF, Franco JC, Escobar NI, Betancur L, 
Betancur MJ (2022) Virtual reality game for physical and emo-
tional rehabilitation of landmine victims. Sensors 22(15):5602
Prabhu VG, Linder C, Stanley LM, Morgan R (2019) An affective com-
puting in virtual reality environments for managing surgical pain 
and anxiety. 2019 IEEE International Conference on Artificial 
Intelligence and Virtual Reality (AIVR), San Diego, CA, USA. 
pp. 235–2351. https://​doi.​org/​10.​1109/​AIVR4​6125.​2019.​00049
Price WN, Cohen IG (2019) Privacy in the age of medical big data. 
Nat Med 25(1):37–43
Quan W, Liu S, Cao M, Zhao J (2024) A comprehensive review of 
virtual reality technology for cognitive rehabilitation in patients 
with neurological conditions. Appl Sci 14(14):6285
Rahman MA, Brown DJ, Mahmud M, Harris M, Shopland N, Heym 
N, Lewis J (2023) Enhancing biofeedback-driven self-guided 
virtual reality exposure therapy through arousal detection from 
multimodal data using machine learning. Brain Inform 10(1):14
Razzak R, Li YJ, He JS, Jung S, Mei C, Huang Y (2025) Using virtual 
reality to enhance attention for autistic spectrum disorder with 
eye tracking. High-Confidence Computing 5(1):100234
Razzaq MA, Hussain J, Bang J, Hua CH, Satti FA, Rehman UU, Lee 
S (2023) A hybrid multimodal emotion recognition framework 
for UX evaluation using generalized mixture functions. Sensors 
23(9):4373
Ringeval F, Sonderegger A, Sauer J, Lalanne D (2013) Introducing 
the RECOLA multimodal corpus of remote collaborative and 
affective interactions. 2013 10th IEEE International Conference 
and Workshops on Automatic Face and Gesture Recognition 
(FG), Shanghai, China, 2013. pp. 1–8. https://​doi.​org/​10.​1109/​
FG.​2013.​65538​05
Rivas JJ, Orihuela-Espina F, Palafox L, Bianchi-Berthouze N, del Car-
men Lara M, Hernández-Franco J, Sucar LE (2018) Unobtrusive 
inference of affective states in virtual rehabilitation from upper 
limb motions: A feasibility study. IEEE Trans Affect Comput 
11(3):470–481
Rivas JJ, Orihuela-Espina F, Sucar LE, Palafox L, Hernández-Franco J, 
Bianchi-Berthouze N (2015) Detecting affective states in virtual 
rehabilitation. 2015 9th International Conference on Pervasive 
Computing Technologies for Healthcare (PervasiveHealth), 
Istanbul, Turkey. pp. 287–292. https://​doi.​org/​10.​4108/​icst.​perva​
siveh​ealth.​2015.​259250
Rivas JJ, Orihuela-Espina F, Sucar LE, Williams A, Bianchi-Berthouze 
N (2019) Automatic recognition of multiple affective states in 
virtual rehabilitation by exploiting the dependency relationships. 
2019 8th International Conference on Affective Computing and 
Intelligent Interaction (ACII), Cambridge, UK, 2019. pp. 1–7. 
https://​doi.​org/​10.​1109/​ACII.​2019.​89255​08
Rivas JJ, del Carmen Lara M, Castrejon L, Hernandez-Franco J, Ori-
huela-Espina F, Palafox L, ... , Sucar LE (2021) Multi-label and 
multimodal classifier for affective states recognition in virtual 
rehabilitation. IEEE Transactions On Affective Computing 13(3) 
1183–1194
Rodriguez J, Del-Valle-Soto C, Gonzalez-Sanchez J (2022) Affective 
states and virtual reality to improve gait rehabilitation: a prelimi-
nary study. Int J Environ Res Public Health 19(15):9523
Romero-Ramos L, González-Serna G, López-Sánchez M, González-
Franco N, Valenzuela-Robles B (2024) Emotion Recognition in 
Virtual Reality Learning Environments: A Multimodal Machine 
Learning Approach. In Mexican International Conference on Arti-
ficial Intelligence (pp. 45–52). Cham: Springer Nature Switzerland
Russell JA (1980) A circumplex model of affect. J Pers Soc Psychol 
39(6):1161
Salas-Cáceres J, Lorenzo-Navarro J, Freire-Obregón D, Castrillón-San-
tana M (2024) Multimodal emotion recognition based on a fusion 
of audiovisual information with temporal dynamics. Multimedia 
Tools Appl 84:27327–27343
Sepúlveda A, Castillo F, Palma C, Rodriguez-Fernandez M (2021) 
Emotion recognition from ECG signals using wavelet scattering 
and machine learning. Appl Sci 11(11):4945
Shaver P, Schwartz J, Kirson D, O’connor C (1987) Emotion knowl-
edge: further exploration of a prototype approach. J Pers Soc 
Psychol 52(6):1061
Shih CH, Lin PJ, Chen YL, Chen SL (2024) A post-stroke rehabilita-
tion system with compensatory movement detection using vir-
tual reality and electroencephalogram technologies. IEEE Access 
12:61418–61432
Smith E, Storch EA, Vahia I, Wong ST, Lavretsky H, Cummings JL, 
Eyre HA (2021) Affective computing for late-life mood and cog-
nitive disorders. Front Psychiatry 12:782183
Song KS, Nho YH, Seo JH, Kwon DS (2018) Decision-level fusion 
method for emotion recognition using multimodal emotion rec-
ognition information. In 2018 15th international conference on 
ubiquitous robots (UR) (pp. 472–476). IEEE
Sousa A, Young K, D’aquin M, Zarrouk M, Holloway J (2023) Intro-
ducing CALMED: multimodal annotated dataset for emotion 
detection in children with autism. In International Conference 
on Human-Computer Interaction (pp. 657–677). Cham: Springer 
Nature Switzerland
Journal of King Saud University Computer and Information Sciences (2026) 38:71	
Page 25 of 25 
71
Tadayon R, Amresh A, McDaniel T, Panchanathan S (2018) Real-time 
stealth intervention for motor learning using player flow-state. In 
2018 IEEE 6th international conference on serious games and 
applications for health (SeGAH) (pp. 1–8). IEEE
Tan C, Ceballos G, Kasabov N, Puthanmadam Subramaniyam N (2020) 
Fusionsense: emotion classification using feature fusion of mul-
timodal data and deep learning in a brain-inspired spiking neural 
network. Sensors (Basel) 20(18):5328
Tasci G, Loh HW, Barua PD, Baygin M, Tasci B, Dogan S, Acharya 
UR (2023) Automated accurate detection of depression using 
twin Pascal’s triangles lattice pattern with EEG signals. Knowl-
Based Syst 260:110190
Titung R, Alm CO (2024) FUSE-FrUstration and Surprise Expressions: A 
Subtle Emotional Multimodal Language Corpus. In Proceedings of 
the 2024 Joint International Conference on Computational Linguis-
tics, Language Resources and Evaluation (LREC-COLING 2024) 
(pp. 7544–7555). https://​aclan​tholo​gy.​org/​2024.​lrec-​main.​666/
Tsai YHH, Bai S, Liang PP, Kolter JZ, Morency LP, Salakhutdinov R 
(2019) Multimodal transformer for unaligned multimodal lan-
guage sequences. In Proceedings of the conference. Association 
for computational linguistics. Meeting (Vol. 2019, p. 6558–6569)
Tsalera E, Papadakis A, Samarakou M, Voyiatzis I (2022) Feature 
extraction with handcrafted methods and convolutional neural 
networks for facial emotion recognition. Appl Sci 12(17):8455
Wang Y, Song W, Tao W et al (2022) A systematic review on affective 
computing: Emotion models, databases, and recent advances[J]. 
Information Fusion 83:19–52
Wang Y, Gu Y, Yin Y, Han Y, Zhang H, Wang S, Li C, Quan D (2023) 
Multimodal transformer augmented fusion for speech emotion 
recognition. Front Neurorobot 17:1181598
Wen Yean C, Wan Ahmad WK, Mustafa WA, Murugappan M, Raja-
manickam Y, Adom AH, Bakar SA (2020) An emotion assess-
ment of stroke patients by using bispectrum features of EEG 
signals. Brain Sci 10(10):672
Xie J, Wang J, Wang Q, Yang D, Gu J, Tang Y, Varatnitski YI (2023) A 
multimodal fusion emotion recognition method based on multitask 
learning and attention mechanism. Neurocomputing 556:126649
Yan X, Xue H, Jiang S, Liu Z (2022) Multimodal sentiment analysis 
using multi-tensor fusion network with cross-modal modeling. 
Appl Artif Intell 36(1):2000688
Zadeh A, Chen M, Poria S, Cambria E, Morency LP (2017) Tensor 
fusion network for multimodal sentiment analysis. arXiv preprint 
arXiv:​1707.​07250
Zadeh AB, Liang PP, Poria S, Cambria E, Morency LP (2018) Mul-
timodal language analysis in the wild: Cmu-mosei dataset and 
interpretable dynamic fusion graph. In Proceedings of the 56th 
Annual Meeting of the Association for Computational Linguis-
tics (Volume 1: Long Papers) (pp. 2236–2246)
Zhang S, Zhang S, Huang T, Gao W, Tian Q (2017) Learning affec-
tive features with a hybrid deep model for audio–visual emo-
tion recognition. IEEE Trans Circuits Syst Video Technol 
28(10):3030–3043
Zhang Z, Fort JM, Giménez Mateu L (2023a) Facial expression recog-
nition in virtual reality environments: challenges and opportuni-
ties. Front Psychol 14:1280136
Zhang Y, Wang J, Liu Y, Rong L, Zheng Q, Song D, ..., Qin J (2023b) 
A multitask learning model for multimodal sarcasm, sentiment 
and emotion recognition in conversations. Inform Fusion 93 
282–301
Zhang Y, Yu Y, Guo Q, Wang B, Zhao D, Uprety S, ... , Qin J (2023c) 
CMMA: benchmarking multi-affection detection in chinese 
multi-modal conversations. Adv Neural Inform Processing Syst 
36, 18794–18805
Zhang T, Chung T, Dey A, Bae SW (2025) AXAI-CDSS: An Affec-
tive Explainable AI-Driven Clinical Decision Support System for 
Cannabis Use. arXiv preprint arXiv:2503.06463
Zheng WL, Liu W, Lu Y, Lu BL, Cichocki A (2018) Emotionmeter: a 
multimodal framework for recognizing human emotions. IEEE 
Trans Cybern 49(3):1110–1122
Zhong B, Qin Z, Yang S, Chen J, Mudrick N, Taub M, ... , Lobaton E 
(2017) Emotion recognition with facial expressions and physi-
ological signals. In 2017 IEEE symposium series on computa-
tional intelligence (SSCI) (pp. 1–8). IEEE
Zhou H, Du J, Zhang Y, Wang Q, Liu QF, Lee CH (2021) Informa-
tion fusion in attention networks using adaptive and multi-level 
factorized bilinear pooling for audio-visual emotion recognition. 
IEEE ACM Trans Audio Speech Lang Process 29:2617–2629
Zhu T, Duan S, Liang H, Li F, Zhang W (2025) Multiangle correlation 
feature extraction and disease prediction model construction for 
patients with post-stroke dysarthria. IEEE Transactions on Neu-
ral Systems and Rehabilitation Engineering
Zvarevashe K, Olugbara O (2020) Ensemble learning of hybrid acous-
tic features for speech emotion recognition. Algorithms 13(3):70
Publisher's Note  Springer Nature remains neutral with regard to 
jurisdictional claims in published maps and institutional affiliations.
