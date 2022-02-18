# How Do vision transformers works?
First read on: Feb 16, 2022

## State at the front
This paper show the reasons behind the success of multi-head self-attentions(MSAs) for computer vision. 
**It gives me so many intuition on how model structure can affect on (robostness and generalization, and even training ability) performance. Good Reading!**

Here is the [home page](https://arxiv.org/abs/2202.06709) for this paper, and you can find the corresponding [official github repository](https://github.com/xxxnell/how-do-vits-work) here. To make it run-able on my own Colab platform, the modified version by myself is upload to [here](). **There are so many horizontal comparison between different model scheme, which provid a neat definition for {AlexNet, (Preact) VGG, (Preact) ResNet, ResNeXt, WideResNet, SEResNet ,ViT, PiT, Mixer}. Make sure you play with them! And Transform them on your new porject.**

## Main Contribution

## BackGround
This paper contains so many techinique expression and specific "common ground" in Image task performance. All of the useful links will be cited here with a brief description. Always step back and equipped yourself with sufficient knowledge.


* What is agnostic in ML? refer to this [Blog](https://analyticsindiamag.com/understanding-agnostic-approach-in-machine-learning/)    
In general, **"agnostic" is on the opposite of "specified"**, and interoperable across the scenarios (as there are no prejudices towards different cases/setups).
	- **Convs** are **data-agnostic** (same filter can serve images with different input size), and **channel-specific** (only recive RGB 3-channel input)
	- **MSAs** are **data-specific** (only accept data with certain deminsion), and **channel-agnostic** (fluctuating on the depth dimension).

* LINK TO THIS PAPER ON [ImageNet-trained CNNs are biased towards texture; increasing shape bias improves accuracy and robustness](https://arxiv.org/abs/1811.12231), WHILE MSAs IS SHAPE BIASED!!

* ViT model represents [Vision Transformers in Image Recognition](https://viso.ai/deep-learning/vision-transformer-vit/)

## Reading Notes

