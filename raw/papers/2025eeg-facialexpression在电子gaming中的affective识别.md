InSight: RIVIER ACADEMIC JOURNAL, VOLUME 20, NUMBER 1, FALL 2025
 
 
Copyright © 2025 Bhaskar Abburi, Akash Reddy Reddy, Haran Kumar Ravalkole, Akhil Bochu, Kishore Dhulipalla, Santosh Kumar 
Pooja, and Darlien Barker. Published by Rivier University, with permission. ISSN 1559-9388 (online version).  
ISSN 1559-9396 (CD-ROM version).   
 
          1  
 
Abstract 
This study explores the integration of multimodal approaches to enhance emotion recognition in gaming 
and virtual reality (VR) contexts. By leveraging a combination of electroencephalography (EEG), facial 
expression analysis, and in-game data, the research aims to develop more accurate and responsive 
emotion detection systems. The methodology focuses on advanced neural network architectures, such as 
Convolutional Neural Networks (CNNs) and Transformers, to process and classify emotional states 
dynamically. Additionally, mechanisms like dynamic difficulty adjustment (DDA) and real-time 
physiological monitoring are employed to adapt gaming experiences to players’ emotional states. The 
results demonstrate significant advancements in player engagement, social-emotional skill development, 
and adaptive gameplay design. The implications of this research extend beyond gaming to include 
applications in healthcare and education, particularly in personalized therapeutic and learning 
environments. This work underscores the transformative potential of emotion-driven systems in creating 
immersive and user-centric digital experiences. Our contribution provides a summary of recent 
advancements in emotion recognition systems, highlighting the integration of multimodal approaches, 
including EEG, facial expression analysis, and in-game metrics, to improve real-time emotion detection 
and adaptive gaming experiences.  
I. Introduction  
The integration of emotion recognition systems in gaming and virtual reality (VR) applications has the 
potential to revolutionize user engagement by tailoring experiences to individual emotional states [1]. These 
systems leverage advanced technologies to detect and interpret emotions in real-time, enabling more 
personalized and immersive interactions [2]. Previous studies have demonstrated promising results using 
modalities such as EEG signals and facial expression analysis to predict emotions, but challenges related to 
data variability, context sensitivity, and real-time adaptability remain significant hurdles [3]. 
Previous studies have shown promising results using EEG and facial expression analysis to predict 
emotions, yet challenges such as data variability and real-time adaptability persist, as shown in Tables I, II, V, 
VI, III, and IV. 
We explored innovative approaches that combine multimodal data, including physiological signals and 
behavioral analysis, to create more immersive and adaptive gaming environments. In Table I, we outline 
advancements in emotion recognition and adaptive gaming technologies. Table II highlights key 
contributions and methodologies in EEG-based emotion recognition, while Table III showcases innovations 
in emotion recognition across gaming, VR, and educational systems. Finally, Table IV discusses recent 
A SUMMARY OF EMOTION RECOGNITION IN VIDEO GAMES 
 
Bhaskar Abburi, Akash Reddy Reddy, Scarlet Haran Kumar Ravalkole, Akhil Bochu,  
Kishore Dhulipalla, Santosh Kumar Pooja, 
Graduate students, Computer Science Department, Rivier University 
and  
Darlien Barker, 
Assistant Professor, Computer Science Department, Rivier University 
 
Keywords: Multimodal Analysis, Emotion Recognition, Adaptive Gaming, EEG Integration, 
Facial Expression Analysis, Gaming Metrics 
Bhaskar Abburi, Akash Reddy Reddy, Haran Kumar Ravalkole, Akhil Bochu,  
Kishore Dhulipalla, Santosh Kumar Pooja, and Darlien Barker  
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          2  
advancements in emotion recognition systems, summarizing their impact on gameplay, healthcare, and 
education. These insights collectively emphasize the growing importance of integrating multimodal systems 
for real-time emotion detection and adaptive gaming experiences. 
 
 
Fig. 1. A participant playing VR games while wearing wearable devices, providing subjective assessments [4]. 
 
This research explores innovative approaches that combine multimodal data, including physiological 
signals and behavioral patterns, to enhance the adaptability and responsiveness of these systems [5]. By 
addressing these challenges, this work aims to advance the development of emotion-driven applications with 
transformative potential in fields such as gaming, healthcare, and education, ultimately creating more 
engaging and meaningful user experiences [6]. 
A. Problem 
Video games and virtual reality environments provide dynamic platforms for analyzing and adapting to 
player emotions. However, understanding and modeling these emotional responses remains a challenge due 
to the complex interplay of physiological signals, user behaviors, and environmental stimuli. Current 
emotion recognition systems often face limitations in accuracy, adaptability, and the integration of 
multimodal data. 
II. Literature Review  
Recent studies have explored how video games and virtual reality (VR) can decode and adapt to player 
emotions, demonstrating significant advancements in emotion recognition. Research has shown that 
emotions such as boredom and humor can be detected with up to 98.21% accuracy through EEG analysis and 
the GAMEEMO dataset using Random Forest models [7]. Additionally, VR horror games have been used to 
detect fear through physiological signals like heart rate and movement, achieving 90.47% accuracy [8]. VR 
exercise games have also benefited from improved emotional detection by analyzing cleaned data, leading to 
better adaptive designs for these games [9]. These studies underscore the potential of emotion-adaptive 
gaming applications, paving the way for more responsive and immersive player experiences.  
Game design research has increasingly focused on integrating emotion regulation and dynamic responses 
to enhance player engagement. Studies have found that longer gameplay can intensify emotions, both 
positive and negative, highlighting the importance of emotional regulation during play [10]. Dynamic 
difficulty adjustment (DDA), which tailors the game’s challenge level based on player emotions, has shown 
promise in improving engagement, particularly in first-person shooter games, although its effectiveness 
varies across different player types [11]. Further, serious games like ”Emotion Detectives” have proven 
effective in improving emotion recognition in children with autism and ADHD [12]. These advancements in 
emotional responsiveness in game design also extend to addressing toxic behaviors in multiplayer games 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          3  
A SUMMARY OF EMOTION RECOGNITION IN VIDEO GAMES 
[13] and exploring culturally adaptive frameworks that integrate psychology and game design to enhance 
emotional engagement [14]. 
 
Table I. Advancements in emotion recognition and adaptive gaming technologies 
 
 
Recent studies have highlighted the growing role of electroencephalography (EEG) in understanding and 
enhancing emotional experiences in gaming. Lim and Teo (2024) demonstrated how EEG data mining and 
machine learning can predict player emotions during gameplay, offering valuable insights for game design 
[17]. Similarly, Du et al. (2023) used convolutional and fuzzy neural networks to classify for personalized 
gaming experiences [18]. The GAMEEMO dataset, provided by Alakus et al. (2020), serves as a robust 
resource for emotion recognition research by offering EEG signals captured during various gaming scenarios 
Bhaskar Abburi, Akash Reddy Reddy, Haran Kumar Ravalkole, Akhil Bochu,  
Kishore Dhulipalla, Santosh Kumar Pooja, and Darlien Barker  
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          4  
[19]. These studies underscore EEG technology’s potential to integrate emotional feedback into game design, 
transforming gameplay interactions. 
 
 
 
Fig. 2. Accuracy rates for Level Features Fusion for Different SVM’s Kernels in Arousal and Valence Model [22]. 
 
Table II. Key contributions and methodologies in EEG-based emotion recognition 
 
 
The integration of multimodal approaches has further advanced emotion recognition systems by combining 
EEG with other physiological and behavioral data. Yang et al. (2018) used electrocardiography (ECG) and 
electromyography (EMG) to detect emotional responses during gameplay, paving the way for more immersive 
gaming experiences [1]. Additionally, Andreu-Perez et al. (2021) employed functional near infrared spectroscopy 
(fNIRS) and facial emotion analysis, achieving a classification accuracy of 91.44% in decoding gamer expertise 
[20]. Research by Abramov et al. (2022) explored emotional dynamics in esports tournaments using speech 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          5  
A SUMMARY OF EMOTION RECOGNITION IN VIDEO GAMES 
analysis and hidden Markov models, advancing the psychology of competitive gaming [21]. These advancements 
demonstrate the potential of emotion recognition in enhancing gaming immersion and contributing to broader 
applications in healthcare, education, and human-computer interaction. 
 
Table III. Innovations in emotion recognition across gaming, VR, and educational systems 
 
 
 
Bhaskar Abburi, Akash Reddy Reddy, Haran Kumar Ravalkole, Akhil Bochu,  
Kishore Dhulipalla, Santosh Kumar Pooja, and Darlien Barker  
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          6  
Recent developments in emotion recognition have increasingly leveraged gaming and virtual environments as 
dynamic platforms for analyzing and adapting to users’ emotional states. For instance, studies like Emo Galaxy 
demonstrated how computer games can improve emotional recognition and social skills in students with 
intellectual disabilities. Through a quasi-experimental design, the study showed significant improvements in the 
experimental group’s social skills, underscoring the potential of emotion-focused games in developmental 
interventions [27]. Similarly, mobile applications like Chezer, utilizing multimodal games, achieved 90% 
accuracy in detecting children’s emotions, offering an accessible and cost-effective tool for families in low-
income settings [6]. EmoAnim further explored emotion recognition by assessing children’s ability to identify 
emotions through animations, particularly distinguishing between typically developing children and those with 
autism, thus providing a novel method for remote autism screening [28]. 
 
 
Fig. 3. 2D and 3D examples of eight emotional expressions from task 1 to task 8 (from left to right), respectively [30]. 
 
The integration of emotion recognition into immersive virtual reality (VR) environments has enhanced user 
behavior analysis and adaptive systems. For example, a dynamic social presence visualization system improved 
team performance in cooperative gaming by providing visual feedback of social presence [29]. The MART 
method also advanced emotion recognition by introducing masked affective modeling and cross-modal attention 
mechanisms to capture complex emotional dynamics across temporal dimensions in video emotion analysis [30]. 
Real-time emotion recognition using EEG technology has further transformed humanities education by improving 
engagement through accurate Valence, Arousal, and Dominance (VAD) estimation, achieving a 94% accuracy 
rate [31]. These advancements emphasize the growing potential of multimodal emotion recognition in gaming and 
other interactive domains, where combining diverse data sources, such as eye-tracking, spatio-temporal models, 
and multimodal input, provides more accurate and responsive systems for detecting and responding to emotions 
[32], [33], [34]. 
 
 
Fig. 4. Overview of the procedure for one exercise bout at a given exercise intensity. Red cells denote a warm-up 
phases and blue cells denote cool down phases, both in the Neutral VE. Grey squares denote an exposure phase of 60-
seconds in an Emotion VE [45]. 
 
Speech Emotion Recognition (SER) has seen significant advancements with the development of algorithms 
like FE-motion, which optimize feature selection for specific emotions. By utilizing features such as Mel for 
anger and MFCC for happiness, F-Emotion achieved accuracies of 82.3% and 88.8% on the RAVDESS and 
EMO-DB datasets, respectively [38]. OpenCV-based facial recognition systems have also improved real-time 
detection, contributing to applications in IoT security, biometric verification, and processes like online proctoring 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          7  
A SUMMARY OF EMOTION RECOGNITION IN VIDEO GAMES 
and ATM access [39]. These advancements underscore the growing integration of SER and facial recognition in 
diverse fields such as healthcare, elder care, and security, demonstrating their broad applicability in both 
interactive and practical domains. 
 
Table IV. Recent advancements in emotion recognition systems 
 
 
 
 
 
Fig. 5. Experiment scene on one half-time match. The presented elements from top to bottom are: screen recording, 
player video, physiological signals (HR, Respiration, EDA, pre-processed EMG and pre-processed ACC), and 
annotations [13]. 
 
In facial expression recognition, psychological models have been leveraged to enhance accuracy and 
generalization. A tree-structured approach based on the emotion-wheel model improved recognition across 
Bhaskar Abburi, Akash Reddy Reddy, Haran Kumar Ravalkole, Akhil Bochu,  
Kishore Dhulipalla, Santosh Kumar Pooja, and Darlien Barker  
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          8  
datasets like CK+ and AFEW, achieving state-of-the-art results [40]. Additionally, dynamic game adaptation 
algorithms that incorporate real-time facial expression analysis have positively impacted player engagement and 
immersion, with ongoing work aimed at integrating in-game performance metrics to refine responsiveness [41]. In 
Virtual Reality (VR) environments, emotion recognition faces unique challenges due to head-mounted displays 
(HMDs) that obscure facial features, but CNN-based models trained on datasets like FER2013 have successfully 
recognized emotions such as fear and happiness in VR games like Astro Bot Rescue Mission and Paranormal 
Activity [42]. These findings emphasize the importance of feature prioritization, particularly in vulnerable 
populations like children and the elderly, to design inclusive and effective emotion recognition systems. 
Furthermore, advancements in 3D facial animation, like FlowVQTalker and SDETalk, have revolutionized 
lifelike emotional expression in virtual environments, paving the way for more immersive human-computer 
interactions in entertainment, communication, and VR settings [43], [44]. 
 
Table V. Key contributions and methodologies in emotion recognition systems 
 
 
 
Recent studies have highlighted the potential of multimodal emotion recognition systems to enhance 
applications in gaming, healthcare, and education. For example, [46] developed a three-step emotion recognition 
approach that combines facial expression analysis with the Viola-Jones algorithm for face detection, feature 
extraction, and Support Vector Machines (SVM) for classification. This approach showed promising results when 
tested on the Ryerson Multimedia Laboratory dataset. Similarly, [47] proposed the HERO algorithm, an ensemble 
deep learning model that combines multiple subnetworks to analyze facial features such as the eyes and mouth, 
significantly improving accuracy on datasets like FER2013 and JAFFE. Additionally, [48] introduced a non-
intrusive emotion detection method for gaming, utilizing Bi-LSTM for heart rate signals and CNN for facial 
expressions, which demonstrated reliable emotional readings during gameplay. These innovations underscore the 
growing sophistication of emotion recognition systems, making them increasingly applicable across a variety of 
real-world domains. 
Emotion recognition has also proven beneficial for assisting children with autism spectrum disorder (ASD) in 
developing social skills. For instance, the “Guess What?” game developed by [49] employed Discrete Trial 
Training (DTT) to improve emotion recognition and expression, achieving an impressive 83% frame accuracy 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          9  
A SUMMARY OF EMOTION RECOGNITION IN VIDEO GAMES 
compared to previous systems that only reached 51.6%. Similarly, [50] created a game-based platform with eye-
tracking features to assess gaze-following and social interaction skills in children with ASD. These systems 
leverage multimodal technologies, such as gaze analysis and facial emotion recognition, to provide personalized 
interventions that enhance social training outcomes for children with ASD. In gaming contexts, EEG-based 
systems are also being utilized to analyze emotional responses during gameplay. For example, [51] used the 
FEEL dataset to improve EEG signal feature extraction through 1-D Local Binary Patterns (LBP) and Conflict 
Learning approaches, achieving over 92% accuracy in emotion classification. These advancements in multimodal 
emotion recognition are paving the way for more immersive and responsive gaming and therapeutic experiences, 
offering significant promise for applications in various sectors. 
 
Table VI. Advancements in facial emotion recognition [52] 
 
 
 
Facial emotion recognition has significantly advanced through the integration of machine learning and deep 
learning techniques. The Active Appearance Model (AAM) has been effectively used to mimic facial expressions 
by capturing detailed features such as skin texture and wrinkles, facilitating applications like interactive systems 
involving famous faces [53]. Additionally, a study using Support Vector Machines (SVM) with the Shi Tomasi 
method achieved over 90% accuracy in real-time emotion classification, advancing human-computer interaction 
by creating more responsive systems [54]. These advancements are further complemented by the innovative use 
of Gaussian mixture modeling and Gabor wavelets to better represent daily facial expressions, improving the 
accuracy and reliability of emotion recognition systems [55]. 
Deep learning approaches have further revolutionized the field of facial emotion recognition. Convolutional 
neural networks (CNNs) have been employed to focus on specific facial areas, achieving near-perfect accuracy in 
emotion predictions, with an F-measure of 1.0 [56]. The introduction of ICANet, which combines multiple data 
sources such as audio, video, and optical flow, improved emotion recognition in short videos, achieving 80.77% 
accuracy on the IEMOCAP dataset [57]. Additionally, DenseNet demonstrated strong performance in recognizing 
Bhaskar Abburi, Akash Reddy Reddy, Haran Kumar Ravalkole, Akhil Bochu,  
Kishore Dhulipalla, Santosh Kumar Pooja, and Darlien Barker  
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          10  
emotions in individuals wearing head-mounted displays (HMDs) by focusing on the lower facial regions, 
overcoming challenges posed by obscured facial features [58]. Hybrid systems have also made strides, with 
multimodal frameworks combining EEG, facial expression analysis, and game-generated data improving 
emotional perception and data labeling in participants [59]. The integration of fNIRS brain imaging with facial 
analysis further advanced this field, achieving 91.44% accuracy in identifying gamer expertise levels [60]. These 
hybrid methods highlight the potential of combining diverse data sources to create more comprehensive emotion 
recognition systems. 
 
Fig. 7. The correlation matrix presents the average intensity of three facial EMG expressions [62]. 
 
III. Methodology 
This paper synthesizes recent advancements in emotion recognition systems, focusing on the integration of 
multimodal approaches to enhance adaptive gaming experiences [52]. The methodology began with a 
comprehensive review of research studies to classify advancements in emotion recognition based on their 
application domains, including gaming, virtual reality (VR), healthcare, and education [63]. Key methodologies 
such as machine learning algorithms, neural networks, and multimodal frameworks were identified and analyzed 
for their contributions to emotion detection and system adaptability [64]. 
To ensure a robust analysis, data from existing studies were aggregated, emphasizing accuracy metrics, 
innovative methodologies, and commonly used datasets such as GAMEEMO [65]. A thematic analysis was then 
conducted to uncover recurring patterns and challenges in emotion recognition systems, such as the need for real-
time processing, improved adaptability, and the integration of diverse data sources like EEG, facial expression 
analysis, and gameplay metrics [66]. 
IV. Potential Impact on Society 
In gaming, emotion-adaptive frameworks can create highly immersive and personalized experiences, reducing 
player frustration and enhancing satisfaction [67]. For example, emotion driven dynamic difficulty adjustment has 
been shown to maintain player engagement in FPS games [11]. In healthcare, emotion recognition can be utilized 
for mental health interventions, such as managing anxiety and phobia through immersive VR experiences, 
leveraging findings where physiological signals like heart rate were used to detect fear states with 90.47% 
accuracy [8]. In education, serious games like Emotion Detectives have demonstrated improvements in social-
emotional skills for children with autism and ADHD, proving the viability of emotion-based tools for cognitive 
training [12]. 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          11  
A SUMMARY OF EMOTION RECOGNITION IN VIDEO GAMES 
V. Key Findings 
The integration of multimodal approaches, including EEG, facial expressions, and in-game metrics, has 
significantly advanced emotion recognition in video games [68]. Table I highlights the role of EEG in detecting 
emotions such as boredom and humor with an accuracy of 98.21%, while fear detection in VR horror games 
reached 90.47%. These results demonstrate the effectiveness of physiological signals for enhancing gaming 
experiences [59]. 
Table II elaborates on EEG-based methodologies, such as the GAMEEMO dataset and machine learning 
models, which have enabled accurate emotion recognition in gaming [46]. Additionally, innovations outlined in 
Table III—such as adaptive gameplay and emotion-based storytelling—underscore the potential of emotion 
recognition to improve engagement and immersion in both entertainment and educational settings. Lastly, Table 
IV discusses recent technological advancements, including algorithms like F-Emotion and MART, which 
optimize emotion recognition pipelines for real-time applications [69]. These findings emphasize the 
transformative potential of multimodal emotion recognition across diverse domains [70]. 
VI. Future Works 
Given additional time and funding, future research will focus on improving cross-cultural emotion detection by 
expanding datasets to represent diverse demographics [2]. Multimodal systems will be enhanced with voice 
analysis and haptic feedback to capture a broader range of emotional cues. For example, studies integrating ECG 
and EMG with EEG have already shown success in enhancing emotion detection accuracy in VR settings [1]. 
Further, optimizing real-time emotion detection pipelines to work seamlessly in low-latency environments will be 
prioritized, ensuring smoother gameplay [71]. Collaboration with behavioral psychologists and game developers 
will also allow for the integration of emotion based adaptive storytelling, deepening player immersion and 
narrative engagement [63]. 
VII. Conclusion 
This paper presents a comprehensive framework for emotion recognition in video games, leveraging multimodal 
data and advanced neural networks to deliver real-time adaptive gameplay experiences [51]. By integrating EEG 
signals, facial expression analysis, and gameplay metrics, the proposed approach addresses the challenges of data 
variability and real-time responsiveness [72]. The incorporation of dynamic difficulty adjustment (DDA) and 
personalized storytelling enhances player immersion, engagement, and satisfaction [73]. 
Beyond gaming, the methodologies outlined hold transformative potential in fields like healthcare, education, 
and human-computer interaction [8]. Applications such as emotion-based mental health interventions, adaptive 
learning environments, and therapeutic VR experiences demonstrate the broader societal impact of this research 
[74]. By fostering emotionally intelligent systems, this project aims to bridge the gap between technology and 
human emotion, creating innovative and inclusive solutions that enrich user experiences across diverse domains 
[23]. 
We were able to show a summary of recent advancements in emotion recognition systems, highlighting the 
integration of multimodal approaches, including EEG, facial expression analysis, and in-game metrics, to improve 
real-time emotion detection and adaptive gaming experiences. 
References  
[1] W. Yang, M. Rifqi, C. Marsala, and A. Pinna, “Physiological-based emotion detection and recognition in a video game 
context.” In:  2018 International Joint Conference on Neural Networks (IJCNN), 2018, pp. 1–8. 
[2] K. Mitsis, K. Zarkogianni, E. Kalafatis, K. Dalakleidi, A. Jaafar, G. Mourkousis, and K. S. Nikita, “A multimodal 
approach for real time recognition of engagement towards adaptive serious games for health,”Sensors, vol. 22, no. 7, p. 
2472, 2022. 
Bhaskar Abburi, Akash Reddy Reddy, Haran Kumar Ravalkole, Akhil Bochu,  
Kishore Dhulipalla, Santosh Kumar Pooja, and Darlien Barker  
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          12  
[3] E. P. Torres, E. A. Torres, M. Herna´ndez-A´ lvarez, and S. G. Yoo,“Emotion recognition related to stock trading using 
machine learning algorithms with feature selection,”IEEE Access, vol. 8, pp. 199 719–199 732, 2020. 
[4] M. Yalcin and M. E. Latoschik, “Deepfear: Game usage within virtual reality to provoke physiological responses of 
fear.” In:  Extended Abstracts of the CHI Conference on Human Factors in Computing Systems, 2024, pp. 1–8. 
[5] C. Vaishnavi and S. Palaniswamy, “Emotion recognition from online classroom videos using meta learning.” In:  2022 
International Conference on Advancements in Smart, Secure and Intelligent Computing (ASSIC). Los Alamitos, CA, 
USA: IEEE Computer Society, Nov. 2022, pp. 1–6. [Online]. Available: 
https://doi.ieeecomputersociety.org/10.1109/ASSIC55218.2022.10088292 
[6] S. Suhan, K. Kalaichelvan, L. Samarage, D. Alahakoon, P. Samarasinghe, and M. Nadeeshani, “Automated evaluation 
of child emotion expression and recognition abilities.” In:  2022 International Conference on Information Technology 
Systems and Innovation (ICITSI), 2022, pp. 388–393. 
[7] K. Shahzad, Z. Ali, U. Rauf, A. U. Rehman, S. Khan, and S. H. Noorani, An EEG-driven framework for emotion 
recognition during gameplay.” In: 2024 5th International Conference on Advancements in Computational Sciences 
(ICACS), 2024, pp. 1–6. 
[8] H. Zhang, X. Li, Y. Sun, X. Fu, C. Qiu, and J. M. Carroll, “Vrmnbd: A multi-modal natural behavior dataset of 
immersive human fear responses in VR stand-up interactive games.” In:  2024 IEEE Conference Virtual Reality and 3D 
User Interfaces (VR), 2024, pp. 320–330. 
[9] D. Potts, Z. Broad, T. Sehgal, J. Hartley, E. O’Neill, C. Jicol, C. Clarke, and C. Lutteroth, “Sweating the details: 
Emotion recognition and the influence of physical exertion in virtual reality exergaming.” In:  Proceedings of the CHI 
Conference on Human Factors in Computing Systems, 2024, pp. 1–21. 
[10] A. Kumar, S. Dodda, N. Kamuni, and V. S. M. Vuppalapati, “The emotional impact of game duration: A framework 
for understanding player emotions in extended gameplay sessions,” arXiv preprint arXiv:2404.00526, 2024. 
[11] N. Fisher and A. K. Kulshreshth, “Exploring dynamic difficulty adjustment methods for video games.” In:  Virtual 
Worlds, vol. 3, no. 2. MDPI, 2024, pp. 230–255. 
[12] J. L¨oyt¨om¨aki, P. Ohtonen, and K. Huttunen, “Serious game the emotion detectives helps to improve social–
emotional skills of children with neurodevelopmental disorders,” British Journal of Educational Technology, vol. 55, 
no. 3, pp. 1126–1144, 2024. 
[13] B. Kordyaka, S. Laato, and B. Niehaves, “A toxic triad: Aggression, anger and authoritarianism-a study with 
multiplayer online battle arena game players.” In:  8th International GamiFIN Conference, GamiFIN 2024, 2024. 
[14] M. Croissant, G. Schofield, and C. McCall, “ Emotion design for video games: A framework for affective 
interactivity,” ACM Games: Research and Practice, vol. 1, no. 3, pp. 1–24, 2023. 
[15] M. Malaspina, J. A. Barbato, M. Cremaschi, F. Gasparini, A. Grossi, and A. Saibene, “An experimental protocol to 
access immersiveness in video games,” arXiv preprint arXiv:2310.16431, 2023. 
[16] R. Somarathna and G. Mohammadi, “Exploring emotions in multicomponent space using interactive VR games,” 
arXiv preprint arXiv:2404.03239, 2024. 
[17] K. Liang, J. Chen, T. He, W. Wang, A. K. Singh, D. B. Rawat, H. Song, and Z. Lyu, “Review of the open data sets for 
contactless sensing,” IEEE Internet of Things Journal, vol. 11, no. 11, pp. 19 000–19 022, 2024. 
[18] G. Du, W. Zhou, C. Li, D. Li, and P. X. Liu, “An emotion recognition method for game evaluation based on 
electroencephalogram,” IEEE Transactions on Affective Computing, vol. 14, no. 1, pp. 591–602, 2023. 
[19] A. Raheel, N. Liaqat, M. Dua, A. Zaidi, S. H. Noorani, and A. Arsalan,“A neurocognitive approach to evaluate mobile 
game player’s experience using EEG.” In:  2023 25th International Multitopic Conference (INMIC), 2023, pp. 1–5. 
[20] M. K, C. Sridevi, K. B, and M. T. Ganesh Roy, “Emotional resonance in brainwaves: EEG based classification of 
emotional dynamics.” In: 2024 Tenth International Conference on Bio Signals, Images, and Instrumentation (ICBSII), 
2024, pp. 1–11. 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          13  
A SUMMARY OF EMOTION RECOGNITION IN VIDEO GAMES 
[21] S. Abramov, A. Korotin, A. Somov, E. Burnaev, A. Stepanov, D. Nikolaev, and M. A. Titova, “Analysis of video 
game players’ emotions and team performance: An esports tournament case study,” IEEE Journal of Biomedical and 
Health Informatics, vol. 26, no. 8, pp. 3597–3606, 2022. 
[22] W. M. Ben Henia and Z. Lachiri, “Emotion classification in arousal-valence dimension using discrete affective 
keywords tagging.” In:  2017 International Conference on Engineering MIS (ICEMIS), 2017, pp. 1–6. 
[23] P. Kalansooriya, G. D. Ganepola, and T. Thalagala, “Affective gaming in real-time emotion detection and smart 
computing music emotion recognition: Implementation approach with electroencephalogram.” In: 2020 International 
Research Conference on Smart Computing and Systems Engineering (SCSE). IEEE, 2020, pp. 111–116. 
[24] T. B. Alakus， and T¨urko˘glu, “EEG-based emotion estimation with different deep learning models.” In:  2019 4th 
International Conference on Computer Science and Engineering (UBMK), 2019, pp. 33–37. 
[25] S. A. Bargal, E. Barsoum, C. C. Ferrer, and C. Zhang, “Emotion recognition in the wild from videos using images.” In:  
Proceedings of the 18th ACM international conference on multimodal interaction, 2016, pp. 433–436. 
[26] J. Wang, Y. Song, X. Zhao, and Z. Bai, “Research on emotional cognition of game players based on functional brain 
network.” In: 2024 IEEE International Conference on Mechatronics and Automation (ICMA), 2024, pp. 32–37. 
[27] L Kashani-Vahid, M. Mohajeri, H. Moradi, and A. Irani, “Effectiveness of computer games of emotion regulation on 
social skills of children with intellectual disability.” In:  2018 2nd National and 1st International Digital Games 
Research Conference: Trends, Technologies, and Applications (DGRC), 2018, pp. 46–50. 
[28] E. G. Dizicheh, H. Moradi, M. B. Nezam Abadi, F. Shahrokh, R. Samani, and L. Kashani-Vahid, “Emoanim: A 
serious game for screening children with autism using emotions in animations.” In:  2021 International Serious Games 
Symposium (ISGS), 2021, pp. 75–80. 
[29] G. T.-T. B. H.-O. Maria Teresa Cepero, Luis G. Montan´e-Jim´enez and C. A. Ochoa, “Social presence awareness 
visualization in a collaborative videogame.” International Journal of Human–Computer Interaction, vol. 40, no. 5, pp. 
1133–1149, 2024. [Online]. Available: https://doi.org/10.1080/10447318.2022.2132357 
[30] Z. Zhang, P. Zhao, E. Park, and J. Yang, “Mart: Masked affective representation learning via masked temporal 
distribution distillation.”In: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, 
2024, pp. 12 830–12 840. 
[31] M. A. Blanco-Rıos, M. O. Candela-Leal, C. Orozco-Romo, P. Remis-Serna, C. S. Velez-Saboya, J. d. J. Lozoya-Santos, 
M. Cebral-Loureda, and M. A. Ramırez-Moreno, “Real-time EEG-based emotion recognition for neurohumanities: 
perspectives from principal component analysis and tree-based algorithms,” Frontiers in Human Neuroscience, vol. 18, 
p. 1319574, 2024. 
[32] J. Wei, G. Hu, X. Yang, A. T. Luu, and Y. Dong, “Learning facial expression and body gesture visual information for 
video emotion recognition,” Expert Systems with Applications, vol. 237, p. 121419, 2024. 
[33] M. Bekler, M. Yilmaz, and H. E. Ilgın, “Assessing feature importance in eye-tracking data within virtual reality using 
explainable artificial intelligence techniques,” Applied Sciences, vol. 14, no. 14, p. 6042, 2024. 
[34] R. Pan, J. A. Garcıa-Dıaz, M. A´ . Rodrıguez-Garcıa, and R. Valencia-Garcıa, “Spanish meacorpus 2023: A 
multimodal speech–text corpus for emotion analysis in spanish from natural environments,” Computer Standards & 
Interfaces, vol. 90, p. 103856, 2024. 
[35] D. Ciraolo, M. Fazio, R. S. Calabro, M. Villari, and A. Celesti, “Facial expression recognition based on emotional 
artificial intelligence for telerehabilitation,”Biomedical Signal Processing and Control, vol. 92, p. 106096, 2024. 
[36] N. K. H. Tran, “ Development of a machine learning system for aspect-based sentiment analysis and text 
summarization of video game reviews on steam,” Ph.D. dissertation, Hochschule f¨ur Angewandte Wissenschaften, 
Hamburg, 2024. 
[37] X. Zhang, L. Yin, J. F. Cohn, S. Canavan, M. Reale, A. Horowitz, P. Liu, and J. M. Girard, “Bp4d-spontaneous: a 
high-resolution spontaneous 3D dynamic facial expression database,” Image and Vision Computing, vol. 32, no. 10, pp. 
692–706, 2014. 
Bhaskar Abburi, Akash Reddy Reddy, Haran Kumar Ravalkole, Akhil Bochu,  
Kishore Dhulipalla, Santosh Kumar Pooja, and Darlien Barker  
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          14  
[38] L.-M. Zhang, G. W. Ng, Y.-B. Leau, and H. Yan, “A parallel-model speech emotion recognition network based on 
feature clustering,” IEEE Access, vol. 11, pp. 71 224–71 234, 2023. 
[39] A. Kumari Sirivarshitha, K. Sravani, K. S. Priya, and V. Bhavani, “An approach for face detection and face recognition 
using opencv and face recognition libraries in python.” In:  2023 9th International Conference on Advanced Computing 
and Communication Systems (ICACCS), vol. 1, 2023, pp. 1274–1278. 
[40] R. Miyoshi, S. Akizuki, K. Tobitani, N. Nagata, and M. Hashimoto, “Convolutional neural tree for video-based facial 
expression recognition embedding emotion wheel as inductive bias.” In:  2022 IEEE International Conference on Image 
Processing (ICIP), 2022, pp. 3261–3265. 
[41] K. Kutt, Sciga, and G. J. Nalepa, “Emotion-based dynamic difficulty adjustment in video games.” In:  2023 IEEE 10th 
International Conference on Data Science and Advanced Analytics (DSAA), 2023, pp. 1–5. 
[42] F. Dehghani and L. Zaman, “Facial emotion recognition in VR games. “In: 2023 IEEE Conference on Games (CoG), 
2023, pp. 1–4. 
[43] S. Tan, B. Ji, and Y. Pan, “Flowvqtalker: High-quality emotional talking face generation through normalizing flow and 
quantization.” In:  2024 IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), 2024, pp. 26 307
–26 317. 
[44] S. Lee, J. Lee, H. Song, and S. Lee, “ Speech-driven emotional 3D talking face animation using emotional 
embeddings.” In:  ICASSP 2024 - 2024 IEEE International Conference on Acoustics, Speech and Signal Processing 
(ICASSP), 2024, pp. 7840–7844. 
[45] R. Vatsal, S. Mishra, R. Thareja, M. Chakrabarty, O. Sharma, and J. Shukla, “An analysis of physiological and 
psychological responses in virtual reality and flat screen gaming,” IEEE Transactions on Affective Computing, vol. 15, 
no. 3, pp. 1696–1710, 2024. 
[46] K. A. Sannikov, A. A. Bashlikov, and A. A. Druki, “Classification algorithms; face; training; algorithm design and 
analysis; neurons; face detection; feature extraction; image processing; artificial neural networks; Viola Jones algorithm; 
face detection; facial expression classification.” In:  2017 International Siberian Conference on Control and 
Communications (SIBCON), 2017, pp. 1–5. 
[47] W. Hua, F. Dai, L. Huang, J. Xiong, and G. Gui, “Hero: Human emotions recognition for realizing intelligent internet 
of things,” IEEE Access, vol. 7, pp. 24 321–24 332, 2019. 
[48] G. Du, S. Long, and H. Yuan, “Non-contact emotion recognition combining heart rate and facial expression for 
interactive gaming environments,”IEEE Access, vol. 8, pp. 11 896–11 906, 2020. 
[49] H. Kalantarian, K. Jedoui, P. Washington, and D. P. Wall, “A mobile game for automatic emotion-labeling of images,
” IEEE Transactions on Games, vol. 12, no. 2, pp. 213–218, 2020. 
[50] Y.-L. Chien, C.-H. Lee, Y.-N. Chiu, W.-C. Tsai, Y.-C. Min, Y.-M. Lin, J.-S. Wong, and Y.-L. Tseng, “Game-based 
social interaction platform for cognitive assessment of autism using eye tracking,” IEEE Transactions on Neural 
Systems and Rehabilitation Engineering, vol. 31, pp. 749–758, 2023. 
[51] O. Almanza-Conejo, J. G. Avina-Cervantes, A. Garcia-Perez, and M. A. Ibarra-Manzano, “Emotion recognition in 
gaming dataset to reduce artifacts in the self-assessed labeling using semi-supervised clustering,” IEEE Access, vol. 12, 
pp. 52 659–52 668, 2024. 
[52] J. Weymouth and R. Atuah, “Review of video games amp; simulation in computer science education.” In:  2022 
International Conference on Computational Science and Computational Intelligence (CSCI). Los Alamitos, CA, USA: 
IEEE Computer Society, Dec. 2022, pp. 2091–2096. [Online]. Available:  
https://doi.ieeecomputersociety.org/10.1109/CSCI58124.2022.00376 
[53] T. Nitta, Y. Iribe, K. Katsurada, and R. Fukui, “Facial expression mimicking system.” In:  International Conference on 
Pattern Recognition, Los Alamitos, CA, USA: IEEE Computer Society, Aug. 2010, pp. 3776 –3779. [Online]. 
Available: https://doi.ieeecomputersociety.org/10.1109/ICPR.2010.920 
[54] C. Maaoui, A. Pruski, and F. Abdat, “Human-computer interaction using emotion recognition from facial expression.” 
In: UKSIM European Symposium on Computer Modeling and Simulation, Los Alamitos, CA, USA: IEEE Computer 
Society, Nov. 2011, pp. 196–201. [Online]. Available: https://doi.ieeecomputersociety.org/10.1109/EMS.2011.20 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          15  
A SUMMARY OF EMOTION RECOGNITION IN VIDEO GAMES 
[55] H. Song, J. Lu, Z. Wang, and W. Liu, “An expression space model for facial expression analysis.” In: Processing of the 
Congress on Image and Signal, vol. 3. Los Alamitos, CA, USA: IEEE Computer Society, May 2008, pp. 680–684. 
[Online]. Available: https://doi.ieeecomputersociety.org/10.1109/CISP.2008.216 
[56] M. Cesarelli, F. Martinelli, F. Mercaldo, and A. Santone, “Emotion recognition from facial expression using 
explainable deep learning.” In: 2022 IEEE International Conference on Dependable, Autonomic and Secure Computing, 
Int. Conf. on Pervasive Intelligence and Computing, Int. Conf. on Cloud and Big Data Computing, Int. Conf. on Cyber 
Science, and Technology Congress (DASC/PiCom/CBDCom/CyberSciTech). Los Alamitos, CA, USA: IEEE Computer 
Society, Sept. 2022, pp. 1–6. [Online]. Available: 
https://doi.ieeecomputersociety.org/10.1109/DASC/PiCom/CBDCom/Cy55231.2022.9927951 
[57] B. Yang, Q. Zhang, and Z. Liu, “Icanet: A method of short video emotion recognition driven by multimodal data.” In:  
2022 2nd International Conference on Networking Systems of AI (INSAI). Los Alamitos, CA, USA: IEEE Computer 
Society, oct 2022, pp. 22–25. [Online]. Available:  
https://doi.ieeecomputersociety.org/10.1109/INSAI56792.2022.00014 
[58] H. Yong, J. Lee, and J. Choi, “Emotion recognition in gamers wearing head-mounted display.” In:  2019 IEEE 
Conference on Virtual Reality and 3D User Interfaces (VR). Los Alamitos, CA, USA: IEEE Computer Society, March 
2019, pp. 1251–1252. [Online]. Available: https://doi.ieeecomputersociety.org/10.1109/VR.2019.8797736 
[59] K. Shingjergji, D. Iren, F. Bottger, C. Urlings, and R. Klemke, “Interpretable explainability in facial emotion 
recognition and gamification for data collection.” In:  2022 10th International Conference on Affective Computing and 
Intelligent Interaction (ACII). Los Alamitos, CA, USA: IEEE Computer Society, Oct. 2022, pp. 1–8. [Online]. 
Available: https://doi.ieeecomputersociety.org/10.1109/ACII55700.2022.9953864 
[60] A. R. Andreu-Perez, M. Kiani, J. Andreu-Perez, P. Reddy, J. Andreu-Abela, M. Pinto, and K. Izzetoglu, “Single-trial 
recognition of video gamer’s expertise from brain hemodynamic and facial emotion responses,” Brain Sciences, vol. 
11, no. 1, 2021. [Online]. Available: https://www.mdpi.com/2076-3425/11/1/106 
[61] R. Priya, M. Hanmandlu, and S. Vasikarla, “Emotion recognition using deep learning.” In:  2021 IEEE Applied 
Imagery Pattern Recognition Workshop (AIPR). Los Alamitos, CA, USA: IEEE Computer Society, oct 2021, pp. 1–5. 
[Online]. Available: https://doi.ieeecomputersociety.org/10.1109/AIPR52630.2021.9762207 
[62] A. Psaltis, K. Kaza, K. Stefanidis, S. Thermos, K. C. Apostolakis, K. Dimitropoulos, and P. Daras, “Multimodal 
affective state recognition in serious games applications.” In:  2016 IEEE international conference on imaging systems 
and techniques. IEEE, 2016, pp. 435–439. 
[63] K. Kutt, L. Sciga, and G. J. Nalepa, “Emotion-based dynamic difficulty adjustment in video games.” In:  2023 IEEE 
10th International Conference on Data Science and Advanced Analytics (DSAA). IEEE, 2023, pp. 1–5. 
[64] S. F. Vural, B. Yurdusever, A. B. Oktay, and I. Uzun, “Stress recognition from facial images in children during 
physiotherapy with serious games,” Expert Systems with Applications, vol. 238, p. 121837, 2024. 
[65] K. Boson, S. Gurdal, E. Claesdotter-Knutsson, and S. Kapetanovic, “Adolescent gaming and parent–child emotional 
closeness: Bivariate relationships in a longitudinal perspective,” Current Psychology, pp. 1–11, 2024. 
[66] P. A. Silva and R. Santos, “An opinion mining methodology to analyze games for health,” Multimedia Tools and 
Applications, vol. 82, no. 9, pp. 12 957–12 976, 2023. 
[67] R. A. Vacca, A. Augello, L. Gallo, G. Caggianese, V. Malizia, S. La Grutta, M. Murero, D. Valenti, A. Tullo, B. Balech 
et al., “Serious games in the new era of digital-health interventions: a narrative review of their therapeutic applications to 
manage neurobehavior in neurodevelopmental disorders,” Neuroscience & Biobehavioral Reviews, vol. 149, p. 105156, 
2023. 
[68] A. Cruz, B. Bhanu, and N. Thakoor, “Facial emotion recognition in continuous video.” In:  2012 21st International 
Conference on Pattern Recognition (ICPR 2012). Los Alamitos, CA, USA: IEEE Computer Society, Nov. 2012, pp. 
1880–1883. [Online]. Available: https://doi.ieeecomputersociety.org/ 
[69] Panizo-Lledot, J. Torregrosa, R. Menendez-Ferreira, D. Lopez-Fernandez, P. P. Alarcon, and D. Camacho,“Youngres: 
A serious game-based intervention to increase youngsters’ resilience against extremist ideologies,” IEEE Access, vol. 
10, pp. 28 564–28 578, 2022. 
Bhaskar Abburi, Akash Reddy Reddy, Haran Kumar Ravalkole, Akhil Bochu,  
Kishore Dhulipalla, Santosh Kumar Pooja, and Darlien Barker  
 
 
 
 
 
 
 
 
 
 
 
 
 
 
          16  
[70] G. N. Yannakakis, K. Isbister, A. Paiva, and K. Karpouzis, “Guest editorial: Emotion in games,” IEEE Transactions 
on Affective Computing, vol. 5, no. 1, pp. 1–2, 2014. 
[71] D. O, S. S, E. Edwin, S. P, M. Thanka, and V. Ebenezer, “Face and emotion recognition using deep learning with 
convolutional neural networks in industry application.” In: 2024 3rd International Conference on Sentiment Analysis and 
Deep Learning (ICSADL). Los Alamitos, CA, USA: IEEE Computer Society, mar 2024, pp. 438–443. [Online]. 
Available: https://doi.ieeecomputersociety.org/10.1109/ICSADL61749.2024.00077 
[72] J. Wei, G. Hu, X. Yang, A. T. Luu, and Y. Dong, “Learning facial expression and body gesture visual information for 
video emotion recognition,” Expert Systems with Applications, vol. 237, p. 121419, 2024. [Online]. Available: 
https://www.sciencedirect.com/science/article/pii/S0957417423019218 
[73] R. Cowie, E. Douglas-Cowie, S. Kollias, S. Ioannou, M. Wallace, and J. Taylor, “An intelligent system for facial 
emotion recognition.” In:  2005 IEEE International Conference on Multimedia and Expo. Los Alamitos, CA, USA: 
IEEE Computer Society, July 2005, p. 4 pp. [Online]. Available:  
https://doi.ieeecomputersociety.org/10.1109/ICME.2005.1521570 
[74] M. Cerezo-Pizarro, F.-I. Revuelta-Domınguez, J. Guerra-Antequera, and J. Melo-Sanchez, “The cultural impact of 
video games: A systematic review of the literature,” Education Sciences, vol. 13, no. 11, p. 1116, 2023. 
