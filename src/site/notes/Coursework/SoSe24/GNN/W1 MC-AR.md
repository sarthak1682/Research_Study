---
{"dg-publish":true,"permalink":"/coursework/so-se24/gnn/w1-mc-ar/","noteIcon":""}
---

---
## Markov Chains

**Markov Chain Definition:**
- Sequence of random variables: $X_1, X_2, ..., X_n$
- Markov property: $P(X_t|X_1,...,X_{t-1}) = P(X_t|X_{t-1})$
	- $t$, and (RV) $X_t$ are discrete
**Joint Distribution:**
$P(X_1=i_1,...,X_n=i_n) = P(X_1=i_1) \prod_{t=2}^n P(X_t=i_t|X_{t-1}=i_{t-1})$

**General Case:** 
**Transition Matrix:**
$A_{ij}^{t+1} = P(X_{t+1}=j|X_t=i)$

**Joint Probability for the General Case:**
$P(X_1=i_1,...,X_n=i_n) = \pi_{i_1} \times A_{i_1,i_2}^{(2)} \times ... \times A_{i_{n-1},i_n}^{(T)}$

![Screenshot 2024-09-21 at 13.06.59.png](/img/user/Attachments/Screenshot%202024-09-21%20at%2013.06.59.png)

Parameters: (K-1) + (T-1)K(K-1)

**Stationary Markov Chain:**
$P(X_1=i) = \\pi_i$ and $P(X_{t+1}=j|X_t=i) = A_{ij}$

**Transition Matrix:**
$A_{ij} = P(X_{t+1}=j|X_t=i)$

**Joint Probability for Stationary Case:**
$P(X_1=i_1,...,X_n=i_n) = \pi_{i_1} \times A_{i_1,i_2} \times ... \times A_{i_{n-1},i_n}$

Parameters: (K-1) + K(K-1)

![Screenshot 2024-09-21 at 13.12.33.png](/img/user/Attachments/Screenshot%202024-09-21%20at%2013.12.33.png)




Random Walk: 

Time Homogeneous discrete MCs = State Machines

Ex:
![Screenshot 2024-09-21 at 13.15.05.png](/img/user/Attachments/Screenshot%202024-09-21%20at%2013.15.05.png)




$\textbf{Task 1: Determine: } A_{ij}(n) = \mathbb{P}(X_{t+n} = j | X_t = i)$
	$\text{In words, } A_{ij}(n) = \text{probability of getting from state } i \text{ to state } j \text{ in } n \text{ steps.}$

$\text{How to compute } A_{ij}(n)?$

$$A_{ij}(n) = \mathbb{P}(X_{t+n} = j | X_t = i)
= \sum_{k=1}^{K} \mathbb{P}(X_{t+n} = j, X_{t+n-1} = k | X_t = i)
= \sum_{k=1}^{K} \mathbb{P}(X_{t+n} = j | X_{t+n-1} = k, X_t = i) \mathbb{P}(X_{t+n-1} = k | X_t = i)
$$

$\text{Therefore:  } A_{ij}(n) = \sum_{k=1}^{K} A_{kj} A_{ik}(n-1)$



$\textbf{Task 2: Determine: } \pi_j(t) = \mathbb{P}(X_t = j)$

$\text{In words, } \pi_j(t) = \text{probability of reaching state } j \text{ in step } t.$

$\text{How to compute } \pi_j(t)?$

$$
\mathbb{P}(X_t = j) = \sum_{i=1}^{K} \mathbb{P}(X_t = j | X_{t-1} = i) \mathbb{P}(X_{t-1} = i)
= \sum_{i=1}^{K} A_{ij} \pi_i(t-1)

\Rightarrow \pi(t) = \pi(t-1) A

\Rightarrow \pi(t) = \pi A^{(t-1)}
$$ 
$\text{where } \pi(t) \text{ and } \pi \text{ are row vectors.}$



## AR Models

**AR Model Definition:**
$X_t = c + \sum_{i=1}^p \phi_i X_{t-i} + \varepsilon_t$

Where:
- $\phi_1, ..., \phi_p$ are the parameters
- $c$ is a constant
- $\varepsilon_t \sim N(0, \sigma)$ is white noise
- $X_{t-i}$ is the lagged value at time $i$
- Variables are not independent

**Mean Function:**
$\mu(t) = E[X_t]$

**Autocovariance:**
$\gamma(t,i) = Cov(X_t, X_{t+i})$

The autocorrelation function, also known as the Pearson autocorrelation function, is a normalized version of the autocovariance function.

• denoted as $\rho(t,i) = \frac{\text{cov}(X_t, X_{t+i})}{\sqrt{\text{var}(X_t) \cdot \text{var}(X_{t+i})}}$
• values range between -1 and 1
• serves as an indicator of the dependence of the variable Xt on past variables (Xt-1, Xt-2, etc.)


**Probability Distribution:**
$P(X_t|X_{t-1}, ... X_{t-p}) \sim N(c + \sum_{i=1}^p \phi_i X_{t-i}, \sigma)$


![C7B071D8-926C-43C6-82A9-8C056CA6CB61.jpeg](/img/user/Attachments/C7B071D8-926C-43C6-82A9-8C056CA6CB61.jpeg)



### Param Learning

Least-Sq Regression
![Screenshot 2024-09-21 at 14.49.19.png](/img/user/Attachments/Screenshot%202024-09-21%20at%2014.49.19.png)


### Stationarity

1. $E X_t = E X_{t-i} = \mu, \forall t, \forall i$
2. $Cov(X_t, X_{t-i}) = \gamma_i, \forall t, \forall i$
3. $E|X_t|^2 < \infty, \forall t$

These conditions ensure that:
- The mean function $E(X_t)$ is constant
- The autocovariance $Cov(X_t, X_{t+i})$ only depends on the lagged value at time $i$, not on $t$
- The process has finite variance

The benefits of stationarity in time series analysis:

• It is often a good modelling assumption (similar to the i.i.d. assumption)
• For stationary processes, it's possible to estimate mean and autocovariance by averaging measures over time
• Parameters learned from past observations will generalize to future observations


#### Yule-Walker Eq

The Yule-Walker equations relate the AR model parameters $\phi_1, \dots, \phi_p$ to the autocovariances or autocorrelations of the time series. These equations are derived from the assumption that the series is **stationary** and use the autocovariances $\gamma_k = \text{Cov}(x_t, x_{t-k})$.

![Screenshot 2024-09-21 at 15.06.28.png](/img/user/Attachments/Screenshot%202024-09-21%20at%2015.06.28.png)


Thus, solving this system yields the AR model parameters $\phi_1, \dots, \phi_p$.


The 3 steps to solve the Yule-Walker equations for variance are:

1. **Estimate the moments** γ₀, γ₁, ..., γₚ
2. **Inverse Yule-Walker matrix** to estimate φ₁, ..., φₚ
3. **Use γ₀ equation** to estimate σ²
