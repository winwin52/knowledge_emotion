HAL Id: hal-04923269
https://hal.science/hal-04923269v1
Submitted on 31 Jan 2025
HAL is a multi-disciplinary open access
archive for the deposit and dissemination of sci-
entific research documents, whether they are pub-
lished or not.
The documents may come from
teaching and research institutions in France or
abroad, or from public or private research centers.
L’archive ouverte pluridisciplinaire HAL, est
destinée au dépôt et à la diffusion de documents
scientifiques de niveau recherche, publiés ou non,
émanant des établissements d’enseignement et de
recherche français ou étrangers, des laboratoires
publics ou privés.
HAL Authorization
Gradient Boosting, AdaBoost, and LightGBM for
Emotion Recognition: A Comparative Analysis on
Wearable Sensor Data
Zikri Kholifah Nur, Rifki Wijaya, Gia Septiana Wulandari
To cite this version:
Zikri Kholifah Nur, Rifki Wijaya, Gia Septiana Wulandari. Gradient Boosting, AdaBoost, and Light-
GBM for Emotion Recognition: A Comparative Analysis on Wearable Sensor Data. 2024 12th Inter-
national Conference on Information and Communication Technology (ICoICT), Aug 2024, Bandung,
Indonesia. pp.585-591, ￿10.31219/osf.io/xp6v5￿. ￿hal-04923269￿
This corrected version of the original publication (DOI: 10.1109/ICoICT61617.2024.10698721). A terminological error in the methodology 
section—misstating Linear Regression instead of Logistic Regression—has been rectified. While the results are unaffected (as the correct 
algorithm was implemented), this revision ensures the text accurately reflects the classification methodology employed. 
 
Gradient Boosting, AdaBoost, and LightGBM for 
Emotion Recognition: A Comparative Analysis on 
Wearable Sensor Data 
 
1st Zikri Kholifah Nur* 
School Of Computing 
Telkom University 
Bandung, Indonesia 
https://orcid.org/0009-0003-4318-3062 
2nd Rifki Wijaya 
School Of Computing  
Telkom University 
Bandung, Indonesia 
https://orcid.org/0000-0002-8247-6584 
3rd Gia Septiana Wulandari 
School Of Computing 
Telkom University 
Bandung, Indonesia 
https://orcid.org/0000-0002-6155-8601
Abstract—This study investigates how well advanced 
machine learning algorithms, specifically Gradient Boosting 
(GB), AdaBoost, and LightGBM, enhance emotion recognition 
using wearable sensor data. Heart rate and movement data from 
fifty participants were collected during three scenarios: 
watching a movie clip before walking, listening to music before 
walking, and listening to music while walking. Model 
performance was assessed for classifying binary (happy vs. sad) 
and multi-class (happy vs. neutral vs. sad) emotions, using 
metrics such as AUC, F1 score, accuracy, and user lift score. 
Results indicate that both GB and LightGBM consistently 
outperform established models like Random Forest and Logistic 
Regression across all scenarios and both types of emotion 
classification. Notably, LightGBM achieved the highest 
accuracies: 91.8% for binary classification and 84.2% for multi-
class classification in the 'listening to music while walking' 
scenario. While AdaBoost's performance was slightly lower 
than that of Random Forest, it still outperformed the baseline 
and Logistic Regression models. These findings underscore the 
potential of GB, AdaBoost, and LightGBM to significantly 
enhance the accuracy of wearable-based emotion recognition 
systems. 
Keywords—gradient boosting; adaboost; lightgbm; wearable 
sensor data; emotion recognition; body movement; heart rate 
I. INTRODUCTION 
In the digital age, developing intelligent systems capable 
of understanding and responding to human emotions is crucial 
[1], [2]. This endeavor has significant implications for fields 
such as mental health monitoring, personalized user 
experiences, and human-computer interaction [3], [4]. 
Wearable technology, renowned for its ability to continuously 
and unobtrusively collect data, presents a promising avenue 
for deciphering nuanced affective states [5], [6]. By 
leveraging physiological signals and movement patterns, 
these devices offer a unique perspective on real-world 
emotional experiences [7]. 
Previous research by Quiroz et al. has utilized wearable 
sensor data to classify emotions using established machine 
learning models, such as Random Forest (RF) and Logistic 
Regression (LR) [8]. Their work demonstrated the feasibility 
of classifying emotions such as happy, neutral, and sad, 
achieving median accuracies exceeding 78% in binary 
classifications [8]. However, the potential benefits of 
 
*e-mail: zikrikn@student.telkomuniversity.ac.id  
advanced ensemble methods, which have shown promise in 
enhancing classification accuracy across various domains, 
have not been explored. 
To address this gap, our study introduces three advanced 
ensemble learning methods: Gradient Boosting (GB), 
AdaBoost, and LightGBM. Ensemble methods are recognized 
for their ability to improve model performance by combining 
predictions from multiple models [9]. These approaches 
leverage the strengths of various algorithms to create more 
robust predictive models. 
Our research conducts a comparative analysis of these 
ensemble methods for emotion classification using a 
comprehensive dataset collected from 50 participants engaged 
in emotionally evocative tasks while wearing wearable 
devices. Participants engaged in activities such as watching a 
movie clip and walking, listening to music and walking, and 
listening to music while walking. Their emotional states were 
monitored through heart rate and movement data, providing 
rich insights into the dynamics of emotional responses in 
naturalistic settings. 
Through rigorous analysis, our study aims to identify 
patterns that differentiate emotional states, thereby advancing 
the state-of-the-art in wearable-based emotion recognition. 
We compare the performance of GB, AdaBoost, and 
LightGBM against established models (RF and LR) and a 
baseline (DummyClassifier), offering insights into their 
relative strengths and weaknesses. Gradient Boosting builds 
models sequentially, each correcting errors made by the 
previous one, often resulting in high accuracy [10], while 
AdaBoost enhances the performance of weak learners through 
boosting [11]. LightGBM, known for its efficiency and 
scalability, particularly with large-scale data, offers faster 
training speeds and higher efficiency [12]. 
By extending prior research, our study contributes to the 
growing body of knowledge in emotion recognition through a 
detailed evaluation of these methods in a specific application. 
We aim to provide practitioners and researchers with valuable 
insights into selecting appropriate models for emotion 
recognition tasks, with potential applications in mental health 
monitoring and personalized user experiences. These 
advancements are crucial for developing more intuitive and 
responsive technological systems that can better understand 
and respond to human emotions [13] . 
II. RESEARCH METHODOLOGY 
A. System Design 
The initial system design, developed by Quiroz et al. and 
available on GitHub [8]. However, we have modified and 
expanded the original design by integrating new algorithms, 
specifically Gradient Boosting, AdaBoost, and LightGBM. 
The system design comprises three main phases: data 
collection, preprocessing, and model implementation. The 
data collection phase involves gathering heart rate and 
movement data from wearable devices. Preprocessing 
includes generating walking data and extracting relevant 
features. In the model implementation phase, several machine 
learning algorithms are employed. These include a baseline 
DummyClassifier with the 'most_frequent' strategy, Logistic 
Regression, Random Forest, and the newly integrated 
Gradient Boosting, AdaBoost, and LightGBM models. The 
performance of each model is then rigorously evaluated. Fig. 
1 presents a block diagram of the system's workflow, outlining 
the step-by-step process from data collection to model 
evaluation.  
 
B. Participants and Data Collection 
The data utilized in this study were originally collected by 
prior research and are accessible through the Juancq/emotion-
recognition-smartwatch GitHub repository [8]. Participants 
included 50 young adults (predominantly female, n = 43) from 
a university in North-West UK, with a mean age of 23.18 
years. They met specific inclusion criteria, such as the absence 
of visual or hearing impairments and the ability to walk 
unaided. 
Distinct patterns in physiological parameters, notably 
heart rate variability (HRV), and movement dynamics are 
associated with different emotional states. Research has 
demonstrated that gait patterns associated with sadness and 
depression include slower walking speeds, reduced arm 
swings, less vertical head movement, greater lateral body 
sway, and a more slumped posture. [14]. These findings 
underscore the correlation between body movement and 
emotional states. 
Similarly, HRV reflects the complex interplay between 
internal physiological processes (like the parasympathetic and 
sympathetic nervous systems) and external triggers, including 
emotions [15]. This intricate interplay generates complex, 
non-linear HRV patterns [16], which can be quantified as a 
series of values reflecting the continuous adaptation of heart 
rate to emotional experiences [17].  
To explore this relationship, participants were equipped 
with Samsung Gear 2 smartwatches on their left wrists and 
Polar H7 heart rate monitors around their chests to capture 
heart rate responses. The Samsung Gear 2 smartwatches 
continuously recorded tri-axial accelerometer and gyroscope 
data, capturing movement patterns, while the Polar H7 heart 
rate monitors measured heart rate variability. Additionally, a 
Polar M400 watch was used by the experimenter to monitor 
heart rate data in real time. 
Participants were presented with various audiovisual 
stimuli designed to elicit specific emotional responses. Happy 
emotions were intended to be evoked using clips from movies 
such as the scene in "10 Things I Hate About You" (1999) 
where Patrick serenades Katarina in the stadium, the cafe 
discussion about orgasms in "When Harry Met Sally" (1989), 
and the hair gel scene in "There's Something About Mary" 
(1998). To contrast these, sad emotions were intended to be 
induced using clips such as the scene in "Interstellar" (2014) 
where Cooper watches video messages sent by his children, 
the moment in "Click" (2006) where Michael rewinds his past 
to recall not saying goodbye to his father, and the poignant 
scene of Hachiko waiting at the train station in "Hachi" 
(2009).  Meanwhile, for a neutral emotional state, participants 
listened to classical music pieces, including "Clair de lune" by 
Debussy. (For a complete list of stimuli, see [8]). 
The experimenter noted the start and end times of each 
participant's walking to isolate the sensor data specifically 
corresponding to the walking periods. Data collected during 
briefings and while participants were engaged with stimuli 
before walking were excluded. Walking periods were labeled 
based on the emotional stimulus presented before the walk. 
For instance, features extracted from walking data following 
a happiness-inducing movie clip were labeled as happy. These 
labels were then used to train classifiers to distinguish between 
happy and sad emotions, as well as to detect happy, neutral, 
and sad emotions. 
To verify emotional states, participants' emotions were 
rechecked using the Positive and Negative Affect Schedule 
(PANAS), a psychometric scale measuring positive and 
negative affect, both before and after each walking condition. 
Participants were also inquired whether they had previously 
seen the movie clips; on average, only one participant had. 
They self-reported experiencing the intended emotions for all 
clips, with intensity ratings ranging from 5.0 to 6.5 for the 
happy and sad clips, respectively. 
The data were stored in a CSV file containing participant 
IDs, conditions, ages, sexes, and session times, along with raw 
data CSV files for accelerometer, gyroscope, and heart rate 
measurements. A block diagram illustrating the data 
collection procedure is presented in Fig. 2. 
 
C. Data Preprocessing 
Initial data preparation involved crucial steps to refine raw 
data for subsequent analysis. The first step was to create a 
CSV file containing participant details and start/end times for 
each condition, linking these to raw data CSV files containing 
sensor measurements. This integration between the user study 
encoding file and raw data files enabled the extraction of 
timestamps and sensor readings. Activity durations were 
determined, and columns for emotion and experimental 
conditions were generated accordingly, adjusting the column 
order as necessary. Processed walking data were then stored 
in CSV format for further analysis, with filenames including 
Fig. 1. System design flow from data collection to evaluation 
Fig. 2. Block diagram of data collection 
participant IDs and condition labels to differentiate each 
dataset. 
The preprocessing phase culminated in the extraction of 
pertinent features, visually summarized in Fig. 3, which 
illustrates the workflow from raw data acquisition to walking 
data. 
 
In the feature extraction stage, the previously generated 
walking data were processed further to create multiple 
features. Initially, the raw accelerometer data underwent 
filtering using a mean filter with a window size of three 
samples, effectively reducing noise and enhancing data 
quality. Subsequently, the data were segmented into sliding 
windows of one second (24 samples with a 50% overlap). This 
method, commonly employed in activity recognition from 
smartphone accelerometer data, treated each window as an 
independent sample, capturing dynamic movements and heart 
rate responses over time. 
From each window of tri-axial accelerometer and 
gyroscope data, a comprehensive set of 17 statistical features 
was extracted. These features included: (1) mean, (2) standard 
deviation, (3) max, (4) min, (5) energy, (6) kurtosis, (7) 
skewness, (8) root mean square, (9) root sum square, (10) sum, 
(11) sum of absolute values, (12) mean of absolute values, 
(13) range, (14) median, (15) upper quartile, (16) lower 
quartile, and (17) median absolute deviation. 
Additionally, angles between the signal mean and the x-
axis, y-axis, and z-axis, standard deviation of the signal 
magnitude, and heart rate were calculated as well, resulting in 
a total of 107 features for each window's feature vector. These 
features collectively provide a robust representation of 
movement and heart rate patterns sensed by the devices. 
These extracted features serve as essential inputs for 
machine learning models aimed at differentiating between 
happy, sad, and neutral emotional states. By leveraging the 
rich information embedded in raw sensor data, this approach 
enables accurate classification based on distinctive patterns 
associated with each emotion.  
 
Following feature extraction, machine learning models are 
trained and evaluated using the extracted features to classify 
emotional states. Fig. 4 visually represents the feature 
extraction flow. 
 
D. Baseline Model: Dummy Classifier ‘most_frequent’ 
To establish baseline performance for evaluating our 
machine learning models, we used a simple classifier that 
always predicts the most frequent class in the dataset. For 
instance, given the nearly equal number of happy and sad 
samples in this study, the baseline accuracy was 
approximately 50%. This baseline serves as a crucial reference 
point for assessing the improvement of more advanced 
models, showing how effectively they leverage underlying 
data patterns compared to frequency-based predictions.  
E. Random Forest 
Random Forest is an ensemble technique that builds 
multiple decision trees and provides the average prediction for 
regression or the majority vote for classification [18]. Each 
tree is trained on random data and feature subsets, reducing 
overfitting and improving generalization. In this study, we use 
Random Forest for classification, represented as: 
 
𝑦̂ = 𝑚𝑜𝑑𝑒(𝑦1, 𝑦2,… , 𝑦𝑛)  
(1) 
where 𝑦̂ represents the predicted class label, and  𝑦1, 𝑦2, … , 
𝑦𝑛  are the individual tree predictions. Fig. 5 outlines the 
Random Forest classification process, from data splitting to 
majority voting. 
 
F. Logistic Regression 
Logistic regression is a statistical method used to model 
the probability of a binary outcome based on one or more 
independent variables [19]. Unlike linear regression, which 
predicts a continuous output, logistic regression is specifically 
designed for cases where the dependent variable is categorical, 
typically binary (e.g., yes/no, 0/1). It uses an S-shaped curve, 
known as the logistic function, to map predicted values to 
probabilities that range between 0 and 1. 
In addition to binary classification, logistic regression can 
be extended for multi-class classification problems. This is 
done through methods like One-vs-Rest (OvR) or multinomial 
logistic regression, allowing the model to predict outcomes 
across multiple categories by providing probabilities for each 
class and selecting the one with the highest likelihood. 
Fig. 6 visualizes a Logistic Regression model for binary 
classification, showing the characteristic S-shaped curve and 
how predicted probabilities are constrained within the 0 to 1 
range.
 
G. AdaBoost 
AdaBoost, short for Adaptive Boosting, is an ensemble 
learning algorithm that improves classification accuracy by 
combining multiple weak classifiers into a single strong 
Fig. 3. Block diagram of generating walking data flow 
Fig. 4. Block diagram of the feature extraction flow 
 
Fig. 5. Visualization of random forest classification 
 
Fig. 6. Visualization of logistic regression 
classifier [20]. It starts by assigning equal weights to all 
training samples. In each iteration, a weak classifier is trained 
on the weighted data, and its error rate is calculated. Weights 
of misclassified samples are increased to focus on harder cases 
in subsequent iterations. The final prediction is a weighted 
majority vote of the weak classifiers. The formula for the final 
classifier 𝐻(𝑥) in AdaBoost is: 
 
𝐻(𝑥) = 𝑠𝑖𝑔𝑛 (∑
∝𝑡ℎ𝑡(𝑥)
𝑀
𝑡=1
)  
(3) 
where ℎ𝑡(𝑥)  is the prediction of the weak classifier t on 
sample 𝑥, and ∝𝑡 is the weight assigned to weak classifier t, 
calculated as: 
 
∝𝑡= 
1
2 ln(
1−𝜀𝑡
𝜀𝑡)   
(4) 
where 𝜀𝑡 is the error rate of weak classifier 𝑡. 𝑀 is the total 
number of weak classifiers. Fig. 7 shows the iterative process 
of training weak classifiers and adjusting sample weights in 
the AdaBoost algorithm.  
 
 
H. Gradient Boosting 
Gradient Boosting (GB) is a machine learning method that 
improves prediction accuracy by sequentially integrating 
several simple prediction models, usually decision trees, to 
create a stronger overall model [21]. Each tree is trained to 
correct the errors of its predecessors, leveraging gradients to 
refine predictions iteratively. This methodological approach 
not only accommodates large datasets and intricate problem 
domains but also mitigates the risk of overfitting, making GB 
particularly adept at handling complex tasks. The iterative 
refinement guided by gradients ensures that the model 
optimally learns from its mistakes, thereby improving overall 
performance. Fig. 8 visually illustrates the iterative nature of 
Gradient Boosting, highlighting its step-by-step approach to 
refining 
predictions 
and 
improving 
overall 
model 
performance. 
 
I. LightGBM 
LightGBM, short for Light Gradient Boosting Machine, is 
an efficient implementation of the GB algorithm. It is known 
for its speed and efficiency, particularly when dealing with 
large datasets. LightGBM introduces two novel techniques: 
(1) Gradient-based One-Sided Sampling (GOSS): This 
technique focuses on training instances with larger gradients, 
as these are considered more informative for calculating 
information gain [22]. By excluding instances with small 
gradients, LightGBM can achieve accurate estimations with a 
smaller dataset, improving training speed and reducing 
computational complexity. (2) Exclusive Feature Bundling 
(EFB): This technique addresses the issue of sparse features 
by bundling mutually exclusive attributes together [22]. This 
reduces the number of features, further enhancing efficiency. 
LightGBM's unique characteristic is its leaf-wise tree growth 
strategy. Unlike traditional GB methods that grow trees level-
wise, LightGBM selects the leaf that will reduce the loss the 
most at each step [23], as shown in Fig. 9. This approach often 
leads to more accurate models with fewer iterations.  
 
III. RESULT AND DISCUSSION 
A. Processed Walking Data and Feature Extraction 
 
The processed data was then used to extract 107 features, 
including statistical measures of accelerometer and gyroscope 
data, angles derived from acceleration vectors, and heart rate 
variability metrics. 
TABLE I.  
WATCH MOVIE THEN WALK DATA 
emo 
ax 
ay 
az 
rot_x 
rot_y 
rot_z 
heart 
1 
-2.20 
-0.26 
1.32 
-91.28 
8.89 
-125.51 
81 
1 
-2.68 
-2.11 
0.84 
-122.85 
-6.93 
-112.77 
81 
1 
-2.35 
-2.14 
0.84 
-35.14 
-10.43 
-90.65 
81 
1 
-2.46 
-1.73 
0.47 
-16.10 
-18.55 
-54.32 
81 
1 
-2.50 
-1.50 
-0.28 
-31.15 
-40.74 
-29.89 
81 
TABLE II.  
LISTEN TO MUSIC THEN WALK DATA 
emo 
ax 
ay 
az 
rot_x 
rot_y 
rot_z 
heart 
0 
0.18 
-0.08 
-1.02 
10.08 
14.91 
-60.48 
117 
0 
-0.26 
1.32 
-0.40 
77.35 
24.57 
-53.76 
117 
0 
0.66 
1.52 
0.26 
51.45 
3.08 
-60.48 
117 
0 
3.51 
1.42 
0.21 
32.62 
0.28 
-52.64 
117 
0 
3.54 
0.71 
0.65 
33.95 
14.70 
-32.76 
117 
 
Fig. 7. Visualization of AdaBoost 
 
Fig. 8. Visualization of gradient boosting 
 
Fig. 9. Visualization of LightGBM 
TABLE III.  
LISTEN TO MUSIC WHILE WALKING DATA 
emo 
ax 
ay 
az 
rot_x 
rot_y 
rot_z 
heart 
-1 
0.39 
0.33 
-0.18 
-5.88 
34.72 
27.72 
85 
-1 
0.05 
-0.33 
0.96 
7.28 
27.02 
29.89 
85 
-1 
0.78 
0.01 
-0.69 
6.16 
36.47 
26.53 
85 
-1 
0.46 
0.12 
1.10 
12.74 
36.05 
32.06 
85 
-1 
0.79 
0.20 
-1.21 
20.37 
44.80 
26.53 
85 
 
 
 
Tables I, II, and III present examples of the processed 
walking data, showcasing the values of the accelerometer (ax, 
ay, az), gyroscope (rot_x, rot_y, rot_z), and heart rate (heart) 
for each experimental condition and the corresponding 
expected emotion (emo). The 'emo' column represents the 
anticipated emotional state (1 for happy, 0 for neutral, and -1 
for sad). 
TABLE IV.  
WATCH MOVIE THEN WALK EXTRACTED DATA 
acc_x_std 
gyro_x_std 
angle_x 
mag 
heart 
emotion 
1.96 
71.05 
1.09 
0.67 
81 
1 
1.31 
96.83 
0.96 
0.73 
81 
1 
0.95 
134.85 
0.78 
0.89 
81 
1 
1.13 
133.53 
0.85 
0.87 
81 
1 
1.15 
116.86 
1.07 
1.00 
81 
1 
TABLE V.  
LISTEN TO MUSIC THEN WALK EXTRACTED DATA 
acc_x_std 
gyro_x_std 
angle_x 
mag 
heart 
emotion 
1.68 
47.20 
2.42 
0.75 
119 
0 
1.95 
42.74 
1.71 
0.86 
119 
0 
2.07 
41.49 
0.17 
0.82 
119 
0 
1.78 
41.71 
0.33 
0.77 
119 
0 
1.67 
47.10 
0.26 
0.80 
120 
0 
TABLE VI.  
LISTEN TO MUSIC WHILE WALKING EXTRACTED DATA 
acc_x_std 
gyro_x_std 
angle_x 
mag 
heart 
emotion 
0.23 
11.11 
2.15 
0.39 
108 
-1 
0.20 
12.53 
2.11 
0.20 
109 
-1 
0.31 
11.70 
1.99 
0.36 
109 
-1 
0.35 
13.46 
1.73 
0.33 
109 
-1 
0.51 
17.28 
1.56 
0.21 
109 
-1 
 
Tables IV, V, and VI display a subset of the 107 features 
extracted from the walking data. These features include the 
standard deviation of acceleration along the x-axis 
(acc_x_std), the standard deviation of gyroscope readings 
along the x-axis (gyro_x_std), the angle between the mean 
acceleration vector and the x-axis (angle_x), the magnitude 
of acceleration (mag), the heart rate (heart), and the 
corresponding emotion label (emotion). Each row in these 
tables represents a single data point with its extracted features 
and associated emotion label. 
B. Binary Classificatioin: Happy vs. Sad 
The results of the binary classification task, as illustrated 
in Fig. 10 and Table VII, underscore the exceptional 
performance of Gradient Boosting (GB) and LightGBM 
models in distinguishing between happy and sad emotions 
compared to previous research that relied on logistic 
regression and random forest models. LightGBM consistently 
outperformed all other models, achieving the highest average 
accuracy across all three experimental conditions: an 
impressive 89.4% accuracy for the "watch movie then walk" 
condition, 85.3% for "listen to music then walk," and a 
remarkable 91.8% for the "listen to music while walk" 
condition. This consistently superior performance can be 
attributed to LightGBM's ability to effectively capture and 
leverage subtle nuances present in both heart rate and 
movement data, even in dynamic and changing scenarios. 
 
TABLE VII.  AVERAGE USER LIFT AND AVERAGE MACHINE LEARNING 
MODEL ACCURACY FOR HAPPY AND SAD CONDITIONS ASCROSS EACH 
CONDITION 
Condition 1 
Watch movie 
then walk 
AUC 
F1 
Accuracy 
User 
Lift 
P-
value 
Baseline 
0.500 
(0.000) 
0.347 
(0.018) 
0.512 
(0.016) 
 
 
Logistic 
Regression 
0.877 
(0.084) 
0.817 
(0.088) 
0.818 
(0.088) 
0.306 
0.000 
Random Forest 
0.922 
(0.059) 
0.853 
(0.073) 
0.853 
(0.073) 
0.341 
0.000 
Adaboost 
0.912 
(0.076) 
0.847 
(0.091) 
0.847 
(0.091) 
0.335 
0.000 
GB 
0.937 
(0.060) 
0.878 
(0.079) 
0.878 
(0.079) 
0.366 
0.000 
LightGBM 
0.950 
(0.047) 
0.894 
(0.071) 
0.894 
(0.071) 
0.382 
0.000 
Condition 2 
Listen to music 
then walk 
AUC 
F1 
Accuracy 
User 
Lift 
P-
value 
Baseline 
0.500 
(0.000) 
0.342 
(0.007) 
0.508 
(0.006) 
 
 
Logistic 
Regression 
0.813 
(0.081) 
0.749 
(0.071) 
0.749 
(0.071) 
0.242 
0.000 
Random Forest 
0.887 
(0.046) 
0.807 
(0.046) 
0.808 
(0.046) 
0.300 
0.000 
Adaboost 
0.867 
(0.063) 
0.788 
(0.060) 
0.788 
(0.059) 
0.281 
0.000 
GB 
0.910 
(0.050) 
0.833 
(0.052) 
0.834 
(0.052) 
0.326 
0.000 
LightGBM 
0.928 
(0.043) 
0.853 
(0.050) 
0.853 
(0.050) 
0.346 
0.000 
Condition 3 
Listen to music 
while walking 
AUC 
F1 
Accuracy 
User 
Lift 
P-
value 
Baseline 
0.500 
(0.000) 
0.356 
(0.031) 
0.520 
(0.027) 
 
 
Logistic 
Regression 
0.901 
(0.095) 
0.850 
(0.107) 
0.850 
(0.106) 
0.330 
0.000 
Random Forest 
0.948 
(0.057) 
0.891 
(0.080) 
0.892 
(0.079) 
0.372 
0.000 
Fig. 10. Boxplot of accuracies for distinguishing happy vs. sad conditions 
Adaboost 
0.932 
(0.077) 
0.878 
(0.099) 
0.878 
(0.098) 
0.358 
0.000 
GB 
0.955 
(0.054) 
0.903 
(0.077) 
0.904 
(0.077) 
0.383 
0.000 
LightGBM 
0.966 
(0.044) 
0.918 
(0.068) 
0.918 
(0.068) 
0.398 
0.000 
 
GB also demonstrated strong performance in the 
classification task, achieving average accuracies of 87.8%, 
83.4%, and 90.4% across the three conditions, respectively. 
These results further validate GB's effectiveness in accurately 
differentiating between happy and sad emotional states. Its 
sequential learning approach, where each tree in the model is 
trained to correct the errors of the previous one, proved to be 
well-suited for capturing the nuanced differences between 
these emotions. 
While AdaBoost also exhibited notable performance with 
average accuracies of 84.7%, 78.8%, and 87.8% across the 
three conditions, its performance did not surpass that of the 
random forest models utilized in earlier research. However, 
AdaBoost consistently outperformed logistic regression, 
highlighting its capability in this classification task. 
C. Multi-class Classification: Happy vs. Neutral vs. Sad 
The multi-class classification task, as depicted in Fig. 11 
and Table VIII, presented a greater challenge compared to 
binary classification. Although LightGBM maintained its 
leading position with average accuracies of 80.3%, 76.3%, 
and 84.2%, the overall accuracies were lower, highlighting 
the complexities involved in differentiating between three 
distinct emotional states. 
GB continued to demonstrate robust performance, with 
average accuracies of 75.9%, 71.7%, and 80.9%, solidifying 
its position as a reliable method for emotion recognition and 
surpassing the performance of previous models. However, 
AdaBoost experienced a slight decline in accuracy, achieving 
average accuracies of 64.2%, 61.3%, and 69.4%, indicating 
its limitations compared to random forest in this more 
complex task. 
IV. CONCLUSION AND FUTURE WORK 
This study highlights the superior capabilities of Gradient 
Boosting (GB) and LightGBM algorithms in emotion 
recognition tasks using wearable sensor data. Notably, 
LightGBM 
consistently 
outperformed 
other 
models, 
achieving average accuracies of 88.8% for binary 
classification (happy vs. sad) and 80.2% for multi-class 
classification (happy, neutral, and sad) across all conditions 
(watch movie then walk, listen to music then walk, and listen 
to music while walking). GB also proved to be a robust 
method, with average accuracies of 87.2% and 76.2% for 
binary and multi-class classifications, respectively, across the 
same conditions. Both significantly surpassed the baseline 
DummyClassifier, Logistic Regression, and Random Forest 
models used in previous research. AdaBoost, while not 
surpassing Random Forest, still demonstrated its potential in 
emotion recognition by exceeding the baseline model and 
Logistic Regression, with average accuracies of 83.7% for 
binary and 64.9% for multi-class classifications across all 
conditions. 
The findings of this study have several implications for the 
development of future emotion recognition systems. The 
superior performance of LightGBM and GB suggests that 
ensemble 
methods, 
particularly 
those 
with 
efficient 
implementations and innovative tree-growing strategies, are 
promising avenues for improving emotion recognition 
accuracy. Furthermore, the use of wearable sensor data, such 
as heart rate and movement patterns, can provide valuable 
insights into real-world emotional experiences. 
Nonetheless, future studies should tackle the shortcomings 
of this research, particularly the limited number of participants 
and the specific experimental procedures used. Expanding the 
sample size and diversifying the experimental conditions 
would enhance the generalizability of the findings. 
Additionally, exploring the combination of multiple ensemble 
methods or the integration of other data sources, such as facial 
expressions or electrodermal activity, could further improve 
the accuracy and robustness of emotion recognition systems. 
 
 
TABLE VIII.  AVERAGE USER LIFT AND AVERAGE MACHINE LEARNING 
MODEL ACCURACY FOR HAPPY AND SAD CONDITIONS ASCROSS EACH 
CONDITION 
Condition 1 
Watch movie 
then walk 
AUC 
F1 
Accuracy 
User 
Lift 
P-
value 
Baseline 
0.500 
(0.000) 
0.175 
(0.010) 
0.343 
(0.011) 
 
 
Logistic 
Regression 
0.797 
(0.082) 
0.633 
(0.104) 
0.635 
(0.104) 
0.292 
0.000 
Random Forest 
0.878 
(0.061) 
0.721 
(0.090) 
0.723 
(0.090) 
0.380 
0.000 
Adaboost 
0.810 
(0.067) 
0.640 
(0.089) 
0.642 
(0.089) 
0.299 
0.000 
GB 
0.899 
(0.063) 
0.758 
(0.098) 
0.759 
(0.098) 
0.416 
0.000 
LightGBM 
0.928 
(0.048) 
0.802 
(0.087) 
0.803 
(0.087) 
0.460 
0.000 
Condition 2 
Listen to music 
then walk 
AUC 
F1 
Accuracy 
User 
Lift 
P-
value 
Baseline 
0.500 
(0.000) 
0.173 
(0.004) 
0.340 
(0.004) 
 
 
Logistic 
Regression 
0.763 
(0.057) 
0.591 
(0.062) 
0.593 
(0.062) 
0.253 
0.000 
Random Forest 
0.854 
(0.038) 
0.684 
(0.050) 
0.685 
(0.050) 
0.345 
0.000 
Adaboost 
0.792 
(0.047) 
0.611 
(0.058) 
0.613 
(0.058) 
0.272 
0.000 
GB 
0.879 
(0.041) 
0.716 
(0.057) 
0.717 
(0.057) 
0.377 
0.000 
LightGBM 
0.910 
(0.037) 
0.762 
(0.058) 
0.763 
(0.058) 
0.423 
0.000 
Condition 3 
Listen to music 
while walking 
AUC 
F1 
Accuracy 
User 
Lift 
P-
value 
Fig. 11. Boxplot of accuracies for distinguishing happy vs. neutral vs. sad 
conditions 
Baseline 
0.500 
(0.000) 
0.179 
(0.014) 
0.348 
(0.015) 
 
 
Logistic 
Regression 
0.853 
(0.083) 
0.710 
(0.114) 
0.712 
(0.113) 
0.364 
0.000 
Random Forest 
0.916 
(0.053) 
0.782 
(0.085) 
0.783 
(0.085) 
0.436 
0.000 
Adaboost 
0.843 
(0.059) 
0.686 
(0.090) 
0.694 
(0.084) 
0.346 
0.000 
GB 
0.931 
(0.050) 
0.809 
(0.088) 
0.809 
(0.088) 
0.462 
0.000 
LightGBM 
0.950 
(0.041) 
0.842 
(0.077) 
0.842 
(0.077) 
0.495 
0.000 
 
ACKNOWLEDGMENT 
We extend our heartfelt gratitude to Telkom University for 
their invaluable financial and institutional support, which has 
been instrumental in the successful completion of this 
research. 
REFERENCES 
[1] 
G. Walker and J. Venker Weidenbenner, “Social and Emotional 
Learning in the age of virtual play: technology, empathy, and 
learning,” Journal of Research in Innovative Teaching and 
Learning, vol. 12, no. 2, pp. 116–132, Aug. 2019, doi: 
10.1108/JRIT-03-2019-0046/FULL/PDF. 
[2] 
B. C. Stahl, Artificial Intelligence for a Better Future. Cham: 
Springer International Publishing, 2021. doi: 10.1007/978-3-030-
69978-9. 
[3] 
G. Airlangga, “Evaluating Machine Learning Models for Mental 
Health Diagnostics: A Comparative Analysis and Visual 
Insights,” KLIK: Kajian Ilmiah Informatika dan Komputer, vol. 
4, no. 4, pp. 2058–2068, 2024. 
[4] 
A. Thieme, D. Belgrave, and G. Doherty, “Machine Learning in 
Mental Health,” ACM Transactions on Computer-Human 
Interaction, vol. 27, no. 5, pp. 1–53, Oct. 2020, doi: 
10.1145/3398069. 
[5] 
N. Howell, “Emotional Meaning Making with Data,” UC 
Berkeley, 2020. 
[6] 
A. H. Bettis, T. A. Burke, J. Nesi, and R. T. Liu, “Digital 
Technologies for Emotion-Regulation Assessment and 
Intervention: A Conceptual Review,” Clinical Psychological 
Science, vol. 10, no. 1, pp. 3–26, Jan. 2022, doi: 
10.1177/21677026211011982. 
[7] 
F. Larradet, R. Niewiadomski, G. Barresi, D. G. Caldwell, and L. 
S. Mattos, “Toward Emotion Recognition From Physiological 
Signals in the Wild: Approaching the Methodological Issues in 
Real-Life Data Collection,” Front Psychol, vol. 11, Jul. 2020, 
doi: 10.3389/fpsyg.2020.01111. 
[8] 
J. C. Quiroz, E. Geangu, and M. H. Yong, “Emotion Recognition 
Using Smart Watch Sensor Data: Mixed-Design Study,” JMIR 
Ment Health, vol. 5, no. 3, p. e10153, Aug. 2018, doi: 
10.2196/10153. 
[9] 
M. A. Ganaie, M. Hu, A. K. Malik, M. Tanveer, and P. N. 
Suganthan, “Ensemble deep learning: A review,” Eng Appl Artif 
Intell, vol. 115, p. 105151, Oct. 2022, doi: 
10.1016/j.engappai.2022.105151. 
[10] 
A. Callens, D. Morichon, S. Abadie, M. Delpey, and B. Liquet, 
“Using Random forest and Gradient boosting trees to improve 
wave forecast at a specific location,” Applied Ocean Research, 
vol. 104, p. 102339, Nov. 2020, doi: 10.1016/j.apor.2020.102339. 
[11] 
O. Hornyák and L. B. Iantovics, “AdaBoost Algorithm Could 
Lead to Weak Results for Data with Certain Characteristics,” 
Mathematics, vol. 11, no. 8, p. 1801, Apr. 2023, doi: 
10.3390/math11081801. 
[12] 
J. Zhang, D. Mucs, U. Norinder, and F. Svensson, “LightGBM: 
An Effective and Scalable Algorithm for Prediction of Chemical 
Toxicity–Application to the Tox21 and Mutagenicity Data Sets,” 
J Chem Inf Model, vol. 59, no. 10, pp. 4150–4158, Oct. 2019, 
doi: 10.1021/acs.jcim.9b00633. 
[13] 
G. Pei, H. Li, Y. Lu, Y. Wang, S. Hua, and T. Li, “Affective 
Computing: Recent Advances, Challenges, and Future Trends,” 
Intelligent Computing, vol. 3, Jan. 2024, doi: 
10.34133/icomputing.0076. 
[14] 
J. Michalak, N. F. Troje, J. Fischer, P. Vollmar, T. Heidenreich, 
and D. Schulte, “Embodiment of Sadness and Depression—Gait 
Patterns Associated With Dysphoric Mood,” Psychosom Med, 
vol. 71, no. 5, pp. 580–587, Jun. 2009, doi: 
10.1097/PSY.0b013e3181a2515c. 
[15] 
E. N. Marieb and K. Hoehn, Human anatomy & physiology. 
Pearson, 2013. 
[16] 
R. Wijaya, T. Latifah, E. Rajab, A. Setijadi, R. Karel, and W. 
Mengko, “Hypertension Heart Disease Heart Rate Time Series 
Classification using Reshape Detrended Fluctuation Analysis,” 
2018. [Online]. Available: http://www.ripublication.com 
[17] 
J. Zhu, L. Ji, and C. Liu, “Heart rate variability monitoring for 
emotion and disorders of emotion,” Physiol Meas, vol. 40, no. 6, 
p. 064004, Jul. 2019, doi: 10.1088/1361-6579/ab1887. 
[18] 
R. Genuer and J.-M. Poggi, “Random Forests with R,” 2020, doi: 
10.1007/978-3-030-56485-8. 
[19] 
A. Saidi, S. Ben Othman, M. Dhouibi, and S. Ben Saoud, 
“FPGA-based implementation of classification techniques: A 
survey,” Integration, vol. 81, pp. 280–299, Nov. 2021, doi: 
10.1016/j.vlsi.2021.08.004. 
[20] 
P. Beja-Battais, “Overview of AdaBoost : Reconciling its views 
to better understand its dynamics,” Oct. 2023, [Online]. 
Available: http://arxiv.org/abs/2310.18323 
[21] 
C. Bentéjac, A. Csörgő, and G. Martínez-Muñoz, “A comparative 
analysis of gradient boosting algorithms,” Artif Intell Rev, vol. 
54, no. 3, pp. 1937–1967, Mar. 2021, doi: 10.1007/s10462-020-
09896-5. 
[22] 
I. D. Mienye and Y. Sun, “A Survey of Ensemble Learning: 
Concepts, Algorithms, Applications, and Prospects,” IEEE 
Access, vol. 10, pp. 99129–99149, 2022, doi: 
10.1109/ACCESS.2022.3207287. 
[23] 
D. D. Rufo, T. G. Debelee, A. Ibenthal, and W. G. Negera, 
“Diagnosis of diabetes mellitus using gradient boosting machine 
(Lightgbm),” Diagnostics, vol. 11, no. 9, Sep. 2021, doi: 
10.3390/diagnostics11091714. 
 
 
