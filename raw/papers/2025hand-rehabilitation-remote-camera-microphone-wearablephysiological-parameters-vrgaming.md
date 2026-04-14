Academic Editor: Luca Mesin
Received: 31 December 2024
Revised: 9 February 2025
Accepted: 19 February 2025
Published: 21 February 2025
Citation: Hadjar, H.; Vu, B.; Hemmje,
M. Empowering Recovery: The
T-Rehab System’s Semi-Immersive
Approach to Emotional and Physical
Well-Being in Tele-Rehabilitation.
Electronics 2025, 14, 852. https://
doi.org/10.3390/electronics
14050852
Copyright: © 2025 by the authors.
Licensee MDPI, Basel, Switzerland.
This article is an open access article
distributed under the terms and
conditions of the Creative Commons
Attribution (CC BY) license
(https://creativecommons.org/
licenses/by/4.0/).
Article
Empowering Recovery: The T-Rehab System’s Semi-Immersive
Approach to Emotional and Physical Well-Being in
Tele-Rehabilitation
Hayette Hadjar 1,*
, Binh Vu 2 and Matthias Hemmje 1,*
1
Faculty of Mathematics and Computer Science, University of Hagen, 58097 Hagen, Germany
2
Applied Data Science and Analytics, SRH University Heidelberg, 69123 Heidelberg, Germany;
binh.vu@srh.de
*
Correspondence: hayette.hadjar@fernuni-hagen.de (H.H.); matthias.hemmje@fernuni-hagen.de (M.H.)
Abstract: The T-Rehab System delivers a semi-immersive tele-rehabilitation experience by
integrating Affective Computing (AC) through facial expression analysis and contactless
heartbeat monitoring. T-Rehab closely monitors patients’ mental health as they engage
in a personalized, semi-immersive Virtual Reality (VR) game on a desktop PC, using a
webcam with MediaPipe to track their hand movements for interactive exercises, allowing
the system to tailor treatment content for increased engagement and comfort. T-Rehab’s
evaluation comprises two assessments: system performance and cognitive walkthroughs.
The first evaluation focuses on system performance, assessing the tested game, middleware,
and facial emotion monitoring to ensure hardware compatibility and effective support for
AC, gaming, and tele-rehabilitation. The second evaluation uses cognitive walkthroughs to
examine usability, identifying potential issues in emotion detection and tele-rehabilitation.
Together, these evaluations provide insights into T-Rehab’s functionality, usability, and
impact in supporting both physical rehabilitation and emotional well-being. The thorough
integration of technology inside T-Rehab ensures a holistic approach to tele-rehabilitation,
allowing patients to participate comfortably and efficiently from anywhere. This technique
not only improves physical therapy outcomes but also promotes mental resilience, marking
an important step advance in tele-rehabilitation practices.
Keywords: T-Rehab; tele-rehabilitation; emotion recognition; contactless heartbeat moni-
toring; semi-immersive game; CNN; multimodal emotion recognition
1. Introduction and Motivation
Tele-rehabilitation [1] involves the virtual supervision of physical, occupational,
speech, and other therapeutic interventions aimed at enhancing motor, cognitive, and
neuropsychiatric functions. Compared to traditional in-person or inpatient rehabilitation,
tele-rehabilitation typically lowers costs for both healthcare providers and patients [2].
Following a stroke, patients often experience weakness in the arm and hand, but significant
practice can lead to mobility recovery [3]. Achieving maximum motor function may require
performing arm movements over 2500 times [4]. Gaming systems with controllers and
video monitoring provide accessible and cost-effective solutions that can be incorporated
into rehabilitation programs [4].
This paper connects two projects: the first is SenseCare (Sensor-Enabled Affective
Computing for Enhancing Medical Care) [5] which uses sensors to recognize emotions and
improve medical care; the second is SMILE (Supporting Mental Health in Young People:
Electronics 2025, 14, 852
https://doi.org/10.3390/electronics14050852
Electronics 2025, 14, 852
2 of 20
Integrated Methodology for cLinical dEcisions and evidence-based interventions), a project
that helps young people with their mental health by supporting better clinical decision and
offering proven interventions.
This research explores key questions to enhance tele-rehabilitation through applied
gaming. It looks at how gaming environments can aid in rehabilitation, how VR training
can include emotion detection and vital sign monitoring, and how collected data can
improve rehabilitation programs. The project also focuses on creating secure, scalable
systems that protect patient data while allowing for future updates and new features. These
efforts aim to create flexible and effective solutions for patient rehabilitation and training
development. The goal is to introduce a new approach to tele-rehabilitation with T-Rehab,
a semi-immersive application that uses the camera to interact with games for upper limb
rehabilitation. This innovative solution aims to address the key challenges identified earlier.
The remainder of this paper is organized as follows: Section 2 explores the related
work in tele-rehabilitation using gaming. Section 3 presents the conceptual modeling,
information models, and architecture of the T-Rehab system, outlining its components
and functions. In Section 4, we detail the methodology used to develop and implement
the T-Rehab system. Section 5 discusses experimentation and evaluation of the T-Rehab
system. Section 6 displays advantages of the T-Rehab system. Finally, Section 7 concludes
the paper by summarizing the main ideas and proposing future directions for research and
development in the field of tele-rehabilitation.
2. Related Work
Motor impairment can be caused by conditions such as stroke, paralysis, dystonia,
and traumatic brain injury. These conditions often lead to expensive and frustrating reha-
bilitation, frequently resulting in treatment discontinuation [6,7]. Remote rehabilitation, or
tele-rehabilitation, allows patients to receive therapy at home using digital tools. Studies
show that gaming and virtual reality (VR) applications [8], by immersing users in inter-
active virtual environments, help treat NDs (Neurodegenerative Disorders) [9,10]. XR
(Extended Reality) games are seen as promising tools for functional tele-rehabilitation
and will be explored and evaluated in our research. In [11,12], Gamification increased
motivation through engaging tasks customized to the user’s situation and influenced by
emotions. XR (Extended Reality) technologies, from fully immersive virtual worlds to the
real world, are becoming more accessible and user-friendly. Concurrently, the HomeCoRe
system, as described by S. Quaglini et al. in their publication “Studies in Health Technology
and Informatics” in August 2019 [13], offers individuals with cognitive impairments per-
sonalized rehabilitation routines and activities through a web platform. The therapy plan
parameters, including frequency and duration, can be remotely established and monitored
using the therapist’s side dashboard. The study of Ding et al. (2018) [14] explores a Kinect-
based virtual rehabilitation system for upper limb disorders, showing its effectiveness in
improving motor recovery and patient engagement. The system offers real-time feedback
and adaptable exercises tailored to individual needs. Evaluation data from the system
helps monitor progress and adjust treatment plans for better outcomes.
Our previous works employed a semi-immersive approach for two key applications:
game-based upper limb tele-rehabilitation [15] and resilience building [16] using the Leap
Motion Controller (LMC). However, since the LMC is not certified for medical use, this
study proposes replacing it with a standard PC or laptop camera, utilizing Mediapipe for
motion detection. MediaPipe Hands is an on-device, real-time hand tracking tool that rec-
ognizes hand landmarks in video input, enabling gesture detection and human–computer
interaction [17]. The hand landmark model identifies 21 key points on the hand, focusing
on knuckle positions within detected hand regions. It was trained using around 30,000 real-
Electronics 2025, 14, 852
3 of 20
world images along with synthetic hand models placed on diverse backgrounds [18].
Figure 1 illustrates the detection of 21 hand landmarks using MediaPipe.
 
Figure 1. MediaPipe hand landmarks [18].
Islam et al. (2022) [19] developed a hand gesture-controlled version of Need for Speed
(NFS), utilizing MediaPipe for real-time hand tracking and Pygame for game development.
This strategy enables players to interact with the game without using traditional controllers,
resulting in a more immersive experience. The technology recognizes hand motions with
great accuracy, resulting in easy gameplay with minimal delay. By replacing traditional
input techniques with natural hand movements, the game becomes more accessible and
interesting. The study also emphasizes the possibility of adopting hand motion detection
in interactive applications other than gaming.
Emotion detection [20] and caregiver feedback are essential for monitoring and ad-
justing tasks during rehabilitation, supporting patient progress. Emotions can be classified
using either discrete or dimensional techniques. A combination of both methods, known
as a hybrid model, might offer a strong classification system. Wearable sensors play a key
role in continuously monitoring human activities [21]. Our study uses a hybrid model
of emotion classification and visualization, combining discrete and interactive graphical
techniques. This approach is aimed at accurately and flexibly identifying emotions. Facial
emotion recognition is improved using Convolutional Neural Networks (CNNs), which
are highly effective in analyzing image features and enhancing recognition accuracy.
Several tele-rehabilitation systems exist. Table 1 presents their approaches and impacts.
Table 1. Comparison of tele-rehabilitation approaches.
Study Source
Focus Area
Technology/Approach
Impact Observed
Levy et al.
(2015) [22]
Home tele-rehabilitation
Video-based
tele-rehabilitation
Positive improvements in patient
functionality and quality of life.
Ostrowska et al.
(2021) [23]
Home-based tele-rehabilitation for
cerebral palsy
(COVID-19)
Serious games
Patients maintained recovery progress
during restricted access to clinics.
da Silva et al.
(2021) [24]
Online multicomponent physical
exercise interventions
Serious game
platform
Patients maintained recovery progress
during restricted access to clinics.
Mayela et al.
(2023) [25]
Videoconference physical training
for seniors
Online physical
exercise programs
Participants demonstrated considerable
increases in physical activity levels.
Kuldavletova
et al. (2021) [26]
Videoconference-based training is safe
and beneficial for seniors, enhancing
physical activity and health outcomes.
Videoconference
training
Improved physical activity and safety,
particularly among isolated seniors.
Choukou et al.
(2023) [27]
Virtual reality for stroke
tele-rehabilitation
VR
Increased motivation and participation
among stroke survivors undergoing
tele-rehabilitation.
Electronics 2025, 14, 852
4 of 20
In comparison to existing tele-rehabilitation systems, T-Rehab demonstrates several
functional advantages that address key limitations in the field, as outlined in Table 1.
While previous studies focus primarily on either video conferences or serious games or VR,
T-Rehab combines the best of both approaches by integrating serious games, video calls,
VR, and emotion monitoring. This comprehensive approach ensures that patients receive
personalized, engaging, and adaptive rehabilitation support, bridging the gap between
traditional methods and advanced tele-rehabilitation technologies.
3. Conceptual Design
In this section, the T-Rehab system’s conceptual modeling is explored, with a focus
on a User-Centered System Design (UCSD) approach [28] to ensure that the system effec-
tively achieves the requirements of patients, caregivers, developers, and medical experts.
In the Conceptual Modeling Phase for the T-Rehab System, Unified Modeling Language
(UML) [29] is applied to develop a solid software foundation and clarify crucial. Class
diagrams provide a clear view of the system’s structure, helping both developers and
stakeholders. Use-case diagrams highlight user interactions, state diagrams depict system
changes over time, and object diagrams capture unique system states. Figure 2 illustrates
the patient intervention using applied gaming with emotion monitoring use case dia-
gram. In this use case, patients engage with XR games designed for rehabilitation while
their emotions are monitored in real-time using audiovisual sensors and wearable sensors
(e.g., Smartwatch). This use case includes steps such as setting up the game engine, setting
up the virtual environment, handling user input, and analyzing the patient’s emotions
during gameplay. By integrating emotion monitoring into the game engine, the system
can better understand the patient’s emotional responses and design the rehabilitation
experience accordingly.
Figure 2. T-Rehab Intervention—UML use case diagram for applied gaming with emotion recognition.
The T-Rehab System’s Emotion Detection Component is designed to detect and recog-
nize various emotions displayed by patients during gaming encounters via audiovisual
sensors and wearable devices. The system starts by preparing to monitor the patient’s
emotions, using cameras to capture facial images for emotion detection and microphones to
analyze speech for emotional information. Furthermore, wearable sensors, such as smart-
watches, monitor vital signs to provide additional physiological data, while a microphone
records audio to detect speech emotions. To fully comprehend the patient’s emotional
Electronics 2025, 14, 852
5 of 20
states, the system integrates speech, facial expressions, and vital signs into its analysis of
the gathered data.
In Figure 3, the architecture model of T-Rehab focuses on the system’s structure,
highlighting both the frontend and backend components.
Figure 3. T-Rehab architecture model.
The T-Rehab architecture model comprises both frontend and backend components.
The frontend component consists of multiple interfaces. The Patient Interface enables
patients to log in, play games, and submit feedback. The Caregiver Interface allows care-
givers to manage patient schedules, analyze emotions during sessions, receive reports,
and offer assistance. Caregivers collaborate with therapists to adjust rehabilitation plans,
evaluate patient progress, and refine therapies as needed. Developers use the Developer
Interface to modify and update gaming features, incorporate new technologies, and imple-
ment adaptations. The backend component is composed of databases and services. The
User Database stores information about user accounts (Patients, Therapists, and Admins).
The Rehabilitation Monitoring Database stores data from emotion detection sensors used
during therapy sessions. The System Configuration Database contains system settings,
user roles, and permissions. The services include user authentication, alert management,
rehabilitation game management, and feedback management.
Electronics 2025, 14, 852
6 of 20
4. Implementation
T-Rehab employs strategies to integrate its three core contexts: Emotion Recognition,
Applied Gaming, and the integration of Emotion with Applied Gaming. T-Rehab combines
emotion recognition and applied gaming for interactive rehabilitation. The system tracks
patients’ emotions and adjusts the games to keep them motivated and balanced during
rehab, improving both physical recovery and emotional well-being.
The T-Rehab platform architecture is divided into three separate layers. The first layer,
the User Interface (UI), offers a web-based interface for patients to access rehabilitation
exercises. This layer integrates various interactive technologies, including immersive
game interfaces, audiovisual sensors like cameras and microphones, wearable sensors for
tracking emotions and vital signs, and cameras for both facial emotion recognition and hand
tracking during gameplay. The second layer, Application Logic, runs in a cloud computing
environment and analyzes sensor data using methods such as Machine Learning (ML)
and CNN. This layer also handles data storage in databases, as well as the immersive
rehabilitation game. Figure 4 illustrates the implementation architecture of T-Rehab.
 
Figure 4. Implementation architecture of T-Rehab.
The T-Rehab experiment employed a monolithic architecture to simplify development
and deployment. All components were combined into a single Virtual Machine (VM)
on Hagen University’s cloud. The architecture implementation of T-Rehab consists of
two main layers: the Edge Layer and the Cloud Layer. The Edge Layer provides user
interfaces for patients, caregivers, and administrators, enabling real-time monitoring and
analysis of the patient’s condition during tele-rehabilitation. Data from microphones, cam-
eras, and wearable sensors is processed locally using pre-trained AI models and sent to
the cloud for further storage and analysis. To enhance interaction, the LMC is connected
to the browser via WebSocket technology, allowing patients to use hand gestures during
rehabilitation exercises. WebSocket servers also enable video calls for patient support when
needed. Therapists can view data and make informed decisions through their interface.
Electronics 2025, 14, 852
7 of 20
Currently, real-time monitoring of emotions and heartbeat is achieved using the patient’s
camera, with plans to incorporate wearable sensors and microphones for more compre-
hensive monitoring. The Cloud Layer stores data from the Edge Layer, including user
profiles, processed information, and appointments, while hosting AI models, rehabilitation
games, and a secure backup of all data. Data are efficiently processed, combined, and
managed within a secure database layer. The backend was built using Node.js for speedy
asynchronous operations and Express for optimized server-side functionality, including
interfaces for patient registration, appointment scheduling, consent management, tele-
rehabilitation, and administrative tasks. Central to its design is the integration of a CNN’s
models trained to recognize emotions directly within a web browser, enabling the assess-
ment of users’ emotional states in real time during rehabilitation tasks. The T-Rehab system
uses cloud computing to accelerate data processing and storage, ensuring adaptability and
user accessibility.
4.1. Applied Game
T-Rehab focuses on applied gaming, using interactive simulations and role-playing
to support healthcare. These games are designed to simulate real-world rehabilitation
scenarios, allowing patients to recover their upper and lower body limbs and promote
well-being. Initially, our focus is on the recovery of upper limbs, with medical specialists
collaborating to create each game based on individual requirements. WebXR [30,31] is used
for interactive simulations. Storyboards will guide the design, and a basic prototype will
be created for testing. The game will be accessible via web browsers with simple graphics
and audio.
Semi-immersive desktop gaming is used in this method, with emotion recognition
handled by a laptop or PC camera, while game interaction is facilitated through the same
camera. For the semi-immersive rehabilitation experience, the camera tracks hand gestures,
offering an interactive tool for physical therapy in both hospitals and at home. MediaPipe
is used to track hand and finger movements in three dimensions. Combining MediaPipe
with the PC camera provides an affordable and accessible way for remote rehabilitation,
letting users engage in exercises and monitor their progress without needing specialized
equipment. Figure 5 shows the T-Rehab hyper-limb remote rehabilitation process. The
process begins with Step 1: Camera Input, where the camera captures live hand movements,
providing the data needed for tracking. In Step 2: Hand Tracking, 3D Visualization, and
Gesture-Based Interaction, MediaPipe tracks hand landmarks and converts them into
3D coordinates, which are then displayed in a virtual environment using Three.js [32].
This enables real-time interaction with virtual objects through gestures such as pinching,
swiping, rotating, and grabbing. In Step 3: Task-Oriented Rehabilitation Exercises, the
therapist selects a 3D game for the patient, guiding them through tasks like reaching,
grasping, and object manipulation. Visual and auditory feedback is provided throughout
to support motor recovery and increase engagement.
ColorMatch Rehab is an interactive recovery game that helps patients improve co-
ordination and motor skills. Using hand movements, they guide cubes to planes of the
same color. The game is built with Three.js for 3D visuals and MediaPipe for hand tracking,
making rehabilitation more engaging and immersive. A demo of the ColorMatch Rehab
game is available at this link: https://studev5.fernuni-hagen.de:5189/modalhand.html
(accessed on 18 February 2025).
People who need specific hyper-limb treatment, such as hand rehabilitation after a
fracture, will be selected to participate in the experiment. New games will be developed
or existing ones adapted in collaboration with medical experts, with diagnostic criteria
incorporated to better address the needs of patients. After development, the games will be
Electronics 2025, 14, 852
8 of 20
integrated into the platform, and personalized session plans will be created for each patient.
The T-Rehab demo is available at the following URL: https://studev5.fernuni-hagen.de:
5189/home (accessed on 18 February 2025).
Figure 5. Overview of the T-Rehab system for hyper-limb remote rehabilitation.
4.2. Multimodal Emotion Recognition
Emotion detection using a single camera and non-contact heart rate monitoring (BPM)
is identified as a core element of this research. Based on Keary’s AC-Strata model (2018) [33],
which emphasizes the importance of integrating visual data with wearable sensor inputs to
achieve accuracy in AC, the proposed approach combines facial expression analysis and
BPM (Beats Per Minute) data. This integration aims to create a more reliable and accurate
system, addressing the limitations of relying on a single data source. By integrating these
inputs, the approach aims to improve emotion recognition and reduce potential ambiguity.
Real-time video processing utilizes a TensorFlow-based Convolutional Neural Net-
work (CNN) to identify facial expressions. As established in our previous work [34], the
system operates seamlessly within a web browser. For emotion detection, two models are
employed: SSD Mobilenet v1 and Face Expression Net.
The SSD Mobilenet v1 model is responsible for detecting faces in an image by deter-
mining their location and size. Once the faces are identified, the Face Expression Net model
analyzes them to classify emotions. This model is capable of recognizing seven distinct
emotions: happiness, sadness, anger, surprise, fear, disgust, and neutral. Together, these
models effectively detect faces and accurately classify their corresponding emotions.
Contactless heart rate monitoring begins with face detection, a crucial step before
identifying the Region of Interest (RoI). The Viola–Jones algorithm, employing Haar-like
features, efficiently detects facial areas within video frames. After the face is identified,
the RoI (e.g., in the forehead) is isolated. Remote PhotoPlethysmography (rPPG) is then
applied to the RoI to extract heart rate data. Figure 6 illustrates the data fusion of facial
expression analysis with contactless heart rate monitoring from real-time video processing.
Adults should expect to have a resting heart rate between 60 and 100 BPM [35]. In order
to guarantee precise emotion recognition, the analysis takes into account the emotional
states and heart rates that are measured within this range. The accuracy can be obtained
using the following formula:
Emotion Recognition Accuracy (%) = Nv
Nt × 100%
Electronics 2025, 14, 852
9 of 20
where Nv refers to the number of emotional states detected with BPM values ranging from
60 to 100 bpm, and Nt refers to the total number of emotional states detected. Furthermore,
instances in which the BPM passes below 60 bpm or above 100 bpm are noted for additional
examination. These variations, particularly when linked to feelings like fear, anger, or
disgust, may be indications of extreme stress or pain. This method guarantees a more
accurate evaluation of physiological and mental states. For example, if the system detects
10 emotions during a session and 8 of them have BPM values within the normal adult range
(60–100 bpm), the emotion recognition accuracy will be determined as:
Accuracy = 8/10 × 100
Figure 6. Data fusion of facial expression analysis and contactless heart rate monitoring.
So, Accuracy = 80%. This shows that the system accurately detected 80% of the
emotions, with BPM values being within the expected range. The other two emotions
with BPMs outside of this range would be flagged for further investigation to determine
potential peak stress or pain, particularly if they are associated with negative emotions
(such as sadness, fear, anger, or disgust).
Figure 7 shows how facial emotions and heart rate are tracked during a rehab session
to monitor stress and pain over time. Emotions are displayed with clear color coding and
simple levels to make the chart easy to read. Heart rate and emotion data are pulled from
the server in real time, and the chart is automatically updated as the session progresses.
Each emotion is placed at a specific level on the chart for clarity, and labels are added to
highlight important points.
Figure 7. Fusion of facial expressions and heart rate monitoring to detect stress and pain during rehab.
Electronics 2025, 14, 852
10 of 20
The design is responsive, so it works well on a variety of screen sizes and uses
Chart.js [36] library for data visualization. This allows clinicians to observe how participants
operate emotionally and physically during their rehabilitation.
4.3. Real-Time Patient–Therapist Support with Video Calls in Remote Rehabilitation
In line with our work on the TheraSense system [37], the video call functionality in
this system shares a similar foundation but does not incorporate emotion monitoring. Its
primary purpose is to provide audiovisual guidance for patients, particularly during their
initial rehabilitation sessions. Therapists can demonstrate how to rehabilitate the upper
limb by explaining and showing hand movements and interactions with the game. Patients
can access the video call in a separate browser window during gameplay for real-time
support. Additionally, they can schedule extra calls if they encounter challenges or need
further assistance. The feedback system enables patients to request video calls, ensuring
clear guidance and accelerating recovery.
T-Rehab uses WebRTC for direct connections between patients and therapists.
A Node.js server facilitates the connection by sharing necessary data, while Socket.io
handles the signaling process, enabling the exchange of connection information to establish
the WebRTC link. Once established, video and audio streams are transmitted directly
between the devices. This setup ensures real-time support and guidance during therapy
sessions, improving communication and enhancing patient care.
5. Experimentation and Evaluation
In the first evaluation, a quantitative assessment will be conducted to evaluate the
system performance [38,39] of the T-Rehab game, T-Rehab middleware, and the T-Rehab
facial emotion monitoring process. This evaluation ensures that the required hardware
is compatible with running the game and that the middleware effectively supports all
functionalities related to AC, gaming, and tele-rehabilitation. Additionally, it assesses the
effectiveness of the models used for emotion monitoring and verifies hardware compati-
bility for game execution. Collectively, these evaluations ensure that T-Rehab is not only
effective but also user-friendly, meeting the diverse needs of its users.
In the second evaluation, quantitative cognitive walkthroughs [40] will be used as
a method to assess usability and identify potential issues in emotion detection and tele-
rehabilitation, aligning with T-Rehab’s goals.
5.1. Quantitative Performance Evaluation of the T-Rehab System: Game, Middleware, and Facial
Emotion Monitoring
To ensure that T-Rehab operates smoothly and effectively supports gaming, AC,
and tele-rehabilitation, this evaluation examines the system’s performance, including its
game, middleware, and facial emotion monitoring. It focuses specifically on hardware
compatibility, system efficiency, and the effectiveness of the emotion detection models.
5.1.1. Quantitative Performance Evaluation of the T-Rehab Game: Hardware Requirements
and Execution Compatibility
Five devices were used to evaluate the hardware requirements and execution com-
patibility of the T-Rehab ColorMatch Rehab Game. These devices were assessed for their
ability to support WebGL rendering, WebXR capabilities, camera access, hand detection,
and complete game execution. The findings reveal notable differences in performance.
Device 1 (MacBook Air, 25 GB RAM, macOS Sonoma 14.1.1, One Apple Park Way,
Cupertino CA 95014, USA) executed perfectly, with full compatibility for WebXR, WebGL,
and camera access, allowing the game to run without errors and supporting hand detection.
Device 2 (Toshiba Laptop, Intel Core i3, 4 GB RAM, Windows 7) encountered several
Electronics 2025, 14, 852
11 of 20
problems, including a WebXR error caused by an overridden API, a failure to create a
WebGL2 context preventing 3D rendering, and a “Could not start video source” error that
blocked camera access and hand detection. Device 3 (MacBook, Intel Core 2 Duo, 4 GB
RAM, macOS High Sierra) had similar WebXR and WebGL issues to Device 2, making
it unable to render the game, though its camera functioned properly. However, hand
detection was still not possible due to WebGL limitations. Device 4 (Alphatron, Intel Core
i7, 16 GB RAM, Windows 10 Pro) had no issues, running the game smoothly with full
WebXR, WebGL, and camera support, including hand detection. Likewise, Device 5 (Redmi
9T Smartphone, 64 GB RAM, Android QKQ1.2008.002) successfully ran the game without
errors, demonstrating complete compatibility with WebXR, WebGL, and camera-based
hand detection. Table 2 shows detailed results. The ✅ (Supported/Runs successfully)
symbol indicates that the feature is fully functional and works as expected, while the ❌
(Not Supported/Fails) symbol signifies that the feature is not supported or encounters
critical errors preventing functionality.
Table 2. T-Rehab game—device compatibility and performance.
N
Device
Name
Hardware
Specifications
WebXR
Issues
WebGL
Issues
Camera
Access Issues
Hand
Detection
Game
Execution
1
MacBook
Air
25 GB RAM,
macOS Sonoma
14.1.1
No error.
No error.
No error.
✅ 
Supported
✅ Runs
successfully
2
Toshiba
Laptop
Intel Core i3, 4 GB
RAM, Windows 7
- Error related to
webxr-polyfill.js.
- WebXR emulator
extension is active.
- Native WebXR API
overridden by polyfill.
- WebGL context
creation failed.
- Could not create a
WebGL2 context.
- Warnings
regarding WebGL
context.
- “Could not
start video
source” error.
- Possible
camera
permission
issue.
❌Not
Supported
❌Fails due
to WebGL
issues
3
MacBook
Intel Core 2 Duo,
4 GB RAM, macOS
High Sierra)
- WebXR polyfill active.
- WebXR emulator
extension enabled.
- Native API overridden
by polyfill.
WebGL2 context
creation failed.
No camera
access issues.
❌Not
Supported
❌Fails due
to WebGL
issues
4
Alphatron
PC
Intel Core i7, 16 GB
RAM, Windows
10 Pro
No error.
No error.
No error.
✅ 
Supported
✅ Runs
successfully
5
Redmi 9T
Smart-
phone
64 GB RAM,
Android
QKQ1.2008.002
No error.
No error.
No error.
✅ 
Supported
✅ Runs
successfully
In contrast to Devices 2 and 3, which failed due to WebGL constraints, Devices 1, 4,
and 5 successfully ran the T-Rehab Game without issues. Optimal performance requires
devices with WebGL2 support for accurate 3D rendering, native WebXR API compatibility
to minimize reliance on polyfills, and a minimum of 8 GB RAM with a dedicated GPU
for stable execution. Additionally, effective hand detection and emotion tracking depend
on unrestricted camera access. Future developments should focus on enhancing WebGL
support, reducing dependency on WebXR polyfills, and improving camera accessibility.
Devices 1, 4, and 5 demonstrated the best performance, as they fully supported hand
detection, ran the game successfully, and showed no problems with compatibility.
5.1.2. Quantitative Evaluation Using System Performance Evaluation of T-Rehab
Prototype Middleware
The System Performance evaluation of the T-Rehab middleware assesses the platform’s
efficacy and reliability by focusing on its support for tele-rehabilitation, emotion monitor-
Electronics 2025, 14, 852
12 of 20
ing, and authentication features, within a semi-immersive applied gaming environment
powered by a Node.js backend.
To calculate the middleware performance response time in the VM of the T-Rehab
system, the curl command was used to measure the time taken for server requests to be
processed. Figure 8 shows the output of the curl command for the doctor login form.
 
Figure 8. Performance measurement of T-Rehab prototype middleware using curl.
To assess the middleware’s response time to user login attempts, a System Performance
evaluation was conducted. A series of queries were sent to the application’s login endpoint
using the curl command, and the response times for each request were recorded. The
recorded response times for the seven login attempts were 93 ms, 157 ms, 155 ms, 237 ms,
231 ms, 157 ms, and 230 ms. After converting these measurements to milliseconds, the total
response time for all attempts was calculated to be 1260 ms. Table 3 illustrates these results.
Table 3. Middleware performance: user login attempt response times.
Metric
Value
Number of login attempts
7
Response times (ms)
93, 157, 155, 237, 231, 157, 230
Total response time (ms)
1260
Average response time (ms)
180
The average response time was estimated to be approximately 180 ms by dividing the
total response time (1260 ms) by the number of requests (7). This average represents the
middleware’s efficiency in processing user authentication requests, showing satisfactory
application performance. Continuous monitoring and testing are essential for ensuring high
system performance and identifying potential areas for improvement, thereby improving
the entire user experience during the remote rehabilitation process.
5.1.3. Quantitative Evaluation of the T-Rehab System: System Performance Assessment for
Facial Emotion Monitoring
Facial emotion recognition plays a crucial role in evaluating and optimizing the game
experience for patients during tele-rehabilitation sessions. To assess the CNN models used
in this process, a script was developed and is available at this URL https://studev5.fernuni-
hagen.de:5184/ (accessed on 18 February 2025). This script includes essential functionalities
such as loading pre-trained models (ssdMobilenetv1 and faceExpressionNet) for facial
detection and emotion recognition, uploading an image for analysis, and displaying the
detected emotions along with inference time.
The experimentation and evaluation of the models were conducted using publicly
available datasets (FACES: a database of facial expressions in young, middle-aged, and
older women and men [41]), ensuring reproducibility and reliability of the results.
The experimentation and evaluation of the models were conducted using a database
containing 72 images. These images are grouped into various categories based on Emotion
(anger, disgust, fear, happiness, neutrality, sadness), Gender (female, male), and Age Group
Electronics 2025, 14, 852
13 of 20
(young, middle-age, old). This categorization ensures comprehensive testing across diverse
demographic and emotional variations.
The testing was performed on a PC equipped with an Alffatron processor, 16 GB RAM,
running Windows, and utilizing an ADSL internet connection. The network conditions
were measured as follows: latency of 2 ms, download speed of 76.84 Mbps, and upload
speed of 93.71 Mbps. These specifications provide the necessary computational power and
network stability to validate the system effectively.
The results of the experimentation are summarized in the following table, which
can be accessed through the Excel file URL https://studev5.fernuni-hagen.de:5184/data_
processing_Faces.xlsx (accessed on 18 February 2025).
The results of the experimentation are summarized in the following table, which can
be accessed through the Excel file. This table provides details about the image ID, the actual
emotion, the predicted emotion, and additional evaluation metrics such as the following:
Inference Time (ms): the time required for the model to process the image and produce
a detected emotion; Confidence Score: this score, derived from faceExpressionNet, reflects
the probability assigned to each emotion; Correct/Incorrect: this indicates whether the
predicted emotion matched the actual emotion.
Out of 72 images, 61 were correctly predicted, resulting in an accuracy of 84.72%.
Accuracy = 61
72 × 100
Table 4 provides a summary of emotion detection accuracy across different age groups,
focusing on both positive and negative emotions.
Table 4. Age group-based accuracy analysis for positive and negative emotions.
Age Groupe
Accuracy—Positive Emotion
Accuracy—Negative Emotion
middle-age
100.00%
81.25%
old
100.00%
50%
young
100.00%
100%
The system shows excellent accuracy for positive emotions, achieving 100% across all
age groups. However, there are noticeable differences in accuracy for negative emotions.
For the middle-aged group, the accuracy is 81.25%, which is relatively good but not
perfect. The young group matches the positive emotion performance with 100% accuracy.
In contrast, the old group shows a much lower accuracy of 50%, revealing potential issues
or biases in the detection model. This highlights the need to examine the training data’s
diversity and the model’s ability to identify age-related expression differences. Addressing
these gaps could improve performance and ensure balanced accuracy for all age groups.
Figure 9 illustrates a comparison of accuracy for positive and negative emotions across
different age groups, highlighting these discrepancies.
Additionally, Figure 10 provides insights into confidence scores, where part (a) presents
a chart of confidence scores for correct predictions, while part (b) shows a chart for
incorrect predictions.
Furthermore, the average confidence score for correctly predicted images is 96.22%,
calculated by dividing the total inference scores for correct predictions by 61. This shows
that the model is reliable and accurate in most cases.
Figure 11 shows the inference time (in milliseconds) required for emotion recognition
for each image using two models: SSD MobileNet v1 and Face Expression Net. Most infer-
ence times range between 326.4 ms and 665 ms, with an average of 415.98 ms, demonstrating
consistent performance. The standard deviation of 60.11 ms indicates moderate variability
Electronics 2025, 14, 852
14 of 20
in processing times. Excluding the top three highest values provides a clearer analysis by
focusing on typical behavior. Ultimately, the model demonstrates strong performance, but
minimizing occasional delays could further enhance its speed and reliability.
Figure 9. Comparison of positive and negative emotion detection accuracy across age groups.
 
 
(a) 
(b) 
Figure 10. Confidence score analysis: (a) confidence scores for correct predictions; (b) confidence
scores for incorrect predictions.
In conclusion, faceExpressionNet achieved an accuracy of 84.72% with 61 out of
72 images correctly predicted. It performed excellently with positive emotions, achieving
100% accuracy across all age groups. However, accuracy for negative emotions varied, with
the middle-aged group at 81.25% and the older group at 50%, suggesting potential issues
with age-related expression recognition. faceExpressionNet average confidence score for
correct predictions was 96.22%, indicating high reliability. Inference times were generally
consistent, with an average of 415.98 ms and moderate variability. Further improvements
could address age-related accuracy gaps and optimize processing times.
Table 5 summarizes the system’s facial emotion recognition performance, highlighting
accuracy, confidence scores, and areas for improvement.
Electronics 2025, 14, 852
15 of 20
Figure 11. Inference time analysis: model performance per image.
Table 5. Summary of facial emotion recognition evaluation.
Metrics
Findings/Results
Prediction Accuracy
84.72% (61 out of 72 images correctly predicted)
Positive Emotion Accuracy
100% across all age groups
Negative Emotion Accuracy
100%: young group; middle-aged group: 81.25%; older group: 50%, indicating issues with age-related
expression recognition
Average Confidence Score
96.22% for correct predictions, indicating high reliability
Inference Time (Average)
415.98 ms, with moderate variability
Recommendations
Address age-related accuracy gaps and optimize processing times for further improvements
5.2. Qualitative Evaluation Using Cognitive Walkthroughs Evaluation for T-Rehab
Table 6 highlights the essential tasks for conducting a qualitative evaluation of the
T-Rehab system utilizing cognitive walkthroughs. It focuses on doctor–patient interaction,
system usability, and the use of emotion and heart rate to guide rehabilitation decisions.
The T-Rehab prototype requires patients to use a semi-immersive solution, including a PC
or laptop with a camera, for interacting with the game and monitoring emotions and pulse
rate while engaging in rehabilitation activities.
The T-Rehab experiment was conducted on a MacBook Air with an Apple M2 chip
and 24 GB of RAM, One Apple Park Way, Cupertino CA 95014, USA. The built-in laptop
camera was used with MediaPipe, a library that facilitates hand and finger tracking for
rehabilitation exercises in the T-Rehab system.
For Task 7, the evaluation focused on whether the patient received real-time feedback
on their progress, emotional state, and heart rate during the session. An example of the
output is shown in Figure 12, where a video of an AI avatar displayed on a smartphone,
positioned facing the camera, provides real-time monitoring data. The video was generated
using the website Heygen [42]. This demonstrates the system’s ability to effectively analyze
and display both emotional and physiological states, even with a simulated or virtual
subject, ensuring a comprehensive monitoring experience.
Electronics 2025, 14, 852
16 of 20
Table 6. Tasks for cognitive walkthroughs of T-Rehab.
Task
Objective
Evaluation Results
1. Doctor Login
Doctor accesses the T-Rehab platform via a specific URL.
https://studev5.fernuni-hagen.de:5189/logindoctor
(accessed on 18 February 2025).
- Usability: the login process is smooth and intuitive.
- Feedback: the system confirms successful login and notifies the user if the
login data are incorrect.
- Security: the doctor account data are secure (Hashed password in database,
and the use of HTTPS in the application).
2. Create New Patient
Profile
Doctor creates a new patient profile, entering essential
information.
- Confirmation: the creation of a new profile is clearly confirmed.
3. Schedule Remote
Session
Doctor schedules a rehabilitation session for an existing
patient.
- Navigation: The scheduling feature is easy to find and use.
- Clarity: session details are (date, time, etc.) easy to input and review.
4. Select Adaptive Game
Doctor selects a rehabilitation game tailored to the patient’s
health status.
- Adaptability: the doctor easily matches the game to the patient’s condition.
- Confirmation: the selection process is clear and verified by the system.
5. Patient Login
Patient logs into their personal space using a provided URL
https://studev5.fernuni-hagen.de:5189/loginpatient
(accessed on 18 February 2025).
- Ease of Access: the login process is intuitive.
- Feedback: the system confirms successful login and notifies the user if the
login data are incorrect.
6. Patient/Therapist
Video Call
Enable audiovisual communication between the therapist
and patient before, during, or as needed during a session.
A “Start Video Call” is available on both the patient and therapist dashboards
to ensure communication between the patient and therapist at the
scheduled time.
7. Start Semi-Immersive
Setup
Patient sets up the PC or laptop with a camera for emotion
and heartbeat monitoring.
- Setup Process: the semi-immersive setup is easy to follow with
clear instructions.
- System Feedback: the system confirms that monitoring and interaction
devices are active.
8. Participate in
Scheduled Session
The patient selects the scheduled session and starts playing
the rehabilitation game, using the hand-tracking camera
for interaction.
- Usability: The game features intuitive controls using the camera.
9. Submit Feedback
and Rating
Patient provides text feedback and a rating score at the end
of the session.
- Ease of Use: the feedback form is simple and quick to complete.
- Clarity: rating options are clearly defined.
10. Doctor Reviews
Monitoring Data
Doctor reviews the patient’s emotion and heartbeat
monitoring results on their dashboard.
- Visualization: the monitoring results (e.g., emotion trends, heart rate) is
clearly displayed.
- Interpretability: the doctor can easily understand and analyze the data.
11. Adjust
Rehabilitation Plan
Based on monitoring results (e.g., if negative emotions
exceed positive ones), the doctor updates the
patient’s game.
- Adaptability: updating the rehabilitation plan is straightforward.
- System Feedback: the system confirms and implements the updated game
effectively.
 
Figure 12. Real-time feedback display of emotional and physiological states using AI avatar in
T-Rehab game.
In Task 8, the patient selects the scheduled session and begins playing the rehabilitation
game using the hand-tracking camera for interaction. Figure 13 displays a screenshot of
Electronics 2025, 14, 852
17 of 20
the game, showing the user closing their hand to move a cube onto a plane of the same
color. Mediapipe landmark points are visible, highlighting the hand-tracking interaction.
 
Figure 13. Hand-tracking interaction in ColorMatch Rehab.
For task 10, an example of the output visualization is shown in Figure 7. The interactive
chart helps detect stress or pain during gameplay by tracking changes over time.
The web game interface utilizes the browser’s audiovisual sensors, including a camera
for facial expression detection and contactless vital signs monitoring, and hand interac-
tion during gameplay. However, the T-Rehab prototype has not yet been tested directly
with patients.
6. Discussion
This semi-immersive tele-rehabilitation system is designed for patients with upper
limb rehabilitation needs. It is cost-effective, requiring only a good PC with a camera
instead of expensive virtual reality headsets. Additionally, it enhances safety compared to
full-immersion systems, reducing the risk of accidents.
A key advantage of this approach is its integration with the real environment. Patients
can interact naturally with their environment while performing exercises, promoting
comfort and psychological well-being. The minimal setup and space requirements make
semi-immersive systems ideal for home-based rehabilitation.
Web-based games further support rehabilitation by encouraging social interaction and
psychological engagement. They enable patients to connect with others while allowing
therapists to provide remote guidance, improving the effectiveness of therapy. WebXR
and Three.js provide an engaging and immersive gaming experience by creating realistic
3D scenes with interactive audio. These technologies enhance rehabilitation by making
exercises more visually appealing and responsive, helping patients stay motivated. The
realistic environments and spatial audio improve immersion, making therapy sessions
feel more natural and engaging. Web-based games also allow patients to play with others,
which promotes collaboration, boosts motivation, and creates a supportive and engaging
rehabilitation experience.
Electronics 2025, 14, 852
18 of 20
Hand-based camera systems enhance motivation by making rehabilitation interactive
and engaging. Patients use natural hand movements, such as grabbing and pointing, to
perform intuitive exercises. Instant feedback helps track progress in accuracy and strength,
while WebXR games create immersive experiences accessible from any device. The system
dynamically adjusts difficulty levels to maintain a balance between challenge and engage-
ment, while remote supervision and multiplayer options offer additional social support.
Deploying the system in a cloud-based VM provides significant technical benefits.
It enables efficient processing of large datasets, optimizing therapy exercises and the overall
rehabilitation experience. Additionally, it ensures scalability and incorporates strong
security measures to protect patient and therapist data.
Integrating an interactive chart that combines the monitoring of contactless vital
signs (e.g., heart rate, respiration) with emotion detection offers valuable insights during
rehabilitation. By analyzing these data points, therapists can identify moments of height-
ened stress or discomfort and adjust exercises accordingly for a more personalized and
effective treatment.
7. Conclusions
In this paper, the T-Rehab system is proposed for remote hyper-limb rehabilitation.
Rehabilitation using semi-immersive systems with a home computer is highlighted for
its numerous benefits, making it an appealing option for many patients. The conceptual
design and architecture of the T-Rehab system were presented, along with its architectural
implementation, methods, and evaluation focusing on system performance, usability, and
user experience.
The T-Rehab system’s future development will be focused on improving its capabilities
to better support patient rehabilitation. One significant advance is the incorporation of
contactless respiration rate monitoring, which will provide a fuller view of the patient’s
physiological and mental well-being. Additionally, the system will implement real-time
alert notifications to tell therapists or caregivers of negative emotional states or elevated
stress levels, which will facilitate quicker interventions and improve patient safety. Also,
the development of collaborative gaming allows patients to share gaming experiences with
others, promoting social engagement, motivation, and assistance from others during the
recovery process. Regarding compliance with health data regulations, full adherence to
GDPR, HIPAA, and other relevant privacy regulations will be ensured when the system is
tested with patients. These steps will be incorporated in the future stages of the research as
real-world applications are introduced.
Future research will also focus on providing full-body rehabilitation with accurate
detection of upper and lower limb movements using MediaPipe. Additionally, efforts will
be made to enhance WebGL support, reduce reliance on WebXR polyfills, and improve cam-
era accessibility. Optimizing models to address age-related accuracy gaps and increasing
processing speed will be essential for enhancing system performance.
Supplementary Materials: The following supporting information on model evaluation can be
downloaded at: https://studev5.fernuni-hagen.de:5184/data_processing_Faces.xlsx (accessed on
18 February 2025).
Author Contributions: Conceptualization, H.H.; methodology, H.H.; validation, B.V. and M.H.;
investigation, M.H.; writing—original draft, H.H.; supervision, B.V. and M.H. All authors have read
and agreed to the published version of the manuscript.
Funding: This research received no external funding.
Electronics 2025, 14, 852
19 of 20
Data Availability Statement: The original contributions presented in this study are included in the
article/Supplementary Materials. Further inquiries can be directed to the corresponding authors.
Conflicts of Interest: The authors declare no conflicts of interest.
References
1.
Sarfo, F.S.; Ulasavets, U.; Opare-Sem, O.K.; Ovbiagele, B. Tele-Rehabilitation after Stroke: An Updated Systematic Review of the
Literature. J. Stroke Cerebrovasc. Dis. 2018, 27, 2306–2318. [CrossRef] [PubMed]
2.
Palumbo, A.; Vizza, P.; Calabrese, B.; Ielpo, N. Biopotential signal monitoring systems in rehabilitation: A review. Sensors 2021,
21, 7172. [CrossRef] [PubMed]
3.
Winstein, C.J.; Stein, J.; Arena, R.; Bates, B.; Cherney, L.R.; Cramer, S.C.; Deruyter, F.; Eng, J.J.; Fisher, B.; Harvey, R.L.; et al.
Guidelines for Adult Stroke Rehabilitation and Recovery: A Guideline for Healthcare Professionals from the American Heart
Association/American Stroke Association. Stroke 2016, 47, e98–e169. [CrossRef] [PubMed]
4.
Anderson, K.R.; Woodbury, M.L.; Phillips, K.; Gauthier, L.V. Virtual reality video games to promote movement recovery in stroke
rehabilitation: A guide for clinicians. Arch. Phys. Med. Rehabil. 2015, 96, 973–976. [CrossRef]
5.
Engel, F.; Bond, R.; Keary, A.; Mulvenna, M.; Walsh, P.; Zheng, H.; Wang, H.; Kowohl, U.; Hemmje, M. Sensecare: Towards an
experimental platform for home-based, visualisation of emotional states of people with dementia. In Lecture Notes in Computer
Science (Including Subseries Lecture Notes in Artificial Intelligence and Lecture Notes in Bioinformatics); Bornschlegl, M.X., Engel, F.C.,
Bond, R., Hemmje, M.L., Eds.; Springer International Publishing: Cham, Switzerland, 2016; pp. 63–74. [CrossRef]
6.
Frascarelli, F.; Masia, L.; Di Rosa, G.; Cappa, P.; Petrarca, M.; Castelli, E.; Krebs, H.I. The impact of robotic rehabilitation in
children with acquired or congenital movement disorders. Eur. J. Phys. Rehabil. Med. 2009, 45, 135–141.
7.
Aisen, M.L.; Kerkovich, D.; Mast, J.; Mulroy, S.; Wren, T.A.; Kay, R.M.; Rethlefsen, S.A. Cerebral palsy: Clinical care and
neurological rehabilitation. Lancet Neurol. 2011, 10, 844–852. [CrossRef]
8.
Bryant, L.; Brunner, M.; Hemsley, B. A review of virtual reality technologies in the field of communication disability: Implications
for practice and research. Disabil. Rehabil. Assist. Technol. 2020, 15, 365–372. [CrossRef]
9.
Coelho, T.; Marques, C.; Moreira, D.; Soares, M.; Portugal, P.; Marques, A.; Ferreira, A.R.; Martins, S.; Fernandes, L. Promoting
reminiscences with virtual reality headsets: A pilot study with people with dementia. Int. J. Environ. Res. Public Health 2020,
17, 9301. [CrossRef]
10.
Abdessalem, H.B.; Ai, Y.; Swamy, K.S.M.; Frasson, C. Virtual Reality Zoo Therapy for Alzheimer’s Disease Using Real-Time
Gesture Recognition. Adv. Exp. Med. Biol. 2021, 1338, 97–105. [CrossRef]
11.
Glover, I. Play As You Learn: Gamification as a Technique for Motivating Learners. In Proceedings of the EdMedia 2013—World
Conference on Educational Media and Technology, Victoria, BC, Canada, 24–28 June 2013; Herrington, J., Couros, A., Irvine, V.,
Eds.; Association for the Advancement of Computing in Education (AACE): Victoria, BC, Canada, 2013; pp. 1999–2008. Available
online: https://www.learntechlib.org/primary/p/112246/ (accessed on 19 February 2025).
12.
Deterding, S.; Dixon, D.; Khaled, R.; Nacke, L. From game design elements to gamefulness: Defining “gamification”. In Proceed-
ings of the 15th International Academic MindTrek Conference: Envisioning Future Media Environments, MindTrek, Tampere,
Finlan, 28–30 September 2011; Volume 2011, pp. 9–15. [CrossRef]
13.
Quaglini, S.; Panzarasa, S.; Alloni, A.; Sacchi, M.; Sinforiani, E.; Bottiroli, S.; Bernini, S. HomeCoRe: Bringing Cognitive
Rehabilitation at Home. Stud. Health Technol. Inform. 2019, 264, 1755–1756. [CrossRef]
14.
Ding, W.L.; Zheng, Y.Z.; Su, Y.P.; Li, X.L. Kinect-based virtual rehabilitation and evaluation system for upper limb disorders:
A case study. J. Back Musculoskelet. Rehabil. 2018, 31, 611–621. [CrossRef] [PubMed]
15.
Hadjar, H.; Mckevitt, P.; Hemmje, M. Home-based Immersive Web Rehabilitation Gaming with Audiovisual Sensors. In ACM
International Conference Proceeding Series, Proceedings of the 33rd European Conference on Cognitive Ergonomics, Kaiserslautern, Germany,
4–7 October 2022; Association for Computing Machinery: New York, NY, USA, 2022; pp. 1–7. [CrossRef]
16.
Hayette, H.; Hemmje, M.; Zineb, H.; Vu, B.; Abdelkrim, M. Applied Gaming-Based Emotion-Driven on Disaster Resilience
Training. In Proceedings of the 2024 1st International Conference on Innovative and Intelligent Information Technologies (IC3IT),
Batna, Algeria, 3–5 December 2024; pp. 1–6. [CrossRef]
17.
Zhang, F.; Bazarevsky, V.; Vakunov, A.; Tkachenka, A.; Sung, G.; Chang, C.L.; Grundmann, M. Mediapipe hands: On-device
real-time hand tracking. arXiv 2020, arXiv:2006.10214.
18.
MediaPipe Solutions Guide|Google AI Edge|Google AI for Developers. Available online: https://ai.google.dev/edge/
mediapipe/solutions/guide (accessed on 9 February 2025).
19.
Islam, M.R.; Rahman, R.; Ahmed, A.; Jany, R. NFS: A hand gesture recognition based game using MediaPipe and pygame. arXiv
2022, arXiv:2204.11119.
20.
Cabanac, M. What is emotion? Behav. Process. 2002, 60, 69–83. [CrossRef]
21.
Mukhopadhyay, S.C. Wearable Sensors for Human Activity Monitoring: A Review. IEEE Sens. J. 2015, 15, 1321–1330. [CrossRef]
Electronics 2025, 14, 852
20 of 20
22.
Levy, C.E.; Geiss, M.; David Omura, D.P.T.; MH, A. Effects of physical therapy delivery via home video telerehabilitation on
functional and health-related quality of life outcomes. J. Rehabil. Res. Dev. 2015, 52, 361. [CrossRef]
23.
Ostrowska, P.M.; ´Sliwi´nski, M.; Studnicki, R.; Hansdorfer-Korzon, R. Telerehabilitation of Post-Stroke Patients as a Therapeutic
Solution in the Era of the COVID-19 Pandemic. Healthcare 2021, 9, 654. [CrossRef]
24.
Silva, T.D.; Silva, P.L.; Valenzuela, E.J.; Dias, E.D.; Simcsik, A.O.; de Carvalho, M.G.; Fontes, A.M.G.G.; Alberissi, C.A.O.; Araújo,
L.V.; Brandão, M.V.C.; et al. Serious game platform as a possibility for home-based telerehabilitation for individuals with Cerebral
Palsy during COVID-19 quarantine--a cross-sectional pilot study. Front. Psychol. 2021, 12, 622678. [CrossRef]
25.
Mayela, D.L.V.-C.E.; Miriam, L.-T.; Isabel, G.-G.A.; Oscar, R.-C.; Alejandra, C.-A. Effectiveness of an online multicomponent
physical exercise intervention on the physical performance of community-dwelling older adults: A randomized controlled trial.
Geriatr. Nurs. 2023, 54, 83–93. [CrossRef]
26.
Kuldavletova, O.; Pasquier, F.; Bigot, L.; Langeard, A.; Gauthier, A.; Quarck, G. Videoconference-Based Adapted Physical Exercise
Training Is a Good and Safe Option for Seniors. Int. J. Environ. Res. Public Health 2021, 18, 9439. [CrossRef]
27.
Choukou, M.-A.; He, E.; Moslenko, K. Feasibility of a Virtual-Reality-Enabled At-Home Telerehabilitation Program for Stroke
Survivors: A Case Study. J. Pers. Med. 2023, 13, 1230. [CrossRef] [PubMed]
28.
Pea, R.D. User Centered System Design: New Perspectives on Human-Computer Interaction. J. Educ. Comput. Res. 1987, 3,
129–134.
29.
Muller, P.A. Modélisation Objet Avec UML; Eyrolles: Paris, France, 1999; Volume 514.
30.
GitHub-Immersive-Web/Webxr: Repository for the WebXR Device API Specification. Available online: https://github.com/
immersive-web/webxr (accessed on 23 February 2022).
31.
WebXR Export|Develop and Export WebXR Experiences Using Unity WebGL. Available online: https://de-panther.github.io/
unity-webxr-export (accessed on 1 February 2024).
32.
Three.js—JavaScript 3D Library. Available online: https://threejs.org/ (accessed on 24 April 2024).
33.
Keary, A. Affective Computing for Emotion Detection Using Vision and Wearable Sensors. Ph.D. Thesis, Cork Institute of
Technology, Cork, Ireland, 2018.
34.
Hadjar, H.; Lange, J.; Vu, B.; Engel, F.; Mayer, G.; Mc Kevitt, P.; Hemmje, M.L. Video-based automated emotional monitoring in
mental health care supported by a generic patient data management system. In Proceedings of the Symposium on Psychology-
Based Technologies, Naples, Italy, 28–29 September 2020.
35.
Chuquimarca, L.; Roca, D.; Torres, W.; Amaya, L.; Orozco, J.; Sánchez, D. Mobile IoT device for BPM monitoring people with
heart problems. In Proceedings of the 2020 International Conference on Electrical, Communication, and Computer Engineering
(ICECCE), Istanbul, Turkey, 12–13 June 2020; pp. 1–5.
36.
Chart.js|Open Source HTML5 Charts for Your Website. Available online: https://www.chartjs.org/ (accessed on 28 August 2021).
37.
Hadjar, H.; Vu, B.; Hemmje, M. TheraSense: Deep Learning for Facial Emotion Analysis in Mental Health Teleconsultation.
Electronics 2025, 14, 422. [CrossRef]
38.
Calingaert, P. System performance evaluation: Survey and appraisal. Commun. ACM 1967, 10, 12–18. [CrossRef]
39.
Lucas, H., Jr. Performance evaluation and monitoring. ACM Comput. Surv. 1971, 3, 79–91. [CrossRef]
40.
Polson, P.G.; Lewis, C.; Rieman, J.; Wharton, C. Cognitive walkthroughs: A method for theory-based evaluation of user interfaces.
Int. J. Man. Mach. Stud. 1992, 36, 741–773. [CrossRef]
41.
FACES. FACES: A Database of Facial Expressions in Young, Middle-Aged, and Older Women and Men (Publicly Available
Datasets). Available online: https://faces.mpdl.mpg.de/imeji/collection/IXTdg721TwZwyZ8e?q=# (accessed on 27 July 2021).
42.
HeyGen.
AI Video Generator.
Available online: https://www.heygen.com/?sid=rewardful&via=dankieft (accessed on
23 November 2024).
Disclaimer/Publisher’s Note: The statements, opinions and data contained in all publications are solely those of the individual
author(s) and contributor(s) and not of MDPI and/or the editor(s). MDPI and/or the editor(s) disclaim responsibility for any injury to
people or property resulting from any ideas, methods, instructions or products referred to in the content.
