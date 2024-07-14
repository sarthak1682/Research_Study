---
{"dg-publish":true,"permalink":"/coursework/so-se24/gen-ai/ch-4-va-es/","noteIcon":""}
---

#### Autoencoders

What? 
	Autoencoders are a type of neural network architecture used for unsupervised learning. Their primary purpose is to learn efficient data codings in an automatic manner.
	By forcing the network to reconstruct the input through a bottleneck, it learns to capture the most important features of the data.
	Unlike VAEs, regular autoencoders don't have a probabilistic formulation. They simply learn to compress and decompress data efficiently.

Can one sample from AEs? 
	In standard AEs, we don't have a well-defined probabilistic structure for the latent space z.

#### VAEs

##### Setting

What is? 
Prob. Spin on AEs, let's one sample from the model to generate data, modelling the density EXPLICITLY. 

Model Assumption
	VAEs assume that the observed data x is generated from some unobserved (latent) variables z. This generative process can be described as:
	z ~ p(z) (prior) x ~ p(x|z) (likelihood)


True Prior and True Conditional? 
	- True prior p(z): This is the assumed distribution of the latent variables before observing any data. In VAEs, this is typically chosen to be a standard normal distribution N(0, I).
	- True conditional p(x|z): This represents the true process that generates the observed data x from the latent variables z. In practice, we don't know this true conditional and must approximate it.


Repr.?
	VAEs use neural networks to represent:
	- An encoder network q_φ(z|x) to approximate the posterior p(z|x)
	- A decoder network p_θ(x|z) to model the likelihood

##### Intractibility

Goal? 
	to estimate the true parameters θ of the generative model that maximizes the likelihood of the observed data:
	p(x) = ∫ p(x|z)p(z)dz
	This marginal likelihood is often intractable to compute directly.




##### Max Data Likelihood
![Screenshot 2024-07-13 at 23.23.25.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2023.23.25.png)



##### Putting it all together


![Screenshot 2024-07-13 at 23.33.39.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2023.33.39.png)

![Screenshot 2024-07-13 at 23.33.25.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2023.33.25.png)
![Screenshot 2024-07-13 at 23.33.03.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2023.33.03.png)




##### Data Synthesis with VAEs

Generate new data:

- Sample random points from the latent space
- Pass these points through the trained decoder
##### Recap
![Screenshot 2024-07-13 at 23.43.28.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2023.43.28.png)

![Screenshot 2024-07-13 at 23.49.23.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2023.49.23.png)


#### ED Framework for disentangling shape and appearance


Variational U-Net (VU-Net)
![Screenshot 2024-07-13 at 23.59.53.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2023.59.53.png)

- Shape Estimator: This component extracts structural information from the input image, producing a shape representation (s). The output appears to be a simplified skeleton or pose estimation of the person.
- Appearance Encoder (app enc): This encodes the appearance information from the input image x, conditioned on the shape s. It produces q(a|s,x), which is an approximation of the appearance distribution.
- Decoder: The large block on the right represents the decoder. It takes the shape information s and samples from the appearance distribution p(a|s) to reconstruct the image.
- KL Divergence: There's a KL divergence term between q(a|s,x) and p(a|s), which encourages the learned appearance distribution to be close to the prior.
- Reconstruction: The output x̃ is compared to the input x to compute the reconstruction loss L(x,x̃).
- Objective Function: The overall objective is to maximize log p(x|s,a) - KL(q(a|s,x)||p(a|s)).
    - log p(x|s,a) is the reconstruction term (maximizing the likelihood of the data)
    - KL(q(a|s,x)||p(a|s)) is the disentanglement term (encouraging the appearance to be independent of shape)

