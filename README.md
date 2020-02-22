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

Week of X
On a scale of 1-10, how do we rate our progress over the past week?
What did we accomplish from last week's tasks?
What problems or concerns do we have?
What do we plan to accomplish do over the next week?
