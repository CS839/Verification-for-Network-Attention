# Verification-for-Network-Attention

## Problem and technique description

### What is the problem you're trying to solve?
We are trying to design a training strategy that could alleviate the unfairness 
in neural network. If we are going to train a binary classifier, many unrelated 
elements could easily bias the prediction. If we have two group of images, one 
is monkey and another is dog. The network may treat forest as a key factor to 
discriminate between them, since monkey often lives in forest and dog often in
city.

### What have people done about it and what are the limitations of existing techniques?
There is a paper called "Balanced Datasets Are Not Enough: Estimating and 
Mitigating Gender Bias in Deep Image Representations" trying to mitigate the 
gender bias in classifying job by using explicitly  adversarial loss. This is 
based on the known bias factor "gender". We are trying to design a training 
strategy to mitigate unknown bias.

### What do you propose to do?
We propose to use an attacker network that could generate the mask that could 
fool the discriminator. And the mask's size is limited so that network should
only focus on the "main" component to complete the classification task.

### What are your measures of success?
We have the ground truth bounding box for the objects to be classified. By 
aligning the true box and attention mask, we could measure how close they are.

## Week of 1
### On a scale of 1-10, how do we rate our progress over the past week?
We have to firstly set up a valid task to attack. This task has to expose the existing neural net's disadvantage, which is the misplacement of attention even given the correct prediction. To show the attention, we could use a common visualization tool called CAM("Learning Deep Features for Discriminative Localization").  
### What did we accomplish from last week's tasks?
We set up a dataset called "1234" task. The first group of images contains number 4 and other random number in {1,2,3} while another group does not contain "4". 
### What problems or concerns do we have?
How to set up a "fair" training dataset so that the neural network will not be biased by other information should be carefully considered. 
### What do we plan to accomplish do over the next week?
We plan to set up a traditional neural network to train based on such task and visualize its attention to see if such phenomenone exists.


## Week of 2
### On a scale of 1-10, how do we rate our progress over the past week?
9.5
### What did we accomplish from last week's tasks?
1. We finished the coding for constructing a dataset described in week 1 report. 
2. We set up a resnet18 model to finish the binary classification task.
3. We implement the CAM method to see the attention of the traditional neural network.

Demo for CAM on the resnet18 network.
[![](https://github.com/CS839/Verification-for-Network-Attention/blob/master/images/1.jpg)](https://github.com/CS839/Verification-for-Network-Attention/blob/master/images/1.jpg "demo")
### What problems or concerns do we have?
We find the network's attention is wandering everywhere which is totally different with what human-being's attention.
### What do we plan to accomplish do over the next week?
We plan to set up a new mechanism to let neural net be "focus" on the correct attention. 



## Week of 3
### On a scale of 1-10, how do we rate our progress over the past week?
8.5
### What did we accomplish from last week's tasks?
We proposed a training strategy that is similar to [Balanced Datasets Are Not Enough: Estimating and Mitigating Gender Bias in Deep Image Representations](https://arxiv.org/abs/1811.08489). We set up an "attacker" network that tries to cover the most "important" part of image to fool the "discriminator" network. In this way, we hope that "attacker" network could learn the correct attention of image.
### What problems or concerns do we have?
The adversarial structure could be extremely hard to train. The result is unstable.
### What do we plan to accomplish do over the next week?
Trying to adjust the structure and hyper-parameters to see if any positive change happens. 



## Week of 4
### On a scale of 1-10, how do we rate our progress over the past week?
7.5
### What did we accomplish from last week's tasks?
We finish the training of adversarial architecuture. The strategy is mentioned in the previous week's report. We have the initial result here: 
[![](https://github.com/CS839/Verification-for-Network-Attention/blob/master/images/2.png)](https://github.com/CS839/Verification-for-Network-Attention/blob/master/images/2.png "demo2")

We see that the "attacker" successfully capture the key information in the image. 
### What problems or concerns do we have?
As mentioned in the previous report, such structure is hard to train. So we seek out to propose an alternative structure that could directly capture the key region's information. 
### What do we plan to accomplish do over the next week?
Propose alternative structure to replace the "adversarial" strategy



## Week of 5
### On a scale of 1-10, how do we rate our progress over the past week?
7
### What did we accomplish from last week's tasks?
We propose to come up an alternative structure that could directly capture the key region information. We add an additional attention mechanism on the final feature map in Resnet18. At the same time, we restrict the size of attention by extra L1 loss.
### What problems or concerns do we have?
Still tuning the hyperparameter..
### What do we plan to accomplish do over the next week?
We want to set up the proposed mechanism to see if it works as we expected.



## Week of 6
### On a scale of 1-10, how do we rate our progress over the past week?
7.5
### What did we accomplish from last week's tasks?
We successfully bound the region of network's attention to localize on the correct region without using the heavy adversarial architecture. Instead, we can just easily use an extra attention layer and restrict it with L1 loss. 

### What do we plan to accomplish do over the next week?
We plan to set up the model and test on more general dataset.

