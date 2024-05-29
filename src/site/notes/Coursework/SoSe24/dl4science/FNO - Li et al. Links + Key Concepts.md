---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/fno-li-et-al-links-key-concepts/","noteIcon":""}
---

---
[Zongyi Li | Fourier Neural Operator](https://zongyi-li.github.io/blog/2020/fourier-pde/): Intro by Author
[Neural Operator](https://zongyi-li.github.io/neural-operator/): General Intro into Neural Operators by the Author
[neuraloperator/fourier\_3d.py at master · neuraloperator/neuraloperator · GitHub](https://github.com/neuraloperator/neuraloperator/blob/master/fourier_3d.py) : Code
[[2010.08895] Fourier Neural Operator for Parametric Partial Differential Equations](https://arxiv.org/abs/2010.08895): Paper
[Fourier Neural Operator for Parametric Partial Differential Equations (Paper Explained) - YouTube](https://www.youtube.com/watch?v=IaS72aHrJKE): Kilcher Video (Explanation)

---
### Summary
Li et al. introduce the Fourier Neural Operator, which is efficient (quasi-linear complexity), invariant to discretization and (more) accurate at the same time. The architectures comprises of multiple fourier layers, where the convolution is implemented by applying a fourier transform, a linear transform on the lower fourier modes R, and an inverse fourier. 
They experiment with Burgers’ equation, Darcy flow, and Navier-Stokes equation and show that their method has significantly lower error rates for all three experiments. 


### Intro: Key Concepts
[[Mesh\|Mesh]]: Grid (can be fine or coarse in the traditional numerical Solvers)
[[Coursework/SoSe24/dl4science/Operator vs Function\|Operator vs Function]]
[[Coursework/SoSe24/dl4science/Boundary Conditions\|Boundary Conditions]]
[[Coursework/SoSe24/dl4science/Parametrising Something (e.g the Model or Function)\|Parametrising Something (e.g the Model or Function)]]
[[Function Space\|Function Space]] : Just like Input/Output Space, nothing special
[[Coursework/SoSe24/dl4science/Kernel Function\|Kernel Function]] 
[[Coursework/SoSe24/dl4science/Fourier Space\|Fourier Space]]
[[Coursework/SoSe24/dl4science/Local vs Global Convolution\|Local vs Global Convolution]]
[[Coursework/SoSe24/dl4science/Burgers Equation\|Burgers Equation]]
[[Coursework/SoSe24/dl4science/Navier Stokes Equation\|Navier Stokes Equation]]
[[Coursework/SoSe24/dl4science/Bayesian Inverse Problem\|Bayesian Inverse Problem]]


### General Intro: Key Concepts

### Paper: Key Concepts


### Other Key Concepts

[[Hamiltonian\|Hamiltonian]]
[[Hessian\|Hessian]]
[[Coursework/SoSe24/dl4science/Dirichlet Boundary\|Dirichlet Boundary]]
[[Coursework/SoSe24/dl4science/Convolution Theorem\|Convolution Theorem]]
[[Fast Fourier Transform (FFT)\|Fast Fourier Transform (FFT)]]
[[MCMC\|MCMC]]
[[ResNet\|ResNet]]

Q Slide 15: Why would we not want dependency on initial condition? 
Q Slide 19: "Cutting off the top Nodes" : But do they not say they can recover it?  "The activation functions help to recover the Higher frequency modes and non-periodic boundary which are left out in the Fourier layers."


### Questions

Do you need all of this if Fourier Transform is doing all the heavy lifting? 
