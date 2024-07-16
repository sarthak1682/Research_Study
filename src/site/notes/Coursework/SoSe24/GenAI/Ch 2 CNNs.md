---
{"dg-publish":true,"permalink":"/coursework/so-se24/gen-ai/ch-2-cn-ns/","noteIcon":""}
---

---
### Network Topology of Hierarchical Models


##### Activation Functions
Sigmoid Activation
	Problems
		1. Saturated Neurons kill the Gradients (**Saturated Neurons**: Neurons with inputs that produce outputs near 0 or 1.)
		2. Outputs not 0-Centered
	$$ g(x) = \frac{1}{1+ e^{-x}}$$
	![Screenshot 2024-07-12 at 16.31.25.png](/img/user/Attachments/Screenshot%202024-07-12%20at%2016.31.25.png)



Tanh(x)
	Good:
		Zero-Centered
	Bad: 
		Still kills the Gradient
	$$  \tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}} $$
	![Screenshot 2024-07-12 at 16.31.40.png](/img/user/Attachments/Screenshot%202024-07-12%20at%2016.31.40.png)


ReLU
	Good:
		Does not saturate in the +ve Region
		Comp. Efficient
		In practice: Converges much faster than tanh/sigmoid(6x)
	Bad: 
		Not Zero-Centered
		Gradient when x<0? : Annoyance
		**Dying ReLU Problem**
			In the dying ReLU problem, if a neuron gets stuck in the negative side of the ReLU function, it will always output 0 for any input, effectively becoming inactive or “dead”. This can happen if the neuron weights are updated in such a way that the input to the neuron is always negative. Once a neuron dies, it might never recover because the gradient of ReLU for negative inputs is zero, and hence it won’t contribute to learning anymore.

	f(x) = max(0,x)

Leaky ReLU
	Good: (apart from ReLU)
		will not "die"!
	f(x) = max($\alpha$x, x)
		where  $\alpha$  is a small positive constant, typically set to 0.01 or a similar value. 



##### MLPs
A 2-Layer Net: 
$$ f = W_2*max(0,W_1*x)$$

Expressiveness: 
1. Every continous function can be modeled with one hidden layer
2. Every function can be modeled with 2 hidden layers


##### Regularization

For what? 
	prevent overfitting, improve generalization, and stabilize solutions

How to? 
.	L1 Regularization (Lasso):
	•	Adds a penalty equal to the absolute value of the magnitude of coefficients.
	•	Effect: Can drive some coefficients to zero, effectively performing feature selection.
		$\text{Loss function} = \text{Original Loss} + \lambda \sum_{i} |\theta_i|$
	2.	L2 Regularization (Ridge):
	•	Adds a penalty equal to the square of the magnitude of coefficients.
	•	Effect: Shrinks coefficients but doesn’t necessarily set any to zero.
		$\text{Loss function} = \text{Original Loss} + \lambda \sum_{i} \theta_i^2$
****
Dropout

	![Pasted image 20240712164435.png](/img/user/Attachments/Pasted%20image%2020240712164435.png) Randomly set Neurons to zero
	![Pasted image 20240712164548.png](/img/user/Attachments/Pasted%20image%2020240712164548.png)






### CNNs

#### Motivation
1. Incorporate Receptive Fields
2. Reduce the # of Paramaters
	1. Conv with small Kernels (W)
	2. Downsampling at the later levels (reduce the spatial dimensions (height and width) of feature maps.)
		1. Max Pooling (e.g on a 2x2 Window)
		2. Strided Conv. 
	3. FC only at coarse levels

$$  (f * g)(n) = \sum_{k=0}^{N-1} f(k) \cdot g(n - k) $$
	f  (input),  
	g  (kernel), 
	n  (output position),
	k  (summation index)
#### Principles, Basic Elements

Elements
	Conv. Layer
	ReLU
	Pooling 
	Norm. Layer
	FC Layer

##### Conv
![Pasted image 20240712170529.png](/img/user/Attachments/Pasted%20image%2020240712170529.png)



Conv. Layer
	W.size() = FxFxDepth
	Stride S 
		S = 1: Std. Conv. 
		S>1: Conv. + DownSampling
	Padding (std: Zero)




##### Pool

![Pasted image 20240712171026.png](/img/user/Attachments/Pasted%20image%2020240712171026.png)



Conv to FC: If the output from a Conv layer is  (N, H, W, C) , you flatten it to  (N, H \times W \times C)  before connecting to a FC layer.
FC to Conv: If the output from a FC layer is  (N, M) , you reshape it to  (N, H, W, C)  before feeding it into a Conv layer.


Power of Small Filters


![Pasted image 20240712171345.png](/img/user/Attachments/Pasted%20image%2020240712171345.png)
$\text{Number of Multiply-Adds} = H{\prime} \times W{\prime} \times K_H \times K_W \times C_{\text{in}} \times C_{\text{out}}$
$\text{Number of Weights} =  \times K_H \times K_W \times C_{\text{in}} \times C_{\text{out}}$

$H{\prime} \times W{\prime}$  is the number of output pixels.
$K_H \times K_W \times C_{\text{in}}$  is the number of parameters (weights) per kernel.	
$C_{\text{out}}$  is the number of output channels.

Example Calculation

For example, if:

Input size $H \times W \times C_{\text{in}} = 32 \times 32 \times 3$  (a 32x32 RGB image),
Kernel size  $K_H \times K_W \times C_{\text{in}} \times C_{\text{out}} = 3 \times 3 \times 3 \times 64$  (a 3x3 kernel with 3 input channels and 64 output channels),
Output size  $H{\prime} \times W{\prime} \times C_{\text{out}} = 32 \times 32 \times 64$, 
	then the number of multiply-adds would be:
	$\text{Number of Multiply-Adds} = 32 \times 32 \times 3 \times 3 \times 3 \times 64 = 1,179,648$
 


![Pasted image 20240712171402.png](/img/user/Attachments/Pasted%20image%2020240712171402.png)
##### Normalization

Decorrelation? 
	Decorrelation refers to the process of transforming the data so that the features (variables) are uncorrelated with each other. In other words, after decorrelation, the covariance matrix of the data becomes diagonal, with zeros in the off-diagonal elements, indicating no linear correlation between different features.

Whitening? 
	Whitening (or sphering) extends decorrelation by additionally scaling each feature to have unit variance, resulting in a dataset where all variables are uncorrelated and have the same variance. This transformation can be seen as a normalization step that removes redundant information and makes the data distribution more spherical in the transformed space.


![Pasted image 20240712171811.png](/img/user/Attachments/Pasted%20image%2020240712171811.png)



Batch Norm
![Pasted image 20240712172046.png](/img/user/Attachments/Pasted%20image%2020240712172046.png)





##### Skip Connections & Layer Patterns
Resnet
![Screenshot 2024-07-13 at 14.08.53.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2014.08.53.png)
```
def residual_block(x, filters, kernel_size=3, stride=1):
	# Save the input for the shortcut connection
	shortcut = x
	
	# First convolutional layer
	x = Conv2D(filters, kernel_size=kernel_size, strides=stride, padding='same')(x)
	x = BatchNormalization()(x)
	x = ReLU()(x)
	
	# Second convolutional layer
	x = Conv2D(filters, kernel_size=kernel_size, strides=1, padding='same')(x)
	x = BatchNormalization()(x)
	
	# Add the shortcut to the output
	**x = Add()([x, shortcut])** #This is the thing!
	x = ReLU()(x)
	
	return x

	
```



##### Data Augmentation
![Screenshot 2024-07-13 at 14.15.42.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2014.15.42.png)


