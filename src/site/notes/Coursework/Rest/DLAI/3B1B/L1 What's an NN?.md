---
{"dg-publish":true,"permalink":"/coursework/rest/dlai/3-b1-b/l1-what-s-an-nn/","noteIcon":""}
---

---
[But what is a neural network? | Chapter 1, Deep learning - YouTube](https://www.youtube.com/watch?v=aircAruvnKk&list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi)
Next : [[Coursework/Rest/DLAI/3B1B/L2 GD - How NNs Learn\|L2 GD - How NNs Learn]]

---



## What are Neurons? 
A Node that holds a Number between 0 an 1, better thought of as a Function, that takes the outputs of all the Neurons in the previous Layer and spits out a Number between 0 and 1. 

## Layers
- Hidden Layers
- Number of Neurons per Layer

## Why Layers? 
Ideally, for learning Subcomponents (on the last hidden Layer), Sub-Sub-C for the third Last, and so on. 
![Screenshot 2023-11-23 at 15.08.31.png](/img/user/Attachments/Screenshot%202023-11-23%20at%2015.08.31.png)
## Edge Detection Example
Weighted Sum for Edge Detection, higher Weights for the desired Region, Neg or Zero in undesired Region. 
Bias is useful when one wants the (weighted Sum - Bias) Term to be bigger than 0 and not just the weighted Sum. 

![Screenshot 2023-11-23 at 15.26.26.png](/img/user/Attachments/Screenshot%202023-11-23%20at%2015.26.26.png)


## Notation and LA

![Screenshot 2023-11-23 at 15.30.14.png](/img/user/Attachments/Screenshot%202023-11-23%20at%2015.30.14.png)

Apply the Sigmoid Function to each resulting Vector inside, that is, to for each Node in the subsequent Layer. 
