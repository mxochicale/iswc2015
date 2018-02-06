

ABSTRACT 
This paper presents a description of the use of time-delay embedding, using Taken's Theorem, to analyse data from Inertial Measurement Units mounted on people performing Salsa dance steps.  The aim of the work is to understand how dexterity can be described in terms of the consistency and variability of human activity.  To this end, approaches which rely on the definition of discrete events or states might not capture dexterity in the same manner. The paper shows the application of the approach to expert, intermediate and novice dancers, and how these different dancers can be distinguished from the patterns of data the approach produces.  The paper concludes with a discussion of the potential uses of time-delay embedding for Human Activity Recognition using data from wearable sensors.


INTRODUCTION 

The use of data from wearable sensors to identify human activity is a staple of wearable computer research Bulling et al. [7]. A core challenge arises from the need to partition these data into segments which can be used to label repetitions of discrete events which correlate with specific actions. Such an approach draws on signal processing techniques and can, through stochastic processes, be used to recognise sequences of events. As Hammerla et al. [16] note “[t]herefore information about what subjects are doing is readily available, rendering activity segmentation a straight-forward follow up task”.  

In previous work, we have shown that it is possible to distinguish between skill levels for jewellery students performing simple tasks, using sensors embedded in their tools [4].  This study used Principal Components Analysis of the data from accelerometers and strain gauges to define clusters of variables that formed classes which could be used to distinguish between novice, intermediate and expert performance.  In their study of the dynamics of tennis serves,  Ahmadi et al. [1], show that use of marker-based motion-capture or inertial measurement units (accelerometer and gyroscope) on the person, can be equally effective in identifying the level of skill shown by people making serves in tennis.  They showed that skill level corresponds to peak values in velocity for shoulder rotation, wrist flexion and upper arm internal rotation prior to a tennis serve. These studies suggest that the objective classification of skill can be made from data acquired from on-body sensors. Such an approach accords well with the view of expertise as the definition of a motor schema (see below). However, dexterity can also be explained as the optimal control of specific parameters and, for this perspective, recognition of sequences of events might not be sufficient.   An alternative is to apply time-series techniques to such data.

The focus of this paper is on the use of a specific time-series technique to explore a specific aspect of dextrous performance. However, the approach can be easily applied to other data and domains. Before explaining the approach, the paper begins with a short discussion of dexterity in human performance. 




DEXTERITY IN HUMAN PERFORMANCE AND HUMAN ACTIVITY RECOGNITION 

Studies of skilled psychomotor performance indicate that expertise is not simply a matter of performing actions in a more consistent manner than novices [17]. Often the expert is able to produce different but contextually appropriate actions in a manner that the novice is unable to perform. This highlights a paradox in human motor control: in order to act consistently, people need to produce stable patterns of movement which can be repeated efficiently, but these movements also need to exhibit sufficient variability to cope with changes in contextual demand. Biomechanics research explains this control of movement in two broad approaches: a common approach is to assume that movement is specified in a hierarchy of commands, with a high-level description of a movement goal defined in terms of location of end-point for a movement, from which is possible to calculate optimal paths for movement. For these approaches, consistency is explained through the definition of “motor schema” which specify the neural commands required to enervate the musculoskeletal system to perform a specific action. In such a system, variability in movement arises from noise and interference in the translation of motor command to the performance of the movement. This means that variability is seen as something which needs to be either ignored or dismissed. For Human Activity Recognition, the motor schema view could lead to the assumption that it is beneficial to either filter out such noise or to define averaged patterns which capture the underlying consistency in movement and recognise activity against these patterns. 

An alternative approach sees variability in human movement as defined by the originating system. Yamamoto and Gohara [28] define dexterity as “... the capacity of goal-directed movement to adapt itself to changes in the external environment..."  An action involves the coordination of muscles and joints in an efficient manner and this raises the ”degrees of freedom“, or ”motor equivalence“, problem [6]. The motor equivalence problem notes that each joint in the human body has several degrees of freedom in the postural angles that it can adopt, and that combining several joint angles in a given movement can result in a great many alternative postures, particularly when actions are performed dynamically. While people might appear to be making consistent motions in repetitive actions, there is sufficient variability to make it difficult to define a single solution to the motor equivalence problem. The challenge here is to reconstruct the originating system in such a way as to allow us to predict the parameters which are being optimised in the performance of the movement. From this perspective, dexterity, or expert performance, could arise from the use of specific parameters in the control of movement and the assumption is that experts seek to optimise different parameters to novices. 

Previous work on the application of dynamical systems approaches to the study of human activity sought to reconcile Bernsteins [6] 'degrees of freedom' problem with the mathematics of dynamical systems [18]. An influential early research paradigm was devleoped by Haken, Kelso and Bunz [15] In this work, participants performed a very simple task (alternate tapping of index fingers in time to a metronome) and it was demonstrated that, once the speed exceeds a certain threshold, the two fingers stop moving out of phase and move in phase. This shift is abrupt and indicates a change in attractor state of a dynamical system which is seeking to optimise specific order parameters [4,5]. Viewing human motor control in terms of dynamical systems allows researchers to consider how dexterity capitalises on the inherent ”noisiness“ of the human movement system. This approach has been particularly fruitful in the field of skill in sports [11] and we believe that it offers an interesting perspective for activity recognition. Applying this assumption to Human Activity Recognition, the goal would be to identify the parameters that are being optimised in a data stream that is produced when activity is performed, rather than in identifying discrete events within that data stream. 



RECOGNISING DEXTERITY IN DANCE 

As Miura et al. [20] point out ”...how the human motor system produces dance movements in still poorly understood.“ A key issue concerns the manner in which experienced dancers solve the degrees of freedom problem in the face of changing contextual demands. Miura et al. [21] measured muscle activation using electromyography (EMG) collected from muscles in the lower limb, for a task requiring participants to bounce up and down in time to a metronome beat. They demonstrated that experienced dancers show much better precision in synchronizing movements to beat than non-dancers, i.e., dancers maintained much lower standard deviation in temporal deviation against the beat than non-dancers. This result is consistent with work which shows that, compared with inexperienced-or non-dancers, trained ballet dancers exhibit superior postural stability [10] , and show superior ability in position matching of upper limbs [24]. 

Capturing dance activity through sensors has tended to rely 
on motion capture [2] or sensors mounted on the person [19] 
or in their shoes [22] or from their smartphones [27]. Much 
of this work has been concerned with using the dancers motion 
to work with multimedia presentations that augment and 
complement the dance [14, 23] or as interfacing to a game [9] or commercial games, such as Dance Dance Revolution.  While the range of sensing technology used in these papers is  diverse and the result of the activity recognition is varied, it is fair to say that few of the papers have considered variation in how well dance is performed. In their work, Aristidou et al. [3] have considered the manner in which dance steps conform to a set of defined templates that describe steps in terms of three-dimensional rotation (described using quaternions). The implication is that a goodness-of-fit can be ascertained to determine how well a dancer performs a step, and how any  deviation from good can be modified through practice. 

For this paper, we are interested in the question of how time-
series techniques can provide insight into the dexterity of 
dancers. To this end, we consider the performance of a set of 
steps from Salsa dance and compare untrained, inexperienced or non-dancers in one cohort with experienced dancers in another. Before explaining how data were collected, the next section outlines the approach to time-series analysis, phase space representation used in this paper.  It should be noted that dynamical systems research offers a range of techniques for the study of human activity (see [13] for an overview of alternative techniques). However, this paper focuses on a specific technique which utilises Taken's Theorem.

PHASE SPACE REPRESENTATION 

In this work we follow the notation employed in [26]. The purpose of the Takens’s Theorem, also known as time-delay embedding theorem, is to reconstruct a D..dimensional manifold M s(t) of an unknown dynamical system from time series x(t) of that system.  Thus, we assume that the single that we are observing has been produced by some time-varying system (rather than been generated entirely at random).  The assumption that the source of the signal exhibits systematic variation then leads to the further assumption that this signal should, over some time period, exhibit a repeated pattern or a meta-stability.  What we do not know is what this time period might be or what this pattern might look like.  Thus, time-delay embedding assumes that the time series is a sequence x(t)= h(s(t)), where h : M . RD is a measurement function on the unknown dynamical system, being x(t) observable. The time delay reconstruction in m dimensions with time delay t  is defined as: x(t)=(x(t);x(t -), :::, x(t-(m - 1))) which defines a map F : M . Rm such that x(t)= (s). . :is a further transformation that is considered as a more general transformation in which for the current work we are applying the Principal Component Analyis PCA  algorithm (Figure 1).   [NOTE: This last sentence is confusing and doesn't really explain why there is a need for PCA or why, if you do apply PCA, you need Taken's Theorem. This is the question that Neil has been asking: why not simply apply PCA to the 'raw' data and produce profiles].

Determining the minimum embedding dimension 

In Human Activity analysis, Takens’s Theorem has been used extensevely in gait recognition and walking, running and cycling activities.  However, some problems remain to be solved: the most pressing of which is how best to determine the values for m and tau. Sama et al. [25] state that the minimal embedding parameters are largely dependent on the application at hand, and estimated the minimal embedded dimension with False Nearest Neighbours (FNN) method. However, Cao [8] pointed out that the FNN algorithm can be subjected to different threshold parameters Rtol and Atol which lead to different results and the FNN method cannot differenciate random series.  On the other hand, Frank et al. [12] used a grid search to find the embedded parameters, but their paper does not provide detail about their approach. Nevertheless, there is still research to be done to find the minimal embedded parameters (m 
and ). 

Cao’s method for computing the minimal embedding dimmension is based on the mean values (E1(d), E2(d)) of a modified version of the FNN method, both values are only dependant on m 
and t [8]. E1(d) is used to obtain the minimal dimension and it stops changing when d comes from an attractor [NOTE: this is not clear - what does the word 'attractor' mean here?]. On the other hand E2(d) is used to distinguish deterministic signals from stochastic signals in which case the E2(d) values will be approximately equal to 1 for any d. 

DATA COLLECTION 

Data from 3-axis accelerometer, gyroscope and magnetometer were collected at a sampling rate of 50 Hz using four Razor 9DOF Inertial Measurement Units (IMUs) with Bluetooth (Adeunis 
ARF7044). The IMUs were attached to custom-made bracelets worn by participants: two sensors were located in the front part of the right and left ankle, one in the back of the hip and another in back of the neck. 

Participants
Thirteen participants with different years of experience 
in dancing salsa were invited, one (male) expert dancer (14 years of experience), one intermediary (male) dancer (4 years of experience)and eleven non-dancers. The non-dancers were students of engineering (mean age 22 years; 4 female and 7 male).  While 2 of these dancers (1 male and 1 female) had danced previously, none of this group had experience in Salsa dancing.  

Experimental Conditions
The design of the experiment met the University of XXX ethics approval and all participants provided informed consent prior to participation.

On arrival, participants were assisted in attaching the IMUs and the manner in which data were collected from these IMUs was demonstrated to them.  Once they were comforable with the fit of IMUs, the experimental task was explained to them.  

Each participant was shown a series of video clips (recorded by the expert dancer) demonstrating Salsa steps.  Each video clip showed one step repeated several times for 20 seconds.  For the analysis in this paper, we report two Salsa step patterns (step 1 = mambo and step 2 = side crossover).  Participants watched the video clip and were then asked to copy the steps in time to music.  The video was played during the data collection (so that participants did not have to rely on their memory of the steps).

Data were collected from the IMUs and recorded.  For this paper, the analysis reported will focus on data taken from the sensor mounted on the left ankle. 

DATA ANALYSIS 

Data from the inertial sensor for left ankle of the expert 
dancer were used to compute the E1(d) and E2(d) 
values. From E1(d) values (Figures 2, 3 and 4) one can notice that the minimal value for the embedded dimmension is approximately equal to 10.  We define the minimal value as the point on the graph where the line appears to asymptote (or, at least, where the increase becomes very slight). It is important to note that neither the axis of the intertial sensor nor the time-delay values are a factor for having different embedded dimension parameters. On the other hand, from E2(d) values (Figures 5, 6 and 7) one can appreciate that the accelerometer data appear more random since their values are closer to 1 which is also the case for the x-axis in the gyroscope and magnetometer sensor. Fortunately, y and z axis in the gyroscope and magnetometer provide more deterministic data. We therefore choose the magnetometer data with z-axis for step 1 and y-axis for step 2. Takens’ Theorem is applied with m = 10 and t =1 and then the first two components of the PCA were used to plot a 2-D reconstructed state space.   We also illustrate the problem of the minimal embedded parameters by presenting different reconstructed state spaces in Figure 9. 

RESULTS

Figure 8 illustrates the 2-D reconstructed state space for the 
non-dancer, intermediate and expert dancers which visually 
help us to distinguish different levels of skills.  It is immediately noticeable that the shape of the state space for each level (novice, intermediate, expert) appear visually similar across step 1.  As the participants are meant to be performing the same action, this similarity is to be expected.  However, the state spaces also show a tighter and less varied pattern for the expert than for the other skill levels.  This suggests that the expert is producing more repeatable, more consistent actions than the other skill levels.  While this is to be expected, the reconstructed state spaces provide interesting illustrations of this phenomenon.  For step 2, on the other hand, (which was a more complicated sequence of movements), one can see a marked contrast across skill levels.  Again, the expert is showing a consistent and repeatable action.  The intermediate participant is showing a consistent action but this is different to that of the expert, and the novice is showing a pattern which appears disjointed and noisy.  Indeed, for the novice dancer, the state space reconstruction of step 2 seems to have more in common with their state space for step 1 than it does with the other dancers performing step 2.  


DISCUSSION

Although Takens’ Theorem is still subject to the embedded parameters, the phase space representation applies a model of consistency to the data for skill assessment. The control of variability then becomes desirable because expert dancers are better able to moderate their actions in response to contextual demands in way that produces a state space reconstruction that appears consistent.  The novice dancer, on the other hand, appears to been producing similar patterns of movement for both steps rather than attempting to fully engage with the requirements of step 2.  

While the results provide some indication of difference between levels of skill, the interpretation of the state space reconstructions remains qualitative.  While this is not unusual in the literature which applies time-delay embedding to the analysis of human activity, further work is required to develop reliable and robust techniques to analyse these reconstructions.  A promising line of enquiry would be to investigate the geometry of the state space reconstructions which could be used to support comparison [25] and also could aid in the computation of the minimal embedded parameters. 
 
The results in this paper are only from a single axis of a single sensor.  One can see from the E2(d) values that there accelerometer data is more noisy than that from the gyroscope and magnetometer.  While this is most likely due to effects of gravity on the accelerometer (although the ADXL345 accelerometer used in the Razor offers simple gravity compensation), there interference with the signal can be further filtered and compensated.  It would be interesting to determine how combinations of sensor data can be used to create similar state space reconstructions and this will be explored in the next phase of work. 



ACKNOWLEDGMENTS 

The work reported in this paper is partly supported by a studentship from ConaCyt, Mexico. 

REFERENCES 

1. Ahmadi, A., Rowlands, D., and James, D. A. (2010)Towards a 
wearable device for skill assessment and skill 
acquisition of a tennis player during the first serve, 
Sports Technology, 2, 3-4, 129–136. 
2. Alexiadis, D. S., and Daras, P. (2014)Quaternionic signal 
processing techniques for automatic evaluation of dance 
performances from MoCap data, IEEE Transactions on 
Multimedia, 16, 5, 1391–1406. 
3. Aristidou, A., Stavrakis, E., and Chrysanthou, Y. (2014) Motion Analysis for Folk Dance Evaluation, EUROGRAPHICS Workshop on Graphics and Culture Heritage 
4. XXXXX
5. Beek, P., Peper, C., and Stegeman, D. (1995) Dynamical 
models of movement coordination, Human Movement 
Science, 14, 4-5, 573–608. 
6. Bernstein, N. A. (1967)The Coordination and Regulation of 
Movements. Oxford, New York, Pergamon Press. 
7. Bulling, A., Blanke, U., and Schiele, B.(2014) A tutorial on 
human activity recognition using body-worn inertial 
sensors, ACM Computing Surveys (CSUR) 46, 3, 1–33. 
8. Cao, L. (1997) Practical method for determining the minimum 
embedding dimension of a scalar time series. Physica D: 
Nonlinear Phenomena, 110 , 43–50. 
9. Chu, N. N. Y., Yang, C. M., and Wu, C. C. (2012) Game interface using digital textile sensors, accelerometer and gyroscope, IEEE Transactions on Consumer Electronics, 8, 2 , 184–189. 
10. Crotts, D., Thompson, B., Nahom, M., Ryan, S., and 
Newton, R. A. (1996) Balance abilities of professional dancers 
on select balance tests, The Journal of orthopaedic and 
sports physical therapy, 23, 1 , 12–17. 
11. Davids, K., Glazier, P., Araujo, D., and Bartlett, R. (2003)
Movement systems as dynamical systems: the functional 
roles of variability and its implications for sports 
medicine, Sports Medicine, 33, 4 , 245–260. 
12. Frank, J., Mannor, S., and Precup, D. (2010) Activity and Gait Recognition with Time-Delay Embeddings Time-Delay 
Embeddings, AAAI Conference on Artificial Intelligence, 407–408. 
13. Guastello, S. J. and Gregson, R.A.M. (2011) Nonlinear Dynamical Systems Analyis for the Behavioral Sciences using Real Data.. Boca Raton, FL:   CRC Press. 
14. Griffith, N., and Fernstr¨om, M. (1998) LiteFoot: A floor space for recording dance and controlling media. Proceedings 
of the 1998 International Computer Music Conference , 475–481. 
15. Haken, H., Kelso, J.A.S. and Bunz, H. (1985) A theoretical model of phase transitions in human hand movements, Biological Cybernetics, 51, 347–356.
16. Hammerla, N., Ploetz, T., Andras, P., and Olivier, P. (2011)
Assessing Motor Performance with PCA, Proc. Int. Workshop on Frontiers in Activity Recognition using Pervasive Sensing, 18–23. 
17. Kelso, J. S. (2014). Human motor behavior: An introduction. Psychology Press.
18. Kugler, P.N.,  Kelso, J.A.S. and Turvey, M.T. (1982) On the control and coordination of naturally developing systems, In J.A.S. Kelso and J.E. Clark (eds) The development of movement control and coordination, Chichester: John Wiley.
19. Lynch, A., Majeed, B., O’Flynn, B., Barton, J., Murphy, 
F., Delaney, K., and O’Mathuna, S. C. (2005) A wireless 
inertial measurement system (WIMS) for an interactive 
dance environment, Journal of Physics: Conference Series, 15 , 95–100. 
20. Miura, A., Fujii, S., Yamamoto, Y., and Kudo, K. (2015) Motor 
Control of Rhythmic Dance from a Dynamical Systems Perspective, Journal of Dance Medicine and Science, 19, 11–21. 
21. Miura, A., Kudo, K., Ohtsuki, T., Kanehisa, H., and Nakazawa, K. (2013)Relationship between muscle cocontraction and proficiency in whole-body sensorimotor synchronization: a comparison study of street dancers and nondancers, Motor control, 17,1, 18–33. 
22. Paradiso, J., and Hu, E. (1997) Expressive footwear for 
computer-augmented dance performance, Digest of Papers of the First International Symposium on Wearable Computers, October , 20–21. 
23. Park, C., Chou, P. H., and Sun, Y. (2006) A wearable wireless 
sensor platform for interactive dance performances, Proceedings -Fourth Annual IEEE International Conference on Pervasive Computing and Communications, PerCom 2006, 52–57. 
24. Ramsay, J. R., and Riddoch, M. J. (2001) Position-matching in 
the upper limb: professional ballet dancers perform with 
outstanding accuracy, Clinical rehabilitation 15,3, 324–330. 
25. Sam`a, A., Ruiz, F. J., Agell, N., P´erez-L´opez, C., Catal`a, A., and Cabestany, J. (2013) Gait identification by means of box approximation geometry of reconstructed attractors in latent space, Neurocomputing, 121, 79–88. 
26. Uzal, L. C., Grinblat, G. L., and Verdes, P. F. (2011) Optimal reconstruction of dynamical systems: A noise amplification approach, Physical Review E -Statistical, Nonlinear, and Soft Matter Physics, 84, 1 (2011). 
27. Wei, Y., Yan, H., Bie, R., Wang, S., and Sun, L. (2014)Performance monitoring and evaluation in dance teaching with mobile sensing technology, Personal and Ubiquitous Computing 18, 8, 1929–1939. 
28. Yamamoto, Y., and Gohara, K. (2000) Continuous hitting movements modeled from the perspective of dynamical systems with temporal input, Human Movement Science, 19, 3, 341–371. 
29. Yap, H. L., Eftekhari, A., Wakin, M. B., and Rozell,  C. J. (2014) A First Analysis of the Stability of Takens Embedding. GlobalSIP2014: Information Processing  for Big Data, 5. 




