# The Weekly Meeting
Good online courses: 
* [MIT Deep Learning](http://introtodeeplearning.com)  
The corresponding Codes in download and modified [here](https://github.com/ice-bear-git/ML-paperReading/tree/main/CodeBase/introtodeeplearning-master)   
* [Uwaterloo Intro to ML](https://cs.uwaterloo.ca/~ppoupart/teaching/cs480-spring19/schedule.html)   
Zoom Links: [here](https://zoom.us/j/95071756890)    
* Good Jupyter NoteBook Implementation for [Transformers--preprocessing](https://github.com/huggingface/notebooks)    


## Apr 11
### Recommend a potential undergraduate researcher
Last week, I recommended your course on linear algebra for ML to a CS undergraduate student Shangjun Jia, as well as your lab topics. He is one of my CS course TA and is good at algorithm. Although I know know his performance on foundamental CS concepts -- Like Tree structure and graphs, but he might help us build up pytorch implementaion in a faster/more efficiency way.  
I heard he already got you email back. No matter how, I thought keeping touch with some pure Cs guy might help us to build up the Pitt's local lab team. Hope this commendation is worthy your time.
### Still following the MIT lab
As the lecture covers the RL for a while, I also spend some time on `gym`, which is a new package for instereting trails like `Inverse-Pendulum`. Also, trying to build a MPC loop training (a simple version of PPO in RL -- likes the Adam in ML) for a raceCar model. 
### As approaching the end of semester
I might put more effort on the course project and final preparation.
### Keep touch with PhD RuiXuan Tang
We had another meeting during the weekend mainly about the basic info of his NLP experience. He might be more familiar with the NLP classification task instead of understanding. 


## Apr 4

### NLP
I met with Ruixuan Tang, and it was a good talk. Due to the essay for his graduation, he will be available for the `BERT+NoisyMixup` project around end of July. We will keep in touch on slack for sure.    
To be better equipped with solid understanding on NLP, I asked him for the resource relates to NLP. For now, he shared me the link for his past course: [UVa CS 4501 Machine Learning for NLP](https://yangfengji.net/uva-nlp-course/). Although they do not implement a `BERT` at the end, they go through all of `Linear Regression`, `CNN`, `LSTM` models. As the link includes all the lectures and recordings, I think it???s would be a good starting point for me.

After going through all of the basic model, it would be easy for me to implement a `BERT` then. And maybe it???s the time for `Attention` mechanism as well. As `Attention` is specifically wait for more advanced time-sequential model that beyonds `LSTM`.

### Explore gym on Colab
As same as the idea that combine BERT with NoisyMixup Training, we can try this on many interesting implementation in `gym` (a virtual simulation Env). Some of examples are so inspiring and famous, like `Inverse-Pendulum`.   
As it usually requires the GPU for large training, shifting all the work onto Colab is necessary.
* When it combine with Baseline for parallel acceleration. [Here](https://colab.research.google.com/drive/14ioV27tIw8CigcJLbNTVKtHVRI_LB289?usp=drive_fs).  

### Open Lecture
Keep learning the [MIT Deep Learning](http://introtodeeplearning.com) for Lec3, Lec4;



--------  
## Mar 21

### NLP
A famous source: [its Github](https://github.com/allenai/allennlp)


### MPC
Model-Preductuve Control, here is a [quick demo](https://github.com/mcarfagno/mpc_python)   
I found that's hard to translate pseudo-code 


### The Corresponding Website for [Uwaterloo Intro to ML](https://cs.uwaterloo.ca/~ppoupart/teaching/cs480-spring19/schedule.html)
Que:
1. The Computational Graph is elegant, but it's hard to make sense for me.  

![Figure2](https://github.com/ice-bear-git/ML-paperReading/blob/main/WeeklyMeeting/TF-2.PNG)

2. Is the Fully Connection (like dense Net) character matters? ---- The reason of long range dependency.  
![Figure1](https://github.com/ice-bear-git/ML-paperReading/blob/main/WeeklyMeeting/TF-1.PNG)

![Figure3](https://github.com/ice-bear-git/ML-paperReading/blob/main/WeeklyMeeting/TF-3.PNG)
![Figure4](https://github.com/ice-bear-git/ML-paperReading/blob/main/WeeklyMeeting/TF-4.PNG)

### The MIT's course is released --- just start watching