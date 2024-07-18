---
{"dg-publish":true,"permalink":"/coursework/so-se24/gen-ai/ch-1-intro/","noteIcon":""}
---


###### Generative Modelling

Formulate as density estimation:
Explicit DE: Define+solve p_model(x)
	 This avoids specifying the density function directly. Instead, it focuses on learning a model that can generate new data points that resemble the training data
	 e.g KDE
Implicit DE: learn model that can sample from p_model without explicitly defining it
	 This avoids specifying the density function directly. Instead, it focuses on learning a model that can generate new data points that resemble the training data
	 e.g. GANs


Taxonomy
![Screenshot 2024-07-17 at 01.32.00.png](/img/user/Attachments/Screenshot%202024-07-17%20at%2001.32.00.png)
###### Generative vs Discriminative Models


 Feature                | Generative Models                                                  | Discriminative Models                                           |
| ---------------------- | ------------------------------------------------------------------ | --------------------------------------------------------------- |
| **Objective**          | Model joint distribution \( P(X, Y) \), Model Likelihood and Prior | Model conditional distribution \(     P(Y\|X)), Model Posterior |
| **Data Understanding** | Understands how data is generated                                  | Focuses on decision boundaries between classes                  |
| **Tasks**              | Classification, density    estimation, data generation             | Primarily classification                                        |
| **Flexibility**        | Can handle missing data and multiple tasks                         | Optimized for classification                                    |
| **Examples**           | Naive Bayes, HMMs, GMMs, VAEs, GANs                                | Logistic Regression, SVMs, Random Forests      |
| **Assumptions**        | Often make strong assumptions about data distribution              | Fewer assumptions, more focused on discriminative power         |

##### Bayes' Rule

$$ P(Y|X) = \frac{P(X|Y) \cdot P(Y)}{P(X)} $$

where:
- \( P(Y|X) \) is the posterior probability, the probability of the hypothesis \( Y \) given the data \( X \).
- \( P(X|Y) \) is the likelihood, the probability of the data \( X \) given the hypothesis \( Y \).
- \( P(Y) \) is the prior probability, the initial probability of the hypothesis \( Y \).
- \( P(X) \) is the marginal probability, the total probability of the data \( X \) under all possible hypotheses.


Bayes' Rule can be expressed in terms of the posterior ratio, likelihood ratio, and prior ratio as follows:

$$ \frac{P(Y_1|X)}{P(Y_2|X)} = \frac{P(X|Y_1)}{P(X|Y_2)} \cdot \frac{P(Y_1)}{P(Y_2)} $$

where:
- $\frac{P(Y_1|X)}{P(Y_2|X)}$ is the posterior ratio, the ratio of the probabilities of hypotheses \( Y_1 \) and \( Y_2 \) given the data \( X \).
- $\frac{P(X|Y_1)}{P(X|Y_2)}$ is the likelihood ratio, the ratio of the probabilities of the data \( X \) given hypotheses \( Y_1 \) and \( Y_2 \).
- $\frac{P(Y_1)}{P(Y_2)}$ is the prior ratio, the ratio of the initial probabilities of hypotheses \( Y_1 \) and \( Y_2 \).



##### Terminology

Latent Space
	Latent space refers to an abstract, often lower-dimensional space that captures the essential features and structure of the original data. It is a way to represent data in a compressed form, where each point in the latent space encodes significant information about the original data.

Statistical Learning
	Natural Data (High-D) actually lies in a low-D Space


Complexity of KNN
	training: O(1)
	testing: O(NM) (N: Images_Train, M: Images_Test)


Softmax
	For a given vector z = (z_1, z_2, …, z_n) , the softmax function  $$\sigma(\mathbf{z})$$  is defined as:
	
	 $$\sigma(z_i) = \frac{e^{z_i}}{\sum_{j=1}^{n} e^{z_j}}$$
CE-Loss
For a single data point, given the true label  y  (as a one-hot vector) and the predicted probability distribution  \hat{y}  (output of the softmax function), the cross-entropy loss  L  is defined as:

 $$L(y, \hat{y}) = -\sum_{i=1}^{n} y_i \log(\hat{y}_i) $$

Here,  y_i  is the true probability of class i (either 0 or 1), and  \hat{y}_i  is the predicted probability of class i.


Ex.
Suppose we have a neural network for classifying handwritten digits (0-9). For a given input image, the network outputs the following logits:

z = [2.0, 1.0, 0.1] 

Applying the softmax function:
$$
 \sigma(\mathbf{z}) = \left[ \frac{e^{2.0}}{e^{2.0} + e^{1.0} + e^{0.1}}, \frac{e^{1.0}}{e^{2.0} + e^{1.0} + e^{0.1}}, \frac{e^{0.1}}{e^{2.0} + e^{1.0} + e^{0.1}} \right] 

 
 \approx [0.659, 0.242, 0.099] 
$$
Now, suppose the true label for this image is the first class (represented as a one-hot vector [1, 0, 0]). The cross-entropy loss is calculated as:

$$
 L(y, \hat{y}) = -[1 \log(0.659) + 0 \log(0.242) + 0 \log(0.099)] 

 \approx -\log(0.659) \approx 0.417 
 $$

KL-Div

$$ D_{KL}(P \parallel Q) = \sum_{x} P(x) \log \left( \frac{P(x)}{Q(x)} \right) $$
1.	Non-Symmetry: KL divergence is not symmetric.  D_{KL}(P \parallel Q) \neq D_{KL}(Q \parallel P) . It measures the information lost when  Q  is used to approximate  P .
2.	Non-Negativity:  D_{KL}(P \parallel Q) \geq 0  for all distributions  P  and  Q . It is zero if and only if  P  and  Q  are identical almost everywhere.
3.	Information Gain: KL divergence can be interpreted as the expected amount of additional information required to encode samples from  P  using  Q  instead of the true distribution  P .


KL-Loss
- In VAEs, we have:
    - q(z|x) = N(μ, σ²): the encoder's output (approximate posterior)
    - p(z) = N(0, 1): the prior distribution (standard normal)
- The KL divergence between these distributions is: KL(q(z|x) || p(z)) = ∫ q(z|x) log(q(z|x) / p(z)) dz
- For multivariate Gaussian distributions, this has a closed-form solution: KL(N(μ, σ²) || N(0, 1)) = ½ ∑ᵢ (μᵢ² + σᵢ² - log(σᵢ²) - 1)
- In practice, we work with log(σ²) for numerical stability. Let's denote log(σ²) as λ: KL = ½ ∑ᵢ (μᵢ² + exp(λᵢ) - λᵢ - 1)
- Rearranging: KL = ½ ∑ᵢ (μᵢ² + exp(λᵢ) - (λᵢ + 1))
- Negating (for minimization during training): -KL = -½ ∑ᵢ (μᵢ² + exp(λᵢ) - (λᵢ + 1))
- Distributing the negative sign: -KL = ½ ∑ᵢ (-μᵢ² - exp(λᵢ) + λᵢ + 1)
- Final form: -KL = ½ ∑ᵢ (1 + λᵢ - μᵢ² - exp(λᵢ))

Almost Everywhere
	• **Measure Zero**: A set has measure zero if its “size” or “volume” is zero in the context of the given measure. For instance, in the real numbers with the usual Lebesgue measure, a single point has measure zero, and a countable set of points (like the rational numbers) also has measure zero.
	• **Almost Everywhere**: A property is said to hold almost everywhere if it holds for all points except for those in a set of measure zero.
	The function f(x) = 1/x is defined for all x \neq 0. It is undefined at x = 0. The set where the function is undefined (\{0\}) has Lebesgue measure zero. Therefore, we can say f(x) = 1/x is defined almost everywhere on \mathbb{R}.






##### Optimizers
Simple SGD
 $$\theta_{t+1} = \theta_t - \eta \nabla_{\theta} J(\theta_t) $$

Momentum Update
Momentum is a method that helps accelerate SGD in the **relevant direction and dampens oscillations**. It adds a fraction \gamma of the update vector of the past step to the current update vector:

 $$v_{t+1} = \gamma v_t + \eta \nabla_{\theta} J(\theta) $$

where:

v_t $ is the velocity vector at time step  t ,
$\gamma$  (often set to 0.9 or a similar value) is the momentum parameter,
 $\eta$ is the learning rate,
$\nabla_{\theta} J(\theta)$  is the gradient of the loss function  J  with respect to the parameters  \theta .

The parameters are then updated as:

 $$\theta_{t+1} = \theta_t - v_{t+1} $$
This allows the updates to **build up speed** in directions where gradients consistently point.



Nesterov Momentum

 $$\theta_{t+1} = \theta_t - v_{t+1} $$
where,
$$v_{t+1} = \gamma v_t + \eta \nabla_{\theta} J(\theta -  \gamma v_t) $$





RMSProp (Root Mean Square Propagation):

$$ v_t = \beta v_{t-1} + (1 - \beta) g_t^2 $$

$$ \theta_t = \theta_{t-1} - \frac{\eta}{\sqrt{v_t + \epsilon}} g_t $$

Where:

- $v_t$: Exponential moving average of squared gradients
- $\beta$: Decay rate (typically 0.9)
- $g_t$: Gradient at time step $t$
- $\theta_t$: Parameters at time step $t$
- $\eta$: Learning rate
- $\epsilon$: Small constant to avoid division by zero (typically 1e-8)

RMSProp adv:

=> Adaptive Learning Rate: since it uses a moving average of squared gradients to normalize, learning rate gets adjusted in a dynmical way. Not too small, not too large. It also handles sparse gradients well with the normalization.

Adam (Adaptive Moment Estimation):

$$ m_t = \beta_1 m_{t-1} + (1 - \beta_1) g_t $$

$$ v_t = \beta_2 v_{t-1} + (1 - \beta_2) g_t^2 $$

$$ \hat{m}_t = \frac{m_t}{1 - \beta_1^t} $$

$$ \hat{v}_t = \frac{v_t}{1 - \beta_2^t} $$

$$ \theta_t = \theta_{t-1} - \frac{\eta}{\sqrt{\hat{v}_t} + \epsilon} \hat{m}_t $$

Where:

- $m_t$: First moment estimate (mean of gradients)
- $v_t$: Second moment estimate (uncentered variance of gradients)
- $\beta_1$: Exponential decay rate for first moment estimate (typically 0.9)
- $\beta_2$: Exponential decay rate for second moment estimate (typically 0.999)
- $g_t$: Gradient at time step $t$
- $\theta_t$: Parameters at time step $t$
- $\hat{m}_t$: Bias-corrected first moment estimate
- $\hat{v}_t$: Bias-corrected second moment estimate
- $\eta$: Learning rate
- $\epsilon$: Small constant to avoid division by zero (typically 1e-8)
- $t$: Time step
  

Adam Adv.:

=> combines adv. of momentum and RMSProp., it adjusts the learning rate for each parameter based on the moving average of the squared gradients (like RMSProp) and incorporates a moving average of the gradients themselves (momentum)