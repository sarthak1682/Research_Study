---
{"dg-publish":true,"permalink":"/coursework/so-se24/gen-ai/ch-8-diffusion/","noteIcon":""}
---

---

##### Intro
Denoising Diffusion Models
1. Forward: add noise to the input
2. Reverse: learn to generate data by denoising![Screenshot 2024-07-16 at 00.14.09.png](/img/user/Attachments/Screenshot%202024-07-16%20at%2000.14.09.png)

##### Forward diffusion Process

The transition probability q(x_t | x_t-1) represents the probability of obtaining x_t given x_t-1 in the forward process. This is defined as:
q(x_t | x_t-1) = N(x_t; √(1 - β_t) * x_t-1, β_t * I)
Where:

- N(μ, σ²) denotes a normal distribution with mean μ and variance σ²
- β_t is a variance schedule that controls the amount of noise added at each timestep
- I is the identity matrix

The intuition behind this is:

- The mean √(1 - β_t) * x_t-1 slightly reduces the intensity of x_t-1
- The variance β_t * I adds some Gaussian noise

Reparameterization:

The process can be reparameterized to sample x_t directly given x_0:

q(x_t | x_0) = N(x_t; √(ᾱ_t) * x_0, (1 - ᾱ_t) * I)

Where ᾱ_t = ∏ᵗ_s=1 (1 - β_s) is the cumulative product of the complements of the β schedule.

x_t = √(ᾱ_t) * x_0 + √(1 - ᾱ_t) * ε

Where ε is sampled from a standard normal distribution N(0, I).



##### Reverse Diffusion Process

p_θ(x_0:T) = p(x_T) * ∏ᵀ_t=1 p_θ(x_t-1|x_t)

Where:

- p(x_T) is the prior distribution, typically a standard Gaussian
- p_θ(x_t-1|x_t) is the learned reverse transition probability

 Reverse transition probability: The key component is p_θ(x_t-1|x_t), which represents the probability of recovering x_t-1 given x_t. This is modeled as a Gaussian:

p_θ(x_t-1|x_t) = N(x_t-1; μ_θ(x_t, t), Σ_θ(x_t, t))

Where:

- μ_θ(x_t, t) is the predicted mean
- Σ_θ(x_t, t) is the predicted covariance matrix

Simplification: In practice, Σ_θ is often fixed to σ_t²I for simplicity, where σ_t is a time-dependent constant. This leaves us to learn only μ_θ.


Parameterization of μ_θ: The mean μ_θ is typically parameterized as:

μ_θ(x_t, t) = (1/√(1-β_t)) * (x_t - (β_t/√(1-ᾱ_t)) * ε_θ(x_t, t))

Where:

- ε_θ(x_t, t) is a neural network that predicts the noise in x_t
- β_t and ᾱ_t are the same as in the forward process

Learning objective: The model is trained to minimize the difference between the predicted noise ε_θ(x_t, t) and the actual noise used to generate x_t from x_0 in the forward process.
	The score function, typically denoted as  s_\theta(x_t, t) , represents the gradient of the log probability density function of the data at time  t  with respect to the data point  x_t :
	 s_\theta(x_t, t) = \nabla_{x_t} \log p_t(x_t) 

Content-Detail Tradeoff
![Screenshot 2024-07-16 at 00.22.37.png](/img/user/Attachments/Screenshot%202024-07-16%20at%2000.22.37.png)





##### DM to LDM

Combine Adv. of ARM/DM and those of CNNs:
	Expr. for long-range context + computational Inductive Bias

![Screenshot 2024-07-16 at 00.25.11.png](/img/user/Attachments/Screenshot%202024-07-16%20at%2000.25.11.png)


![Screenshot 2024-07-16 at 00.25.24.png](/img/user/Attachments/Screenshot%202024-07-16%20at%2000.25.24.png)


- Input image (x): The process begins with an input image x in the Pixel Space (pink area on the left).
- CNN Encoder (E): The input image x is passed through a Convolutional Neural Network (CNN) encoder E. This encoder transforms the image from pixel space into a latent representation z in the Latent Space (green area).
- Latent Space: The latent space contains the compressed representation z of the input image. This is where the main diffusion process occurs.
- Diffusion Process: The latent representation z undergoes a diffusion process, which gradually adds noise to the latent representation over multiple steps.
- Denoising U-Net (εθ): The core of the denoising process is a U-Net architecture εθ. This network is designed to remove noise from the diffused latent representation.
- Denoising steps: The U-Net is applied iteratively in multiple steps (represented by the Q, K, V blocks). Each step aims to denoise the latent representation further.
- Cross-attention mechanism: Each denoising step incorporates a cross-attention mechanism (represented by the Q, K, V notation), allowing the model to focus on relevant parts of the input during denoising.
- Skip connections: There are skip connections (dotted lines) between denoising steps, allowing information to flow directly between non-adjacent layers of the U-Net.
- Conditioning: On the right side, there's a Conditioning module that provides additional input to guide the denoising process. This can include:
    - Semantic Map
    - Text
    - Representations
    - Images
- CNN Decoder (D): After the denoising process, the final latent representation zT is passed through a CNN decoder D, which transforms it back into pixel space, producing the output image x̃.


Classifier Free Guidance

- Traditional Classifier Guidance: Initially, diffusion models used a separate classifier to guide the generation process towards desired attributes. This classifier would be trained to recognize specific features or classes.
- Classifier-Free Approach: Instead of using a separate classifier, this method incorporates the guiding information directly into the diffusion model's training and sampling process.
- Implementation:
    - During training, the model learns to generate images both with and without conditioning information.
    - At inference time, the model can interpolate between these two learned behaviors.



Fixed Text Encoder + Multi Res. Training


##### Semi-Param Neural Syn.
Semi-parametric neural image synthesis is an approach to image generation that combines parametric neural networks with non-parametric retrieval of image patches from a database.


##### Retrieval Augmented DM
Key Features:
a) Database: A large collection of image patches or features extracted from real images.

b) Retrieval mechanism: During the denoising process, the model queries the database to find relevant visual information.

c) Integration: The retrieved information is incorporated into the diffusion process, guiding the generation towards more realistic and detailed outputs.

d) Adaptability: The retrieval component allows the model to adapt to new domains or specific styles more easily than a purely parametric model.



##### Flow Matching
helps sample fast
![Screenshot 2024-07-16 at 01.05.59.png](/img/user/Attachments/Screenshot%202024-07-16%20at%2001.05.59.png)



