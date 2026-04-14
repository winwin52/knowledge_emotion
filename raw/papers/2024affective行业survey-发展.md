Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
1
REVIEW ARTICLE
Affective Computing: Recent Advances, 
Challenges, and Future Trends
Guanxiong  Pei 1, Haiying  Li 2, Yandi  Lu 3, Yanlei  Wang4, Shizhen  Hua1,  
and Taihao  Li1*
1Research Center for Multi-Modal Intelligence, Research Institute of Artificial Intelligence, Zhejiang 
Lab, Hangzhou, China. 2National Science Library, Chinese Academy of Sciences, Beijing, China. 
3Center for Psychological Sciences, Zhejiang University, Hangzhou, China. 4De.InnoScience, Deloitte, 
Shanghai, China.
*Address correspondence to: lith@zhejianglab.com
Affective computing is a rapidly growing multidisciplinary field that encompasses computer science, 
engineering, psychology, neuroscience, and other related disciplines. Although the literature in this field 
has progressively grown and matured, the lack of a comprehensive bibliometric analysis limits the overall 
understanding of the theory, technical methods, and applications of affective computing. This review 
presents a quantitative analysis of 33,448 articles published in the period from 1997 to 2023, identifying 
challenges, calling attention to 10 technology trends, and outlining a blueprint for future applications. The 
findings reveal that the emerging forces represented by China and India are transforming the global research 
landscape in affective computing, injecting transformative power and fostering extensive collaborations, 
while emphasizing the need for more consensus regarding standard setting and ethical norms. The 5 core 
research themes identified via cluster analysis not only represent key areas of international interest but 
also indicate new research frontiers. Important trends in affective computing include the establishment 
of large-scale datasets, the use of both data and knowledge to drive innovation, fine-grained sentiment 
classification, and multimodal fusion, among others. Amid rapid iteration and technology upgrades, 
affective computing has great application prospects in fields such as brain–computer interfaces, empathic 
human–computer dialogue, assisted decision-making, and virtual reality.
Introduction
According to basic emotion theory, emotion is the grammar of 
social living and serves as a crucial means of exchanging infor-
mation, maintaining relationships, and communicating ideas 
between individuals. Moreover, it is a fundamental psychologi-
cal element that ensures basic human survival while shaping 
social habits and supporting advanced thinking [1,2]. Given its 
central role in numerous human intellectual activities such as 
perception, learning, decision-making, reasoning, and social-
izing, emotion is an important force driving the continuous 
and diverse prosperity of human civilization.
The importance of emotions to human beings can be sum-
marized in 5 crucial aspects. First, the survival function is a 
learned physiological response that allows individuals to adapt 
positively to their environment [3]. Emotions play a pivotal role 
in strengthening the capacity to adapt to the environment by 
regulating attention, memory, perception, and other cognitive 
processes. This ensures a greater chance of survival and develop-
ment during the evolutionary process. Second, the communica-
tion function highlights the importance of emotions for the 
accurate expression and understanding of human intentions [4]. 
The same words spoken with different emotions carry different 
connotations. Thus, emotions are inseparable from natural lan-
guage and are critical for semantic disambiguation. Third, emo-
tions have a decision-making function that manifests in both fast 
and slow modes of thinking. The commonly used unconscious 
“System 1” mainly relies on emotions and experiences, while the 
conscious “System 2” depends on rational deliberation [5]. 
Therefore, emotions are widely involved in higher-level thinking 
and decision-making processes that profoundly affect the results 
and efficiency of decisions. Fourth, emotions serve a motivational 
function in stimulating and sustaining individuals’ behaviors, 
thereby affecting the degree of resource input, behavioral persist­
ence, and evaluation of outcomes [6]. Finally, emotions perform 
a maintenance function as bonds between members of ethnic 
groups, families, social circles, social classes, and other groups. 
During human socialization, emotions serve as the core of low-
cost maintenance of social relations, forming potential social 
interaction contracts, and are closely tied to individual moral 
constraints and codes of conduct [7,8]. Hence, the nature and 
functions of emotions ensure that they are inseparable from 
human survival and development.
As the era of a human–machine symbiotic society approaches, 
endowing machines with emotional intelligence becomes increas-
ingly crucial. Emotional intelligence represents a fundamental 
Citation: Pei G, Li H, Lu Y, Wang Y, 
Hua S, Li T. Affective Computing: 
Recent Advances, Challenges, 
and Future Trends. Intell. Comput. 
2024;3:Article 0076. https://doi.
org/10.34133/icomputing.0076
Submitted 15 October 2023  
Accepted 6 December 2023  
Published 5 January 2024
Copyright © 2024 Guanxiong Pei et al. 
Exclusive licensee Zhejiang Lab. No 
claim to original U.S. Government 
Works. Distributed under a Creative 
Commons Attribution License 4.0 
(CC BY 4.0).
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
2
technology and an essential prerequisite for realizing naturalized 
and anthropomorphic human–computer interaction. It is of great 
value for opening up the era of intelligence and digitization. Picard 
is credited with being the first to propose a comprehensive defini-
tion of affective computing. In her 1997 book, Affective computing, 
she defined it as “computing that relates to, arises from, or delib-
erately influences emotions” [9]. The goal of affective computing 
is to create a computing system capable of perceiving, recognizing, 
and understanding human emotions and responding intelligently, 
sensitively, and naturally, thus making human–computer interac-
tion more natural. The epochal importance of affective computing 
lies in its impact on changing how emotions are perceived as 
abstractions within psychology, making it possible for emotions 
to be measured, computed, and machine-learned.
Affective computing encompasses various disciplines, includ-
ing computer science, engineering science, brain and psychologi-
cal science, and social sciences. Computer science and engineering 
science focus on providing various information technology tools 
and engineering capabilities to enable digital reconstruction and 
computational realization of emotion perception, recognition, 
understanding, and feedback, allowing machines to possess 
human-like emotional and cognitive functions. The psychological 
and consciousness aspects of the brain and psychological sciences 
provide theories on the basic definition of human emotions and 
the structure of related elements, laying the foundation for model-
ing emotion theories. Cognitive neuroscience, another branch 
of the brain and psychological sciences, examines the emotion-­
processing mechanism of the human brain and establishes a func-
tional network of psychological elements associated with emotions, 
providing important inspiration and strategic guidance for devel-
oping affective computing models. Social and medical sciences 
offer numerous opportunities for the application of affective com-
puting and serve as a resource for designing application scenarios 
for such technologies.
Research in affective computing
The research content of affective computing primarily covers 
5 aspects. The first aspect is the fundamental theory of emotion, 
which currently relies on the discrete emotion model and the 
dimensional emotion model from the field of psychology to 
define various types of emotions, ranging from basic to com-
pound. The second aspect involves collecting emotional signals, 
such as text, speech, facial expressions, gestures, and physio-
logical signals, to establish corresponding datasets. The third 
aspect is sentiment analysis, which utilizes machine-learning 
and deep-learning algorithms to model and identify emotional 
signals. The fourth aspect is multimodal fusion, which lever-
ages multimodal emotional features and fusion algorithms to 
enhance the accuracy of emotional classification. Finally, the 
fifth aspect is generating and expressing emotions, processes 
that enable robots to express emotional states through facial 
expressions, voice intonation, body movements, etc., and facili-
tates natural, anthropomorphic, and personified human–robot 
interaction. Figure 1 illustrates the specific content and devel-
opment status of these 5 aspects.
Basic theory of emotion
The field of affective psychology has numerous grounded theories 
of emotion and serves as an important source of inspiration for 
the development of computable emotion models. The discrete 
emotion model and the dimensional emotion model are the most 
commonly used theoretical models for artificial intelligence 
emotion modeling. The discrete emotion model categorizes emo-
tions individually rather than in correlated groups, as does Ekman’s 
basic emotion classification model, which is based on facial expres-
sion analysis [10] and comprises happiness, sadness, anger, disgust, 
surprise, fear, and contempt. Although the discrete emotion model 
is clearly defined, interpretable, easy to understand, and capable 
of semantically integrating vocabulary and concepts, it lacks gran-
ularity and provides a limited quantitative description of emotions. 
In contrast, dimensional affective models represent different emo-
tions through multidimensional vectors in affective space. Such 
models include the valence–arousal affective model [11] and the 
3-dimensional pleasure–arousal–dominance model [12,13]. These 
models are highly quantitative, abstract, and inductive and have 
continuous emotional value vectors. They are suitable for handling 
changes in emotional states over time but are not intuitively inter-
pretable; thus, it is difficult for machines to use them to develop 
rich coping strategies for emotional interactions. The selection of 
the model depends on the actual application tasks and scene 
requirements, as both discrete and dimensional emotion models 
have advantages and disadvantages.
Collection of emotional signals
To support data acquisition and the comparison of algorithms 
in affective computing, numerous open-source databases have 
been established. They contain datasets that can be categorized 
as textual, speech/audio, visual, physiological, or multimodal. 
The characteristics of these databases considerably impact model 
design and network architecture in affective computing.
Text-based resources on various communication carriers serve 
as massive datasets for emotional text mining [14]. Representative 
datasets include the internet movie database (IMDb) [15], the 
Stanford sentiment treebank, which contains sentences from 
movie reviews [16], and the Multi-Domain Sentiment Dataset, 
which contains Amazon.com product reviews [17]. Speech is 
another crucial modality for decoding emotions in human inter-
communication. Speech signals comprise both the emotional 
content of the speech and the emotional characteristics of the 
sound itself. Representative datasets include EmoDB [18], the 
SEMAINE database [19], and CSED [20]. Visual-emotional sig-
nals such as body movements and facial expressions are now more 
convenient to gather because of low-cost sensors such as cameras 
and camcorders, and they do not require direct contact with the 
user [21]. This field has vast amounts of data and many related 
research papers with considerable data collected directly from 
real-world scenarios, making it more conducive to grounded 
applications [22]. Representative datasets include the Expression-
in-the-Wild (ExpW) dataset [23], AffectNet [24], the Real-world 
Affective Faces Database (RAF-DB) [25], and SMIC, a database 
of spontaneous microexpressions [26].
Physiological data have an advantage over signal data such 
as text, speech, and facial expressions in that they can more 
directly, objectively, and accurately reflect an individual’s emo-
tional state while being less influenced by subjective conscious-
ness [27,28]. Consequently, physiological data have become a 
research hotspot in affective computing. Commonly used 
physiological data in this field include electroencephalograms 
(EEGs), skin electricity, cardiac electricity, electromyography 
(EMG), eye electricity, respiration, skin temperature, and 
blood volume pulse. However, obtaining physiological data 
requires the use of complex sensors. Thus, such data are expen-
sive and challenging to collect for use in practical applications. 
Consequently, the scale of physiological data used in laboratory 
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
3
research is generally small [29]. Representative datasets include 
the Database for Emotion Analysis using Physiological Signals 
(DEAP) [30], the Shanghai Jiao Tong University Emotion EEG 
Dataset (SEED) [31], and WESAD, a dataset for wearable stress 
and affect detection [32].
Sentiment analysis
Text analysis. This method focuses on extracting, analyzing, 
understanding, and generating emotional information in natu-
ral language. Early text affective recognition relied mainly on 
manually constructed affective dictionaries and rules for affec-
tive analysis. These methods judge sentiment polarity by 
matching sentiment words with grammatical rules in a text 
[33,34]. However, this approach is limited by emotional lexicon 
coverage and rules, making it challenging to support multido-
main sentiment analysis. With the advancement of machine 
learning, text emotion recognition methods based on statistical 
and machine learning algorithms have emerged. By training 
on large-scale text datasets, machine learning models can auto-
matically learn emotional expression and semantic features, 
enhancing the accuracy and generalization ability of sentiment 
classification [35,36]. In recent years, deep-learning technol-
ogy has considerably impacted text emotion recognition. 
Neural network-based models, such as recurrent neural net-
works (RNNs), convolutional neural networks (CNNs), long 
short-term memory (LSTM) networks, bidirectional encoder 
representation from transformers (BERT), and generative pre-
trained transformers (GPT), have been successful in various 
sentiment analysis tasks [37–39]. They can capture contextual 
information and semantic relationships to better understand 
and analyze sentiments.
Speech analysis. Speech emotion recognition is the process 
by which a computer automatically recognizes the emotional 
state signaled by speech. Speech contains emotional informa-
tion, such as speech rate and intonation, in addition to semantic 
information. Speech emotion analysis combines linguistic and 
acoustics-related technologies to analyze the syntax, semantics, 
and acoustic feature information related to the speaker’s emo-
tional state [40]. This analysis mainly revolves around rhyme, 
spectrum, and sound quality features. The numerous acoustic 
features related to affective states include fundamental fre-
quency, duration, speech rate, resonance peaks, pitch, mel-filter 
bank (MFB), log-frequency power coefficients (LFPC), linear 
predictive cepstral coefficients (LPCC), and mel-frequency ceps-
tral coefficients (MFCC) [41–43]. These features are represented 
as fixed dimensional feature vectors, with each component rep-
resenting the statistical value of each acoustic parameter, includ-
ing the mean, variance, maximum or minimum value, and range 
of variation. Recently, the ability of neural networks to extract 
suitable feature parameters has received increasing attention. 
Deep speech emotion features are learned from speech signals 
or spectrograms through tasks related to speech emotion rec-
ognition. Deep speech features learned from large-scale training 
data are widely used as speech emotion features in speech event 
detection and speech emotion recognition tasks, as in the 
VGGish and wav2vec projects [44,45], for example. In recent 
years, algorithms such as ConvNet learning [46], ConvNet-RNN 
[47], and adversarial learning [48] have considerably improved 
speech emotion recognition performance.
Visual analysis. Visual emotion recognition research primar-
ily focuses on facial expression recognition (FER) and emotional 
body gesture recognition. The conventional method involves 
Fig. 1. Research content of affective computing.
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
4
feature extraction followed by classification. Typically, hand-
crafted features for static image analysis include local binary pat-
tern (LBP), histogram of oriented gradients (HOG), local phase 
quantization (LPQ), and Gabor features [49,50]. Some scholars 
have proposed dynamic feature extraction methods, such as LBP 
on three orthogonal planes (LBP-TOP) [34]. Features are usually 
classified using pattern recognition classification methods such 
as K-nearest neighbors, support vector machines (SVMs), or 
multi-layer perceptrons (MLPs). Another approach is the feature 
learning approach, which combines the end-to-end training of 
feature representations and classifiers on a given task target, typi-
cally a combination of the entire connection layer and softmax. 
The feature-learning method employs features learned from big 
data through layer-by-layer feature transformation and can 
describe the intrinsic information of data better than handcrafted 
features. However, supervised training methods such as deep 
CNNs are not universal and rely on large amounts of sample data. 
Therefore, it is too early to abandon traditional feature-extraction 
methods. In visual emotion analysis, automatic training features 
can be extracted and integrated with traditional features, which 
may further improve system performance.
Physiological signal analysis. Physiological changes that 
occur with emotions, including brain electrical activity, heart 
rate changes, electrical skin response, muscle tension, and res-
piration rate, are supported by mainstream theories, such as 
the physiological theory of emotion [51] and Lange’s theory of 
emotion [52]. By detecting changes in these physiological sig-
nals, patterns associated with emotions can be recognized and 
then used to develop computer systems that can automatically 
recognize emotions. Physiological signals are more challenging 
to recognize than text, speech, and facial expression signals 
mentioned above, and they have unique properties. For exam-
ple, computing EEG data requires more complex preprocessing, 
including electrode position localization, bandpass filtering, 
reference conversion, segment analysis interception, artifact 
removal, and bad electrode interpolation. Researchers must 
have cross-field knowledge to apply machine learning or deep 
learning methods to recognize emotions from physiological 
signals [53].
Affective computing mainly employs peripheral nervous system 
(PNS) features, such as facial EMG, galvanic skin potential (GSP), 
photoplethysmography (PPG), heart rate variability (HRV), respi-
ratory rate, and electrocardiogram (ECG), whereas central nervous 
system (CNS) features include EEG, near-infrared, and brain-
imaging features. EEG features have dominated the studies pub-
lished on this topic. For instance, manual feature extraction involves 
multidimensional feature extraction from EEG signals in the time, 
frequency, time–frequency, and nonlinear domains for emotion 
recognition and classification. Recent studies have emphasized the 
integrity and relevance of these features. To construct functional 
brain networks, many studies have started defining a channel as a 
node and quantifying the relationship between individual nodes 
using phase synchronization, inter-correlation, and mutual infor-
mation, treating strength as the functional connectivity between 
the brain regions of the corresponding channel. Complex network 
measures, including efficiency, clustering coefficients, degree dis-
tribution, small-world features, and average shortest distance, are 
then used to extract functional brain network features. Since 2018, 
deep learning methods such as CNNs, RNNs, deep belief networks 
(DBNs), and stacked autoencoders (SAEs) [54–56] are being 
increasingly used for emotional computation of EEG data, general-
izing sentiment analysis to various physiological signals.
Multimodal fusion
Early affective computing primarily involved unimodal data 
analysis and emotion recognition, focusing on a single modality, 
such as text, speech, facial expression, body movement, or physi-
ological signals. However, this approach fails to conform to the 
human perception and expression patterns of emotions and has 
limitations in terms of the information obtained for emotion 
recognition [22]. Humans communicate their emotions through 
multiple channels, including language, tone of voice, facial 
expressions, and body movements. Textual, auditory, and visual 
information together provide more comprehensive emotional 
information than they do individually, just as the brain relies 
on multiple sensory input sources to validate events. Moreover, 
unimodal information is insufficient and can be easily affected 
by various external factors [21]. Emotional signals can be dis-
guised or affected by other signals from a single channel, for 
example, when facial expressions are obscured or when noise 
interferes with speech, resulting in a considerable reduction in 
emotion analysis performance. Multimodal emotion analysis 
considers the complementarity of emotion expression among 
modalities and is thus more robust and aligned with natural 
human behavior expression. Therefore, research on multimodal 
fusion of affective computation has received increasing atten-
tion. Multimodal fusion algorithms integrate information from 
different modalities into a stable multimodal representation, 
enabling comprehensive processing and coordinated optimiza-
tion to identify human emotions as accurately as possible [57]. 
Common multimodal fusion methods can be categorized into 
feature-, model-, and decision-layer-based fusion depending on 
the fusion stage [58].
Generation and expression of emotions
Affective computing enables machines to provide empathic 
feedback based on deep contextual understanding. Robots and 
other agents can deliver expressions and responses, conveying 
the emotional temperature to the user through facial expres-
sions, emotional text responses, and body movements [59,60] 
by building on the results of sentiment analysis and recogni-
tion. Emotional text generation and speech synthesis are the 
most-studied areas of research. Emotional text generation 
involves the automatic generation of emotional response con-
tent that matches the message of the dialogue and is consistent 
with the machine’s strategy, which is chosen according to the 
context [61]. For instance, a traffic enforcement robot may 
exhibit a fundamental difference in the language used for per-
suasion and the language used for enforcement, a difference 
that is crucial to obtaining effective practical traffic manage-
ment results. The goal of emotional text generation is for the 
model to generate text that conforms to a specified sentiment 
category, as expressed by emotion-related keywords or tech-
niques such as metaphors [62]. Pretrained models such as GPTs 
are increasingly being utilized as a base for emotionally con-
trollable text generation and achieving powerful results [63]. 
Responding to text content with emotional color is only the 
first step. The generated text needs to be expressed using a 
related emotional voice. Emotional coding information is inte-
grated into the speech synthesis model to make human–
machine dialogue less cold and mechanical, thereby allowing 
individuals to perceive “machine empathy” and feel warmth 
and affinity. Emotional speech synthesis uses a specific voice 
style and combines text content with emotional tags to provide 
a robot or agent with a voice that expresses a particular emotion 
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
5
[64]. This process inputs textual content and a specific voice 
style into a neural network that synthesizes an output voice in 
that style by utilizing the spectral, rhythmic, and linguistic 
features of human voices that express emotion.
Applications of affective computing
Affective computing is a technology that advances according 
to the actual needs of the industry, which drives progress and 
iteration. To build up reliability, general applications initially 
focused on recreation, leisure, or serving people with urgent 
needs, then gradually expanded to more fields, transforming 
the technology and contributing to productive endeavors. In 
2021, the value of affective computing reached $21.6 billion, 
and it is expected to double by 2024 [65,66]. As the industry 
grows, the creative applications of affective computing tech-
nologies will flourish, yielding satisfactory results in various 
fields.
Education
In the field of education, affective computing is primarily used 
to recognize the emotional state of learners and provide corre-
sponding feedback and adjustment [67]. For example, teachers 
can utilize intelligent emotional teaching systems to better under-
stand students’ engagement levels and adjust the pace and content 
of their teaching to improve the learning experience. An intelli-
gent system can recommend customized learning content based 
on the sentiment analysis of students’ interests. Students can 
provide authentic teaching feedback through intelligent systems 
to improve the comprehensiveness and accuracy of teaching 
evaluations. One advantage of an intelligent system is that it can 
be used in both traditional and online classrooms to strengthen 
the contextualization of online teaching, enhance emotional 
interaction between teachers and students, and improve teaching 
quality. Affective computing techniques are also conducive to the 
research and development of educational games and robots [68], 
providing improved human–computer interaction and achieving 
educational objectives more effectively.
Healthcare
Affective computing research has expanded into various psy-
chiatric disorders in the affective disorders category, such as 
Alzheimer’s [69], Parkinson’s [70], bipolar disorder [71], and 
post-traumatic stress [72], and into healthcare areas including 
relaxation service healthcare [73] and health office systems [74]. 
Affective computing enables the scientific and objective iden-
tification and judgment of patients’ emotions, particularly in 
psychological disorder treatments, providing a useful comple-
ment to more subjective traditional diagnostic tools such as 
behavioral observation and scale filling. Objective data collec-
tion can improve personalized and precise medical treatment 
[75]. In addition, affective computing can be used for the initial 
screening and efficacy assessment of diseases. For instance, 
patients with social anxiety disorder exhibit important differ-
ences in emotional facial processing compared to the normal 
population, differences that can be identified by automated 
monitoring of differential features [76].
Business services
In marketing, where the consumer experience is highly corre-
lated with emotions, affective computing is widely used to under-
stand and recognize the user’s emotional state. The application 
of affective computing can reveal the user’s true preferences and 
improve and streamline the buying process [77]. In the field of 
financial credit, affective computing technologies can be used to 
analyze the emotional state and moral level of a customer based 
on voice and tone, determine the probability of the customer 
lying, and provide a guide for lending decisions. In the field of 
stock investment, investor decisions are influenced by irrational 
judgments. The price trend of a stock is determined not only by 
a company’s fundamentals but also to a large extent by fluctua-
tions in investor emotions. The study of investor sentiment from 
social media data (e.g., data from X, formerly known as Twitter) 
can help identify investors’ emotional preferences and cognitive 
biases for the purpose of predicting the direction of the stock 
market [78].
Integration of science and art
In the current digital era, image, audio, and video data have 
become plentiful and important. Extracting useful information 
from them and retrieving and mining them effectively are crucial. 
For example, in recommending music to users, resource manage-
ment and audio search efficiency are essential. Traditional music 
search methods match content using text (e.g., song title, artist 
name, or lyrics). Including sentiment, a high-level semantic fea-
ture of music, improves the match between user preferences and 
music, thus aiding in the primary task in music sentiment analy-
sis [79]. Affective computing also empowers automated poetry 
generation, where deep learning methods such as RNNPG, an 
RNN-based poem generator, and SeqGAN, a sequence generative 
adversarial network, are gradually replacing Word Salada, genetic 
algorithms, and statistical machine translation methods [80–82]. 
Expressing emotions more richly is key in making generated 
poetry spiritual, i.e., in moving beyond resemblance of form to 
resemblance in spirit.
Importance of this study
The field of affective computing has grown considerably and 
exploded in popularity in the last decade for 2 reasons: techno-
logical developments providing tools for affective computing and 
the growth and expansion of demand. In the era of human–
machine symbiosis, the deepened human understanding of 
emotional connotation and the improvement of the “double 
quotient” (i.e., IQ + EQ) of intelligent machines will become a 
vital innovative force promoting the affective computing disci-
pline, technological evolution, and industrial progress. Despite 
the rapid development in affective computing, a comprehensive 
review of research and systematic analysis of hotspots and trends 
is lacking. Continuous innovation in algorithmic technology, 
broadening application requirements, and increasing research 
efforts necessitate that existing research be summarized and 
future technological directions be identified. Doing so will enable 
academia and industry to better understand the development of 
affective computing technology, thus will facilitate affective com-
puting research, empower applications, and benefit society.
This study aims to fill the gaps in existing research through 
a comprehensive review of affective computing from 1997, 
when Picard formally proposed the concept, up to 2023. We 
adopted a bibliometric analysis method to accurately portray 
the current status of the development of the field and provide 
insights into present challenges and future trends. The main 
contributions of this study are as follows. (a) Facing the aca-
demic frontier, we list the research hotspots and trends that we 
identified by analyzing full-scale papers. This allows readers to 
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
6
quickly and comprehensively grasp the development dynamics 
of the field and understand key common and frontier-leading 
technologies. (b) Facing major needs and the main battlefield 
of the economy, we provide blueprints for technological devel-
opment and insights into current applications. This promotes 
the application and transformation of affective computing, 
facilitating high-quality economic development and digital 
transformation. (c) Facing future trends, we introduce chal-
lenges and developments in the field of affective computing, 
along with predictions for future technology and industry 
application directions. This serves as a forward-looking guide 
to the field.
Materials and Methods
Data collection
This study searched for papers published in affective computing 
from January 1997 to September 2023 in the Web of Science Core 
Collection (WoSCC), which includes the Science Citation Index 
Expanded, Social Sciences Citation Index, Arts & Humanities 
Citation Index, Emerging Sources Citation Index, Conference 
Proceedings Citation Index—Science (CPCI-S), and Conference 
Proceedings Citation Index—Social Sciences & Humanities 
(CPCI-SSH). The search strategy is summarized in Table 1.
The reason this study uses 1997 as the starting point of the 
timeline is that the book Affective computing [9], which was 
published in that year, is regarded as the work that established 
affective computing as an independent academic research field. 
Papers outside this time range were not included in the calcula-
tion of citation statistics. In the statistics of Chinese papers, 
Hong Kong, Macau, and Taiwan are included. The results show 
that 33,448 papers were published worldwide. Among them, 
16,097 (48.13%) were conference papers and 17,351 (51.87%) 
were journal papers. It should be noted that the names of insti-
tutions were standardized using machine and manual meth-
ods. However, when scientists publish papers, the writing of 
the names of institutions is not standardized, which may have 
caused the omission of papers in the statistics and a deviation 
in the index calculation results.
In addition, this study combined the following 3 databases 
for data acquisition: (a) Incites: This database is based on the 
publication date of all document types in the major index 
databases of the WoSCC. It performs publication count and 
index calculations to provide research performance analysis. 
(b) Essential Science Indicators (ESI): This is an in-depth ana-
lytical research tool based on the Web of Science. ESI can iden-
tify influential countries, institutions, papers, and publications, 
as well as the cutting-edge in a research field. (c) Journal Citation 
Reports (JCRs): This is a multidisciplinary journal evaluation 
tool that provides journal evaluation resources based on citation 
data statistics. By citing and counting references, the JCR can 
measure the influence of research at the journal level, revealing 
the relationships between citing and cited journals.
Data analysis
Statistical analysis was performed using a bibliometric method. 
Bibliometrics applies quantitative methods such as mathemat-
ics and statistics to the literature of a scientific or other field 
and processes statistical data based on information science 
theory. This widely accepted approach provides quantitative 
analysis pathways and innovative insights into the assessment 
of research trends based on previous literature [83,84]. Unlike 
peer review and expert judgment, bibliometrics can provide 
quantitative indicators to ensure objectivity through statistical 
analysis of academic achievements [85]. Bibliometric analysis 
enables monitoring and summarizes the status, hotspots, and 
trends of a particular topic, helping researchers identify future 
research directions [86]. In this study, we first cleaned and ana-
lyzed the data using the Derwent Data Analyzer (DDA, version 
10, Clarivate, London, UK), which is well integrated with the 
source data from the Web of Science platform. DDA was used 
for multidimensional data mining, preprocessing, standardiza-
tion, and statistical analysis. Subsequently, the bibliometric 
analysis and knowledge visualization software tool VOSviewer 
(version 1.6.15, Leiden University, Leiden, Netherlands) was 
employed. This analysis tool provides valuable insights into the 
structure, advancement, and collaboration in the field of affec-
tive computing. Notably, its distinctive feature lies in the graph-
ical representation of bibliometric maps, which is particularly 
suitable for large-scale data analysis [87]. VOSviewer was used 
to visualize the data in this study.
Results
Publication trends
From 1997 to 2009, the number of articles published in this field 
steadily increased, exhibiting an overall growth trend despite 
occasional fluctuations (Fig. 2). From 2010 to 2019, with the 
rise of deep learning, a rapid development was observed in the 
field of affective computing, and the number of articles pub-
lished in the field rose rapidly, indicating an explosive growth 
stage of research. After 2019, because of a plateau in the innova-
tion of deep learning methods and the impact of the coronavi-
rus disease 2019 (COVID-19) pandemic on academia, research 
in the field of affective computing also reached a plateau, and 
the rising trend slowed down.
Comparison of countries
To analyze the main research positions in the field of affective 
computing, the country/region fields of all the authors and the 
first author of the paper were counted. As shown in Table 2, 
among the top 20 countries with publications in the field of 
affective computing, China is the country with the largest num-
ber of publications, accounting for 26.2% of all authors and 
24.6% of first authors. China, the United States, India, the United 
Kingdom, and Germany rank among the top 5 in the number 
Table 1. Search strategy for this study
Index field
Search strategy
Theme keywords
“affective recognition” or “mood 
recognition” or “affective computing” 
or “artificial emotional intelligence” or 
“emotion AI” or “expression recognition” 
or “emotion recognition” or “emotion 
learning” or “sentiment analysis” or 
“sentiment recognition”
Literature types
proceedings papers, articles, review 
articles, early access
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
7
of papers published counting all authors or first author, and are 
the most important in terms of research in the field of affective 
computing. The United States ranks second in the number of 
papers published counting all authors, but third in the number 
of papers published counting only first author, after India.
In addition to the 2-year step in 2021–2022, a 4-year step 
was used to count the publication volume of the top 10 coun-
tries in the field of affective computing. The results are shown 
in Fig. 3. Given that the concept of “affective computing” origi-
nated in the United States, which has been a major research 
force in this field, we chose the United States as the benchmark. 
During the entire period, the relative volume of publications 
by China and the United States changed considerably, as shown 
in Fig. 3. From 1997 to 2004, the number of papers published 
by the United States far exceeded that of China. From 1997 to 
2000, the total number of papers published by China was 20% 
of that of the United States. From 2001 to 2004, the total num-
ber of papers published by China rose to 31% of that of the 
United States. In the period from 2005 to 2008, the number of 
papers published by China surpassed that of the United States, 
and the number of papers published by China in 2021–2022 is 
about 3 times that of the United States. It can be seen that in 
recent years, China’s research in the field of affective computing 
has accumulated rapidly, and its large volume of research has 
certain advantages compared with that of the United States. In 
addition, in 2021–2022, the number of papers published by 
India surpassed that of the United States for the first time. India 
has gradually become a major research center in the field of 
affective computing because of its advantages in computer sci-
ence, engineering, and other disciplines.
Main journals
This section analyzes basic data on journal papers. The 17,351 
published papers were distributed in 1,300 journals, among 
which IEEE Access [impact factor (IF) 3.9] had the most (875), 
as shown in Table 3. Across all journals, 1,209 had an IF listed 
in the 2022 JCRs. The distribution of the IFs of the 1,209 jour-
nals is shown in Table 4. Among them, 54 journals have IFs 
greater than 10, and the 5 journals with the highest IFs are 
World Psychiatry (73.3), Lancet Psychiatry (64.3), Nature 
Reviews Neuroscience (34.7), Nature Human Behaviour (29.2), 
and JAMA Psychiatry (25.8). The IFs of most journals are dis-
tributed in the 2 intervals of 2 ≤ IF < 4 and 4 ≤ IF < 7. It is 
worth noting that IEEE Transactions on Affective Computing 
(IF 11.2) is a high-level journal focusing on the field of affective 
computing. It is a cross-disciplinary and international archive 
journal aimed at disseminating the results of research on the 
design of systems that can recognize, interpret, and simulate 
human emotions and related affective phenomena. In addition, 
Expert Systems with Applications, Knowledge-Based Systems, 
Information Processing & Management, IEEE Transactions on 
Multimedia, Neurocomputing, Information Sciences, Pattern 
Recognition, Applied Soft Computing, Decision Support 
Systems, and Future Generation Computer Systems are also 
high-level journals favored by scholars in the field of affective 
computing.
Table 2. The top 20 countries in the field of affective computing
No.
Country
Number of papers
Country
Number of papers
(All authors)
(All authors)
(First author)
(First author)
1
China
8,780
China
8,223
2
USA
4,715
India
3,632
3
India
3,829
USA
3,274
4
UK
2,535
UK
1,432
5
Germany
1,706
Germany
1,253
6
Japan
1,321
Italy
1,022
7
Italy
1,302
Japan
977
8
Australia
1,234
South Korea
931
9
Spain
1,178
Spain
862
10
South Korea
1,121
Australia
788
11
Canada
1,100
Canada
720
12
France
943
France
587
13
Netherlands
778
Turkey
581
14
Saudi Arabia
765
Netherlands
484
15
Turkey
691
Malaysia
479
16
Singapore
640
Pakistan
454
17
Malaysia
609
Brazil
443
18
Pakistan
595
Greece
413
19
Brazil
522
Iran
398
20
Greece
483
Singapore
394
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
8
Fig. 2. Annual scientific production on “affective computing” from 1997 January 1 to 2023 September 25.
Table 3. Top 20 journals with the largest number of articles in the field of affective computing
No.
Journal
Number of papers
1
IEEE Access
875
2
Multimedia Tools and Applications
474
3
IEEE Transactions on Affective Computing
419
4
Sensors
378
5
Frontiers in Psychology
362
6
Applied Sciences-Basel
349
7
Expert Systems with Applications
290
8
International Journal of Advanced Computer Science and Applications
272
9
Neurocomputing
248
10
Knowledge-Based Systems
226
11
Psychiatry Research
191
12
Electronics
167
13
Journal of Intelligent & Fuzzy Systems
151
14
Neural Computing & Applications
144
15
Neuropsychologia
137
16
Schizophrenia Research
135
17
Information Processing & Management
132
18
Computational Intelligence and Neuroscience
114
19
Cognitive Computation
112
20
Information Sciences
110
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
9
High-level international conferences
Combining ESI’s highly cited and hot papers with the “China 
Computer Federation Recommended International Academic 
Conferences” and CORE Computer Science Conference 
Rankings, we identified the high-level international confer-
ences related to affective computing. These include the ACM 
International Conference on Multimedia (ACM MM), AAAI 
Conference on Artificial Intelligence (AAAI), Annual Meeting 
of the Association for Computational Linguistics (ACL), IEEE 
Conference on Computer Vision and Pattern Recognition 
(CVPR), IEEE International Conference on Computer Vision 
(ICCV), International Conference on Affective Computing and 
Intelligent Interaction (ACII), IEEE International Conference and 
Workshops on Automatic Face and Gesture Recognition (FG), 
and the IEEE International Conference on Acoustics, Speech, and 
Signal Processing (ICASSP).
Discipline distribution
This section analyzes the distribution of research fields based on 
statistics on the Web of Science categories of papers in the field 
of affective computing. Studies related to the topic of affective 
Fig. 3. Comparison between the top 10 countries and the United States in the number 
of publications.
Table 4. Journal impact factor distribution
Journal impact factor
Number of journals
IF ≥ 10
54
7 ≤ IF < 10
74
4 ≤ IF < 7
255
2 ≤ IF < 4
406
1 ≤ IF < 2
245
IF ≤ 1
175
Table 5. Top 20 categories with the most papers in the field of affective computing
Web of Science category
Number of papers
Percentage (%)
Computer Science, Artificial Intelligence
12,687
37.90
Engineering, Electrical & Electronic
9,820
29.36
Computer Science, Information Systems
8,714
26.05
Computer Science, Theory & Methods
8,405
25.13
Computer Science, Interdisciplinary 
Applications
3,930
11.75
Telecommunications
3,133
9.37
Computer Science, Software Engineering
2,982
8.92
Neurosciences
2,376
7.10
Psychiatry
2,100
6.28
Computer Science, Cybernetics
1,904
5.69
Imaging Science & Photographic Technology
1,077
3.22
Engineering, Multidisciplinary
1,045
3.12
Automation & Control Systems
997
2.98
Computer Science, Hardware & Architecture
981
2.93
Psychology, Multidisciplinary
884
2.64
Robotics
793
2.37
Engineering, Biomedical
735
2.20
Acoustics
724
2.16
Linguistics
637
1.90
Clinical Neurology
610
1.82
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
10
computing involve computer science, communication, engineer-
ing, psychology, medicine, and other disciplines, reflecting dis-
tinct interdisciplinary characteristics. The top 20 categories with 
the largest number of publications are listed in Table 5. The 
category with the largest proportion is “Computer Science, 
Artificial Intelligence,” with 12,678 publications (37.93% of the 
total), followed by “Engineering, Electrical & Electronic,” with 
9,820 publications (29.36% of the total).
Technology transfer and conversion
This study searched the Derwent Innovation Index, the world’s 
most comprehensive database of value-added patent informa-
tion. Among effective invention patents with transfer records 
and high value, the transferred patents with an IncoPat patent 
value of 10 (the highest level) include “Cognitive content dis-
play device” (US10902058B2, transferred from IBM to Kyndryl 
Inc.) and “Signal processing approach to sentiment analysis for 
entities in documents” (US9436674B2, transferred from Attivio 
Inc. to Servicenow Inc.). However, the number of patent trans-
fer records related to affective computing is small, indicating 
that technology transfer activity needs to be improved.
Global distribution of scholars
This section presents statistical analysis of publications based 
on the country of the first author to provide a macroscopic 
understanding of the global distribution of scholars in the field 
of affective computing. As shown in Table 6, China has the 
largest number (4,240), followed by India (2,391) and the 
United States (2,390). In Fig. 4, darker shading indicates a larger 
number of scholars. It can be seen that Asia and North America 
are the regions with the most concentrated distribution of 
scholars in the field of affective computing.
International collaboration
There is a wide range of international cooperation in the field 
of affective computing. A count of collaborations between the 
top 20 countries is shown in Table 7. The number of articles 
published by China and the United States is the largest (641), 
followed by China and the United Kingdom (343). Although 
cooperation between China and the United States has been 
challenging in recent years, in the field of affective computing, 
they remain each other’s largest partners, maintaining a vital 
and continuous cooperation.
Important research institutions
The top 10 institutions in the world by number of publications 
(counting all authors) are listed in Table 8. This study used indi-
cators such as Citation Impact, Category Normalized Citation 
Impact (CNCI), and Highly Cited Papers to further evaluate 
the influence of various institutions in the field of affective com-
puting. Among them, CNCI is a valuable and unbiased impact 
indicator that excludes the influence of publication year, subject 
field, and document type. A CNCI value of 1 indicates that the 
cited performance of a group of papers is equivalent to the 
Table 6. Number of first authors in the field of affective comput-
ing (top 20 countries)
No.
Country
Number 
of  
scholars
No.
Country
Number 
of  
scholars
1
China
4,240
11
Canada
533
2
India
2,391
12
France
425
3
USA
2,390
13
Turkey
403
4
UK
999
14
Netherlands
349
5
Germany
825
15
Malaysia
331
6
Italy
690
16
Pakistan
324
7
Japan
631
17
Brazil
366
8
South 
Korea
514
18
Greece
248
9
Spain
545
19
Iran
270
10
Australia
496
20
Singapore
229
Fig. 4. Global distribution of scholars in the field of affective computing.
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
11
global average level, a value greater than 1 indicates higher 
performance, and a value less than 1 indicates lower perform­
ance; a value of 2 indicates performance twice as high as the 
global average. The top 5 institutions according to CNCI rank-
ings were Nanyang Technological University (5.06), Imperial 
College London (3.58), Tsinghua University (3.23), the Chinese 
Academy of Sciences (3.15), and the University of California 
System (2.77).
Citation network analysis
This section analyzes the direct citations of all authors in the 
field of affective computing. To highlight the key authors, 40 
authors who had published no fewer than 30 papers were selected 
for analysis. The results are shown in Fig. 5. Authors in clusters 
of the same color have strong correlations and inheritance in 
research content. Representative scholars from the 5 clusters are 
listed in Table 9.
Word frequency analysis
Word frequency refers to the number of times a word occurs 
in the document being analyzed. In scientometric research, 
word frequency dictionaries can be established for specific sub-
ject areas to quantify the analysis of scientists’ creative activities. 
Word frequency analysis is the method of extracting keywords 
or subject words that express the core content of the articles in 
the literature, to study the development trends and research 
hotspots of the field through the frequency distribution of these 
words. The results of conducting frequency and co-occurrence 
analysis on keywords assigned to papers by authors in the field 
of affective computing are shown in Table 10.
The Thomson Data Analyzer was used to automatically and 
manually clean the keywords assigned by the authors of papers 
in the dataset. Subsequently, VOSviewer was used to cluster 
the core (high-frequency) subject words and set a certain co-
occurrence frequency and co-occurrence intensity according 
to the size of the dataset to cluster the keywords. Combined with 
expert interpretation, each cluster was named and interpreted, 
and the topics of the journal articles were identified and ana-
lyzed. After keyword cleaning, 613 keywords appearing more 
than 20 times were selected as analysis objects for cluster calcu-
lation. Five clusters were obtained by clustering the core subject 
words with the highest co-occurrence intensity, as shown in 
Table 11 and Fig. 6.
The average number of citations of a research theme is the 
average number of times that a paper containing these subject 
words has been cited since publication, and the average correla-
tion strength of a research theme indicates the closeness of the 
connection between the core subject words contained in this 
theme concept. The greater the correlation strength, the greater 
the co-occurrence intensity between the core subject words and 
the more concentrated the research. In contrast, relatively lower 
correlation is associated with more scattered research. Research 
on the application of affective computing in the analysis of 
affective disorders has the highest average citation frequency, 
which shows that interdisciplinary research involving affective 
Table 7. Collaborations between the top 20 countries in the field of affective computing
C1
U1
I1
U2
G1
J
I2
A
S1
S2
C2
F
N
S3
T
S4
M
P
B
G2
C1
/
641
79
343
79
256
59
218
43
61
137
44
28
61
12
161
38
57
6
4
U1
641
/
128
232
174
42
120
122
62
83
153
100
105
55
42
71
10
36
53
23
I1
79
128
/
73
15
15
22
37
19
33
26
26
8
67
10
48
26
11
3
2
U2
343
232
73
/
294
40
132
119
96
15
60
89
160
77
25
64
30
43
30
48
G1
79
174
15
294
/
41
69
47
39
11
43
59
99
4
17
17
5
7
13
19
J
256
42
15
40
41
/
4
20
17
7
27
15
11
6
5
18
16
1
3
1
I2
59
120
22
132
69
4
/
22
58
13
25
65
53
10
13
37
4
10
6
7
A
218
122
37
119
47
20
22
/
26
14
30
22
24
27
14
35
25
23
11
3
S1
43
62
19
96
39
17
58
26
/
15
15
42
46
23
12
11
5
10
24
18
S2
61
83
33
15
11
7
13
14
15
/
10
16
6
29
2
9
71
3
3
C2
137
153
26
60
43
27
25
30
15
10
/
45
19
40
10
9
2
12
17
3
F
44
100
26
89
59
15
65
22
42
16
45
/
39
11
4
2
8
16
18
10
N
28
105
8
160
99
11
53
24
46
6
19
39
/
19
8
3
1
11
14
S3
61
55
67
77
4
6
10
27
23
29
40
11
/
8
4
41
120
1
3
T
12
42
10
25
17
5
13
14
12
10
4
19
8
/
5
7
3
2
1
S4
161
71
48
64
17
18
37
35
11
2
9
2
8
4
5
/
4
2
1
M
38
10
26
30
5
16
4
25
5
9
2
8
3
41
7
4
/
40
3
P
57
36
11
43
7
1
10
23
10
71
12
16
1
120
3
2
40
/
3
B
6
53
3
30
13
3
6
11
24
3
17
18
11
1
2
3
/
G2
4
23
2
48
19
1
7
3
18
3
3
10
14
3
1
1
3
/
Note: C1, China; U1, USA; I1, India; U2, UK; G1, Germany; J, Japan; I2, Italy; A, Australia; S1, Spain; C2, Canada; S2, South Korea; F, France; N, Netherlands; T, Turkey; 
S3, Saudi Arabia; S4, Singapore; M, Malaysia; P, Pakistan; B, Brazil; G2, Greece.
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
12
computing and medicine, especially research on affective dis-
orders and depression recognition, has a greater influence. The 
average correlation strength of multimodal sentiment analysis 
based on deep learning is the largest, which shows that the 
research on this topic is the most concentrated.
Discussion
This paper presents a comprehensive analysis and review of 
systematically collected data on papers and major intellectual 
property rights in the field of affective computing. The results 
reveal that over the past 25 years, affective computing has expe-
rienced rapid growth in the number of published papers, rep-
resenting a vibrant academic ecology and an interdisciplinary 
character with a wide range of disciplines. Additionally, scholars 
worldwide actively participate in a relatively close cooperation 
network. In particular, Chinese scholars have led the world in 
terms of the number of publications, scholars, and collaborative 
papers in this field. Among important research institutions, 
Tsinghua University and the Chinese Academy of Sciences stand 
out, with CNCI values indicating that the average number of 
citations of their papers was more than twice the global average. 
Citation network analysis showed that Chinese scholars are 
representative and have become essential nodes in the citation 
network, indicating that China is constructing a large-scale tal-
ent team for affective computing and progressing in both the 
quantity and quality of research. However, China also faces 
disadvantages in academic journals, international conferences, 
and other aspects, leading to weak dominance, which restricts 
China’s academic discourse improvement in this field. Notably, 
in recent years, India’s publication volume has exceeded that of 
the United States for the first time, revealing a robust develop-
ment potential linked to its advantages in computing. 
Nonetheless, India still has room for growth in terms of research 
quality and paper impact as it lacks representative scholars in 
the field of affective computing.
Challenges and technology development trends
Modeling of cultural contexts
This study found that affective computing researchers are dis-
tributed across various countries globally and have a wide range 
of cultural backgrounds. While emotional expression has a 
Table 8. Institutions with a top 10 publication in affective computing
No.
Institution
Number of papers
Citation impact
Category  
Normalized  
Citation Impact
H-index
Percentage in Q1 
journals
Country
1
Chinese Academy 
of Sciences
699
20.97
3.15
60
59.87
China
2
University of 
London
443
50.26
2.29
77
69.45
UK
3
UDICE-French 
Research  
Universities
388
18.86
1.37
42
50.43
France
4
Centre National de 
la Recherche Sci-
entifique (CNRS)
377
19.33
1.36
42
51.56
France
5
University of  
California System
371
40.83
2.77
64
58.72
USA
6
National Institute 
of Technology  
(NIT System)
364
9.68
1.46
29
26.43
India
7
Indian Institute of 
Technology System 
(IIT System)
360
13.51
1.99
36
44.7
India
8
Nanyang Techno-
logical University
350
46.35
5.06
69
68.99
Singapore
9
Tsinghua University
302
24.87
3.23
44
62.93
China
10
Imperial College 
London
300
41.00
3.58
49
70.75
UK
Notes: 1. Citation impact: The citation impact of a set of documents is calculated by dividing the total number of citations of the set of documents by the 
number of documents. Citation impact shows the average number of citations received by a document in the group. 2. Category Normalized Citation Impact 
(CNCI): The CNCI of a document is obtained by dividing the actual number of citations by the expected number of citations of documents of the same type, 
publication year, and subject. When a document is classified into multiple subject areas, the average value of the ratio of actual citations to expected citations 
is used. The CNCI of a country is the average of the CNCIs of the publications of that country.
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
13
degree of consistency across humanity, it is considerably influ-
enced by cultural background. Cultural norms and values 
determine the different emotional experiences of individuals 
and how others perceive these emotions. Therefore, affective 
computing systems developed using a single cultural group may 
fail in other cultural contexts. For example, Chinese, Germans, 
and Japanese express emotions relatively implicitly, whereas 
Americans, British, and Brazilians express emotions more 
overtly. This indicates that emotion agents must match emotion 
calculation rules with the cultural context. Many Western cul-
tural standards may not necessarily apply in Eastern contexts. 
For example, Japanese researchers tend to develop robots that 
can express emotions implicitly because overly direct expres-
sions of emotions may cause user dissatisfaction [88]. Therefore, 
cultural characteristics must be considered in developing uni-
versal cross-cultural emotional agents for people from differ-
ent cultural backgrounds. Hofstede defined culture in terms 
of 5 measures—power distance, identity, gender, uncertainty 
avoidance, and long-term orientation—which can be used to 
summarize the typical rules of emotional expression in differ-
ent cultural contexts [89]. When it is challenging to obtain 
culture-specific empirical affective data, it is more feasible to 
design affective computational models using cultural theories 
and rules.
Emotion generation techniques
The cluster analysis of topic terms in affective computing revealed 
5 important core topics, including “natural language processing 
techniques for affective computing and opinion mining” and 
“facial expression and micro-expression recognition and analysis.” 
Current research focuses more on emotion recognition, with rela-
tively limited attention accorded to emotion generation. Emotion 
recognition and generation are both essential aspects of affective 
computing and constitute an important technical basis for the 
closed loop of human–computer interaction. To enable machines 
to provide more anthropomorphic and natural feedback, it is cru-
cial to focus on the following 2 research areas. (a) Generation of 
facial expressions. The fact that human emotions are expressed 
through visual (55%), voice (38%), and verbal (7%) signals is also 
known as the “3V rule,” which reflects the importance of human 
facial expressions in emotion analysis [90]. Appropriate use of 
facial expressions by avatars and robots can enhance human–robot 
interaction. Thus, current research aims to build a lexicon of facial 
expressions that can translate communicative intent into associ-
ated expressive morphology and dynamic features to express vari-
ous meanings. Meanwhile, a team of animation experts is required 
to achieve realistic facial rendering effects, including lighting and 
muscle textures. (b) Generation of emotional body movement. 
This requires the design of embodied agents using computer mod-
els of body expression. This area involves studying human kine-
matics; however, researchers have yet to determine how to 
characterize the organic combination of body parts, movement 
strength, and posture of specific emotional states.
Fine-grained sentiment classification models
Ekman’s basic emotion theory model is a widely used classification 
model for emotion computation [10]. However, in real life, people’s 
Fig. 5. Citation network of scholars.
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
14
emotions often exist in a mixed state. For example, people often 
simultaneously express surprise and joy, sadness and pain, etc. 
Du et al. [91] proposed the concept of mixed emotions based on 
research conducted using the Facial Action Coding System 
(FACS). They suggested that the combination of 2 basic emotions 
creates mixed emotions and defined different types using scenario 
examples. Using a FACS-based face recognition algorithm model, 
microvariations in facial muscles can be analyzed to accurately 
discriminate between different types of mixed emotions. Martinez 
[92] assessed whether mixed emotions can be semantically labeled 
correctly. The test tasks included prioritization and forced selection 
of mixed emotion labels, and the results showed that subjects per-
formed consistent and accurate categorization. Mixed emotion is 
an essential research direction for expression-based fine-grained 
emotion classification. This concept extends the core idea of FACS, 
aiming to reveal the relationship between mixed and basic emo-
tions. It offers a better solution to the problem of differentiation of 
emotions and clarifies the relationship between differentiated emo-
tions and their original emotions, providing traceable clues and 
measurement possibilities for the generation, development, and 
change of emotions. It summarizes complex emotional changes 
into a logical dynamic composite form with similar configuration 
effects, resulting in strong interpretability, logic, and unity.
Code of ethics and technical standards
Recording an individual’s emotional state has implications for 
privacy, particularly when it comes to recording video or audio. 
Subjects may not agree to provide researchers with authentic 
and naturalistic emotional data and may feel uncomfortable 
being monitored in daily life. For example, the results of AI 
emotion monitoring tools may be analyzed alongside employee 
performance evaluations, predictions of the risk of leaving the 
job, and patterns of employee–team interactions for predicting 
behavior. Although the use of such technology reduces employee 
turnover and saves costs for organizations [66], employees 
may experience constant psychological stress, leading to burn-
out [93]. Additionally, individuals may lose autonomy as they 
become more hesitant to display emotions in public, instead 
choosing to use a “poker face.” While there should be openness 
in the use of affective computing, appropriate regulation is nec-
essary to assess potential risks involving privacy and security, 
and the technology should be reviewed and documented for 
each industry to maximize benefits while minimizing harm, 
risks, and costs. Ethical issues are more likely to be overlooked 
in computing and engineering than in psychology. The collec-
tion of individual data, particularly physiological data, should 
be regulated by human research ethics committees, which are 
best suited to managing informed consent and privacy issues.
Efforts should be made to strengthen the development of 
international standards in the field of affective computing to 
form a universally accepted specification. Currently, the avail-
able standard is “Information technology—Affective computing 
user interface (AUI)” (standard number ISO/IEC 30150-1:2022). 
The first part, “Model,” was released in June 2022, and the second 
part, “Affective Characteristics,” is under construction. However, 
there is a lack of standards for data collection, data security, and 
personal privacy protection in the field of affective computing. 
Therefore, the International Organization for Standardization 
(ISO), International Electrotechnical Commission (IEC), and 
International Telecommunication Union (ITU) should improve 
relevant standards and unify them for global use.
Cognitive neuroscience-inspired affective computing
Just as CNN architectures are inspired by biological visual pro-
cessing and reinforcement learning methods are inspired by 
behaviorist theories in psychology, impulse network models are 
inspired by neuroplasticity. Cognitive neuroscience has also 
developed theories on affective circuits [94], multiple-wave 
models [95], embodied cognition [96], and other related areas, 
providing brain-inspired insights into the design of affective 
computation models. Studies on the physiological representa-
tions of different emotions offer theoretical foundations and 
guidelines for feature extraction in affective computing based 
on facial expressions, psychophysiological measurements, and 
Table 9. Representative scholars in the citation network
Scholar
Organization
Research fields
Baoliang Lu
Shanghai Jiaotong 
University, China
Brain-like computing, neural networks, deep learning, emotion AI, affective brain–computer 
interface
Bjoern Schuller
Imperial College 
London, UK
Machine intelligence, signal processing, affective computing, digital health, speech recogni-
tion
Erik Cambria
Nanyang Techno-
logical University, 
Singapore
Affective computing, sentiment analysis, commonsense reasoning, natural language  
understanding
Fuji Ren
The University of 
Tokushima, Japan 
the University of 
Electronic Science 
and Technology of 
China, China
Natural language processing, artificial intelligence, affective computing, and emotional robots
Wenming Zheng
Southeast  
University, China
Multimodal affective computing, neural computation, pattern recognition, machine learning, 
and computer vision
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
15
Table 10. Frequency analysis of top 25 keywords in affective computing
No.
Number of  
occurrences
Technical keyword
Number of co-occurrences with 
other keywords
Time period
Proportion of occur-
rences within last  
3 years (%)
1
7,621
Sentiment analysis
Machine learning [958]; 
Opinion mining [936]; 
Natural language processing 
[829]
2006–2023
21
2
4,566
Emotion recognition
Feature extraction [422]; 
Affective computing [397]; 
Deep learning [372]
1997–2023
24
3
2,457
Affective computing
Emotion recognition [397]; 
Machine learning [191]; 
Emotion [137]
2000–2023
15
4
2,232
Deep learning
Sentiment analysis [691]; 
Emotion recognition [372]; 
Machine learning [268]
2012–2023
40
5
2,054
Machine learning
Sentiment analysis [958]; 
Natural language processing 
[275];Deep learning [268]
2002–2023
27
6
1,816
Facial expression  
recognition
Deep learning [182]; 
Feature extraction [150]; 
Face recognition [109]
1997–2023
18
7
1,348
Natural language  
processing
Sentiment analysis [829]; 
Machine learning [275]; 
Deep learning [209]
2006–2023
30% of 1,348
8
1,214
Feature extraction
Emotion recognition [422]; 
Sentiment analysis [213]; 
Task analysis [181]
2003–2023
32
9
1,209
Opinion mining
Sentiment analysis [936]; 
Natural language processing 
[159]; 
Machine learning [151]
2006–2023
11
10
1,067
Emotion
Affective computing [137]; 
Emotion recognition [80]; 
Facial expression [78]
1999–2023
13
11
1,007
Twitter
Sentiment analysis [770]; 
Machine learning [160]; 
Social media [145]
2011–2023
18
12
975
Speech emotion  
recognition
Deep learning [86]; 
Feature extraction [72]; 
Emotion recognition [61]
2006–2023
29
13
852
Social media
Sentiment analysis [587]; 
Twitter [145]; 
Machine learning [105]
2009–2023
21
14
732
Social cognition
Schizophrenia [193]; 
Emotion recognition [184]; 
Theory of mind [179]
2001–2023
16
15
657
Text mining
Sentiment analysis [486]; 
Natural language processing 
[87];Opinion mining [87]
2006–2023
15
16
635
EEG
Emotion recognition [357]; 
Affective computing [87]; 
Emotion [51]
2004–2023
27
(Continued)
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
16
neuroimaging. Further human research in the field of cognitive 
neuroscience will ultimately affect the development of affective 
computing and artificial intelligence as a whole. The cognitive 
process of human brain emotion processing, its neural mecha-
nism, and its anatomical basis provide essential inspiration for 
the development of affective computing models. However, to 
ensure that machines have genuine emotions rather than just 
appearing to have emotions, further research in cognitive neu-
roscience is required. This research may involve exploring the 
neural basis for the generation of human consciousness, the 
neural mechanism for the construction of human values, and 
other key scientific issues. Based on this neural theoretical foun-
dation, simulation and machine implementation are feasible 
options for providing machines with authentic emotions.
Construction of large-scale multimodal datasets
The development of affective computing is highly dependent on 
the construction of large-scale open datasets. Three major trends 
are described below. The first trend predicts that dataset sizes will 
continue to grow to meet the demands of deep learning algorithm 
training. Deep-learning models have a substantial number of 
parameters, and the selection of these parameters requires sam-
ples that are typically 100 times the number of parameters. A 
larger dataset size enables the trained model to avoid overfitting, 
which improves model learning. However, the challenge lies in 
labeling these massive datasets. Thus, it is necessary to explore 
active, weakly supervised, and unsupervised learning methods 
to label the meaningful data in large unlabeled datasets or train 
machines for labeling. The second trend highlights the need 
for the collection of multimodal data, the accumulation of 
richer modal information, and fine-grained alignment between 
different modalities. At this stage, machines differ from human 
beings in 2 critical aspects: First, humans exist in a multimodal 
social environment, as evidenced by their joint expression of 
intentions and emotions through language, facial expressions, 
speech, and actions; second, humans can switch between 
modalities for emotional reasoning when dealing with emo-
tions. They can also switch between different modalities to 
search for clues, eliminate ambiguities, and conduct emotional 
reasoning through interconnections. Therefore, creating a 
large-scale multimodal emotion dataset can contribute to the 
development of human-like emotion intelligence technology 
No.
Number of  
occurrences
Technical keyword
Number of co-occurrences with 
other keywords
Time period
Proportion of occur-
rences within last  
3 years (%)
17
620
Classification
Sentiment analysis [208]; 
Machine learning [100]; 
Emotion recognition [84]
2003–2023
19
18
618
Facial expression
Emotion recognition [175]; 
Emotion [78]; 
Affective computing [49]
1998–2023
15
19
582
Convolutional neural 
network
Deep learning [146]; 
Facial expression recognition 
[102]; 
Emotion recognition [100]
2003–2023
30
20
535
Schizophrenia
Social cognition [193]; 
Emotion recognition [88]; 
Theory of mind [68]
1998–2023
8
21
478
Support vector machine
Sentiment analysis [123]; 
Facial expression recognition [79]; 
Emotion recognition [64]
2002–2023
9
22
470
Feature selection
Sentiment analysis [119]; 
Emotion recognition [95]; 
Feature extraction [59]
2001–2023
16
23
423
Face recognition
Feature extraction [155]; 
Emotion recognition [124]; 
Facial expression recognition 
[109]
1997–2023
29
24
422
Transfer learning
Emotion recognition [89]; 
Deep learning [81]; 
Sentiment analysis [77]
2009–2023
40
25
404
Data mining
Sentiment analysis [251]; 
Feature extraction [64]; 
Machine learning [64]
2006–2023
22
Table 10.  (Continued) 
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
17
and the realization of more accurate emotion recognition. The 
third trend focuses on collecting natural-scene data, as emo-
tional data collected in perform­ance or evoked mode may not 
accurately represent real-life scenarios. However, collecting 
high-quality labeled emotional-physiological data in daily 
life remains a challenge due to the lack of hardware collec-
tion devices that are sufficiently comfortable and resistant to 
interference.
Table 11. Five research themes in affective computing
No.
Research theme
Number of core  
subject words
Average number  
of citations
Average correlation 
strength
1
Natural language processing 
techniques used for  
affective computing and 
opinion mining
153
10.41
197.80
2
Facial expression and  
micro-expression  
recognition and analysis
134
15.89
178.77
3
Affective computing  
studies in human– 
computer interaction
121
18.69
110.38
4
Applied research of  
affective computing in  
affective disorder analysis
30
33.5
165.59
5
Multimodal sentiment 
analysis based on deep 
learning
81
9.8
260.95
Fig. 6. Five research themes in affective computing.
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
18
Multimodal fusion technology innovation
Multimodal fusion combines information from multiple modal-
ities using multimodal representations for sentiment classifica-
tion. It can enhance the performance of sentiment-computing 
models by playing a complementary and disambiguating role 
[21]. Multimodal fusion methods can be classified as model-
independent or model-based. Model-independent fusion meth-
ods do not rely on a specific deep-learning method, whereas 
model-based fusion methods do.
There are 3 categories of model-independent fusion meth-
ods: early fusion (feature-based fusion), late fusion (decision-
based fusion), and hybrid fusion (combination of the 2). Early 
fusion integrates features immediately after they are extracted 
and uses multiple signals to create a single feature vector, which 
is then modeled using machine-learning algorithms. The larger 
the number of features and the greater the variation in these 
features, the more challenging feature-level fusion becomes and 
the easier it is to overfit the training data. In contrast, late fusion 
performs integration only after each model outputs the results 
(e.g., classification or regression results). It can better handle 
overfitting but does not allow the classifier to train on all data 
simultaneously. The Dempster–Shafer theory of evidence is a 
generalization of Bayesian theory to subjective probability. It 
is widely used in late fusion models because of its ability to 
model uncertain knowledge and combine beliefs from different 
sources to obtain new beliefs that take into account all available 
evidence. Hybrid fusion combines the outputs of earlier fusion 
methods and unimodal predictors. Although it is flexible, care-
ful design is required to determine the timing, modalities, and 
method of fusion based on the specific application problem 
and research content. Researchers must select the appropriate 
approach at their discretion.
Model-based fusion methods address the multimodal fusion 
problem through implementation techniques and models, 
using 3 common methods: multiple kernel learning (MKL), 
graphical models (GMs), and neural networks (NNs). As these 
methods easily exploit the spatial and temporal structure of the 
data, they are particularly suitable for time-related modeling 
tasks. Additionally, they allow human expert knowledge to be 
embedded in the model, thereby enhancing interpretability. 
However, their disadvantage is that they are computationally 
expensive and challenging to train.
Research has shown that synesthesia is generated not only in 
the cerebral cortex but also in the subcortical limbic system, 
including the thalamus, amygdala, and hippocampus, which are 
closely related to emotional processing [97]. Inspired by the mul-
tistage fusion phenomenon that integrates multisensory informa-
tion in the brain, a multistage multimodal emotion fusion method 
can be developed. This would first involve training a unimodal 
model, splicing it as an implicit state with another modal feature, 
training the bimodal model similarly, and continuing with this 
process until a multimodal model is obtained. In conclusion, 
multimodal fusion technology effectively utilizes the synergistic 
complementarity of different modal information [57], enhances 
emotional understanding and expression, and improves model 
robustness and performance. This represents an important direc-
tion for future research.
Data- and knowledge-driven technological innovation
In its early stages, affective computing research relied heavily on 
collected data to make inferences. However, this data-driven 
approach is both inefficient and ineffective at the application level. 
For humans to understand data fully, they must activate other 
associated information, such as potential knowledge or common 
sense. The human brain can seamlessly combine this information 
to enable more generalized, intelligent, and frugal computation 
for complex problems. Therefore, affective computing requires 
not only big data and extensive computing power but also the 
integration of knowledge. Knowledge guidance and inspiration 
can compensate for insufficient or uneven data quality while con-
serving computational power. For instance, in constructing a 
multidisciplinary and multi-faceted emotional knowledge map, 
fine-grained emotional knowledge integrated through emotional 
commonsense associations is used to enable the modeling of hier-
archical logical relationships between aspect words and emotional 
words. This approach facilitates the dynamic correlation, aggrega-
tion, and reasoning of domain, aspect, and emotional knowledge. 
It provides an optimal solution for various applications of affective 
computing, such as efficient real-time online sentiment analysis, 
emotion-injected dialogue systems, and emotion-injected story 
generation. These applications provide dynamic and accurate 
domain-adaptive sentiment knowledge.
Group affective computing
Current research in affective computing primarily focuses on 
sentiment analysis at the individual level, neglecting the potential 
value of group-affective computing. For instance, emotions felt 
by individual employees can aggregate and spread to create “col-
lective emotions” in the workplace. These shared emotions can 
considerably affect the organization by offering insights into 
absenteeism, intra-team communication, team cohesion and 
performance, and organizational citizenship behavior. As such, 
affective computing research could expand its focus from indi-
vidual to collective affect analysis and the propagation of affect 
across people. Furthermore, group affective computing can pre-
dict consumer behavior. EEG-based hyperscanning technology, 
which explores dynamic brain activity between 2 or more inter-
acting customers and their underlying neuroemotional activities, 
can be used to anticipate shared consumption intentions, panic 
buying, and group-buying marketing effects. Although group 
affective computing currently lacks a well-established research 
methodology, it is a promising direction for future studies.
Unique emotional carriers
Emotions are ubiquitous in human political, economic, and cul-
tural life, and the carriers of emotions are continually increasing 
in number, making them a popular research topic. Several areas 
have been identified as key carriers of emotions. (a) Political 
speeches: CORPS is a corpus that contains political speeches with 
markers indicating audience reactions such as applause, standing 
ovations, and boos [98]. Researchers can use this information to 
predict emotion-evoking actions and persuasive content that may 
induce empathy and sympathy in audiences. (b) Music and drama: 
Affective computing in music and drama provides a basis for the 
categorized retrieval of relevant emotional carriers. Advancements 
in artificial intelligence-generated content (AIGC) technology 
have made machine-generated music possible, and affective com-
puting can enhance the generation of music to conform to emo-
tional classifications. (c) Oil painting: As a representative art form, 
oil painting allows creators to express their innermost emotions. 
Its charm lies not in the degree of realism but in the emotions it 
conveys. Combining affective computing with oil painting 
would enable the exploration of artificial intelligence methods 
for emotional expression, the integration of technology and art, 
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
19
and the establishment of a library of emotion-inducing materials 
for oil paintings, thereby providing resources for the development 
of affective computing disciplines.
Outlook for future applications
Affective brain–computer interfaces
Affective brain–computer interfaces (aBCIs) are primarily 
designed to measure emotional states through neurological mea-
surements and to recognize and/or regulate human emotions. 
Currently, aBCIs are one of the main methods of realizing emo-
tional intelligence. At this stage, the most commonly used physi-
ological signals for emotional brain–computer interfaces are EEG 
signals, which map closely to an individual’s emotional state. As 
in motor brain–computer interfaces, the human brain plays the 
role of a controller for the entire system. The first step involves 
decoding an individual’s initial emotional state and then recogniz-
ing and understanding their emotions. Subsequently, a control 
strategy or system is designed to achieve the target emotion using 
control signals or parameters that provide feedback to the brain, 
thereby forming a closed-loop system.
Unlike facial expressions, physiological signals such as EEG 
signals are difficult to disguise and provide an accurate reflec-
tion of the real emotional state of the individual. As a result, 
affective brain–computer interfaces play a crucial role in clini-
cal diagnostics and therapy. Their uses include detecting work-
load and mental state, using neurofeedback for stress relief, 
aiding in the diagnosis of social anxiety and other disorders 
[76], and enabling objective assessment and intervention in 
depression. Furthermore, affective brain–computer interfaces 
have considerable potential for military applications. They can 
help maximize the physiological capabilities of individual sol-
diers, enhance their endurance and tolerance to extreme envi-
ronments, and improve their overall physical and mental 
fitness. These objectives are achieved by installing electroen-
cephalography electrodes inside combat helmets to detect 
threats and emotional signals emitted by the brain. The signals 
are then converted into computer language using computer 
algorithms, analyzed, and confirmed by combat command. 
Subsequently, threat warnings and reminders about emotional 
regulation are sent to the affected soldiers, and signals to 
cooperate in combat are transmitted to surrounding soldiers. 
In addition, direct transcranial current stimulation, transcra-
nial electromagnetic stimulation, and deep brain cortex stimu-
lation can act on the brain to eliminate fatigue, reduce stress 
and anxiety, control pain sensation, and enhance cognitive 
ability. This system helps improve the situational awareness of 
soldiers on the battlefield, thereby improving their ability to 
survive.
The primary obstacle to the application of affective brain–
computer interfaces is their unstable performance. Cross-modal 
affective models that rely on heterogeneous transfer learning 
(HTL) may be necessary for establishing reliable and robust aBCI 
technology in complex real-world environments. To address the 
missing-modalities problem, cross-modal emotion models com-
prehensively analyze signals from multiple modalities and extract 
correlation characteristics during the training process. In the 
testing stage, predictions are made based on partial modal infor-
mation. For example, correlating EEG signals with eye movement 
enables the use of eye movement alone to assess emotions in 
scenarios where collecting EEG signals is difficult. The HTL 
approach ensures that performance degradation in the absence 
of modalities is acceptable, thereby improving model robustness. 
In addition, transfer-learning techniques based on deep and gen-
erative adversarial networks can solve the problem of individual 
differences. These techniques enable generalization from the 
source domain to the target domain, thereby expanding the scope 
of possible applications of affective brain–computer interfaces.
Empathic human–computer dialogue
There have been 4 waves of change in the way people interact with 
machines. The first wave, represented by Microsoft, involved the 
organic fusion of the user interface, operating system, keyboard, 
and mouse. This greatly reduced the difficulty of human–­computer 
interaction and contributed to the rapid popularization of the 
personal computer. The second wave, represented by Google, 
involved the organic integration of search engine and internet 
technologies. This integration broke down information silos and 
considerably expanded the boundaries of interaction. The third 
wave, represented by Apple, involved the miniaturization of 
computing represented by the smartphone. This breakthrough 
removed the physical space limitations of human–computer inter-
action, enabling interconnectivity anytime, anywhere. Currently, 
we are in the fourth wave, represented by OpenAI. This wave 
involves the comprehensive application of a human–computer 
dialogue system that makes human–computer interaction more 
anthropomorphic and naturalized.
The essence of human–computer dialogue is to make human–
computer interaction more human-like. Humans exchange 
information through natural language and multiple senses, and 
human–computer interaction can imitate this process through 
multimodal information for joint analysis and decision-making. 
Human–computer dialogue involves a diverse range of signals, 
including speech, text, and images (such as individual facial 
expressions and body movements), conveying information in 
both the rational and perceptual dimensions. Linguistic text 
serves as the ontology of intent understanding, but emotional 
information conveyed through voice intonation, facial expres-
sions, and body movements plays a crucial role in disambigua-
tion, which is essential for in-depth communication between 
humans and machines. The use of different emotional colors to 
express the same sentence results in entirely different connota-
tions. As Nobel Prize winner Simon noted, emotion recognition 
is crucial for the communication and understanding of informa-
tion. Therefore, affective computing offers machines the ability 
to achieve deep contextual understanding.
In advanced technology fields, research has expanded to 
include machine expression and action generation, referred to as 
“multimodal emotional expression generation.” A current focus 
area is the development of a “virtual human” interface that not 
only appears human-like but also simulates human demeanor and 
behavior. For instance, voice-driven facial-expression animation 
generation technology can create virtual humans with facial 
expressions and lip, head, and body movements that closely resem-
ble those of real people. The virtual human no longer has an empty 
skin but appears more 3-dimensional and vivid. The personaliza-
tion of human–computer interaction lays the crucial foundations 
for future applications in areas such as elderly companions, intel-
ligent customer service, and mayor hotlines, revealing important 
prospects for practical use.
Emotion-assisted decision-making
Human–computer interaction involves both shallow and deep 
levels. At the shallow level, machines are equipped with the 
ability to read and speak, whereas at the deep level, they are 
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
20
capable of thinking and making decisions like humans. Nobel 
Prize winner Kahneman described human decision-making as 
entailing 2 processes: fast (System 1) and slow (System 2). The 
unconscious “System 1” relies on emotions, experience, and 
rapid judgments, while the conscious “System 2” relies on ratio-
nal deliberation. Emotions play an important role in advanced 
human thinking and decision-making. The book “Descartes’ 
Error” emphasizes that emotions are crucial for rational decision-­
making and behavior [99]. Numerous studies have indicated 
that purely rational decision-making may not always be the 
optimal solution for humans when dealing with problems due 
to the complexity of the social environment. Incorporating emo-
tional factors into the decision-making process may help indi-
viduals identify better solutions. Therefore, inputting emotional 
variables can enable machines to make decisions in a more human-­
like manner. In building a harmonious human–machine sym-
biotic society, it is essential to master this high-level function, 
which is also an important direction in affective computing 
research. The modeling of machine agents has begun to incor-
porate patterns of emotional influence on human rational decision-­
making and mechanisms for deciding and interrupting behaviors 
based on goals [100,101].
Emotion-assisted decision-making abilities can be applied 
widely across various fields of human–machine collaboration. 
For example, in production tool manipulation, the operator’s 
emotional state regarding operation specifications, safety aware-
ness, and accurate judgment has an impact. Monitoring and 
early warning of negative emotions, psychological stress, fatigue, 
and drowsiness, etc., can help identify potential anthropogenic 
risks to production safety. Machines can then optimize manage-
ment decisions, intervene early, and intervene intelligently to 
avoid major accidents. In assisted driving, negative emotions 
such as anger and anxiety can seriously affect the driver’s con-
centration and may lead to traffic accidents. Emotion-assisted 
decision making can be incorporated into driver monitoring 
systems (DMS) that use facial-expression recognition technol-
ogy and wearable devices to provide real-time monitoring of 
the driver’s emotional state. This approach equips the vehicle 
with enhanced safety performance and improves the overall 
driving experience [102].
Affective virtual reality
The metaverse is generating considerable interest in both indus-
trial and academic circles as the next generation of immersive, 
full-fledged internet. It is considered a theme park for digitized 
human beings, a virtual complex resulting from the development 
of cutting-edge technologies, and a utopia where the human body 
and consciousness can cross physical time and space. As a new 
type of future living space, the development of the metaverse 
cannot be limited to creating a virtual space parallel to the real 
world. It should exist in human life like air, enabling humans to 
shuttle freely between the virtual and real worlds. Affective virtual 
reality is crucial for constructing the metaverse because it can 
considerably enhance an individual’s experience of bodily owner-
ship, sense of agency, and situational awareness. In particular, an 
individual’s avatar in the metaverse, which is a core element of the 
metaverse construction, includes voice tone, facial expressions, 
body movements, and gestures that richly and 3-dimensionally 
express the individual’s emotions and create scenes and spaces 
for emotional twins [103]. As in movies and literature, complex 
and emotionally rich avatar characters engage audiences more 
than simple and stable characters do. This appeal creates the 
illusion that avatars are alive and pass the Turing test, which 
enhances the audience’s interest and engagement in the virtual 
world [104]. Affective virtual reality has considerable potential 
for applications in virtual reality socialization, virtual reality 
anchors, and virtual reality marketing.
Limitations
This bibliometric analysis has several limitations that should be 
acknowledged. First, the basic processing unit of information 
in this study is the article in its entirety, and the full content of 
the literature has not been systematically broken down, which 
may result in incomplete analysis and conclusions. Second, the 
assumption that the articles contain information of equal qual-
ity makes it difficult to consider the objective differences in the 
value of the literature. In future research, a combination of bib-
liometrics and content analysis could be used to enhance the 
reliability and accuracy of the analytical results.
Conclusion
Affective computing is a rapidly developing field with broad 
prospects. Emerging forces such as China and India are injecting 
strong momentum into the field. However, the field of affective 
computing also faces challenges and development trends in 10 
aspects, including cultural background modeling, ethical and 
moral norms, and multimodal integration. Affective computing 
has great potential for application in 4 major fields and requires 
the joint efforts of researchers and industry practitioners. These 
efforts can make affective computing beneficial to the progress 
of human society by building a more anthropomorphic, harmo-
nious, and natural human–computer symbiotic social form.
Acknowledgments
Funding: This work was supported by the National Natural 
Science Foundation of China (grant number T2241018), the 
Zhejiang Provincial Natural Science Foundation of China (grant 
number LQ22C090007), the National Science and Technology 
Major Project of the Ministry of Science and Technology of 
China (grant number 2021ZD0114303), and the Open Research 
Project of the Key Laboratory of Brain-Machine Intelligence 
for Information Behavior (Ministry of Education of Shanghai) 
(grant numbers 2023KFKT003 and 2022KFKT002).
Author contributions: G.P.: Conceptualization, methodology, 
writing (original draft), and funding acquisition. H.L.: Methodology, 
data curation, formal analysis, and visualization. Y.L.: Writing 
(review and editing). Y.W.: Data curation, formal analysis, and 
visualization. S.H.: Writing (original draft). T.L.: Resources, super-
vision, validation, and funding acquisition.
Competing interests: The authors declare that they have no 
competing interests.
Data Availability
The data and code used in this study are available from the 
corresponding author upon request.
References
	 1.	 Keltner D, Sauter D, Tracy J, Cowen A. Emotional expression: 
Advances in basic emotion theory. J Nonverbal Behav. 
2019;43(2):133–160.
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
21
	 2.	 Soleymani M, Garcia D, Jou B, Schuller B, Chang S-F, Pantic M. 
A survey of multimodal sentiment analysis. Image Vis Comput. 
2017;65:3–14.
	 3.	 Bach DR, Dayan P. Algorithms for survival: A comparative 
perspective on emotions. Nat Rev Neurosci. 2017;18:311–319.
	 4.	 Chen L, Zhou M, Wu M, She J, Liu Z, Dong F, Hirota K. 
Three-layer weighted fuzzy support vector regression 
for emotional intention understanding in human–robot 
interaction. IEEE Trans Fuzzy Syst. 2018;26(5):2524–2538.
	 5.	 Kahneman D. Thinking, fast and slow. Macmillan, London, 
UK: Farrar, Straus and Giroux; 2011.
	 6.	 Fanselow MS. Emotion, motivation and function. Curr Opin 
Behav Sci. 2018;19:105–109.
	 7.	 Lopes PN, Salovey P, Coté S, Beers M. Emotion regulation 
abilities and the quality of social interaction. Emotion. 
2005;5:113–118.
	 8.	 Suvilehto JT, Glerean E, Dunbar RIM, Hari R, Nummenmaa L. 
Topography of social touching depends on emotional bonds 
between humans. Proc Natl Acad Sci U S A. 2015;112: 
13811–13816.
	
9.	 Picard RW. Affective computing. Cambridge (MA): MIT Press; 1997.
	 10.	 Ekman P. Are there basic emotions? Psychol Rev. 
1992;99(3):550–553.
	 11.	 Russell JA. A circumplex model of affect. J Pers Soc Psychol. 
1980;39:1161–1178.
	 12.	 Mehrabian A. Framework for a comprehensive description 
and measurement of emotional states. Genet Soc Gen  
Psychol Monogr. 1995;121(3):339–361.
	 13.	 Bakker I, Van Der Voordt T, Vink P, De Boon J. Pleasure, 
arousal, dominance: Mehrabian and russell revisited.  
Curr Psychol. 2014;33:405–421.
	 14.	 Pozzi FA, Fersini E, Messina E, Liu B. Chapter 1—Challenges of 
sentiment analysis in social networks: An overview. In: Pozzi FA, 
Fersini E, Messina E, Liu B, editors, Sentiment analysis in  
social networks. Boston: Morgan Kaufmann; 2017. p. 1–11.
	 15.	 Maas AL, Daly RE, Pham PT, Huang D, Ng AY, Potts C.  
Learning word vectors for sentiment analysis. Poster 
presented at: Proceedings of the 49th Annual Meeting of the 
Association for Computational Linguistics: Human Language 
Technologies; Portland, Oregon, USA; 2011. p. 142–150.
	 16.	 Socher R, Perelygin A, Wu J, Chuang J, Manning CD, 
Ng AY, Potts C. Recursive deep models for semantic 
compositionality over a sentiment treebank. Paper presented 
at: Proceedings of the 2013 Conference on Empirical 
Methods in Natural Language Processing; 2013; Seattle, WA, 
USA. p. 1631–1642.
	 17.	 Blitzer J, Dredze M, Pereira F. Biographies, Bollywood, 
boom-boxes and blenders: Domain adaptation for sentiment 
classification. Poster presented at: Proceedings of the 45th 
Annual Meeting of the Association of Computational 
Linguistics; 2007; Prague, Czech Republic. p. 440–447.
	 18.	 Burkhardt F, Paeschke A, Rolfes M, Sendlmeier WF, Weiss B.  
A database of German emotional speech. Interspeech. 
2005;5:1517–1520.
	 19.	 McKeown G, Valstar M, Cowie R, Pantic M, Schroder M. The 
SEMAINE Database: Annotated multimodal records  
of emotionally colored conversations between a person and 
a limited agent. IEEE Trans Affect Comput.  
2011;3(1):5–17.
	 20.	  Xu L, Xu M, Yang D. Chinese emotional speech database for 
the detection of emotion variations. J Tsinghua Univ Nat Sci. 
2009;49(S1):1413–1418.
	 21.	 Poria S, Cambria E, Bajpai R, Hussain A. A review of affective 
computing: From unimodal analysis to multimodal fusion. 
Inf Fusion. 2017;37:98–125.
	 22.	 Wang Y, Song W, Tao W, Liotta A, Yang D, Li X, Gao S, Sun Y, 
Ge W, Zhang W, et al. A systematic review on affective 
computing: Emotion models, databases, and recent advances. 
Inf Fusion. 2022;83–84:19–52.
	 23.	 Zhang Z, Luo P, Loy CC, Tang X. From facial expression 
recognition to interpersonal relation prediction. Int J Comput Vis. 
2018;126:550–569.
	 24.	 Mollahosseini A, Hasani B, Mahoor MH. AffectNet: 
A database for facial expression, valence, and arousal 
computing in the wild. IEEE Trans Affect Comput. 
2019;10:18–31.
	 25.	 Li S, Deng W, Du J. Reliable crowdsourcing and deep locality-
preserving learning for expression recognition in the wild. 
Paper presented at: 2017 IEEE Conference on Computer 
Vision and Pattern Recognition (CVPR); 2017; . Honolulu, HI. 
p. 2584–2593.
	 26.	 Li X, Pfister T, Huang X, Zhao G, Pietikäinen M. A 
spontaneous micro-expression database: Inducement, 
collection and baseline. Paper presented at: 2013 10th IEEE 
International Conference and Workshops on Automatic Face 
and Gesture Recognition (FG); 2013; Shanghai, China. p. 1–6.
	 27.	 Galvão F, Alarcão SM, Fonseca MJ. Predicting exact valence and 
arousal values from EEG. Sensors (Basel). 2021;21(10):3414.
	 28.	 Shalbaf A, Bagherzadeh S, Maghsoudi A. Transfer learning 
with deep convolutional neural network for automated 
detection of schizophrenia from EEG signals. Phys Eng  
Sci Med. 2020;43(4):1229–1239.
	 29.	 Shirahama K, Grzegorzek M. Emotion recognition based 
on physiological sensor data using codebook approach. In: 
Piętka E, Badura P, Kawa J, Wieclawek W, editors. Information 
technologies in medicine. Cham: Springer International 
Publishing; 2016. p. 27–39.
	 30.	 Koelstra S, Muhl C, Soleymani M, Lee J-S, Yazdani A, 
Ebrahimi T, Pun T, Nijholt A, Patras I. DEAP: A database 
for emotion analysis using physiological signals. IEEE Trans 
Affect Comput. 2012;3(1):18–31.
	 31.	 Duan R-N, Zhu J-Y, Lu B-L. Differential entropy feature 
for EEG-based emotion classification. Paper presented at: 
2013 6th International IEEE/EMBS Conference on Neural 
Engineering (NER); 2013; San Diego, CA, USA. p. 81–84.
	 32.	 Schmidt P, Reiss A, Duerichen R, Marberger C,  
Van Laerhoven K. Introducing WESAD, a multimodal dataset 
for wearable stress and affect detection. Paper presented at: 
Proceedings of the 20th ACM International Conference on 
Multimodal Interaction; 2018; Boulder, CO, USA. p. 400–408.
	 33.	 Taboada M, Brooke J, Tofiloski M, Voll K, Stede M. Lexicon-
based methods for sentiment analysis. Comput Linguist. 
2011;37(2):267–307.
	 34.	 Ding X, Liu B, Yu PS. A holistic lexicon-based approach 
to opinion mining. Paper presented at: Proceedings of the 
International Conference on Web Search and Web Data 
Mining—WSDM ’08; 2008; Palo Alto, CA, USA. p. 231.
	 35.	 Mullen T, Collier N. Sentiment analysis using support vector 
machines with diverse information sources. Paper presented 
at: Proceedings of the 2004 Conference on Empirical 
Methods in Natural Language Processing; 2004; Barcelona, 
Spain. p. 412–418.
	 36.	 Pak A, Paroubek P. Text representation using dependency 
tree subgraphs for sentiment analysis. In: Xu J, Yu G, 
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
22
Zhou S, Unland R, editors. Database systems for advanced 
applications. Berlin, Heidelberg: Springer Berlin Heidelberg; 
2011. p. 323–332.
	 37.	 Deng J, Ren F. A survey of textual emotion recognition and 
its challenges. IEEE Trans Affect Comput. 2023;14(1):49–67.
	 38.	 Heaton CT, Schwartz DM. Language models as emotional 
classifiers for textual conversation. Paper presented at: 
Proceedings of the 28th ACM International Conference on 
Multimedia; 2020; Seattle, WA, USA. p. 2918–2926.
	 39.	 Mao R, Liu Q, He K, Li W, Cambria E. The biases of pre-
trained language models: An empirical study on prompt-
based sentiment analysis and emotion detection. IEEE Trans 
Affect Comput. 2022;14(3):1743–1753.
	 40.	 Lee CM, Narayanan SS. Toward detecting emotions in 
spoken dialogs. IEEE Trans Audio Speech Lang Process. 
2005;13(2):293–303.
	 41.	 Lugger M, Yang B. The relevance of voice quality features in 
speaker independent emotion recognition. Paper presented 
at: 2007 IEEE International Conference on Acoustics, 
Speech and Signal Processing—ICASSP ’07; 2007; 
Honolulu, HI, USA. p. IV-17–IV–20.
	 42.	 Likitha MS, Gupta SRR, Hasitha K, Raju AU. Speech based 
human emotion recognition using MFCC.Paper presented at: 
2017 International Conference on Wireless Communications, 
Signal Processing and Networking (WiSPNET); 2017; 
Chennai, India. p. 2257–2260.
	 43.	 Bitouk D, Verma R, Nenkova A. Class-level spectral features 
for emotion recognition. Speech Commun. 2010;52(7–8): 
613–625.
	 44.	 Alisamir S, Ringeval F. On the evolution of speech 
representations for affective computing: A brief 
history and critical overview. IEEE Signal Process. Mag. 
2021;38(6):12–21.
	 45.	 Stappen L, Baird A, Schumann L, Schuller B. The multimodal 
sentiment analysis in car reviews (MuSe-CaR) dataset: 
Collection, insights and improvements. IEEE Trans Affect 
Comput. 2023;14(2):1334–1350.
	 46.	 Huang Z, Dong M, Mao Q, Zhan Y. Speech emotion 
recognition using CNN. Paper presented at: Proceedings of 
the 22nd ACM International Conference on Multimedia; 
2014; New York, NY, USA. p. 801–804.
	 47.	 Neumann M, Vu NT. Improving speech emotion recognition 
with unsupervised representation learning on unlabeled 
speech. Paper presented at: ICASSP 2019 - 2019  
IEEE International Conference on Acoustics, Speech and 
Signal Processing (ICASSP); 2019; Brighton, UK.  
p. 7390–7394.
	 48.	 Abdelwahab M, Busso C. Domain adversarial for acoustic 
emotion recognition. IEEE/ACM Trans Audio Speech  
Lang Process. 2018;26(12):2423–2435.
	 49.	 Shan C, Gong S, McOwan PW. Facial expression recognition 
based on Local Binary Patterns: A comprehensive study. 
Image Vis Comput. 2009;27(6):803–816.
	 50.	 Chao W-L, Ding J-J, Liu J-Z. Facial expression recognition 
based on improved local binary pattern and class-
regularized locality preserving projection. Signal Process. 
2015;117:1–10.
	 51.	 James W. Review of la pathologie des emotions by Ch. Féré. 
Philos Rev. 1893;2:333–336.
	 52.	 Cannon WB. The James-Lange theory of emotions: A 
critical examination and an alternative theory. Am J Psychol. 
1987;100:567–586.
	 53.	 Kim M-K, Kim M, Oh E, Kim S-P. A review on the 
computational methods for emotional state estimation 
from the human EEG. Comput Math Methods Med. 
2013;2013:Article e573734.
	 54.	 Craik A, He Y, Contreras-Vidal JL. Deep learning for 
electroencephalogram (EEG) classification tasks: A review.  
J Neural Eng. 2019;16(3):Article 031001.
	 55.	 Maria MA, Akhand MAH, Shimamura T. Emotion 
recognition from EEG with normalized mutual 
information and convolutional neural network. Paper 
presented at: 2022 12th International Conference on 
Electrical and Computer Engineering (ICECE); 2022; 
Dhaka, Bangladesh. p. 372–375.
	 56.	 Rahman MM, Sarkar AK, Hossain MA, Hossain MS, Islam MR, 
Hossain MB, Quinn JMW, Moni MA. Recognition of human 
emotions using EEG signals: A review. Comput Biol Med. 
2021;136:Article 104696.
	 57.	 D’mello SK, Kory J. A review and meta-analysis of 
multimodal affect detection systems. ACM Comput Surv. 
2015;47(3):1–36.
	 58.	 He Z, Li Z, Yang F, Wang L, Li J, Zhou C, Pan J. Advances in 
multimodal emotion recognition based on brain–computer 
interfaces. Brain Sci. 2020;10(10):687.
	 59.	 Filippini C, Perpetuini D, Cardone D, Chiarelli AM, Merla A. 
Thermal infrared imaging-based affective computing and its 
application to facilitate human robot interaction: A review. 
Appl Sci. 2020;10(8):2924.
	 60.	 Spezialetti M, Placidi G, Rossi S. Emotion recognition 
for human-robot interaction: Recent advances and future 
perspectives. Front Robot AI. 2020;7:Article 532279.
	 61.	 Peng Y, Fang Y, Xie Z, Zhou G. Topic-enhanced emotional 
conversation generation with attention mechanism.  
Knowl Based Syst. 2019;163:429–437.
	 62.	 Dybala P, Ptaszynski M, Rzepka R, Araki K, Sayama K. 
Metaphor, humor and emotion processing in human-
computer interaction. Int J Comput Linguist Res. 2013.
	 63.	 Goswamy T, Singh I, Barkati A, Modi A. Adapting a 
language model for controlled affective text generation. 
Paper presented at: Proceedings of the 28th International 
Conference on Computational Linguistics; 2020; Barcelona, 
Spain. p. 2787–2801.
	 64.	 Lei Y, Yang S, Wang X, Xie L. MsEmoTTS: Multi-scale 
emotion transfer, prediction, and control for emotional 
speech synthesis. IEEE/ACM Trans Audio Speech  
Lang Process. 2022;30:853–864.
	 65.	 Crawford K. Time to regulate AI that interprets human 
emotions. Nature. 2021;592(7853):167.
	 66.	 Ho M-T, Mantello P, Nguyen H-KT, Vuong Q-H. Affective 
computing scholarship and the rise of China: A view from 
25 years of bibliometric data. Humanit Soc Sci Commun. 
2021;8:Article 282.
	 67.	 Yadegaridehkordi E, Noor NFBM, Ayub MNB, Affal HB, 
Hussin NB. Affective computing in education: A systematic 
review and future research. Comput Educ. 2019;142: 
Article 103649.
	 68.	 Wu C-H, Huang Y-M, Hwang J-P. Review of affective 
computing in education/learning: Trends and challenges.  
Br J Educ Technol. 2016;47(6):1304–1323.
	 69.	 Liberati G, Veit R, Kim S, Birbaumer N, von Arnim C, 
Jenner A, Lulé D, Ludolph AC, Raffone A, Belardinelli MO, 
da Rocha JD, Sitaram R. Development of a binary fMRI-
BCI for Alzheimer patients: A semantic conditioning 
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
23
paradigm using affective unconditioned stimuli. Paper 
presented at: 2013 Humaine Association Conference on 
Affective Computing and Intelligent Interaction; 2013; 
Geneva, Switzerland. p. 838–842.
	 70.	 Yuvaraj R, Murugappan M, Mohamed Ibrahim N,  
Iqbal Omar M, Sundaraj K, Mohamad K, Palaniappan R, 
Mesquita E, Satiyan M. On the analysis of EEG power, frequency 
and asymmetry in Parkinson’s disease during emotion 
processing. Behav Brain Funct. 2014;10:12.
	 71.	 Baki P, Kaya H, Çiftçi E, Güleç H, Salah AA. A multimodal 
approach for mania level prediction in bipolar disorder.  
IEEE Trans Affect Comput. 2022;13(4):2119–2131.
	 72.	 Mohammadi-Ziabari SS, Treur J. Integrative biological, 
cognitive and affective modeling of a drug-therapy for a post-
traumatic stress disorder. In: Fagan D, Martín-Vide C,  
O’Neill M, Vega-Rodríguez MA, editors. Theory and 
practice of natural computing. Cham: Springer International 
Publishing; 2018. p. 292–304.
	 73.	 Tivatansakul S, Ohkura M. Healthcare system focusing on 
emotional aspects using augmented reality—Implementation 
of breathing control application in relaxation service. Paper 
presented at: 2013 International Conference on Biometrics 
and Kansei Engineering; 2013; Tokyo, Japan. p. 218–222.
	 74.	 Zenonos A, Khan A, Kalogridis G, Vatsikas S, Lewis T, 
Sooriyabandara M. HealthyOffice: Mood recognition at work 
using smartphones and wearable sensors. Paper presented at: 
2016 IEEE International Conference on Pervasive Computing 
and Communication Workshops (PerCom Workshops); 
2016; Sydney, NSW, Australia. p. 1–6.
	 75.	 Weziak-Bialowolska D, Bialowolski P, Lee MT, Chen Y, 
VanderWeele TJ, McNeely E. Psychometric properties 
of flourishing scales from a comprehensive well-being 
assessment. Front Psychol. 2021;12:Article 652209.
	 76.	 Pei G, Xiao Q, Pan Y, Li T, Jin J. Neural evidence of face 
processing in social anxiety disorder: A systematic review 
with meta-analysis. Neurosci Biobehav Rev. 2023;152: 
Article 105283.
	 77.	 Pei G, Li T. A literature review of EEG-based affective 
computing in marketing. Front Psychol. 2021;12:Article 
602843.
	 78.	 Valle-Cruz D, Fernandez-Cortez V, López-Chau A, 
Sandoval-Almazán R. Does twitter affect stock market 
decisions? Financial sentiment analysis during pandemics: A 
comparative study of the H1N1 and the COVID-19 periods. 
Cognit Comput. 2022;14(1):372–387.
	 79.	 Gómez LM, Cáceres MN. Applying data mining for 
sentiment analysis in music. In: De la Prieta F, Vale Z, 
Antunes L, Pinto T, Campbell AT, Julián V, Neves AJR, 
Moreno MN, editors. Trends in cyber-physical multi-agent 
systems. Cham: Springer International Publishing; 2018.  
p. 198–205.
	 80.	 Yu L, Zhang W, Wang J, Yu Y. SeqGAN: Sequence generative 
adversarial nets with policy gradient. Paper presented 
at: Proceedings of the AAAI Conference on Artificial 
Intelligence; 2017; San Francisco, CA, USA. p. 31.
	 81.	 Oliveira HG. A survey on intelligent poetry generation: 
Languages, features, techniques, reutilisation and 
evaluation. Paper presented at: Proceedings of the 10th 
International Conference on Natural Language Generation; 
2017; Santiago de Compostela, Spain. p. 11–20.
	 82.	 Zhang X, Lapata M. Chinese Poetry Generation with 
Recurrent Neural Networks. Paper presented at: Proceedings 
of the 2014 Conference on Empirical Methods in Natural 
Language Processing (EMNLP); 2014; Doha, Qatar.  
p. 670–680.
	 83.	 Mao G, Liu X, Du H, Zuo J, Wang L. Way forward for 
alternative energy research: A bibliometric analysis during 
1994–2013. Renew Sustain Energy Rev. 2015;48:276–286.
	 84.	 Haustein S, Larivière V. The use of bibliometrics for 
assessing research: Possibilities, limitations and adverse 
effects. In: Welpe I, Wollersheim J, Ringelhan S, Osterloh M, 
editors. Incentives and performance: Governance of research 
organizations. Cham: Springer International Publishing; 2014. 
p. 121–139.
	 85.	 Hammarfelt B, Rushforth AD. Indicators as judgment 
devices: An empirical study of citizen bibliometrics in 
research evaluation. Res Eval. 2017;26(3):169–180.
	 86.	 Wang J, Veugelers R, Stephan P. Bias against novelty in 
science: A cautionary tale for users of bibliometric indicators. 
Res Policy. 2017;46(8):1416–1436.
	 87.	 Van Eck NJ, Waltman L. Software survey: VOSviewer, a 
computer program for bibliometric mapping. Scientometrics. 
2010;84(2):523–538.
	 88.	 Šabanović S. Robots in society, society in robots. Int J of  
Soc Robotics. 2010;2:439–450.
	 89.	 Hofstede G. Culture’s consequences: Comparing values, 
behaviors, institutions and organizations across nations. 
London, UK: Sage; 2001.
	 90.	 Mehrabian A. Communication without words. Communication 
theory. 2nd ed. London, UK: Routledge; 2008.
	 91.	 Du S, Tao Y, Martinez AM. Compound facial expressions of 
emotion. Proc Natl Acad Sci U S A. 2014; 111(15):E1454–E1462.
	 92.	 Martinez AM. Computational models of face perception. 
Curr Dir Psychol Sci. 2017;26(3):263–269.
	 93.	 Dragano N, Lunau T. Technostress at work and mental 
health: Concepts and research results. Curr Opin Psychiatry. 
2020;33(4):407–413.
	 94.	 LeDoux J. The emotional brain: The mysterious underpinnings of 
emotional life. New York, NY, USA: Simon and Schuster; 1998.
	 95.	 Pessoa L, Adolphs R. Emotion processing and the amygdala: 
From a ‘low road’ to ‘many roads’ of evaluating biological 
significance. Nat Rev Neurosci. 2010;11(11):773–782.
	 96.	 Price TF, Peterson CK, Harmon-Jones E. The emotive 
neuroscience of embodiment. Motiv Emot. 2012;36:27–37.
	 97.	 Cytowic RE. Synesthesia: A union of the senses. Cambridge, 
MA, USA: MIT Press; 2002.
	 98.	 Guerini M, Strapparava C, Stock O. CORPS: A corpus of 
tagged political speeches for persuasive communication 
processing. J Inf Technol Politics. 2008;5(1):19–32.
	 99.	 Damasio AR. Descartes’ error. New York, NY, USA: Random 
House; 2006.
	100.	 Scheutz M. The inherent dangers of unidirectional emotional 
bonds between humans and social robots. In: Lin P,  
Abney K, Bekey GA, editors. Robot ethics: The ethical and 
social implications of robotics. Cambridge (MA): MIT Press; 
2011. p. 205.
	101.	 Scheutz M, Schermerhorn P. Dynamic robot autonomy: 
Investigating the effects of robot decision-making in a 
human-robot team task. Paper presented at: Under review 
for the 4th ACM International Conference on Human-Robot 
Interaction; 2009; La Jolla, CA, USA.
	102.	 Gill R, Singh J. A review of neuromarketing techniques and 
emotion analysis classifiers for visual-emotion mining. Paper 
presented at: 2020 9th International Conference System 
Downloaded from https://spj.science.org on March 19, 2026
Pei et al. 2024 | https://doi.org/10.34133/icomputing.0076
24
Modeling and Advancement in Research Trends (SMART); 
2020; Moradabad, India. p. 103–108.
	103.	 Pei G, Li B, Li T, Xu R, Dong J, Jin J. Decoding emotional 
valence from EEG in immersive virtual reality. Paper 
presented at: 2022 Asia-Pacific Signal and Information 
Processing Association Annual Summit and Conference 
(APSIPA ASC); 2022; Chiang Mai, Thailand. p. 1469–1476.
	104.	 Ochs M, Sadek D, Pelachaud C. A formal model of emotions 
for an empathic rational dialog agent. Auton Agent Multi-
Agent Syst. 2012;24:410–440.
Downloaded from https://spj.science.org on March 19, 2026
Affective Computing: Recent Advances, Challenges, and Future Trends
Guanxiong Pei, Haiying Li, Yandi Lu, Yanlei Wang, Shizhen Hua, and Taihao Li
Citation: Pei G, Li H, Lu Y, Wang Y, Hua S, Li T. Affective Computing: Recent Advances, Challenges, and Future
Trends. Intell Comput. 2024;3:0076.  DOI: 10.34133/icomputing.0076
Affective computing is a rapidly growing multidisciplinary field that encompasses computer science, engineering,
psychology, neuroscience, and other related disciplines. Although the literature in this field has progressively grown
and matured, the lack of a comprehensive bibliometric analysis limits the overall understanding of the theory, technical
methods, and applications of affective computing. This review presents a quantitative analysis of 33,448 articles
published in the period from 1997 to 2023, identifying challenges, calling attention to 10 technology trends, and outlining
a blueprint for future applications. The findings reveal that the emerging forces represented by China and India are
transforming the global research landscape in affective computing, injecting transformative power and fostering
extensive collaborations, while emphasizing the need for more consensus regarding standard setting and ethical norms.
The 5 core research themes identified via cluster analysis not only represent key areas of international interest but
also indicate new research frontiers. Important trends in affective computing include the establishment of large-scale
datasets, the use of both data and knowledge to drive innovation, fine-grained sentiment classification, and multimodal
fusion, among others. Amid rapid iteration and technology upgrades, affective computing has great application prospects
in fields such as brain–computer interfaces, empathic human–computer dialogue, assisted decision-making, and virtual
reality.
Image
View the article online
https://spj.science.org/doi/10.34133/icomputing.0076
Use of this article is subject to the Terms of service
Intelligent Computing (ISSN 2771-5892) is published by the American Association for the Advancement of Science. 1200 New York Avenue
NW, Washington, DC 20005. 
Copyright © 2024 Guanxiong Pei et al.
Exclusive licensee Zhejiang Lab. No claim to original U.S. Government Works. Distributed under a Creative Commons Attribution License
4.0 (CC BY 4.0).
Downloaded from https://spj.science.org on March 19, 2026
