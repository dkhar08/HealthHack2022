# HealthHack2022
My 1st place privater leaderboard solution for Health Data Hack 2022

Competition data represents a set of different events which occurred with the patient. We had information about the patient's medical history, swabs,  different blood tests and etc. Every participant faced a poser: how to generate features for CT from scattered across the timeline events.

I chose the following tactics: most near information was most relevant. I adhered pattern for feature generation: information about the nearest event from a set of events + time to the event. I provided the model information about the 3 nearest events from the most important sets. I found that such kind of tactic worked well enough and exploited it till the end of the competition. Of course, I could extract some meta-features from rnn in order to feel the change over time. But I found that for most of the features, the presence of some tests is more important than their results. And such a strategy is just waste of time.

I found that the values of the C-protein and antibodies(LgG, LgM) in blood tests had the greatest importance. For many other tests and events, the fact that the event occurred has greater importance than the result of it. For example, most of the prescriptions featured antibiotics. People with wheezing in the lungs and not very bad feeling were given a prescription and sent home to be sick. And most of them have first degree of lung damage. So we can perceive issued prescription as a strong hallmark of 1 lung damage degree. 

D-dimer test was conducted only at hospitals. Its presence correlated with more severe Covid cases because only people with high lung damage degree occurred in hospitals.

Based on that I concluded that if I were to build an ML system I would replace most of the features with questionnaires filled out by a doctor during the appointment. As a result, my model would be based on C-protein, LgG, LgM and questionnaires.

Other features that worked for me and improved my leaderboard position:

1) Direct metric optimization with regression
2) Rounding threshold search.

