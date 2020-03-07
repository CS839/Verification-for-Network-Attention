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

[![](https://github.com/CS839/Verification-for-Network-Attention/images/1.jpg)](demo for cam "markdown")
### What problems or concerns do we have?
We find the network's attention is wandering everywhere which is totally different with what human-being's attention.
### What do we plan to accomplish do over the next week?
We plan to set up a new mechanism to let neural net be "focus" on the correct attention. 


