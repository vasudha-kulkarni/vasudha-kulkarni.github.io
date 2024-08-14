---
name: Automated Tracking of Behavioural Synchrony in Cooperating Marmosets
tools: [DeepLabCut, RaspberryPi, CameraCalibrator, Experiments, Writing]
image: /images/projects/proj_marmoset2.jpg
description: Master's thesis project with Prof. Judith Burkart at the University of Zurich.
---

# Automated Tracking of Behavioural Synchrony in Cooperating Marmosets
#### Master's thesis project with Prof. Judith Burkart and Nikhil Phaniraj at the Institute of Evolutionary Anthropology, University of Zurich

[Read the full thesis here](/files/20240514_Behavioural Synchrony_MSThesis_VK.pdf)

<!-- <img src="/images/projects/proj_marmoset5.gif" alt="gif" style="width:500px;height:auto;"> -->

When two people are interacting with each other, they tend to tune in and synchronise with each other at various levels -- heart beat, breathing rate, neural activity, and especially, body posture and facial expression. This temporal coordination of behaviours is known as behavioural synchrony. Several studies have shown that behavioural synchrony leads to better affiliation between individuals, increased social attention and higher cooperation and prosociality in groups. Thus, behavioural synchrony is hypothesized to be the underlying mechanism for creating and maintaining social bonds in humans. 

As humans, what sets us apart from other great apes, is high levels of social cognition, cooperation across spatial and temporal scales, and proactive prosociality. The Cooperative Breeding Hypothesis of human evolution suggests that the evolution of allomaternal care (alll individuals in the group help takce care of the infants) provided the motivation and high social tolerance to acquire species-specific cognitive abilities, such as effective social learning, shared intentionality and cumulative culture. In order to understand the evolutionary mechanisms of human social cognition, we can turn to common marmosets (_Callithrix jacchus_) -- a neotropical primate species, which has independently evolved cooperative breeding and study the cognitive effects of this convergent evolution.

<img src="/images/projects/proj_marmoset1.jpg" alt="image" style="width:400px;height:auto;float:left;margin:0px 20px;">
They are cooperative breeders, wherein individuals who are not the parents help care for the infants. Like humans, marmosets exhibit proactive prosociality and group-level coordination. They live in groups of 6-15 individuals, usually composed of only one socially dominant breeding pair. Other individuals in the group help care for the infants by carrying them, provisioning them, exhibiting anti-predator vigilance, and territorial defence. They are highly cooperative within groups and regularly groom each other, share information about the location of food and feed in proximity to each other.

Marmosets in the group coordinate and cooperate closely to care for the infants. They show a group-level similarity in personality and tend to be in tune with the group at communicative, hormonal and behavioural levels. Closely bonded individuals show synchronised fluctuation of oxytocin, and breeding pairs with strong oxytocin synchronisation tend to care better for their infants. In marmoset dyads, individuals also take turns being vigilant while the other one is feeding, and they calibrate their vigilance to their partner’s risk level. These observations in marmosets, along with their high social tolerance and social monitoring, indicate that synchronisation and tuning-in could be the underlying mechanisms for cooperation that differentiate the social abilities of marmosets from independently breeding sister taxa. 

### **Behavioural Experiments**

In order to study behavioural synchrony in marmosets, we designed an experiment with different task conditions and a 2-minute period before and after the task where the marmoset dyad could interact freely. The Prosocial task involved pulling the prosocial sliding board such that when one individual pulls the board, the other individual gets food reward. Individuals in the dyad would take turns pulling for each other. In contrast, the other task involved pulling an individual sliding board such that they would get the food reward themselves. These experiments were conducted in the experiment room on alternate days, depending on the motivation of the dyads to participate. Each experimental session lasted about 7-10 minutes and was repeated 3 times each per dyad, aside from habituation sessions and other control tasks.

Prosocial Sliding Board                   |  Individual Sliding Board                 |
:----------------------------------------:|:----------------------------------------: |
![](/images/projects/proj_marmoset2.gif)  |  ![](/images/projects/proj_marmoset1.gif) |

The idea was to quantiify baseline behavioural synchrony before the session and after the session and correlate the difference in synchrony with the level of prosociality across sessions. We predicted that marmoset dyads would show increased behavioural synchrony after successful prosocial sessions as compared to the individual sessions, because the task requires them to coordinate and tune in with each other. 

The marmoset dyads in my study were not highly prosocial towards their partner in the experiment room. We also know from previous and ongoing studies that marmosets exhibit intentional prosociality and willingly provide food for the rest of the group members in a task termed as group service. This could be due to one or many of several reasons. One reason could be the group size and group composition. Three out of six dyads in our study live in dyadic groups, without infants or helpers, which decreases the drive to coordinate with the other individual. Second, the experimental room is an alien environment for marmosets, even after habituation, as compared to their home enclosure, which increases their arousal, and they are unwilling to participate in the task unless they get some food reward. 

### **Automated Tracking**

A significant challenge in studying pose synchrony and imitation in non-human primates is a lack of an objective, consensus method to identify and classify them. Manually marking the pose of marmosets, frame by frame, would be too time-consuming and fallible. Thus, it is vital to use an automated pose-tracking software to objectively study pose synchrony. In order to get 3D postures of marmosets, we recorded the experimental session from 4 RaspberryPi cameras, focusing on the task from different angles.

<img src="/images/projects/proj_marmoset3.gif" alt="gif" style="width:400px;height:auto;">

DeepLabCut (DLC) is an open-source, markerless pose estimation algorithm based on transfer learning and convolutional neural networks that detect the geometric configuration of body parts, thus automating tracking and pose estimation of animals in laboratory conditions (see the video of rats above). Once the trajectories of the bodyparts have been extracted, in order to get a 3D reconstruction of these movements, we need to calibrate the cameras to estimate certain parameters that allow us to take the 2D coordinates to 3D coordinates. The camera calibration process involves estimating camera parameters using an algorithm to detect checkerboard corners of known dimensions. These parameters are then applied to transform the 2D coordinates from multiple cameras to get a single 3D coordinate.

Once I had set up the cameras, trained DeepLabCut model to track marmosets, and used MATLAB's StereoCameraCalibrator to reconstruct 3D coordinates, I could then analyse the 3D trajectories of the marmosets. Setting up this automated tracking and analysis pipeline was one of the major goals of my thesis. Plotting the 3D-reconstructed trajectories of marmosets pulling the individual sliding board looks like this --

<img src="/images/projects/proj_marmoset5.gif" alt="gif" style="width:650px;height:auto;">

Using these 3D trajectories, I calculated a head vector (from the ears and nose) to estimate the direction of the gaze of marmosets, and analysed the distribution of gaze and the time they spent looking at the task board. In addition to this, I analysed the trajectories of hand and elbow coordinates to check for hand preference, and similarity in task kinematics while pulling the sliding board. That is, did the two individuals in a dyad show similar patterns of pulling the board, as compared to individuals from other dyads?

### **Results and more**

Given the time constraints of my thesis, I analysed the data from when marmoset dyads were doing the prosocial and individual task. Here are some quick results from my analysis -- 

* Marmosets show distinct gaze patterns across task conditions - during the prosocial task, they look at the other individual more often than in the individual task. This is likely because they are following the food reward. 
* Marmosets are unsuccessful at the prosocial task when they are distracted and don't spend enough time at the task.
* Individuals don't show any hand preference while executing the task.
* Dynamic time warping analysis of the hand trajectories shows that individuals exhibit more consistent task kinematics as compared to dyads

These are just some early results from my thesis. Now that all the experiments have been conducted and the analysis pipeline has been established, the rest of the videos has to be analysed to study gaze patterns and movement synchrony in freely interacting marmoset dyads.

### **Acknowledgements**

It has been an honour and a privilege to work on this project with incredible scientists and marmosets for my master’s thesis that is presented before you. This work wouldn’t have been possible without Prof. Judith Burkart, for whom I am grateful for this incredible opportunity, her guidance and invaluable support throughout the year, and for always being as excited about the project as I was. I am very grateful to Nikhil Phaniraj for sharing his expertise and elevating this project, his comments on the thesis, and his patience and encouraging feedback as I navigated a steep learning curve. I would like to express my gratitude to all the Evolutionary Cognition Group members for the engaging discussions and support during my project – especially the caretakers, Hidir Sengül and Dominique Ziegler for their assistance during the experiments, Dr. Rahel Brügger and Konatsu Ono for advice on working with the marmosets, and Dr. Paola Cerrito and Adele Tuozzi for being the most supportive officemates they are. I would also like to thank Dr. Raghav Rajan for his comments; and Divyansh Gupta and Amogh Rakesh for the discussions that helped me implement some code much faster than I could have by myself. The funding I received from the A.H. Schultz Foundation allowed me to carry out this work in Zürich, for which I’m deeply grateful.

### **Further reading**

* Brügger, RK, Willems, EP, and Burkart, JM (2022). Looking out for each other: coordination and turn taking in common marmoset vigilance. Anim Behav. 
* Burkart, JM, Hrdy, SB, and Van Schaik, CP (2009). Cooperative breeding and human cognitive evolution. Evol Anthropol Issues News Rev 18, 175–186.
* Burkart, JM, Adriaense, JEC, Brügger, RK, Miss, FM, Wierucka, K, and van Schaik, CP (2022). A convergent interaction engine: vocal communication among marmoset monkeys. Philos Trans R Soc B Biol Sci 377, 20210098.
* Burkart, JM, and van Schaik, CP (2020). Marmoset prosociality is intentional. Anim Cogn 23, 581–594.
* Duranton,C,andGaunet,F(2016).Behavioural synchronization from an ethological perspective : Overview of its adaptive value. Adapt Behav 24, 181–191.
* Feldman, R (2012). Bio-behavioral Synchrony: A Model for Integrating Biological and Microsocial Behavioral Processes in the Study of Parenting. Parenting 12, 154–164.
* Herrmann, E, Hernández-Lloreda, MV, Call, J, Hare, B, and Tomasello, M (2010). The Structure of Individual Differences in the Cognitive Abilities of Children and Chimpanzees. Psychol Sci 21, 102–110.
* Lauer, J, Zhou, M, Ye, S, Menegas, W, Schneider, S, Nath, T, Rahman, MM, Di Santo, V, Soberanes, D, Feng, G, et al. (2022). Multi-animal pose estimation, identification and tracking with DeepLabCut. Nat Methods 19, 496–504.
* Mathis, A, Mamidanna, P, Cury, KM, Abe, T, Murthy, VN, Mathis, MW, and Bethge, M (2018). DeepLabCut: markerless pose estimation of user-defined body parts with deep learning. Nat Neurosci 21, 1281–1289.
* Mogan, R, Fischer, R, and Bulbulia, JA (2017). To be in synchrony or not? A meta-analysis of synchrony’s effects on behavior, perception, cognition and affect. J Exp Soc Psychol 72, 13–20.
* Palumbo, RV, Marraccini, ME, Weyandt, LL, Wilder-Smith, O, McGee, HA, Liu, S, and Goodwin, MS (2017). Interpersonal Autonomic Physiology: A Systematic Review of the Literature. Personal Soc Psychol Rev 21, 99–141.
* Sheshadri, S, Dann, B, Hueser, T, and Scherberger, H (2020). 3D reconstruction toolbox for behavior tracked with multiple cameras. J Open Source Softw 5, 1849.
* Tomasello, M, Carpenter, M, Call, J, Behne, T, and Moll, H (2005). Understanding and sharing intentions: The origins of cultural cognition. Behav Brain Sci 28, 675–691.
* Voelkl, B, and Huber, L (2007). Imitation as Faithful Copying of a Novel Technique in Marmoset Monkeys. PLOS ONE 2, e611.

