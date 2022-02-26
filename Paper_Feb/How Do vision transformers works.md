# How Do vision transformers works?
First read on: Feb 16, 2022

## State at the front
This paper show the reasons behind the success of multi-head self-attentions(MSAs) for computer vision. 
**It gives me so many intuition on how model structure can affect on (robostness and generalization, and even training ability) performance. Good Reading!**

Here is the [home page](https://arxiv.org/abs/2202.06709) for this paper, and you can find the corresponding [official github repository](https://github.com/xxxnell/how-do-vits-work) here. To make it run-able on my own Colab platform, the modified version by myself is upload to [here](https://github.com/ice-bear-git/ML-paperReading/tree/main/CodeBase/how-do-vits-work-transformer). **There are so many horizontal comparison between different model scheme, which provid a neat definition for {AlexNet, (Preact) VGG, (Preact) ResNet, ResNeXt, WideResNet, SEResNet ,ViT, PiT, Mixer}. Make sure you play with them! And Transform them on your new porject.**


## QUESTION!!!!:
* What is the meaning of data specificty? 
	- First explanation: "specificity" is on the opposite of (the norm of) "agnostic"?
	- Second explanation: "specificity" is on the opposite of "sensitivity"?
		+ where: specificity means "True negative", while "sensitivity" means "True positive". 
		+ Intuition: MSAs put more penalty on False Positive, which is similar to the idea behind adversarial leanring.


## Main Idea -- Overall Feeling
This section will help you develop an overall feeling about MSA
### MSA itself
MSAs are a transformation of all feature map points with large-sized and data-specific kernels. **Will spend more time to inspecting code and generate the view of how they implementing or inserting MSAs block.**

* MSAs can flatten the loss landscapes.
* MSAs are low-pass filter while Convs are high-pass filters. They are complementary.
* MSAs at the end of a stage play a key role in prediction.

#### Low-pass filter
MSAs are intrinsically shape-bias model, and view low-frequency signal as more informative. Hence, it performs robustness on high-frequency noise for sure.

#### Flatten Loss Landscapes
* We measure the flatteness or convexness by Hessian eignenvalues which represents features of loss landscapes.
Hessian Eigenvalues: The change in the gradient of a loss function as we step an infinitesimal distance in a given direction.

## Contribution
We address the three key questions
### 1. What properties of MSAs Do we need to improve optimization?
Spatial smoothing
#### Inductive Bias
An appropriate inductive bias can imporve the performance by being generalized spatial smoothing
>What is inductive bias?  
>To perform prediction on unseen problem, it's necessary to give some assumption which about the nature of target function. Those assumptions are subsumed in the phrase "inductive bias".
* Local MSAs which calculate self-attention only within small windows, achieve better performance than global MSAs.
* **The Stronger the inductive biases, the stronger the representations (not regularizations)**  When # of assumption increase, efficiency on certain target goes up, and ability of transform learning decrease. Hence, proper inductive biases can help ViT do not overfit on small traning dataset.

#### Compare to ViT and figure out the most important feature -- Flatten loss by Suppressing large negative Hessian eigenvalues
* ViT does not overfit small traning datasets
* ViT's non-convex losses lead to poor performance:   
  ViT has more negative Hessian eigenvalues while ResNet only have few.
* Loss landscape smoothing methods aids in ViT training: Using global average pooling (GAP) to suppresses negative Hessian max eigenvalues as it convexify the loss. It would be the motivation or coonnection behind MSA and GAP classifier.
* MSAs flatten the loss and help NNs learn better representations by suppressing large Hessian eigenvalues.
* Or in large data regimes, the negative Hessian eigenvalues -- the disadvantage of MSAs -- disappers, and only their advantages remian.
* Local MSAs learn stronger representations than global MSA as locality inductive bias suppresses the negative Hessian eigenvalues further -- local MSAs have convex losses.



### 2. Do MSA act like Convs?
MSA are low-pass filters, but Convs are high-pass filter. That's the reason why Convs are vulnerable to high-frequency noise while MSA not. Therefore they are complementary.


#### Convs on early stage while MSAs on later position
The MSAs in the early stages performs like Convs, while show their strength in later part. This could serve as an evidence for a hybrid model that uses Convs in early stages and MSAs in late stages.

#### MSAs aggregate feature maps, but Convs do not
Msas ensemble feature maps and reduce the variance of feature map points, while Convs increase the variance for doing nothing.
* **Variance accumulates in every NN layer and tends to increase -->  the feature map variance in ResNet peasks at the end of each stage. Hence, insert MSAs also at the latter part.**
* MSAs are shape-biased, whereas COnvs are texture-biased.

### 3.How can we harmonize MSAs with Convs?
Applying spatial smoothing at the end of stage improves accuracy by ensembling transformed feature map outputs from each stage. The different repeating patterns have different functionality/features  
![different repeating pattern](https://github.com/ice-bear-git/ML-paperReading/blob/main/Visualization/MSAs-Figure3.png)  

This paper establish a rule to build a MSA-Convs NN, and succesfully mainly leverages the advatages of MSAs + Convs  
![Rule for Alter-NN](https://github.com/ice-bear-git/ML-paperReading/blob/main/Visualization/MSAs-AlterNN-1.png)
![Architecture for Alter-NN](https://github.com/ice-bear-git/ML-paperReading/blob/main/Visualization/MSAs-AlterNN-2.png)
This AlterNet has a strong potential for future improvements. In addition, AlterNet can conveniently replace the back bone for other vision tasks such as dense prediction.
![few simple test on AlterNet](https://github.com/ice-bear-git/ML-paperReading/blob/main/Visualization/MSAs-AlterNN-3.png)


## BackGround -- Reading Notes
This paper contains so many techinique expression and specific "common ground" in Image task performance. All of the useful links will be cited here with a brief description. Always step back and equipped yourself with sufficient knowledge.


* What is agnostic in ML? refer to this [Blog](https://analyticsindiamag.com/understanding-agnostic-approach-in-machine-learning/)    
In general, **"agnostic" is on the opposite of "specified"**, and interoperable across the scenarios (as there are no prejudices towards different cases/setups).
	- **Convs** are **data-agnostic** (same filter can serve images with different input size), and **channel-specific** (only recive RGB 3-channel input)
	- **MSAs** are **data-specific** (only accept data with certain deminsion), and **channel-agnostic** (fluctuating on the depth dimension).

* LINK TO THIS PAPER ON [ImageNet-trained CNNs are biased towards texture; increasing shape bias improves accuracy and robustness](https://arxiv.org/abs/1811.12231), WHILE MSAs IS SHAPE BIASED!!

* ViT model represents [Vision Transformers in Image Recognition](https://viso.ai/deep-learning/vision-transformer-vit/)


