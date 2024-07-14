---
{"dg-publish":true,"permalink":"/coursework/so-se24/gen-ai/ch-7-in-ns/","noteIcon":""}
---

---

#### Normalizing Flows

What? 
	GM buit on invertible transformations. Generally:
	- Eff. to sample from p_x
	- Eff. to evaluate from p_x
	- Highly expressive
	- useful latent repr.
	- straightf. to train
	Also: 
	- Expensive for High-D Data
	- Restrictions on mapping f_n
![Screenshot 2024-07-14 at 16.27.12.png](/img/user/Attachments/Screenshot%202024-07-14%20at%2016.27.12.png)



Change of variables? 
	$p_{x} (x)=p_{z}(f(x))*|detDf(x)|$
	Z = f(x) is an invertible, diff. function 
	Df(x) is the Jacobian of f(x)
	p_z(z) is typically $N(z|0,I)$
	
	![Screenshot 2024-07-14 at 23.49.32.png](/img/user/Attachments/Screenshot%202024-07-14%20at%2023.49.32.png)



What's a Flow? 
	A param Function f(x)
		invertible
		diff. 
		has an eff. computable Inverse and Jacobian Det [[Coursework/SoSe24/ML/Jacobian Matrix\|Jacobian Matrix]]


#### Composition of Flows, (affine) coupling Layers, INNs

Composition of Flows? 
	Det: 
	$det(Df)=det\prod_{k=1}^{K}Df_{k}=\prod_{k=1}^{K}det(Df_k)$
	Likelihood: $$ \underset{\theta}{\operatorname{argmax}} \sum_{i=1}^{N} logp_z(f(x_i|\theta)) + \sum_{k=1}^{K}log|detDf_k(x_i|\theta| $$
	The likelihood formula in the image combines these elements:
	- It evaluates how likely the transformed points are under p_Z
	- It accounts for the volume change induced by f (through the Jacobian determinant)


Coupling Flows? 
	![Screenshot 2024-07-15 at 00.02.46.png](/img/user/Attachments/Screenshot%202024-07-15%20at%2000.02.46.png)
	![Screenshot 2024-07-15 at 00.03.14.png](/img/user/Attachments/Screenshot%202024-07-15%20at%2000.03.14.png)Inverse
	Jacobian?  [ ∂/∂x^A f^(x^B|θ(x^A)),  Df^(x^B|θ(x^A)) ]
	Determinant: det Df(x) = det Df^(x^B|θ(x^A))


Affine Coupling Flows? 
![Screenshot 2024-07-15 at 00.07.01.png](/img/user/Attachments/Screenshot%202024-07-15%20at%2000.07.01.png)

![Screenshot 2024-07-15 at 00.07.11.png](/img/user/Attachments/Screenshot%202024-07-15%20at%2000.07.11.png)

Since direct div. can be numerically problematic -> use the exp fct and clip xtreme values of s_i
![Screenshot 2024-07-15 at 00.07.22.png](/img/user/Attachments/Screenshot%202024-07-15%20at%2000.07.22.png)



Pro?
	Invertible
	Latent Variable Model
	Exact Likelihood

Con? 
	Input and Output must have same dim -> expensive in high-D Spaces (e.g Images)
#### Ill-Posed Problems

![Screenshot 2024-07-15 at 00.10.48.png](/img/user/Attachments/Screenshot%202024-07-15%20at%2000.10.48.png)

How does it work? 
	•	Forward Process (x \rightarrow y): The input x is transformed into y and z through the INN.
	•	Inverse Process ([y, z] \rightarrow x): The observed data y and residuals z are used to reconstruct the input x

MMD? 
	Maximally Mean Discrepancy: used to match the distribution of x to a prior distribution, ensuring that the input data follows a known distribution.

MMD for z?
	This ensures that the residual z matches a standard normal distribution, typically $\mathcal{N}(0,1)$
#### XAI with INNs

##### Disentangling Semantic Concepts with INNs
![Screenshot 2024-07-15 at 00.13.33.png](/img/user/Attachments/Screenshot%202024-07-15%20at%2000.13.33.png)






##### cINNs and recovering Model Invariances

cINNs? 
	incorporate conditional Info
	- Regular INNs learn a bijective mapping between input space X and latent space Z.
	- cINNs learn this mapping conditioned on some additional information C. 

How? 
	 Forward Pass:
    - Input: x (data), c (condition)
    - Output: z (latent representation)
    - Process: z = f(x; c), where f is the cINN
	Inverse Pass:
    - Input: z (latent), c (condition)
    - Output: x (reconstructed data)
    - Process: x = f^(-1)(z; c)

![Screenshot 2024-07-15 at 00.16.06.png](/img/user/Attachments/Screenshot%202024-07-15%20at%2000.16.06.png)


Loss? 
#TODO 



Recovering Model Invariances? 
#TODO 