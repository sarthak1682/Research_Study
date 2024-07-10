---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/cg-coeff/","noteIcon":""}
---

---
calc. products of the composed tensors (fibers),
define multiplication rules for diff. tensor types



![Screenshot 2024-06-29 at 00.11.53.png](/img/user/Attachments/Screenshot%202024-06-29%20at%2000.11.53.png)

combo of spherical harmonics used to build a vector


Wiki:
the CG coefficients are used in [representation theory](https://en.wikipedia.org/wiki/Representation_theory "Representation theory"), particularly of [compact Lie groups](https://en.wikipedia.org/wiki/Compact_Lie_group "Compact Lie group"), to perform the explicit [direct sum](https://en.wikipedia.org/wiki/Direct_sum_of_representations "Direct sum of representations") decomposition of the [tensor product](https://en.wikipedia.org/wiki/Tensor_product_of_representations "Tensor product of representations") of two [irreducible representations](https://en.wikipedia.org/wiki/Irreducible_representation "Irreducible representation") (i.e., a reducible representation into irreducible representations, in cases where the numbers and types of irreducible components are already known abstractly)


---
claude
## 1. Spherical Harmonics

We begin with spherical harmonics, denoted as $Y_l^m(\theta, \phi)$, where:

- $l$ is the degree (0, 1, 2, ...)
- $m$ is the order (-l, -l+1, ..., l-1, l)

These form an orthonormal basis for functions on the sphere and transform in a well-defined way under rotations.

## 2. Equivariant Kernel

An equivariant convolution kernel $K(r)$ can be expressed as a linear combination of spherical harmonics:

$$K(r) = \sum_{l=0}^{L} \sum_{m=-l}^{l} w_{lm} R_l(r) Y_l^m(\theta, \phi)$$

where:

- $R_l(r)$ are radial functions
- $w_{lm}$ are learnable weights

## 3. Tensor Product

When we need to combine two spherical tensor fields, we use the tensor product. For two spherical harmonics $Y_{l_1}^{m_1}$ and $Y_{l_2}^{m_2}$, their tensor product can be expressed as:

$$(Y_{l_1} \otimes Y_{l_2})_{m_1m_2} = \sum_{L=|l_1-l_2|}^{l_1+l_2} \sum_{M=-L}^{L} C(l_1,l_2,L; m_1,m_2,M) Y_L^M$$

Here, $C(l_1,l_2,L; m_1,m_2,M)$ are the Clebsch-Gordon coefficients.

## 4. Clebsch-Gordon Coefficients

The Clebsch-Gordon coefficients are given by the following formula:

$$C(l_1,l_2,L; m_1,m_2,M) = \delta_{m_1+m_2,M} \sqrt{\frac{(2L+1)(L+l_1-l_2)!(L-l_1+l_2)!(l_1+l_2-L)!}{(l_1+l_2+L+1)!}} \times$$

$$\sum_k \frac{(-1)^k(L+M)!(l_1-m_1)!(l_2+m_2)!}{k!(L-l_1+l_2-k)!(l_1-m_1-k)!(l_2+m_2-k)!(L+M-k)!}$$

where the sum is over all $k$ such that the factorial arguments are non-negative.

## 5. Equivariant Convolution

The equivariant convolution operation can be written as:

$$[f * K](x) = \int f(y) K(x-y) dy$$

where $f$ is the input function and $K$ is our equivariant kernel.



is it like fourier? 
Let's explore this connection:

1. Fourier Analysis:
    - In Fourier analysis, we decompose a complex signal into a sum of simpler sinusoidal components.
    - Each sinusoidal component has a specific frequency, and the Fourier coefficients tell us how much of each frequency is present in the original signal.
2. Spherical Harmonics and Clebsch-Gordon:
    - Spherical harmonics are essentially the "Fourier series" on a sphere.
    - When we combine (take the tensor product of) two spherical harmonics, the result can be expressed as a sum of other spherical harmonics.
    - The Clebsch-Gordon coefficients tell us how much of each resulting spherical harmonic is present in this combination.

Key Similarities:

1. Decomposition: Both methods involve breaking down complex patterns into simpler, fundamental components.
2. Basis Functions: Sinusoids in Fourier analysis; spherical harmonics for Clebsch-Gordon.
3. Coefficients: Fourier coefficients and Clebsch-Gordon coefficients both indicate the "amount" of each basis function present.

Key Differences:

1. Dimensionality: Fourier analysis is typically applied to 1D or 2D signals, while spherical harmonics deal with functions on a sphere (3D).
2. Group Structure: Clebsch-Gordon coefficients are deeply connected to the rotation group SO(3), while Fourier analysis is related to simpler translation groups.![Screenshot 2024-07-02 at 00.13.13.png](/img/user/Attachments/Screenshot%202024-07-02%20at%2000.13.13.png)