Biomedical Signal Processing and Control 92 (2024) 106096
Available online 20 February 2024
1746-8094/© 2024 The Author(s). Published by Elsevier Ltd. This is an open access article under the CC BY-NC-ND license (http://creativecommons.org/licenses/by-
nc-nd/4.0/).
Contents lists available at ScienceDirect
Biomedical Signal Processing and Control
journal homepage: www.elsevier.com/locate/bspc
Facial expression recognition based on emotional artificial intelligence for
tele-rehabilitation
Davide Ciraolo a, Maria Fazio a, Rocco Salvatore Calabrò b, Massimo Villari a, Antonio Celesti a,∗
a Department of Mathematics, Informatics, Phyisct and Heart Sciences (MIFT), University of Messina, Italy
b Centro Neurolesi ‘‘Bonino Pulejo", Messina, Italy
A R T I C L E
I N F O
Keywords:
Emotional AI
Cognitive rehabilitation
Machine learning
Emotion detection
MediaPipe
Face mesh
Face Feature Map
Facial expression detection
A B S T R A C T
Tele-rehabilitation aims at increasing clinical outcomes while reducing costs and improving patients’ quality
of life (QoL). However, two main challenges need to be addressed to ensure its effectiveness: remote motor
and cognitive rehabilitation. In this research work, we want to focus on the latter. Our idea is to integrate the
concept of Emotional AI into tele-rehabilitation by monitoring the facial expressions of patients during motor
rehabilitation exercises. Thus, we can assess the patient’s cognitive and emotional state, with the objective
of determining the relationship between motor and cognitive rehabilitation outcomes. Therefore, this study
considers a Cloud/Edge continuum tele-rehabilitation scenario where a Hospital Cloud interacts with remote
rehabilitation and monitoring Edge devices placed in patients’ homes and/or rehabilitation centres. Specifically,
we want to assess the performance of a Facial Expression Recognition (FER) system that can be deployed at
the Edge. To achieve our goal, we employ the MediaPipe suite of libraries, which is optimized to run on low-
resource devices. In particular, we used its Face Mesh module that is capable of generating a face mesh (i.e.,
a set of 3D face points) from an input image. The features of the mesh are then used to train a classifier that
can identify the different facial expressions defined in Ekman’s model (i.e., angry, fear, happy, sad, surprise,
and neutral). In our experiments, we tested several combinations of datasets, face meshes (FMs), face feature
maps (FFMs), and classifiers to identify the best-performing solution and demonstrate the applicability of this
approach in a tele-rehabilitation environment.
1. Introduction
Severe acquired brain injuries (SABI), cerebral stroke, Alzheimer’s,
and Parkinson’s often require the patient’s hospitalization in a medi-
cal centre to let them undergo rehabilitative therapy. This approach
is, however, limited by high costs and/or geographical barriers, and
usually adversely affects the patient’s life especially when long-term
rehabilitation is required. In recent years, thanks to the increasing use
of information and communication technology (ICT), tele-rehabilitation
(TR) has emerged as an effective approach to providing care and
support to frail individuals, their families, and their caregivers. Re-
mote monitoring of patients’ rehabilitation therapy indeed, allows the
optimization of hospital resources by enabling therapists to follow
patients more easily, freeing up hospital beds and ultimately pushing
down clinical costs, while increasing clinical outcomes and improving
patients’ Quality of Life (QoL). TR was initially conceived to provide
equitable access to geographically distant, physically and/or econom-
ically disadvantaged people, but it has the potential to improve the
∗Corresponding author.
E-mail addresses: davciraolo@unime.it (D. Ciraolo), mfazio@unime.it (M. Fazio), roccos.calabro@irccsme.it (R.S. Calabrò), mvillari@unime.it (M. Villari),
acelesti@unime.it (A. Celesti).
quality of rehabilitative healthcare in general by enabling clinicians
to optimize the duration and intensity of therapy, which is often not
possible in the current healthcare system due to the limitations of
in-person treatments.
Cloud computing in combination with Edge Computing and Artifi-
cial Intelligence (AI) are the main enablers for tele-rehabilitation. In
particular, AI can have a great impact on tele-rehabilitation [1,2]. A
pilot study aimed at assessing the feasibility of TR for SABI patients
using Cloud solutions has already been done by us in the Italian
Healthcare Ministry-funded project entitled ‘‘Do Severe Acquired Brain
Injury Patients Benefit from Telerehabilitation? A Cost-effectiveness
analysis study’’ [3,4]. In this pilot study, we conducted a prelimi-
nary investigation of a Cloud computing platform suitable for the
TR scenario, including developing an application to collect, analyze,
and visualize patients’ therapeutic progress. Additionally, the last part
of the project included conducting a preliminary feasibility study on
the use of Machine Learning (ML) to analyze patients’ movements
https://doi.org/10.1016/j.bspc.2024.106096
Received 31 May 2023; Received in revised form 4 January 2024; Accepted 3 February 2024
Biomedical Signal Processing and Control 92 (2024) 106096
2
D. Ciraolo et al.
Fig. 1. Cloud-Edge Tele-Rehabilitation scenario.
during rehabilitation exercises [5]. The research work described in this
paper is part of the TR as a Service (TRaaS) project, i.e., a research
project founded by the Italian ‘‘Projects of Relevant National Interest’’
(PRIN) programme. It aims to overcome the gap in the field of TR
by creating a reference intelligent Cloud/Edge framework architecture
and a standard data model for the development of different kinds of
new de-hospitalized TR services [6]. Specifically, in this paper, we
discuss how to apply the concept of Emotional Artificial Intelligence
to TR by monitoring patients’ facial expressions during motor rehabili-
tation exercises. Thus, assessing their emotional (and cognitive) state is
possible, also paving the way for researching the correlation between
motor and cognitive outcomes. Some evidence of such a correlation
has already been found, especially in stroke patients. Strengthening
cognitive function (e.g., through TR tools) can indeed improve motor
recovery, including upper limb function [7]. On the other hand, aerobic
exercises and physiotherapy, in general, can improve not only muscle
strength and function but also cognitive abilities in brain injury patients
and slow down the progression of neurodegeneration in dementia and
Parkinson’s disease. However, in this paper, we do not yet focus on
verifying this correlation, but rather on developing an AI-based Facial
Expression Recognition (FER) system capable of detecting facial expres-
sions, following Ekman’s model (i.e., sadness, fear, anger, happiness,
surprise and neutral), within video frames generated by an acquisition
device placed at the Edge (e.g., patient’s home), as shown by the
reference scenario in Fig. 1.
As mentioned, this is an application of Emotion AI, a branch of
Affective Computing (AC) which refers to artificial intelligence that de-
tects and interprets human emotional signals. This can be done through
various means, such as natural language processing and sentiment
analysis from text, voice analysis from audio, and analysis of facial
movements, gait, and physiological signals from video and images [8].
Specifically, AI-enabled Edge rehabilitation devices represent a new
frontier of Human-Computer Interaction in tele-medicine: they can
act as smart digital biomarkers sending quantifiable physiological and
behavioral patients’ data to the hospital Cloud, making near/real-time
assessments about the rehabilitation process, providing feedback to
both patient and clinician, thus enabling therapy optimization.
Currently, there are few research works in the literature regarding
the combination of healthcare and emotional AI [9,10]. Specifically,
the application of the latter in TR is very innovative and to the best
of our knowledge, we were the first to introduce this topic with our
preliminary study [11]. With this work, we want to extend it by making
a more comprehensive discussion and evaluation of the performance of
our FER pipeline.
In our reference scenario depicted in Fig. 1, we considered cooper-
ating Cloud and Edge layers in a Cloud/Edge Continuum environment.
The Cloud Layer is deployed in the hospital data center and provides a
set of on-demand TR services from basic data collection and storage
to advanced data analysis applications supporting doctors in patient
monitoring activities. The Edge layer is deployed remotely either at
the patient’s home or in a satellite clinic. It is responsible to collect
data about rehabilitation sessions and pre-process it to monitor the
patient and provide feedback. The collected patient data will be stored
in the Edge device only and, the results of the local data processing
will be sent to the hospital Cloud after applying anonymization and/or
pseudonymization techniques to protect patients’ sensitive data from
potential unauthorized access. According to Appenzeller et al. data pro-
cessing errors can have a major impact on patient privacy, so technical
and organizational measures must be taken to ensure an appropriate
security level of the risk of data processing [12]. Pseudonymization,
in particular, is one of the main requirements of the General Data
Protection Regulation (GDPR) and is increasingly important in today’s
healthcare standards. This is a key requirement for ensuring high data
protection standards for sharing and secondary use of health data [13]
(e.g., composing clinical datasets for research purposes). However,
privacy and security aspects will be investigated in detail in future
works. Further benefits of Edge computing in TR include:
• Low latency: since data is processed in the same place where it is
collected, Edge computing is preferred for real-time applications
because it avoids network latency (due to data transfer) that
occurs when processing data on a remote Cloud.
• Cost-effectiveness: both patients and medical institutions do not
have to face substantial financial burdens thanks to the low cost
and low energy requirement of employed devices. In addition,
medical center saves money by avoiding hospitalization while
patients save money by avoiding moving to the hospital.
• Portability: Edge devices are portable and this allows patients
to perform the rehabilitation therapy where they deem most
appropriate (e.g., changing room).
• Privacy-preserving: Edge devices enable better management of
patient safety and privacy. These devices do not have to be
constantly connected over the Internet, so they are less vulnerable
to cyber attacks. In addition, depending on the adopted data
policies, the patient could decide which kind of data to send and
which not to send to the hospital Cloud. If the Edge device of a
patient is corrupted, no other patient’s data is in danger.
• Decentralization: adopting multiple Edge devices ensures that
there is no single point of failure in terms of storage of the
rehabilitation session data. If the storage of an Edge device is cor-
rupted, no other ones will be affected. Furthermore, the corrupted
device can be replaced without influencing the system’s working
conditions, i.e., the monitoring will be stopped for the specific
patient but will continue for others.
To assess our FER solution, particular attention was paid to the
choice of:
• The training datasets: we chose several datasets containing im-
ages depicting people with different facial expressions. The sam-
ples are heterogeneous in terms of gender, ethnicity, age, and
image features. In addition, we also constructed a mixed dataset
containing all samples from the considered datasets. Having sam-
ples from different sources helps to reduce the data bias that
might be present in each dataset.
• The ML models: We decided to deploy our system on low-resource
Edge devices. Therefore, we have chosen the best-performing
and lightweight ML models for all the pipeline steps involving
ML processes such as feature extraction and classification. For
feature extraction, we decided to use the MediaPipe library as
it is optimized to run on resource-constrained environments. For
classification, we conducted several experiments (Section 5) to
identify the most accurate and fast solution.
Biomedical Signal Processing and Control 92 (2024) 106096
3
D. Ciraolo et al.
• The set of features: the number and type of the selected features
have a great influence on the system performance in terms of
accuracy and processing time. In our pipeline, each frame is
processed to produce a set of face landmarks (i.e., face 3D points
that are red dots in Fig. 8), which represent a Face Mesh (FM).
From an FM (output in Fig. 3), a group of features (e.g., points,
edges, and angles) can be selected to produce a data structure
we refer to as Face Feature Map (FFM). Choosing the appropriate
FFM is crucial for the effectiveness of our approach. In fact, on the
one hand, including a high number of features could slow down
the system, on the other hand, a low number of features could
sacrifice accuracy. Thus, to find the best combination, in our
experiments, we have tested 4 FFMs generated from 3 different
FMs as depicted in Fig. 8.
Specifically, the main contributions of this paper include:
• Defining the Mixed Dataset: a heterogeneous facial expression
image dataset built from datasets available on the web. It includes
images with different colors and resolutions, depicting subjects
with a variety of genders, ethnicities, and ages captured in diverse
environments. Considering its heterogeneity, this dataset can be
used for different application scenarios, including TR. In our
experiments, we compared the performance of the classifiers as
the training dataset changed, including also this mixed dataset.
• Generalizing the FER pipeline proposed by Siam et al. [14]: our
FER pipeline extends it by generalizing several aspects. Siam et al.
created the Emotional FM composed of 27 face points and the
edges linking them, whereas, in our work, we changed it to a
generic FM which is a subset of landmarks extracted by Medi-
aPipe, with their linking edges. We extended their ‘‘Landmark
Analysis and Angular Encoding’’ block to the Face Feature Mapper
block which generates the wanted FM by selecting appropriate
landmarks and, based on that, performs a Feature Selection fol-
lowing the rules defined to construct the wanted FFM as output.
Thus, we also extended the concept of ‘‘feature map composed by
angular values’’, with the more generic FFM which might include
a set of edges, angles, and face points.
• Defining an Empirical FM as shown in Fig. 8(b): in our approach,
selecting the right pair of FM and FFM is crucial as the perfor-
mance of the system strongly depends on them. Therefore, we
decided to compare several solutions, including an empirically
constructed face mesh from which an FFM, consisting of its edges,
was generated.
• Defining the best classifier for our approach: In our experiments,
we wanted to find the classifier with the best performance in
terms of accuracy and processing time. We have tested different
classifiers, i.e., Support Vector Machine (SVM), Decision Tree
(DT), Random Forest (RF), and Multi-layer Perceptron (MLP),
identifying the best one and demonstrating the applicability of
our approach.
The remainder of this paper is organized as follows. The motivation
behind our research work is discussed in Section 2. An overview of
the most recent initiatives about TR, emotional AI, and FER systems
are discussed in Section 3. Materials and methods are discussed in Sec-
tion 4. Experiments performed considering different FFMs, classifiers
(i.e., SVM, DT, RF, and MLP), and datasets are discussed in Section 5.
A discussion on achieved results is provided in Section 6. Section 7
concludes the paper, providing light on the future.
2. Motivation
Patients with a neurological disease often are affected by both motor
and cognitive impairments, so they usually have to undergo a therapy
that involves both physical and mental strengthening, which can be
divided into:
• Motor rehabilitation: a healthcare process aimed at restoring or
improving an individual’s physical function, mobility, and general
well-being after impaired physical abilities due to a particular
medical condition. It generally involves interventions aimed at
strengthening muscles, coordination, and motor skills through
specific exercises.
• Cognitive rehabilitation: a therapeutic process focused on ad-
dressing and improving cognitive function in individuals who
have experienced cognitive impairments due to conditions such as
brain injuries, strokes, or neurodegenerative diseases. It involves
a combination of mental exercises and interventions aimed at
maximizing the cognitive independence and functional abilities
of the individual.
These activities, which today are well established in the in-person
rehabilitation practice, should be readjusted to fit the novel model
of remote rehabilitation treatments. The clinician will no longer be
able to provide physical support to the patient while performing mo-
tor rehabilitation exercises. Additionally, they cannot observe all the
nonverbal social cues, such as facial expressions or body language,
which are crucial for assessing the patient’s mental engagement in
the therapy [15]. Therefore, to ensure the effectiveness of treatment
and optimize therapy according to the patient’s needs, both motor
and cognitive activities must be monitored. To this end, appropriate
techniques need to be applied to enable clinicians to remotely assess
patients’ therapeutic progress (e.g., the goodness of the exercises per-
formed, any pain, and the patient’s emotional response). Specifically,
in this work, we aim to support cognitive rehabilitation by developing
a software system able to monitor the patient’s facial expressions (and
therefore their emotions), which can be seen as an indicator of their
cognitive status. When working with the cognitive model, the patient’s
emotion indicates to the therapist to slow down and begin to identify
and understand what is happening internally to the patient (what
thoughts are occurring and what beliefs are activated) [16]. Therefore,
this information can be useful for physicians to assess the patient’s
improvement and tailor treatment to their needs. Furthermore, from
a neuroscience perspective, the neural systems involved in various
cognitive processes overlap with those activated when processing dif-
ferent emotional stimuli. The ability to communicate and interpret
emotions and intentions through facial expressions requires the inter-
play of cognitive systems [17]. Additionally, the authors in [18] suggest
that motor, cognitive, and emotional systems are interconnected. By
monitoring and measuring the motor system with appropriate tools, it
becomes feasible to unveil affective and cognitive phenomena. Hence,
instead of limiting tracking to the user’s actions exclusively, it can be
beneficial to also observe the user’s emotional responses. This approach
is particularly valuable in computer systems in which patterns from
various modalities can be integrated to enrich the comprehension of
the user’s behavior and emotional state. Furthermore, different studies
have highlighted a correlation between motor exercises and cognitive
functions recovery: in [19] an association between increasing levels
of daily physical activity and improved attention cognitive function
has been found, suggesting that it may be a candidate intervention
for improving attention functioning after stroke. In [20] the authors
provide evidence that motor practice promotes functional recovery
of brain regions in which structural integrity is impaired by stroke.
Therefore, in future work, we also plan to explore the connection be-
tween cognitive and motor improvements by observing patients’ facial
expressions during motor rehabilitation exercises in a TR environment
employing our FER system.
3. Related work
In the last few years, research in the area of telemedicine systems
and TR has gotten an increasing interest, especially caused by the
restrictions imposed in the period of the SARS-CoV-2 pandemic. People
Biomedical Signal Processing and Control 92 (2024) 106096
4
D. Ciraolo et al.
who needed rehabilitation support could not meet physicians in person.
To resolve this issue, remote monitoring systems were studied and
applied to help both physicians and patients during rehabilitation
therapies. One example is the EPHoRt platform proposed by Pérez-
Medina et al. [21], presented as a reference architecture for TR systems.
In their work, they used a Kinect device to track patients’ movements
and to get a reference of the levels of pain that the individual suffers.
Indeed, one of the most important parts to consider in these platforms
is the implementation of techniques to assess the physical and cognitive
state of patients while performing rehabilitation exercises. In this vein,
our research moved towards AC systems capable of detecting human
emotions. As highlighted by Rivas et al. in [22]: affective-aware med-
ical informatics technologies can help in monitoring and personalizing
therapy to the patients’ needs. Furthermore, in the era of AI and remote
working places, a new paradigm was born, with the idea of assessing
workers’ well-being, which can be seen as the natural evolution of
AC: the so-called Emotional AI [23], which combines AC with Big
Data analytics and ML techniques. This can be done also thanks to
the rapidly expanding range of applications and devices for emotion-
sensing. But another aspect to take into consideration in TR platforms
is the affordability of such a system, especially for the patient’s side:
low-cost sensing and computing devices are preferable to compose
the Edge part of the system often hosted in the patient’s home. For
this reason, the focus of this paper is on developing a system based
on ML techniques, able to detect facial expressions in real-time and
to be deployed on cost-effective hardware (e.g., raspberry, common
webcams). Facial expressions are indeed, visible signs of the affective
and psychological state of a person, which is strictly correlated with the
individual’s well-being [24]. These systems are studied in the area of
FER in which usually a Convolutional Neural Network (CNN) [25,26] is
employed to detect from images, the facial expressions (anger, disgust,
happiness, sad, fear, and surprise) defined in the Ekman’s model [27].
Some attempts have been addressed also using transformers and the
attention mechanism [28,29]. In a lot of FER studies, all these deep
learning (DL) models achieved state-of-the-art recognition accuracy
exceeding previous results by a large margin, mainly thanks to the
increase of chip processing abilities, e.g., graphics processing unit
(GPU) [30]. For the same reason, however, these kinds of solutions
are often not suitable for real-time applications or to be employed on
Edge devices because of their network complexity and high hardware
resource requirements. Alternative solutions can be found in [14,31].
Specifically, Siam et al. [14] used the MediaPipe library to extract face
landmarks from the analyzed images and use them in their classifica-
tion pipeline. The advantage of this library is that it is designed to run
on smartphones or low-resource devices even without a dedicated GPU,
which makes it suitable for our case study. In addition, as the authors
point out, the novelty of their method lies in the analysis of key points
and the angular coding algorithm, which generates only 10 features.
Such low dimensionality allows ML-based approaches to achieve opti-
mal performance in a short time, with much lower computational costs
than DL-based approaches. Therefore, in this study we want to build
on their results by also considering their emotional FM and their FFM
(i.e., the set of 10 angles they used to discriminate expressions) in our
experiments, to make a comparison with other FFMs with a different
number and type of features. Although in this work we do not use
10-fold cross-validation, the same datasets and Super Resolution GAN
(SRGAN) (needed in their particular application context to increase the
resolution of the input images), we performed our experiments using
the same hyperparameters as their classifiers.
4. Material and method
This study aims to evaluate the efficacy of an FER system that
utilizes the face mesh generated by the MediaPipe library to train
an ML model. This model then, will be employed to classify facial
expressions within video frames captured during motor rehabilitation
exercises. Specifically, we want to integrate it within a Cloud-Edge tele-
rehabilitation ecosystem, in which the hospital plays the role of Cloud
system while low-resource IoMT devices are deployed as monitoring
systems within the Edge layer (e.g., patients’ homes or satellite clinics).
Fig. 1 shows our reference scenario. FER systems usually rely on CNNs
which are computationally intensive models, require a lot of memory,
and their training and inference times can be very high (depending
on the model architecture), especially when they are not executed
on specialized hardware (e.g., GPUs). In our reference scenario, we
want to deploy the FER system at the Edge. Therefore, to overcome
the limitations imposed by low hardware resources, we chose to use
MediaPipe instead of CNNs. This library is, optimized to run smoothly
and in real-time even in environments with limited resources, and is
employed in our system to enable fast feature extraction. Furthermore,
the inference process of the whole pipeline must be as fast as possi-
ble to analyze video frames without causing significant drops in the
acquisition device’s frame rate. In this study, we want to find the
fastest and most accurate solution (i.e., a combination of FFM and
classifier), while in future work, we want to investigate its performance
on a real Edge device. To conduct our experiments, we trained the
classifiers using different datasets. After this pre-training process, in a
production environment, we can further improve the performance of
our method using a continuous learning approach. This can be done
with various techniques. One approach is to train the model in the
Cloud using anonymized data, and then transfer the model to Edge
devices. Alternatively, the model can be trained directly on the Edge,
depending on the performance of the remote devices. Another option
is to utilize federated learning techniques that leverage the presented
distributed infrastructure. In this section we introduce the considered
datasets (Section 4.1), the MediaPipe library (Section 4.2) and the
proposed approach (Section 4.3), describing in details the landmark
extraction and feature selection steps of our pipeline (Section 4.4) as
well as the considered classifiers (Section 4.5).
4.1. Datasets
To train our facial expression recognition pipeline, we searched for
publicly available datasets containing image samples of the six basic
facial expressions (i.e., our system’s classes): surprise, fear, disgust,
anger, happiness, and sadness. We chose images that were as heteroge-
neous as possible in terms of ethnicity, age, gender, environment, head
position, and finally also in terms of image size and color to evaluate
the applicability and resilience of our system to variation in patients’
video frames. The most used datasets in the literature, e.g., CK+, JAFFE,
and RAF-DB, are available only upon explicit request to their owners,
so to overcome this limitation it was preferred to select open-source
datasets from Kaggle and GitHub. Specifically, we adopted FER2013,
CK+(Small), AffectNet(HQ) and AffectNet(Scaled). Table 1 summarizes
the main characteristics of the considered datasets and how to access
them. Fig. 2 shows the number of image samples contained inside the
datasets for each facial expression.
In the following, we describe each considered dataset. FER2013
[32] is a challenging dataset available on Kaggle and was first intro-
duced in the International Conference on Machine Learning (ICML)
2013 workshop on ‘‘Challenges in Representation Learning’’. The com-
petitors had to design a system able to recognize the emotion expressed
inside human face images. The dataset is composed of images obtained
through a search with Google API for keywords matching different
facial expressions and mixed with words about ethnicity, gender, and
age. The approved images were then cropped, resized to 48 × 48, and
converted to grayscale. In total, the dataset contains 35 887 images
distributed among different facial expressions as depicted in Fig. 2(a).
As we can observe, the peculiarity of this dataset is the high unbalance-
ment of the samples per class which leads, as observed by Goodfellow,
to a human accuracy of about 65 ± 5% and a 60% accuracy for a base
CNN model.
Biomedical Signal Processing and Control 92 (2024) 106096
5
D. Ciraolo et al.
Table 1
Datasets’ features.
Dataset
Samples
Source
Expressions
Access
FER2013
35,887
Web
6 + neutral
https://www.kaggle.com/datasets/msambare/fer2013
CK+ (Small)
920
Lab
7 + neutral
https://github.com/spenceryee/CS229/tree/master
AffectNet (HQ)
31,002
Web
7 + neutral
https://www.kaggle.com/datasets/tom99763/affectnethq
AffectNet (Scaled)
35,187
Web
7 + neutral
https://www.kaggle.com/datasets/arafatshovon/affectnet
Fig. 2. Distributions of dataset samples among facial expressions.
CK+(Small) derives from the original Extended CohnKanade (CK+)
[33]. The CK+ is a widely used dataset for FER systems evaluation
and it is composed of 593 video sequences of the facial behaviors of
123 participants with different ethnicities and ages between 18 and
50 years old. The peak frames of these sequences were then extracted
and labeled with one of the basic facial expressions. However, in
this reduced version there are only 920 images in PNG format, with
640 × 490 and 720 × 480 resolutions whose distribution classes are
depicted in Fig. 2(b). As we can see, the dataset is highly unbalanced
and contains the additional ‘‘contempt’’ class which will be ignored in
the experiments.
AffectNet(HQ) and AffectNet(Scaled) are two datasets available
on Kaggle and derive from the original dataset proposed by Mallahos-
seini et al. in [34]. The latter is composed of 1 million images obtained
from the Internet by querying different search engines with emotion-
related keywords. However, these two datasets contain a much lower
number of samples: the first one comprises 31 003 jpeg files with high
quality, different resolutions, and a total size of 8.12 GB. The second
one contains 35 187 jpeg files, some of which are the same as the
previous dataset, but compressed and with half the resolution, leading
to a total size of only 1.48 GB. The label’s distribution of the two
datasets is shown respectively in Figs. 2(c) and 2(d). As we can see,
the scaled dataset has also a more balanced distribution. Moreover, the
class ‘‘contempt’’ will be ignored in the experiments, just like for the
CK+(Small) dataset.
4.2. MediaPipe
Several efforts have been made in the literature to detect facial
expressions using ML algorithms. Typically, these solutions rely on a
CNN with different combinations of layers to detect faces and synthe-
size relevant features from the input image matrices [30]. Although
consolidated as methods to perform computer vision tasks, they are
usually heavy to train and far from real-time inference time, principally
due to their architecture complexity. In this landscape of solutions,
one among the others emerged as a suite of libraries for processing
perceptual inputs, balancing both resource usage and results quality:
MediaPipe [35]. It contains different modules to perform a variety
of tasks related to human body pose estimation. Specifically, in the
proposed approach, we used the Face Mesh (FM) module, which can
infer a 3D mesh representation of a human face with real-time speed
on mobile CPUs or GPUs (depending on the device) and high prediction
accuracy [36]. The speed of this model is determined by the rapid
processing capability of the BlazeFace module, which is based on the
MobileNetV2 and SSD architectures [37], and in the ‘‘pre-processing’’
phase it is used to detect the presence of a face in the input image.
Biomedical Signal Processing and Control 92 (2024) 106096
6
D. Ciraolo et al.
Fig. 3. Architecture of the MediaPipe Face Mesh prediction module.
Fig. 4. Comparison between the architectures of CNN and our approach.
Once a face is detected, the module encloses it in a frame, detects its
principal key points, and rotates it to create a 256 × 256 cropped RGB
image. This is the input of the face mesh prediction Residual Neural
Network (RNN) which can infer a total of 468 3D landmarks. This
process requires roughly less than 8 ms (depending on the device)
to be completed, with low resource usage and high precision. This
makes MediaPipe suitable for low-resource capacity and cheap single-
board computer (SBC) devices that can be deployed at the Edge,
hence enabling TR scenarios. In our approach, we also enabled the
‘‘refine_landmarks’’ parameter, allowing MediaPipe to use the Attention
Mesh [38], which adds to the mentioned RNN three more specialized
sub-models: two for the eyes and one for the mouth key points. This
more complex network predicts 478 3D landmarks in total, with im-
proved precision in the areas covered by the sub-models, allowing for
better eyes and mouth tracking. Fig. 3 shows the architecture of the
MediaPipe FM prediction module.
4.3. Proposed approach
To develop our AI-based FER pipeline for recognizing patients’
emotions, we drew inspiration from the work presented by Siam et al.
in [14], in which the MediaPipe library is used to extract features for
emotion classification. Specifically, in our scenario, patients will be
monitored by a cost-effective and low-resource IoMT acquisition device
placed in their rehabilitation location (e.g., their home or a partner
clinic). In such resource-constrained IoMT devices, it is important to
optimize software implementations, and for this reason, we decided
to use MediaPipe. Thanks to the efficiency of its FM module, our
pipeline can work in real-time even with low hardware resources,
outperforming (in this application domain) other models based on
heavy CNN architectures. Fig. 4 shows a comparison between a CNN
and our approach.
In the former, the convolutional and pooling layers compose the
feature extraction network, that generates an array of features (which
Biomedical Signal Processing and Control 92 (2024) 106096
7
D. Ciraolo et al.
Fig. 5. Architecture of the proposed FER pipeline.
they have learned to produce in the training process). These features
are then fed to the fully connected layer (which is an MLP) to perform
the classification. Instead, in the latter, the MediaPipe library and
Face Feature Mapper module perform the feature extraction step (as
explained in Section 4.4). This generates an FFM, which is a selection of
features derived from the face mesh recognized within the input image.
The classifier then uses the FFM to detect the facial expression. Fig. 5
describes our approach more in detail.
The input image or video frame is processed by the MediaPipe Face
Mesh module that is responsible for extracting face landmarks. This
module can work with virtually any kind of input source, while still
producing consistent results, which are normalized based on the source
image dimensions. These face points are the input of the Face Feature
Mapper block in which another normalization step is performed, using
a predefined face point as a reference for all the samples. In our exper-
iments, we used the face landmark number 0 (based on MediaPipe’s
indexing for the landmarks) that identifies the center of Cupid’s bow
(on the upper lip). From all the coordinates of the face points we
subtract the coordinates of the reference point and then divide each
coordinate by the maximum value taken on its axis. In this way we re-
align the 3D coordinates of each face point in the range (−1, 1), using
the reference landmark as the origin point of the FM axes. Fig. 6 shows
four different samples, each with its corresponding face mesh contours
before and after normalization, taken from the considered datasets.
After that, we perform the feature selection step, which can be
based on different FMs. The resulting data structure, called FFM is
then given as input to the classifier to perform the classification. The
challenging part of this approach is to identify the best FFM, which
is a set of features (i.e., face points, arcs, or angles), that can help
the model better discriminate among the different emotions. Finally,
for the classification, we tested our approach with four alternative ML
models: SVM, RF, DT, and MLP. In addition, according to differences
in the available datasets, we decided to define six classes to distinguish
among the facial expressions, i.e., sad, angry, neutral, fear, happy, and
surprise.
4.4. Feature extraction
In our approach, the feature extraction process can be divided into
landmark extraction and feature selection steps. At first, the input
samples are processed by the MediaPipe Face Mesh module (Fig. 5)
to extract the full set of landmarks. Each image is analyzed, producing
a set of 478 3D face points (red dots in Fig. 8) representing the 3D
face mesh detected within the sample. Additionally, MediaPipe allows
specifying the ‘‘min_detection_confidence’’ (from 0 to 1) representing
the minimum level of confidence for the inferred points. This allows
for increasing the quality of the extracted features but at the expense
of discarding a higher number of samples. To perform our experiments,
we set this parameter to 0.8 (80% of confidence), thus ignoring all the
images for which the prediction confidence value was lower than this
threshold. Therefore, the final sample distributions are different from
the ones depicted in Fig. 2 and are shown in Fig. 7(a, b, c and d).
The next step in the pipeline is the feature selection, which is
schematized by the FFM block (Fig. 5). During this stage, only a subset
of landmarks is chosen to represent an FM (as shown in Fig. 8). This
FM is a collection of facial points and arcs that are used to generate
the FFM (the set of features for classification). This data structure may
include the length of one or more edges, the width of certain angles
between arcs, or a selection of landmark coordinates. To evaluate the
differences in terms of accuracy and, training and inference times as
the number and type of features change, we decided to define and test
four different FFMs in our experiments:
1. Siam’s feature map: it is a map based on the Emotional FM
(see Fig. 8(c)) presented in [14]. The mesh is composed of 27
key landmarks whose locations are based on the Facial Action
Coding System (FACS) [39] and 38 edges connecting them. In
particular, the authors used 10 angular values as features to mea-
sure the deformation of the face mesh. These values reflect the
contraction and relaxation of facial muscles, which can be used
to identify facial expressions. We used this FFM to evaluate its
performance in our experiments and as a basis for comparing the
results of other FFMs containing a larger number and different
types of features.
2. Siam’s feature map (modified): it is based on the previous
FM but in this case, besides angles amplitude, we considered
also the length of the edges for a total of 48 features. With this
map, we want to understand whether the addition of mesh edge
length to the feature collection can strengthen the classifier’s
discrimination capabilities, given the same FM.
3. Full feature map: contains the length of the edges defined in-
side the ‘‘FACEMESH_TESSELATION’’ constant of the MediaPipe
library. 2556 features in total were derived from the Full FM
(Fig. 8(a)) connecting all the detected 478 face landmarks. This
map is the most complex of the four considered ones and it will
give an idea of the possible drawbacks, in terms of processing
times, when considering a larger number of features.
4. Empiric feature map: it is based on an FM empirically con-
structed by selecting specific facial points (Tables 2–4) that
looked more relevant for facial expressions identification. This
map contains the length of some of the edges (blue lines in
Fig. 8(b)) connecting these landmarks, generating 64 features.
Biomedical Signal Processing and Control 92 (2024) 106096
8
D. Ciraolo et al.
Fig. 6. Examples of landmark normalization.
The main difference between these FFMs is, of course, the number
of features: a higher number of features, as in the Full FM case, could
represent more information but could also bring unwanted redundancy
and higher processing times. Furthermore, different types of features
could carry a diverse load of information. For instance, mouth opening
is one of the most evident aspects to consider for facial expression
discrimination. In the Empiric feature map, we considered both vertical
and horizontal mouth opening lengths, while Siam et al. considered two
angles only: one for the right corner and one for the upper corner of the
mouth. At the same time by considering the arcs of Siam’s face mesh,
we built also the ‘‘modified’’ map, which can be compared with the
others to understand, for instance, whether it is better to use only a
type of features or a combination of them.
4.5. Considered classifiers
The last step in our pipeline is classification. In our experiments
we decided to test four of the most used supervised ML models, ca-
pable of solving both linear and nonlinear problems, to evaluate their
performance in terms of accuracy and, training and inference times:
1. Support Vector Machine (SVM): it is one of the oldest models
in the ML field and it is based on a simple concept: generating a
line or in general, a hyperplane that separates the samples in the
different classes. It works well on binary classification tasks, but
it can be also used for multi-class discrimination. The downside
of this model is that as the number of features and data increase,
both the training time and inference time become longer.
2. Decision Tree (DT): it is an ML model in which the classification
task is divided into a set of decisions based on the values of
the features. Each node of the tree represents a split point in
which the decision can flow to the next node depending on the
combination of the features and some thresholds. This process
proceeds until it arrives at a leaf which is the effective predicted
class for the analyzed sample.
3. Random Forest (RF): it is a widely used ML model for re-
gression and classification problems. It belongs to the ensemble
learning family of ML algorithms, which means it uses the
predictions of multiple models to produce a more accurate pre-
diction. It works by generating multiple decision trees based on
different subsets of samples and by taking the majority vote of
their classification as the effective predicted class of the model;
4. Multi-Layer Perceptron (MLP): it is an ML model based on the
idea of simulating the behavior of the brain and in particular
of a network of neurons. It comprises an input layer, an output
layer, and one or more hidden layers. Each layer is a set of
neurons and each neuron is connected to all the neurons of the
preceding and following layers. The input layer has as many
neurons as the number of features while the number of neurons
of the output layer is the same as the number of labels. The
number of neurons of each hidden layer instead can be chosen
arbitrarily. Depending on the number of layers and neurons,
this model could be the heaviest to train among the considered
classifiers.
5. Experiments
To evaluate the performance of the proposed approach, we per-
formed several experiments to observe the behavior of the system by
varying the training dataset, FFM, and classifier. For each series of
experiments, we took a dataset and performed the following steps:
Biomedical Signal Processing and Control 92 (2024) 106096
9
D. Ciraolo et al.
Fig. 7.
Final distributions of dataset samples after removing contempt and disgust labels, and after the feature extraction process.
1. Landmark extraction: the dataset was processed by the Medi-
aPipe suite of libraries to detect all the face landmarks of the
input images, obtaining 478 3D face points representing 1434
features (478*3) for each sample;
2. Feature selection: for each FFM, we selected the corresponding
set of features derived from the complete set of landmarks
extracted from MediaPipe. Each sample’s features were then
collected inside a CSV file (one for each FFM), representing the
actual dataset used to train the classifiers;
3. Classifiers training: each CSV dataset (based on a specific image
dataset and FFM) was then used to train different ML models,
i.e., SVM, RF, DT, and MLP, to evaluate their performance for
each case study and ultimately, to identify the best one.
All tests have been performed on a desktop Personal Computer (PC)
running Windows 10 and equipped with an Intel® Core™i9-12900k
processor (16 cores @ 4.5 GHz), 32 GB of DDR5 RAM, and a 1Tb
NVME SSD with a read speed of 2400 MBs, in which all datasets
were stored on. As for the software side, we used Python 3.10.0 as
the development environment. The OpenCV 4.7.0.68 library is used to
handle input images. MediaPipe 0.9.1.0 library is used as a block for
the face landmark extraction step. Scikit-learn 1.2.1 and Tensorflow
2.11.0 are used for implementing the classifiers and computing the
evaluation metrics. Imbalanced-learn 0.10.1 is used to balance the
datasets. Pandas, Math, Matplotlib NumpPy, OS, and CSV are used as
supplementary libraries.
Biomedical Signal Processing and Control 92 (2024) 106096
10
D. Ciraolo et al.
Fig. 8. Face meshes (blue lines with their linked red dots).
5.1. Preparation
In our experiments, we decided to exclude the ‘‘contempt’’ class,
which is not present in the FER2013 dataset (Fig. 2(a)), and the ‘‘dis-
gust’’ class due to low sample count in most of the datasets. Moreover,
we created the Mixed Dataset by combining all samples from the four
datasets we considered. This approach allows us to test our classifier
also on a dataset that mitigates potential data bias, as it incorporates
samples from various sources. Relying solely on a single dataset with
samples generated by the same input device or collected through the
same approach might hide data bias, which can negatively impact the
classifier’s accuracy. In this way we can have higher data heterogeneity
and simulate domain shift (e.g., changes in the acquisition device or
environment) during the training phase, thus enhancing the system’s
generalization capabilities. Consequently, our system becomes better
suited for deployment in diverse settings, such as patient homes and
satellite clinics, without the need to restrict it to a particular acqui-
sition device or environment. However, during the dataset generation
process, we found some overlaps in the AffectNet datasets, where some
samples represented the same image (with the same file name) but
with different resolutions. This resulted in fewer samples than expected,
leading to the sample distribution depicted in Fig. 7(e).
In addition, before training the classifiers, each dataset was bal-
anced by using a RandomUnderSampler (with a fixed random seed
of 42), thus taking 𝑁random samples for each class, where 𝑁cor-
responds to the sample count of the class with fewer samples. Fur-
thermore, each dataset was divided into a training set, composed of
75% of the samples, and a testing set, with the remaining 25%. The
distribution of samples for each dataset is presented in Table 5. The
table shows the number of samples in the original dataset (N◦orig.),
after pre-processing (N◦full), and after the balancing step (N◦bal.).
It also highlights the number of samples of the training and testing
partitions (N◦bal. train and N◦bal. test), as well as the number of
samples per label (N◦per label).
To limit the number of tests and to make a more accurate compar-
ison with the experiments of Siam et al. [14], we decided to fix some
hyperparameters for the selected classifiers, using the same values they
have adopted and that are reported in Table 6. In this way, we were
able to compare the performance of our FFMs with the one discussed
in their paper. For the MLP case, we decided to use a hidden layer
with the number of neurons equal to 80% of the number of features,
as is common practice in the literature for this type of model (when
hyperparameter optimization procedures are not performed). The only
exception was for the Siam FFM, in which we used 2 hidden layers with
28 neurons each, as the authors did in their paper. This was done for
two main reasons: firstly, when we applied the same rule to their facial
feature map, we obtained a model architecture with only one hidden
layer and 8 neurons, which resulted in poor performance (probably
caused by the low number of neurons); secondly, we chose to keep
the model architecture of their experiments to allow more accurate
comparison with their work.
5.2. Results
For each set of experiments, we took a dataset, extracted the fea-
tures for each of the four FFMs, and then tested all the classifiers
on each FFM. After that, to show the results we built five tables
containing the results in terms of accuracy (Acc.), precision (Prec.),
Biomedical Signal Processing and Control 92 (2024) 106096
11
D. Ciraolo et al.
Fig. 9. Confusion matrices for the SVM (Mixed Dataset).
Fig. 10. Confusion matrices for the RF (Mixed Dataset).
recall (Rec.), F1-score (F1), training time (Tra. time), and inference
time (Inf. time). The times are relative to the training and test processes
of each dataset divided by the number of samples contained in the
respective training and test sets (to get an idea of the processing
times for the single instance). As an example, considering that the
training time in the case of Mixed Dataset, Full face mesh, and SVM
is about 529.4s we calculated the training time per single instance as
529, 400 ms ÷ 25, 497 𝑠𝑎𝑚𝑝𝑙𝑒𝑠= 20.76 ms. In addition, all the processing
time values are rounded to the second decimal place. The results of
these experiments provide a valuable comparison of the accuracy and
speed performance of the different combinations of datasets, FFMs,
and classifiers. The resulting tables and charts are then discussed in
Biomedical Signal Processing and Control 92 (2024) 106096
12
D. Ciraolo et al.
Table 2
List of edges composing the Empiric face mesh (1) (Left and Right are referred to
viewer perspective).
Edge
Description
Connected MediaPipe landmarks IDs
1
Mouth Upper Lip Outer 0
(61, 40)
2
Mouth Upper Lip Outer 1
(40, 0)
3
Mouth Upper Lip Outer 2
(0, 270)
4
Mouth Upper Lip Outer 3
(270, 291)
5
Mouth Upper Lip Inner 0
(78, 80)
6
Mouth Upper Lip Inner 1
(80, 13)
7
Mouth Upper Lip Inner 2
(13, 311)
8
Mouth Upper Lip Inner 3
(311, 308)
9
Mouth Lower Lip Outer 0
(61, 91)
10
Mouth Lower Lip Outer 1
(91, 17)
11
Mouth Lower Lip Outer 2
(17, 321)
12
Mouth Lower Lip Outer 3
(321, 291)
13
Mouth Lower Lip Inner 0
(78, 88)
14
Mouth Lower Lip Inner 1
(88, 14)
15
Mouth Lower Lip Inner 2
(14, 402)
16
Mouth Lower Lip Inner 3
(402, 308)
17
Around Mouth Left 0
(49, 206)
18
Around Mouth Left 1
(206, 216)
19
Around Mouth Left 2
(216, 212)
20
Around Mouth Left 3
(212, 204)
21
Around Mouth Left 4
(204, 200)
22
Around Mouth Right 0
(279, 426)
23
Around Mouth Right 1
(426, 436)
24
Around Mouth Right 2
(436, 432)
25
Around Mouth Right 3
(432, 424)
26
Around Mouth Right 4
(424, 200)
27
Around Upper Left Eye 0
(147, 70)
28
Around Upper Left Eye 1
(70, 63)
29
Around Upper Left Eye 2
(63, 105)
Table 3
List of edges composing the Empiric face mesh (2) (Left and Right are referred to
viewer perspective).
Edge
Description
Connected MediaPipe landmarks IDs
30
Around Upper Left Eye 3
(105, 66)
31
Around Upper Left Eye 4
(66, 107)
32
Around Lower Left Eye 0
(143, 117)
33
Around Lower Left Eye 1
(117, 118)
34
Around Lower Left Eye 2
(118, 128)
35
Left Cheek 0
(118, 50)
36
Left Cheek 1
(50, 216)
37
Around Upper Right Eye 0
(336, 296)
38
Around Upper Right Eye 1
(296, 334)
39
Around Upper Right Eye 2
(334, 293)
40
Around Upper Right Eye 3
(293, 300)
41
Around Upper Right Eye 4
(300, 372)
42
Around Lower Right Eye 0
(357, 347)
43
Around Lower Right Eye 1
(347, 346)
44
Around Lower Right Eye 2
(346, 372)
45
Right Cheek 0
(347, 280)
46
Right Cheek 1
(280, 436)
47
Left Eyebrow to Upper Nose
(107, 6)
48
Right Eyebrow to Upper Nose
(336, 6)
49
Upper Nose To Nose Tip
(6, 4)
50
Left Eye 0
(33, 159)
51
Left Eye 1
(159, 133)
52
Left Eye 2
(33, 145)
53
Left Eye 3
(145, 133)
54
Right Eye 0
(362, 386)
55
Right Eye 1
(386, 263)
56
Right Eye 2
(362, 374)
57
Right Eye 3
(374, 263)
58
Vertical Mouth Opening
(13, 14)
Section 6 to compare the classifiers’ performance and to identify the
best solutions that, in future work, can be tested on a real Edge device.
In the following, we present the results of the performed experiments.
FER2013. The first round of experiments was performed on the
FER2013 dataset obtaining the results in Table 7. As can be observed,
in this case, the best two classifiers in terms of accuracy are the SVM
Table 4
List of edges composing the Empiric face mesh (3) (Left and Right are referred to
viewer perspective).
59
Horizontal Mouth Opening
(61, 291)
60
Left Eye Opening
(159, 145)
61
Right Eye Opening
(386, 374)
62
Horizontal Eyebrow Distance
(55, 285)
63
Left Cheekbone to Mouth Left Bound
(118, 61)
64
Right Cheekbone to Mouth Right Bound
(347, 291)
and RF, with the first one performing better with the first two feature
maps. For the training time, the best classifier between these two is the
SVM but at the same time, the RF is faster in the inference step.
CK+(Small). The second round of experiments was performed on
the CK+(Small) dataset obtaining the results in Table 8. In this case,
the classifier with the best accuracy was the MLP in two cases out of
four and the SVM in the other 2 cases. Regarding the processing times,
the SVM beats the MLP in both the training (by a large margin) and
inference processes.
AffectNet(HQ). The third round of experiments was performed on
the AffectNet(HQ) dataset obtaining the results in Table 9. Even for
this dataset, the best accuracy is obtained for the SVM classifier while
the RF achieved the best balance between accuracy and inference time,
especially in the ‘‘Full’’ FM case where the inference time of the SVM
is more than 13 ms compared to the 0.11 ms of the RF and the training
time is near 10 ms that is almost double compared to the RF.
AffectNet(Scaled). The fourth round of experiments was performed
on the AffectNet(Scaled) dataset obtaining the results in Table 10. In
this case, the SVM classifier is still the best in terms of accuracy, but
still, the RF and MLP are better in terms of inference time. It is worth
noticing that with the Empiric FM, the MLP classifier beats the RF with
slightly the same inference time, but besides that, the RF is still the
classifier with a more balanced performance.
Mixed Dataset: The last round of experiments was performed on the
Mixed Dataset obtaining the results in Table 11. This dataset is the third
one with the best results and confirms the considerations made before
with the other experiments: the SVM and RF are the best classifiers,
with the second one having better processing times.
Finally, in Figs. 9 and 10 we show the confusion matrices based
on the experiments carried out on the Mixed Dataset, which somewhat
summarizes the characteristics of all the considered datasets, for all the
FFMs in the SVM and RF cases, which achieved the best performance
overall.
6. Discussion
From the performed experiments, we can assert that the SVM clas-
sifier achieved the best overall accuracy but given the particular appli-
cation of our approach (real-time detection), we are also interested in
evaluating the classifier with the best inference time. In fact, taking into
consideration the results of the Mixed Dataset experiments (Table 11)
we can see that, for the ‘‘Full’’ FM case, although we obtained an accu-
racy of about 57%, the SVM has the worst processing times among the
considered classifiers, reaching more than 25 ms for the inference step.
This trend is confirmed also in the experiments performed on the Affect-
Net(HQ) and AffectNet(Scaled), this is probably due to the combination
of a high number of features (2556) and the higher number of samples
(compared to the other datasets). This pattern is not verified instead for
the RF classifier which is the second-best model in terms of accuracy
and it has a more balanced trade-off between accuracy and processing
times. In most cases the accuracy is a little bit lower than the SVM
classifier but with the advantage of a higher inference speed. As for
the other classifiers, we can say that the MLP in most cases is closer to
the RF or even with slightly better accuracy but definitively with worse
processing times. The DT instead had no comparable performance with
any of the other models. It is also worth highlighting that we performed
Biomedical Signal Processing and Control 92 (2024) 106096
13
D. Ciraolo et al.
Table 5
Datasets’ number of samples after pre-processing and balancing.
Dataset
N◦orig.
N◦full
N◦bal.
N◦bal. train
N◦bal. test
N◦per label
FER2013
35,887
10,778
5094
3820
1274
849
CK+ (Small)
920
838
150
112
38
25
AffectNet (HQ)
31,002
23,900
18,960
14,220
4740
3160
AffectNet (Scaled)
35,187
24,191
23,430
17,572
5858
3905
Mixed Dataset
49,454
49,454
33,996
25,497
8499
5666
Table 6
List of hyperparameters used for the considered classifiers.
Classifier
Hyperparameters
SVM
C: 275, Gamma: ‘‘scale’’, Kernel: ‘‘rbf’’
DT
Criterion: ‘‘gini’’, min_samples_leaf: 1, ccp_alpha: 0,
min_samples_split: 2, random_state: 42
RF
n_estimators:79, Criterion: ‘‘entropy’’, random_state: 42
MLP
Activation: ‘‘relu’’, Solver: ‘‘adam’’
Table 7
Classifiers results for FER2013 dataset.
F. Map
Clsfr.
Acc.
Prec.
Rec.
F1
Tra. time
Inf. time
Full
SVM
0.532
0.531
0.532
0.531
2.17 ms
3.84 ms
Full
DT
0.408
0.413
0.408
0.410
1.93 ms
0.04 ms
Full
RF
0.525
0.521
0.525
0.521
4.37 ms
0.05 ms
Full
MLP
0.510
0.504
0.510
0.498
17.43 ms
0.15 ms
Empiric
SVM
0.526
0.525
0.526
0.525
0.15 ms
0.15 ms
Empiric
DT
0.421
0.419
0.421
0.419
0.05 ms
0.03 ms
Empiric
RF
0.515
0.510
0.515
0.510
0.73 ms
0.04 ms
Empiric
MLP
0.492
0.486
0.492
0.478
7.25 ms
0.09 ms
Siam
SVM
0.419
0.422
0.419
0.413
0.13 ms
0.15 ms
Siam
DT
0.355
0.353
0.355
0.354
0.01 ms
0.02 ms
Siam
RF
0.461
0.462
0.461
0.457
0.31 ms
0.04 ms
Siam
MLP
0.373
0.354
0.373
0.335
4.76 ms
0.09 ms
Siam Mod.
SVM
0.487
0.486
0.487
0.484
0.13 ms
0.15 ms
Siam Mod.
DT
0.386
0.386
0.386
0.386
0.04 ms
0.02 ms
Siam Mod.
RF
0.507
0.507
0.507
0.503
0.57 ms
0.03 ms
Siam Mod.
MLP
0.442
0.420
0.442
0.422
3.95 ms
0.08 ms
Table 8
Classifiers results for CK+(Small) dataset.
F. Map
Clsfr.
Acc.
Prec.
Rec.
F1
Tra. time
Inf. time
Full
SVM
0.842
0.864
0.842
0.844
0.29 ms
0.71 ms
Full
DT
0.631
0.634
0.631
0.628
0.74 ms
0.63 ms
Full
RF
0.842
0.878
0.842
0.843
2.14 ms
0.84 ms
Full
MLP
0.868
0.868
0.868
0.868
293.75 ms
2.84 ms
Empiric
SVM
0.763
0.767
0.763
0.752
0.23 ms
0.76 ms
Empiric
DT
0.631
0.638
0.631
0.618
0.23 ms
0.63 ms
Empiric
RF
0.815
0.817
0.815
0.815
0.91 ms
0.84 ms
Empiric
MLP
0.894
0.906
0.894
0.884
242.85 ms
2.28 ms
Siam
SVM
0.842
0.877
0.842
0.843
0.23 ms
0.68 ms
Siam
DT
0.763
0.808
0.763
0.771
0.20 ms
0.71 ms
Siam
RF
0.815
0.854
0.815
0.815
0.73 ms
0.97 ms
Siam
MLP
0.078
0.006
0.078
0.011
20.53 ms
2.31 ms
Siam Mod.
SVM
0.894
0.903
0.894
0.894
0.26 ms
0.71 ms
Siam Mod.
DT
0.815
0.831
0.815
0.812
0.31 ms
0.71 ms
Siam Mod.
RF
0.842
0.903
0.842
0.846
0.86 ms
0.71 ms
Siam Mod.
MLP
0.842
0.871
0.842
0.839
243.75 ms
1.86 ms
the experiments with fixed hyperparameters to limit the number of
tests and no optimizations were carried out for none of the classifiers.
Another important observation is that Siam’s feature map had worse
performance compared to the other maps. This is probably due to the
lower number of features. In fact, it was enough to add the edge length
of the FM (Fig. 8(c)) to the set of features, increasing them from 10
to 48 (in the ‘‘modified’’ FFM), to achieve an accuracy boost of more
than 10% for all the classifiers. Thus, we can say that increasing the
number of features somewhat improves the accuracy as can be seen
Table 9
Classifiers results for AffectNet(HQ) dataset.
F. Map
Clsfr.
Acc.
Prec.
Rec.
F1
Tra. time
Inf. time
Full
SVM
0.614
0.612
0.614
0.612
9.78 ms
13.18 ms
Full
DT
0.391
0.393
0.391
0.392
2.64 ms
0.01 ms
Full
RF
0.545
0.540
0.545
0.540
5.29 ms
0.04 ms
Full
MLP
0.542
0.564
0.542
0.534
7.82 ms
0.11 ms
Empiric
SVM
0.581
0.579
0.581
0.579
0.56 ms
0.54 ms
Empiric
DT
0.404
0.405
0.404
0.404
0.06 ms
0.01 ms
Empiric
RF
0.521
0.516
0.521
0.517
0.89 ms
0.02 ms
Empiric
MLP
0.526
0.519
0.526
0.519
1.94 ms
0.03 ms
Siam
SVM
0.458
0.451
0.458
0.453
0.48 ms
0.46 ms
Siam
DT
0.328
0.329
0.328
0.329
0.01 ms
0.01 ms
Siam
RF
0.429
0.422
0.429
0.425
0.38 ms
0.02 ms
Siam
MLP
0.394
0.387
0.394
387
2.93 ms
0.04 ms
Siam Mod.
SVM
0.537
0.534
0.537
0.534
0.45 ms
0.54 ms
Siam Mod.
DT
0.364
0.367
0.364
0.366
0.04 ms
0.01 ms
Siam Mod.
RF
0.516
0.508
0.516
0.508
0.67 ms
0.02 ms
Siam Mod.
MLP
0.491
0.483
0.491
0.476
2.70 ms
0.04 ms
Table 10
Classifiers results for AffectNet(Scaled) dataset.
F. Map
Clsfr.
Acc.
Prec.
Rec.
F1
Tra. time
Inf. time
Full
SVM
0.563
0.562
0.563
0.561
15.91 ms
31.90 ms
Full
DT
0.364
0.367
0.364
0.365
2.43 ms
0.02 ms
Full
RF
0.501
0.493
0.501
0.495
5.49 ms
0.03 ms
Full
MLP
0.509
0.526
0.509
0.500
9.11 ms
0.12 ms
Empiric
SVM
0.535
0.534
0.535
0.534
0.76 ms
0.70 ms
Empiric
DT
0.369
0.373
0.369
0.371
0.06 ms
0.01 ms
Empiric
RF
0.488
0.481
0.488
0.482
0.92 ms
0.02 ms
Empiric
MLP
0.508
0.505
0.508
0.503
1.95 ms
0.03 ms
Siam
SVM
0.431
0.428
0.431
0.428
0.63 ms
0.58 ms
Siam
DT
0.308
0.312
0.308
0.310
0.01 ms
0.01 ms
Siam
RF
0.407
0.403
0.407
0.405
0.40 ms
0.02 ms
Siam
MLP
0.367
0.359
0.367
358
2.25 ms
0.03 ms
Siam Mod.
SVM
0.505
0.503
0.505
0.503
0.61 ms
0.68 ms
Siam Mod.
DT
0.361
0.363
0.361
0.362
0.05 ms
0.01 ms
Siam Mod.
RF
0.479
0.470
0.479
0.471
0.72 ms
0.02 ms
Siam Mod.
MLP
0.472
0.470
0.472
0.469
1.89 ms
0.03 ms
also by the graphs in Fig. 11, which show the accuracy comparison of
the best classifiers, i.e., SVM and RF, for the four Face Feature Maps
considered in the experiments.
In these graphs, we can see that the increase from 64 (Empiric)
to 2556 (Full) features had a smaller accuracy improvement than the
increase from 10 (Siam) to 64 (Empiric) features, which confirms that
it is not just a matter of adding more features, but choosing significant
ones. In fact, with the Empiric face mesh (and its FFM) we wanted
to consider features that could vary a lot among the different facial
expressions. In contrast, the full face mesh contains redundant and
almost static edges which does not help discriminate among the classes.
Furthermore, considering the matrices in Figs. 9 and 10, we can see
that the best accuracy is achieved for the ‘‘happy’’ facial expression,
with 84% for the SVM and 83% for the RF, in the Full feature map
case. This map is also the one which discriminates better among the
classes, achieving roughly 50% of accuracy for each class in the SVM
case and a little less for the RF classifier, going to a low value of 37%
for the ‘‘sad’’ expression against the 50% of the SVM. At the same time,
however, this feature map is also the most computationally demanding
Biomedical Signal Processing and Control 92 (2024) 106096
14
D. Ciraolo et al.
Fig. 11. Accuracy comparison for the best classifiers.
Table 11
Classifiers results for the Mixed Dataset.
F. Map
Clsfr.
Acc.
Prec.
Rec.
F1
Tra. time
Inf. time
Full
SVM
0.569
0.565
0.569
0.566
20.76 ms
25.22 ms
Full
DT
0.377
0.378
0.377
0.377
2.93 ms
0.01 ms
Full
RF
0.522
0.515
0.522
0.516
5.73 ms
0.03 ms
Full
MLP
0.523
0.532
0.523
0.514
6.90 ms
0.10 ms
Empiric
SVM
0.548
0.544
0.548
0.545
1.24 ms
1.02 ms
Empiric
DT
0.385
0.385
0.385
0.385
0.06 ms
0.01 ms
Empiric
RF
0.511
0.504
0.511
0.505
0.96 ms
0.02 ms
Empiric
MLP
0.510
0.501
0.510
0.502
1.38 ms
0.03 ms
Siam
SVM
0.448
0.442
0.448
0.443
0.97 ms
0.85 ms
Siam
DT
0.330
0.333
0.330
0.331
0.01 ms
0.01 ms
Siam
RF
0.431
0.427
0.431
0.428
0.41 ms
0.02 ms
Siam
MLP
0.395
0.384
0.395
379
1.09 ms
0.03 ms
Siam Mod.
SVM
0.508
0.503
0.508
0.505
1.02 ms
1.03 ms
Siam Mod.
DT
0.369
0.370
0.369
0.369
0.05 ms
0.01 ms
Siam Mod.
RF
0.495
0.485
0.495
0.487
0.75 ms
0.02 ms
Siam Mod.
MLP
0.473
0.461
0.473
0.460
1.57 ms
0.03 ms
in the feature extraction phase because of the larger number of features.
In conclusion, the Full and Empiric feature maps are the ones achieving
the best accuracy, but for the particular application of our approach,
the latter might be preferable due to the lower number of features
that allow faster feature extraction time. For the same reason, the RF
classifier might be preferable compared to the SVM thanks to its higher
inference speed. Indeed, it is crucial to ensure as low as possible feature
extraction and inference times to avoid frame rate drops when our
system is deployed on real Edge devices.
7. Conclusion and future work
This work aimed to evaluate the performance of a real-time AI-based
pipeline, which leverages the landmarks extracted by the MediaPipe
Face Mesh module, to perform FER (or Emotion Detection) in the
context of TR. We started from the work of Siam et al. and we gen-
eralized it by defining the concepts of Face Mesh, Face Feature Map,
and Face Feature Mapper. In the experiments we evaluated different
combinations of FFMs, datasets, and classifiers; however, although the
processing performance is promising, we did not obtain a high enough
accuracy to deploy the presented approach in a real TR environment.
Nevertheless, we find these results very encouraging, considering also
that with more complex FFMs we obtained higher accuracy than with
the feature map of Siam et al. (on the considered datasets) and that
there may be other combinations of features that could provide even
better performance. Furthermore, we have seen that classifiers like SVM
and RF could be faster enough to provide real-time inference time,
further encouraging the study of this approach. Definitely, in the future,
we will perform experiments on a real Edge device (e.g., Raspberry)
to further verify the performance of our pipeline on low-cost IoMT
devices. Moreover, we also plan to explore privacy-related aspects and
as the target objective in future works, we will try to combine data
from motor rehabilitation and facial expression monitoring to assess
the correlation between them and to build useful tools for clinicians.
In addition, in future work, we could test new datasets (including the
most widely used ones in this field) and, to improve the performance of
our approach, we could apply hyperparameter optimization techniques
and explore new FM, FFM, and classifiers.
CRediT authorship contribution statement
Davide Ciraolo: Data curation, Software, Writing – original draft,
Conceptualization,
Methodology.
Maria
Fazio:
Conceptualization,
Methodology. Rocco Salvatore Calabrò: Conceptualization, Method-
ology,
Resources.
Massimo
Villari:
Conceptualization,
Method-
ology.
Antonio
Celesti:
Conceptualization,
Funding
acquisition,
Methodology, Supervision, Validation, Writing – review & editing.
Declaration of competing interest
The authors declare that they have no known competing financial
interests or personal relationships that could have appeared to
influence the work reported in this paper.
Data availability
Data will be made available on request.
Acknowledgments
This work has been partially supported by the Italian PRIN project
‘‘Tele-Rehabilitaion as a Service (TRaaS)’’ (project code 202294473C).
Davide Ciraolo is a Ph.D. student enrolled in the Italian National
PhD on Artificial Intelligence - Health and Life Sciences area, XXXVIII
cycle, coordinated by the Bio-Medical Campus University of Rome and
assigned to the headquarters of the University of Messina.
Biomedical Signal Processing and Control 92 (2024) 106096
15
D. Ciraolo et al.
References
[1] A. Celesti, F. Celesti, M. Fazio, M. Villari, Improving tele-rehabilitation therapy
through machine learning with a NoSQL graph DBMS approach, in: 2020 IEEE
Globecom Workshops, GC Wkshps 2020 - Proceedings, 2020.
[2] A. Celesti, F. Celesti, A. Galletta, M. Fazio, M. Villari, Improving machine
learning algorithm processing time in tele-rehabilization through a NoSQL graph
database approach: A preliminary study, in: Proceedings - IEEE Symposium on
Computers and Communications, Vol. 2020-July, 2020.
[3] R. Calabrò, A. Bramanti, M. Garzon, A. Celesti, M. Russo, S. Portaro, A. Naro,
A. Manuli, P. Tonin, P. Bramanti, Telerehabilitation in individuals with severe
acquired brain injury Rationale, study design, and methodology, Medicine (U.
S.) 97 (50) (2018).
[4] A. Celesti, V. Cimino, A. Naro, S. Portaro, M. Fazio, M. Villari, R. Calabró,
Recent considerations on gaming console based training for multiple sclerosis
rehabilitation, Med. Sci. (Basel Switz.) 10 (1) (2022).
[5] A. Celesti, M. Fazio, A. Ruggeri, F. Celesti, M. Villari, M. Bonanno, R. Cal-
abro, Adopting machine learning-based pose estimation as digital biomarker in
motor tele-rehabilitation, in: Proceedings - IEEE Symposium on Computers and
Communications, 2023.
[6] A. Celesti, G. Sannino, M. Bochicchio, M. Fazio, M. Villari, F. Celesti, M. Bo-
nanno, R. Calabrò, The tele-rehabilitaion as a service (TRaaS) project: Rationale,
study design, and methodology, in: Proceedings 2023 IEEE 19th International
Conference on e-Science, e-Science 2023, 2023.
[7] J. Lee, Y.-H. Kim, Does a cognitive network contribute to motor recovery after
ischemic stroke? Neurorehabilitation Neural Repair (2023) 15459683231177604.
[8] Emotional AI Lab, What is emotional AI?, https://emotionalai.org/so-what-is-
emotional-ai, 2023 (accessed 29.05.2023).
[9] Z. Zhou, M. Asghar, D. Nazir, K. Siddique, M. Shorfuzzaman, R. Mehmood, An
AI-empowered affect recognition model for healthcare and emotional well-being
using physiological signals, Cluster Comput. 26 (2) (2023) 1253–1266.
[10] P. Frank, M. Lu, E. Sasse, Educational and emotional needs of patients with
myelodysplastic syndromes: An AI analysis of multi-country social media, Adv.
Ther. 40 (1) (2023) 159–173.
[11] D.
Ciraolo,
A.
Celesti,
M.
Fazio,
M.
Bonanno,
M.
Villari,
R.S.
Calabrò,
Emotional artificial intelligence enabled facial expression recognition for tele-
rehabilitation: A preliminary study, in: 2023 IEEE Symposium on Computers
and Communications, ISCC, IEEE, 2023, pp. 1–6.
[12] A. Appenzeller, N. Terzer, E. Krempel, J. Beyerer, Towards private medical
data donations by using privacy preserving technologies, in: Proceedings of the
15th International Conference on PErvasive Technologies Related To Assistive
Environments, 2022, pp. 446–454.
[13] M. Pedrosa, A. Zúquete, C. Costa, A pseudonymisation protocol with implicit and
explicit consent routes for health records in federated ledgers, IEEE J. Biomed.
Health Inf. 25 (6) (2020) 2172–2183.
[14] A.I. Siam, N.F. Soliman, A.D. Algarni, F.E. Abd El-Samie, A. Sedik, B.Y. Ding,
Deploying machine learning techniques for human emotion detection, Intell.
Neurosci. 2022 (2022).
[15] D. Simonsen, R. Irani, K. Nasrollahi, J. Hansen, E.G. Spaich, T.B. Moeslund, O.K.
Andersen, Validation and test of a closed-loop tele-rehabilitation system based
on functional electrical stimulation and computer vision for analysing facial
expressions in stroke patients, in: Replace, Repair, Restore, Relieve–Bridging
Clinical and Engineering Solutions in Neurorehabilitation: Proceedings of the 2nd
International Conference on NeuroRehabilitation (ICNR2014), Aalborg, 24-26
June, 2014, Springer, 2014, pp. 741–750.
[16] C.E. Reilly, The role of emotion in cognitive therapy, cognitive therapists, and
supervision, Cogn. Behav. Pract. 7 (3) (2000) 343–345.
[17] K. Erickson, J. Schulkin, Facial expressions of emotion: A cognitive neuroscience
perspective, Brain Cogn. 52 (1) (2003) 52–60.
[18] C.L. Lisetti, D.J. Schiano, Automatic facial expression interpretation: Where
human-computer
interaction,
artificial
intelligence
and
cognitive
science
intersect, Pragmat. Cogn. 8 (1) (2000) 185–235.
[19] M. Veldsman, L. Churilov, E. Werden, Q. Li, T. Cumming, A. Brodtmann, Physical
activity after stroke is associated with increased interhemispheric connectivity of
the dorsal attention network, Neurorehabilitation Neural Repair 31 (2) (2017)
157–167.
[20] R.A. Bosnell, T. Kincses, C.J. Stagg, V. Tomassini, U. Kischka, S. Jbabdi,
M.W. Woolrich, J. Andersson, P.M. Matthews, H. Johansen-Berg, Motor practice
promotes increased activity in brain regions structurally disconnected after
subcortical stroke, Neurorehabilitation Neural Repair 25 (7) (2011) 607–616.
[21] J.-L. Pérez-Medina, K.B. Jimenes-Vargas, L. Leconte, S. Villarreal, Y. Ry-
barczyk,
J.
Vanderdonckt,
ePHoRt:
Towards
a
reference
architecture
for
tele-rehabilitation systems, IEEE Access 7 (2019) 97159–97176, http://dx.doi.
org/10.1109/ACCESS.2019.2927461.
[22] J.J. Rivas, F. Orihuela-Espina, L. Palafox, N. Bianchi-Berthouze, M.d.C. Lara,
J. Hernández-Franco, L.E. Sucar, Unobtrusive inference of affective states in
virtual rehabilitation from upper limb motions: A feasibility study, IEEE Trans.
Affect. Comput. 11 (3) (2020) 470–481, http://dx.doi.org/10.1109/TAFFC.2018.
2808295.
[23] P. Mantello, M.T. Ho, Emotional AI and the future of wellbeing in the post-
pandemic workplace, AI Soc. (2023) http://dx.doi.org/10.1007/s00146-023-
01639-8.
[24] F. Chiarugi, E. Christinaki, S. Colantonio, G. Coppini, P. Marraccini, M. Pedi-
aditis, O. Salvetti, M. Tsiknakis, A virtual individual’s model based on facial
expression analysis: A non-intrusive approach for wellbeing monitoring and
self-management, in: 13th IEEE International Conference on BioInformatics and
BioEngineering, IEEE, 2013, pp. 1–4.
[25] J. Cai, O. Chang, X.-L. Tang, C. Xue, C. Wei, Facial expression recognition
method based on sparse batch normalization CNN, in: 2018 37th Chinese Control
Conference, CCC, IEEE, 2018, pp. 9608–9613.
[26] A. Hassouneh, A. Mutawa, M. Murugappan, Development of a real-time emotion
recognition system using facial expressions and EEG based on machine learning
and deep neural network methods, Inform. Med. Unlocked 20 (2020) 100372.
[27] P. Ekman, W.V. Friesen, Constants across cultures in the face and emotion, J.
Personal. Soc. Psychol. 17 (2) (1971) 124.
[28] X. Chen, X. Zheng, K. Sun, W. Liu, Y. Zhang, Self-supervised vision transformer-
based few-shot learning for facial expression recognition, Inform. Sci. 634 (2023)
206–226, http://dx.doi.org/10.1016/j.ins.2023.03.105.
[29] S. Minaee, A. Abdolrashidi, Deep-emotion: Facial expression recognition using
attentional convolutional network, 2019, arXiv:1902.01019.
[30] S. Li, W. Deng, Deep facial expression recognition: A survey, IEEE Trans.
Affect. Comput. 13 (3) (2022) 1195–1215, http://dx.doi.org/10.1109/TAFFC.
2020.2981446.
[31] A. Farkhod, A.B. Abdusalomov, M. Mukhiddinov, Y.-I. Cho, Development of real-
time landmark-based emotion recognition CNN for masked faces, Sensors 22 (22)
(2022) 8704.
[32] I.J. Goodfellow, D. Erhan, P.L. Carrier, A. Courville, M. Mirza, B. Hamner, W.
Cukierski, Y. Tang, D. Thaler, D.-H. Lee, Y. Zhou, C. Ramaiah, F. Feng, R. Li,
X. Wang, D. Athanasakis, J. Shawe-Taylor, M. Milakov, J. Park, R. Ionescu, M.
Popescu, C. Grozea, J. Bergstra, J. Xie, L. Romaszko, B. Xu, Z. Chuang, Y. Bengio,
Challenges in Representation Learning: A Report on Three Machine Learning
Contests, Springer, 2013.
[33] P. Lucey, J.F. Cohn, T. Kanade, J. Saragih, Z. Ambadar, I. Matthews, The
extended cohn-kanade dataset (CK+): A complete dataset for action unit and
emotion-specified expression, in: 2010 IEEE Computer Society Conference on
Computer Vision and Pattern Recognition - Workshops, 2010, pp. 94–101.
[34] A. Mollahosseini, B. Hasani, M.H. Mahoor, AffectNet: A database for facial
expression, valence, and arousal computing in the wild, IEEE Trans. Affect.
Comput. 10 (1) (2019) 18–31.
[35] C. Lugaresi, J. Tang, H. Nash, C. McClanahan, E. Uboweja, M. Hays, F. Zhang,
C.-L. Chang, M. Yong, J. Lee, et al., Mediapipe: A framework for perceiving and
processing reality, in: Third Workshop on Computer Vision for AR/VR At IEEE
Computer Vision and Pattern Recognition, CVPR, Vol. 2019, 2019.
[36] Y. Kartynnik, A. Ablavatski, I. Grishchenko, M. Grundmann, Real-time facial
surface geometry from monocular video on mobile GPUs, in: CVPR Workshop
on Computer Vision for Augmented and Virtual Reality 2019, Long Beach, CA,
2019.
[37] V. Bazarevsky, Y. Kartynnik, A. Vakunov, K. Raveendran, M. Grundmann,
Blazeface: Sub-millisecond neural face detection on mobile gpus, 2019, arXiv
preprint arXiv:1907.05047.
[38] I. Grishchenko, A. Ablavatski, Y. Kartynnik, K. Raveendran, M. Grundmann,
Attention mesh: High-fidelity face mesh prediction in real-time, 2020, arXiv
preprint arXiv:2006.10962.
[39] P. Ekman, W.V. Friesen, Manual of the Facial Action Coding System (FACS),
Consulting Psychologists Press, 1978.
