---
{"dg-publish":true,"permalink":"/coursework/dlai/3-b1-b/l3-4-backpropagation-and-its-calculus/","noteIcon":""}
---

---
Last : [[Coursework/DLAI/3B1B/L2 GD - How NNs Learn\|L2 GD - How NNs Learn]]

---
Backprop is the Algorithm for determining how a single training Example would like to nudge the Weights and Biases. 

The Stochastic Gradient Descent algorithm requires gradients to be calculated for each variable in the model so that new values for the variables can be calculated.

Back-propagation is an automatic differentiation algorithm that can be used to calculate the gradients for the parameters in neural network

---
## The Chain Rule in Networks

The Network is assumed to be 
![Screenshot 2023-11-26 at 01.17.46.png](/img/user/Attachments/Screenshot%202023-11-26%20at%2001.17.46.png)

 How much does *w*<sup>(L)</sup> affect the Cost Function
![Screenshot 2023-11-26 at 01.08.37.png](/img/user/Attachments/Screenshot%202023-11-26%20at%2001.08.37.png)

---
## Computing relevant Derivatives

![Screenshot 2023-11-26 at 01.11.47.png](/img/user/Attachments/Screenshot%202023-11-26%20at%2001.11.47.png)


---
## What do the Derivatives mean? 



![Screenshot 2023-11-26 at 01.13.14.png](/img/user/Attachments/Screenshot%202023-11-26%20at%2001.13.14.png)
The Above is but one Component of the Gradient Vector, as shown below. 

![Screenshot 2023-11-26 at 01.14.23.png](/img/user/Attachments/Screenshot%202023-11-26%20at%2001.14.23.png)

---
## Sensitivity to Weights/Biases

![Screenshot 2023-11-26 at 01.16.42.png](/img/user/Attachments/Screenshot%202023-11-26%20at%2001.16.42.png)

![Screenshot 2023-11-26 at 01.17.22.png](/img/user/Attachments/Screenshot%202023-11-26%20at%2001.17.22.png)


---
## Layers with additional Neurons

![Screenshot 2023-11-26 at 01.21.30.png](/img/user/Attachments/Screenshot%202023-11-26%20at%2001.21.30.png)![Screenshot 2023-11-26 at 01.21.38.png](/img/user/Attachments/Screenshot%202023-11-26%20at%2001.21.38.png)![Screenshot 2023-11-26 at 01.21.47.png](/img/user/Attachments/Screenshot%202023-11-26%20at%2001.21.47.png)

![Screenshot 2023-11-26 at 01.22.20.png](/img/user/Attachments/Screenshot%202023-11-26%20at%2001.22.20.png)

This one changes : 

![Screenshot 2023-11-26 at 01.22.42.png](/img/user/Attachments/Screenshot%202023-11-26%20at%2001.22.42.png)
