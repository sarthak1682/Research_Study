---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/pin-ns-by-raissi-et-al/","noteIcon":""}
---

---
[Physics-Informed Neural Networks (PINNs) - An Introduction - Ben Moseley | Jousef Murad - YouTube](https://www.youtube.com/watch?v=G_hIppUWcsc): the best video explaining it, steve brunton's deals with a lot of different offshoots. 




Q- Are all in form of PDEs?
Q- Incompressible Fluid? 
Q- Non Linear Problems?
Q- 

Raw outline
#### Abs.

part1: solution (data efficient spatio-temporal function approx.) (Inference, filtering, and smoothing)
"given fixed model parameters λ what can be said about the unknown hidden state u(t, x) of the system?"
part2: discovery of equations (arbitrarily accurate [[Coursework/SoSe24/dl4science/Runge-Kutta time stepping schemes\|Runge-Kutta time stepping schemes]])
(learning, system id)
"what are the parameters λ that best describe the observed data?"


continuous time and discrete time models

small amount of data 

#### Problem Setup

diff. a NN wrt to their input co-ords and model params to get PINNs

basic arch, with tanh, no added reg tech (in fact 5 layer 100 Width) (except what the MSE_f error term does)


they consider parametrized and nonlieanr PDEs of the general form: 
$$ u_{t} + N[u;\lambda] = 0,   x \in \Omega \subset \mathbb R^D, t \in [0,T] $$

u(t, x) denotes the latent (hidden) solution

#### Solutions to PDEs

#####  Cont. time models. 
[[Coursework/SoSe24/dl4science/Boundary Conditions\|Boundary Conditions]]
f = u_t + N[u]: is the PINN: f(t,x)
loss function: intial, boundary conditions loss + physics loss

collocation points: : Collocation points are discrete points {xi} in the domain where the differential equation is enforced to hold true

optimize all loss functions using L-BFGS, a quasi-Newton, full-batch gradient-based optimization algorithm: full-batch since at most thousands of points


"if the given partial differential equation is well-posed and its solution is unique, our method is capable of achieving good prediction accuracy given a sufficiently expressive neural network architecture and a sufficient number of collocation points N f . This general observation deeply relates to the **resulting optimization landscape induced by the mean square error loss of equation** (4), and defines an open question for research that is in sync with recent theoretical developments in deep learning" : identify the assumptions. 

iψt​+21​ψxx​+∣ψ∣2ψ=0
\
go back to p.689 last para

Latin hypercube sampling


L2-Norm of the error being: 1.97x10^-3


limitations
higher D problem coz a lot of Nf collocation points : increase exp.

[[Coursework/SoSe24/dl4science/Runge-Kutta time stepping schemes\|Runge-Kutta time stepping schemes]]


##### discrete time models

it is only the number of parameters in the last layer of the neural network that increases linearly with the total number of stages

physics-informed neural network with 4 hidden layers and 200 neurons per layer, with 100 intermediate stages predict even the almost discontinuous solution
from t = 0.1 to 0.9 sec in a single time step with an
L2 error of 6.99 · 10−3 without sacrificing numerical stability, which are novel.


#### Discovering PDEs

#####  Cont. time models. 
Navier-Stokes in 2D

we are interested in learning the parameters λ as well as the pressure p(t, x, y)

N = 5,000

The predictions remain robust even when the training data are corrupted with 1% uncorrelated Gaussian noise, returning an error of 0.17%, and 5.70%, for λ1 and λ2, **only report the one with noisy data**
)
ntriguing result stems from the network’s ability to provide a qualitatively accurate prediction of the entire pressure field

##### discrete time models
data-driven discovery problem using only two data snapshots



### Summary to be submitted



PINNs leverage the end-to-end differentiability of the neural network, namely by differentiating them wrt to their input co-ordinates and model parameters.  The paper is divided in mainly two parts. The former deals with learning solutions given parameters and the latter with learning parameters given data. Authors put forward continuous time models for each, identify a shortcoming and propose discrete time model for the problems. 

In the first part, the shared parameters of the PINN and the (differentiated) neural net are learned by minimising two MSE Terms, first of which forces initial and boundary conditions, second represents the physical loss (for a finite number of collocation points, sampled through a Latin Hypercube Strategy.) They optimize on the entire batch, since it is at most a few thousand points. Schrodinger's Equation is the example given. They identify that the number of collocation points needed will grow exponentially with the dimensions of the equation, which is circumvented by discrete time models leveraging the Runge-Kutta time-stepping schemes.The apparent advantage of this method is the low cost that a single layer of NN is added due to the q Runge-Kutta stages. The PINN predicts the solution of the Allen-Cahn's Equation without sacrificing numerical stability with very low L2 error, which is one of the novel results of the paper. The fact that they use a normal feedforward NN with tanh activation throughout the experiments makes it even more noteworthy. No extra regularisation is added other than what the physical loss enforces. 

The second part is structurally similar to the first one, the PINN attempts to predict parameters of the infamous Navier-Stokes' Equations. They test it on (artificially) corrupt data and prove their robustness by getting an error of 0.17%, and 5.70%, for λ1 and λ2 respectively. Discrete time models in this part try to learn parameters of PDEs by using only two data snapshots, and predict parameters of KdV equation with 0.057%, and 0.017% errors on noisy training data, respectively. 

This appears to be a quite well thought-out paper on the first glimpse, perhaps further theoretical inquiry will shed light on the important questions that the authors themselves raise. I would love to have the question about the quantity of data needed clarified in this setting. 