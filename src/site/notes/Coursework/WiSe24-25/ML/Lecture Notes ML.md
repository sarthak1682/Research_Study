---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/ml/lecture-notes-ml/","noteIcon":""}
---

---
## L1

Bayes' Rule: See the section in: [[Coursework/SoSe24/GenAI/Ch 1 Intro\|Ch 1 Intro]]



> [!PDF|255, 208, 0] [[ML_Slides_W1_W3.pdf#page=60&annotation=1132R|ML_Slides, p.60]]
> Frank Rosenblatt (1928-1971) developed in 1958 the Perceptron learning rule and formulated a convergence proof; Mark I Perceptron
[[Coursework/SoSe24/GenAI/Ch 1 Intro#Bayes' Rule\| ]] 


> [!PDF|255, 208, 0] [[ML_Slides_W1_W3.pdf#page=72&annotation=1118R|ML_Slides, p.72]]
> Implementation as optical computer?

Wat?


## L2 

### The Perceptron


![Attachments/ML_Slides.jpg](/img/user/Attachments/ML_Slides.jpg)

Can be thought of as weighted voting for a class

[[ML_Slides_W1_W3.pdf#page=103&rect=486,423,691,508|ML_Slides, p.103]]![Attachments/ML_Slides 1.jpg](/img/user/Attachments/ML_Slides%201.jpg)



[[ML_Slides_W1_W3.pdf#page=103&rect=486,172,697,224|ML_Slides, p.103]]> [!PDF|255, 208, 0] [[ML_Slides_W1_W3.pdf#page=103&annotation=1135R|ML_Slides, p.103]]
> The linear classification boundary (separating hyperplane) is defined by h(x) = 0

![Attachments/ML_Slides 2.jpg](/img/user/Attachments/ML_Slides%202.jpg)

[[ML_Slides_W1_W3.pdf#page=111&rect=191,286,614,355|ML_Slides, p.111]]

![Screenshot 2025-01-18 at 07.12.27.png](/img/user/Attachments/Screenshot%202025-01-18%20at%2007.12.27.png)
![Screenshot 2025-01-18 at 07.12.55.png](/img/user/Attachments/Screenshot%202025-01-18%20at%2007.12.55.png)

> [!PDF|255, 208, 0] [[ML_Slides_W1_W3.pdf#page=127&annotation=1138R|ML_Slides, p.127]]
> With separable classes, convergence can be very fast


> [!PDF|255, 208, 0] [[ML_Slides_W1_W3.pdf#page=128&annotation=1141R|ML_Slides, p.128]]
> No convergence, when classes are not separable



### LinRegr

![Screenshot 2025-01-18 at 07.39.23.png](/img/user/Attachments/Screenshot%202025-01-18%20at%2007.39.23.png)![Attachments/ML_Slides 3.jpg](/img/user/Attachments/ML_Slides%203.jpg)

[[ML_Slides_W1_W3.pdf#page=155&rect=74,22,666,396|ML_Slides, p.155]]


ADALINE: Adaptive Linear Element

find the optimum

![Screenshot 2025-01-18 at 07.42.29.png](/img/user/Attachments/Screenshot%202025-01-18%20at%2007.42.29.png)


Complexity: M_p^3 + N*M_p^2

![Screenshot 2025-01-18 at 07.43.42.png](/img/user/Attachments/Screenshot%202025-01-18%20at%2007.43.42.png)


Interesting stuff!
> [!PDF|255, 208, 0] [[ML_Slides_W1_W3.pdf#page=166&annotation=1144R|ML_Slides, p.166]]
> When N >> Mp, the LS solution is stable (small changes in the data lead to small changes in the parameter estimates) • When N < Mp then there are many solutions which all produce zero training error • Of all these solutions, one selects the one that minimizes PM j=0 w2 j = wT w (regularised solution) • Even with N > Mp it is advantageous to regularize the solution, in particular with noise on the target

Regularised Cost Function: (PLS)

![Attachments/ML_Slides 4.jpg](/img/user/Attachments/ML_Slides%204.jpg)

[[ML_Slides_W1_W3.pdf#page=167&rect=68,193,732,385|ML_Slides, p.167]]


---
## L3

###  Fn Approx



> [!PDF|255, 208, 0] [[ML_Slides_W1_W3.pdf#page=218&annotation=1152R|ML_Slides, p.218]]
> ϵB to be the minimum Euclidean distance for the “most difficult” function from the function class
![Attachments/ML_Slides 5.jpg](/img/user/Attachments/ML_Slides%205.jpg)

[[ML_Slides_W1_W3.pdf#page=218&rect=312,235,569,302|ML_Slides, p.218]]


> [!PDF|255, 208, 0] [[ML_Slides_W1_W3.pdf#page=220&annotation=1155R|ML_Slides, p.220]]
> Consider input space dimension M • If in one dimensions, we need M (one-dim) ϕ RBFs (e.g., M (one-dim) ϕ = 10), and we want to maintain the same complexity in higher dimensions, then we need Mϕ =  (M (one-dim) ϕ)^ M RBFs in M dimensions

![Attachments/ML_Slides 7.jpg](/img/user/Attachments/ML_Slides%207.jpg)

[[ML_Slides_W1_W3.pdf#page=222&rect=308,299,567,400|ML_Slides, p.222]]

![Attachments/ML_Slides 6.jpg](/img/user/Attachments/ML_Slides%206.jpg)

[[ML_Slides_W1_W3.pdf#page=223&rect=92,175,726,322|ML_Slides, p.223]]

In general: ![Attachments/ML_Slides 8.jpg](/img/user/Attachments/ML_Slides%208.jpg)

[[ML_Slides_W1_W3.pdf#page=224&rect=292,300,597,353|ML_Slides, p.224]]


Case 1: Both Large (M, Roughness): Curse of Dim
Case2: M small, r large: Blessing
> [!PDF|255, 208, 0] [[ML_Slides_W1_W3.pdf#page=227&annotation=1158R|ML_Slides, p.227]]
> a complex nonlinear classification problem (large roughness) can be solved by a transformation of the lowdimensional input space (M ) into a high-dimensional space (Mϕ) where the problem might even become linearly separable

Case3: M large, r small (smooth target fn in high D)
Case4: Easy

Case 1 is not so daunting either: 3 Scenarios where it's mitigated
(Ia): The target functions have "high-frequency components, but only locally, and a sparse solution is feasible." This means that while the function might be complex, its complexity is concentrated in specific areas rather than being uniformly complex across the entire space. The sparsity of the solution means we don't need to consider all dimensions equally (H basis function << M_phi), with NNs H may even be independent of M (input_dim)

b) Second scenario (Ib): The input data isn't randomly scattered across the high-dimensional space but instead lies on a "low-dimensional manifold" (represented by P(x)). This is actually very common in real-world data - while the data might exist in a high-dimensional space, it often has an inherent structure that can be described using far fewer dimensions. Think of how a piece of paper: while it exists in 3D space, it's essentially a 2D object.

P(x) is often restricted to a subspace with much lower dimension (M_h << M)
When M_h is non-linear -> M_h is manifold
[[Coursework/WiSe24-25/ML/Manifold\|Manifold]]

Third scenario (Ic): The target functions are "composable," meaning they can be broken down into simpler components. This is particularly important because it means we can learn complex functions by combining simpler functions, which is exactly what deep neural networks do.


### Basis Functions

![Attachments/ML_Slides 9.jpg](/img/user/Attachments/ML_Slides%209.jpg)

[[ML_Slides_W1_W3.pdf#page=265&rect=56,36,797,537|ML_Slides, p.265]]
![Attachments/ML_Slides 10.jpg](/img/user/Attachments/ML_Slides%2010.jpg)

[[ML_Slides_W1_W3.pdf#page=266&rect=257,212,633,355|ML_Slides, p.266]]


#### RBFs


Gaussian RBF Kernels

![Screenshot 2025-01-18 at 09.44.27.png](/img/user/Attachments/Screenshot%202025-01-18%20at%2009.44.27.png)


![Screenshot 2025-01-18 at 09.44.44.png](/img/user/Attachments/Screenshot%202025-01-18%20at%2009.44.44.png)

s is the spread param




> [!PDF|255, 208, 0] [[ML_Slides_W1_W3.pdf#page=273&annotation=1129R|ML_Slides, p.273]]
> Note that if data points in x-space are uniformly or Gaussian distributed, in basis function space, data can be on a nonlinear manifold, so neither uniformly nor Gaussian distributed

Consider a Simple One-Dimensional Case: Imagine we start with points that are uniformly distributed along a line between 0 and 1. In the original space, these points are evenly spaced, like marks on a ruler. Let's say we apply an RBF transformation using a center point at 0.5.

The Transformation Process: When we apply the RBF transformation φ(x) = exp(-||x - 0.5||²/2s²), the following occurs:

1. Points near 0.5 get mapped to values close to 1
2. Points far from 0.5 get mapped to values close to 0
3. The decay is exponential, not linear

The Result: The transformed data points are no longer uniformly distributed. Instead, we see a concentration of points near 1 (corresponding to input points near 0.5) and a sparse distribution of points near 0 (corresponding to input points far from 0.5). This creates a nonlinear manifold structure.


Remember Forward and Backward Selection

---
## L5 NNs
![Attachments/ML_NN_W5_DL_W9.jpg](/img/user/Attachments/ML_NN_W5_DL_W9.jpg)

[[ML_NN_W5_DL_W9.pdf#page=29&rect=166,155,722,300|ML_NN_W5_DL_W9, p.29]]

Get the gradient derivations


regularization

![Attachments/ML_NN_W5_DL_W9 1.jpg](/img/user/Attachments/ML_NN_W5_DL_W9%201.jpg)

[[ML_NN_W5_DL_W9.pdf#page=35&rect=52,56,801,471|ML_NN_W5_DL_W9, p.35]]

BCE Derivation
![Attachments/ML_NN_W5_DL_W9 2.jpg](/img/user/Attachments/ML_NN_W5_DL_W9%202.jpg)

[[ML_NN_W5_DL_W9.pdf#page=43&rect=73,143,781,473|ML_NN_W5_DL_W9, p.43]]


Do it also for Softmax![Attachments/ML_NN_W5_DL_W9 3.jpg](/img/user/Attachments/ML_NN_W5_DL_W9%203.jpg)

[[ML_NN_W5_DL_W9.pdf#page=45&rect=68,32,809,474|ML_NN_W5_DL_W9, p.45]]![Attachments/ML_NN_W5_DL_W9 4.jpg](/img/user/Attachments/ML_NN_W5_DL_W9%204.jpg)

[[ML_NN_W5_DL_W9.pdf#page=60&rect=79,105,798,462|ML_NN_W5_DL_W9, p.60]]
Bagging = Bootstrap Aggregating




---
## L9 DL

Optimizers: see Optimizers section in [[Coursework/SoSe24/GenAI/Ch 1 Intro\|Ch 1 Intro]]

Drop out and Regularization [[Coursework/SoSe24/GenAI/Ch 2 CNNs\|Ch 2 CNNs]]
Also for CNNs, just refer to the Above Note




---
## L6 Kernels

smoothness assumptions can be implemented through kernel functions

![Attachments/W678_10.jpg](/img/user/Attachments/W678_10.jpg)

[[W678_10.pdf#page=8&rect=239,288,652,398|W678_10, p.8]]

![Attachments/W678_10 1.jpg](/img/user/Attachments/W678_10%201.jpg)

[[W678_10.pdf#page=9&rect=39,44,754,562|W678_10, p.9]]

![Attachments/W678_10 2.jpg](/img/user/Attachments/W678_10%202.jpg)

[[W678_10.pdf#page=10&rect=42,179,655,425|W678_10, p.10]]

note that this depends on N and not on M_phi

[[Coursework/WiSe24-25/ML/Math_Kernel\|Math_Kernel]]

[[Coursework/WiSe24-25/ML/Gaussian Processes\|Gaussian Processes]]

[[Coursework/WiSe24-25/ML/Other_Kernel\|Other_Kernel]]

---
> [!PDF|255, 208, 0] [[W678_10.pdf#page=62&annotation=1045R|W678_10, p.62]]
> vid

[[Coursework/WiSe24-25/ML/Evidence\|Evidence]]


> [!PDF|255, 208, 0] [[W678_10.pdf#page=65&annotation=1048R|W678_10, p.65]]
> Summary

> [!PDF|255, 208, 0] [[W678_10.pdf#page=74&annotation=1065R|W678_10, p.74]]
> riance, Corr

> [!PDF|255, 208, 0] [[W678_10.pdf#page=73&annotation=1051R|W678_10, p.73]]
> Covariance


> [!PDF|255, 208, 0] [[W678_10.pdf#page=75&annotation=1068R|W678_10, p.75]]
> seful Rule


> [!PDF|255, 208, 0] [[W678_10.pdf#page=76&annotation=1071R|W678_10, p.76]]
> Covariance Matrix of Linear Transformation

> [!PDF|255, 208, 0] [[W678_10.pdf#page=77&annotation=1074R|W678_10, p.77]]
> Continuous Random Variables



> [!PDF|255, 208, 0] [[W678_10.pdf#page=78&annotation=1077R|W678_10, p.78]]
> xpectations for Continuous Variables


## L7

### Linear Classifiers

> [!PDF|] [[W678_10.pdf#page=101&selection=136,6,137,19|W678_10, p.101]]
> that both Gaussian distributions have different modes (centers) but the same covariance matrices


see handwritten notes

### Freq Stats

> [!PDF|] [[W678_10.pdf#page=143&selection=24,20,27,49|W678_10, p.143]]
> requentist statistics: derivation of probabilistic statements under repeatable experiments under identical conditions

![Attachments/W678_10 3.jpg](/img/user/Attachments/W678_10%203.jpg)

[[W678_10.pdf#page=157&rect=70,34,797,551|W678_10, p.157]]




![Attachments/W678_10 4.jpg](/img/user/Attachments/W678_10%204.jpg)

[[W678_10.pdf#page=158&rect=40,66,803,515|W678_10, p.158]]

![Attachments/W678_10 5.jpg](/img/user/Attachments/W678_10%205.jpg)

[[W678_10.pdf#page=159&rect=249,97,663,339|W678_10, p.159]]![Attachments/W678_10 6.jpg](/img/user/Attachments/W678_10%206.jpg)

[[W678_10.pdf#page=163&rect=43,73,812,485|W678_10, p.163]]

![Attachments/W678_10 7.jpg](/img/user/Attachments/W678_10%207.jpg)

[[W678_10.pdf#page=164&rect=48,73,787,455|W678_10, p.164]]


> [!PDF|] [[W678_10.pdf#page=165&selection=4,0,30,82|W678_10, p.165]]
> The ML-estimator has many desirable properties: – The ML-estimator is asymptotically N → ∞ unbiased (although with a finite sample size it might be biases) – Maybe surprisingly, the ML estimator is asymptotically (N → ∞) MSE-efficient among all unbiased estimators – Asymptotically, the estimator is Gaussian distributed, even when the noise is not!


![Attachments/W678_10 8.jpg](/img/user/Attachments/W678_10%208.jpg)

[[W678_10.pdf#page=170&rect=53,309,788,465|W678_10, p.170]]


> [!PDF|] [[W678_10.pdf#page=172&selection=4,0,5,26|W678_10, p.172]]
> In a frequentist setting, the parameters are fixed but unknown and the data are generated by a random process


### Bayesian Stats

> [!PDF|] [[W678_10.pdf#page=172&selection=9,5,9,83|W678_10, p.172]]
> Bayesian approach, also the parameters have been generated by a random process



![Screenshot 2025-02-06 at 23.08.33.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2023.08.33.png)


![Attachments/W678_10 9.jpg](/img/user/Attachments/W678_10%209.jpg)

[[W678_10.pdf#page=176&rect=281,163,615,313|W678_10, p.176]]


Linear Regression: 


![Screenshot 2025-02-06 at 23.11.03.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2023.11.03.png)


![Screenshot 2025-02-06 at 23.11.20.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2023.11.20.png)


![Screenshot 2025-02-06 at 23.11.32.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2023.11.32.png)



### Learning THeories

#### Classical Freq. 

![Attachments/W678_10 10.jpg](/img/user/Attachments/W678_10%2010.jpg)

[[W678_10.pdf#page=251&rect=169,176,745,228|W678_10, p.251]]![Attachments/W678_10 11.jpg](/img/user/Attachments/W678_10%2011.jpg)

[[W678_10.pdf#page=252&rect=65,170,803,338|W678_10, p.252]]

![Attachments/W678_10 12.jpg](/img/user/Attachments/W678_10%2012.jpg)

[[W678_10.pdf#page=254&rect=178,184,690,265|W678_10, p.254]]

![Attachments/W678_10 13.jpg](/img/user/Attachments/W678_10%2013.jpg)

[[W678_10.pdf#page=255&rect=92,291,508,330|W678_10, p.255]]

![Attachments/W678_10 14.jpg](/img/user/Attachments/W678_10%2014.jpg)

[[W678_10.pdf#page=255&rect=78,85,817,286|W678_10, p.255]]

Example: Linear Models

![Attachments/W678_10 15.jpg](/img/user/Attachments/W678_10%2015.jpg)

[[W678_10.pdf#page=256&rect=69,44,783,469|W678_10, p.256]]

![Attachments/W678_10 17.jpg](/img/user/Attachments/W678_10%2017.jpg)

[[W678_10.pdf#page=259&rect=68,184,518,316|W678_10, p.259]]![Attachments/W678_10 18.jpg](/img/user/Attachments/W678_10%2018.jpg)

[[W678_10.pdf#page=263&rect=76,135,802,303|W678_10, p.263]]


![Attachments/W678_10 19.jpg](/img/user/Attachments/W678_10%2019.jpg)

[[W678_10.pdf#page=270&rect=70,89,803,326|W678_10, p.270]]![Attachments/W678_10 20.jpg](/img/user/Attachments/W678_10%2020.jpg)

[[W678_10.pdf#page=271&rect=70,173,647,346|W678_10, p.271]]![Attachments/W678_10 21.jpg](/img/user/Attachments/W678_10%2021.jpg)

[[W678_10.pdf#page=273&rect=205,39,702,294|W678_10, p.273]]![Attachments/W678_10 22.jpg](/img/user/Attachments/W678_10%2022.jpg)

[[W678_10.pdf#page=282&rect=60,160,788,405|W678_10, p.282]]![Attachments/W678_10 23.jpg](/img/user/Attachments/W678_10%2023.jpg)

[[W678_10.pdf#page=283&rect=71,302,791,457|W678_10, p.283]]

![Attachments/W678_10 26.jpg](/img/user/Attachments/W678_10%2026.jpg)

[[W678_10.pdf#page=283&rect=76,42,811,199|W678_10, p.283]]


----
## L11

### Seq Modelling

RNNs

[[Coursework/SoSe24/GenAI/Practice 67890 Important Code\|Practice 67890 Important Code]]
![Screenshot 2025-02-08 at 00.29.29.png](/img/user/Attachments/Screenshot%202025-02-08%20at%2000.29.29.png)
![Screenshot 2025-02-08 at 00.35.20.png](/img/user/Attachments/Screenshot%202025-02-08%20at%2000.35.20.png)
BPTT derivation


Bidir RNNs: pred depend on past and future inputs![Attachments/ML_W11_12.jpg](/img/user/Attachments/ML_W11_12.jpg)

[[ML_W11_12.pdf#page=44&rect=73,130,798,235|ML_W11_12, p.44]]



LSTMs


![Screenshot 2025-02-08 at 00.35.51.png](/img/user/Attachments/Screenshot%202025-02-08%20at%2000.35.51.png)![Screenshot 2025-02-08 at 00.36.04.png](/img/user/Attachments/Screenshot%202025-02-08%20at%2000.36.04.png)


Q1.5a) Explanation of LSTM Gates and Discussion of Non-Linearities
1. Input modulation gate g(t): Purpose: Creates new candidate values that could be added to the cell state. Non-linearity: tanh Motivation: tanh squashes values to the range [-1, 1], allowing the network to represent both +ve and -ve impacts on the cell state, ie representing inhibitng and enhancing effects.
2. Input gate i(t): Purpose: Controls which new information will be stored in the cell state. Non-linearity: Sigmoid Motivation: Sigmoid outputs values between 0 and 1, acting as a "filter". This allows the gate to decide how much of the new information should pass through (1 means let everything through, 0
means let nothing through).
1. Forget gate f(t): Purpose: Decides what information to discard from the cell state. Non-linearity: Sigmoid Motivation: Not unlike the input gate, sigmoid is used here to output values between 0 and 1. This allows the network to "forget" (0) or "remember" (1) parts of the previous cell state, or choose
values in between.
2. Output gate o(t): Purpose: Controls what parts of the cell state will be output to the next hidden state. Non-linearity: Sigmoid Motivation: Again, sigmoid is used to output values between 0 and 1, allowing the gate to control how much of each component of the cell state should be revealed in the output.
---

## L12

Math: 
![Screenshot 2025-02-08 at 00.38.40.png](/img/user/Attachments/Screenshot%202025-02-08%20at%2000.38.40.png)

![Screenshot 2025-02-08 at 00.38.52.png](/img/user/Attachments/Screenshot%202025-02-08%20at%2000.38.52.png)![Attachments/ML_W11_12 1.jpg](/img/user/Attachments/ML_W11_12%201.jpg)

[[ML_W11_12.pdf#page=119&rect=75,53,752,558|ML_W11_12, p.119]]

![Attachments/ML_W11_12 2.jpg](/img/user/Attachments/ML_W11_12%202.jpg)

[[ML_W11_12.pdf#page=121&rect=28,42,808,572|ML_W11_12, p.121]]![Attachments/ML_W11_12 3.jpg](/img/user/Attachments/ML_W11_12%203.jpg)

[[ML_W11_12.pdf#page=123&rect=84,220,697,316|ML_W11_12, p.123]]

### Autoencoder 
 

[[ML_W11_12.pdf#page=159&rect=94,88,812,488|ML_W11_12, p.159]]
![Attachments/ML_W11_12 4.jpg](/img/user/Attachments/ML_W11_12%204.jpg)

[[ML_W11_12.pdf#page=154&rect=78,33,814,470|ML_W11_12, p.154]]



![Attachments/ML_W11_12 6.jpg](/img/user/Attachments/ML_W11_12%206.jpg)

[[ML_W11_12.pdf#page=164&rect=80,270,608,406|ML_W11_12, p.164]]![Attachments/ML_W11_12 7.jpg](/img/user/Attachments/ML_W11_12%207.jpg)

[[ML_W11_12.pdf#page=165&rect=51,93,784,476|ML_W11_12, p.165]]


![Attachments/ML_W11_12 8.jpg](/img/user/Attachments/ML_W11_12%208.jpg)

[[ML_W11_12.pdf#page=167&rect=33,39,802,568|ML_W11_12, p.167]]

VAE

![Attachments/ML_W11_12 9.jpg](/img/user/Attachments/ML_W11_12%209.jpg)

[[ML_W11_12.pdf#page=178&rect=62,26,804,424|ML_W11_12, p.178]]

![Attachments/ML_W11_12 10.jpg](/img/user/Attachments/ML_W11_12%2010.jpg)

[[ML_W11_12.pdf#page=185&rect=113,77,769,496|ML_W11_12, p.185]]


GANs




![Screenshot 2025-02-08 at 00.46.42.png](/img/user/Attachments/Screenshot%202025-02-08%20at%2000.46.42.png)

GAN Math goes here

![Screenshot 2025-02-08 at 00.47.30.png](/img/user/Attachments/Screenshot%202025-02-08%20at%2000.47.30.png)

transposed conv -> batch norm -> leaky ReLU


Transposed Conv. ![Screenshot 2025-02-08 at 00.47.48.png](/img/user/Attachments/Screenshot%202025-02-08%20at%2000.47.48.png)

cGAN (Conditonal GAN): uses class attr. 

cycleGAN (cycle consistent )

![Screenshot 2025-02-08 at 00.51.42.png](/img/user/Attachments/Screenshot%202025-02-08%20at%2000.51.42.png)

