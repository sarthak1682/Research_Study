---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/similar-model-based-on-spherical-representations-in-the-case-of-rotationally-invariant-predictions/","noteIcon":""}
---

---
proof goes here. 

# Relationship between Spherical Harmonics and Clebsch-Gordan Coefficients

Equation 12 from the proof:

$$Y_{m_i}^{(l_i)}(\hat{r})Y_{m_f}^{(l_f)}(\hat{r}) = \sum_{l_o,m_o} \sqrt{\frac{(2l_i+1)(2l_f+1)}{4\pi(2l_o+1)}} C_{(l_f,0),(l_i,0)}^{(l_o,0)} C_{(l_f,m_f),(l_i,m_i)}^{(l_o,m_o)} Y_{m_o}^{(l_o)}(\hat{r})$$

## Key Components:

- $Y_{m}^{(l)}(\hat{r})$: Spherical harmonic function
- $C_{(l_f,m_f),(l_i,m_i)}^{(l_o,m_o)}$: Clebsch-Gordan coefficient

## Intuition:

This equation shows how to decompose the product of two spherical harmonics into a linear combination of other spherical harmonics. The Clebsch-Gordan coefficients determine the weights of this linear combination.

## Significance:

1. Angular Momentum Addition: Represents how angular momenta combine in quantum mechanics.
2. Rotational Symmetry: Preserves rotational invariance in calculations.
3. Basis Transformation: Allows conversion between coupled and uncoupled representations of angular momentum states.




---
# Detailed Derivation of Equation 14

Starting from the spherical harmonics expansion, we derive:

$$\tilde{H}'_a(X, H')(ˆr) = \sum_{l_o,m_o} \tilde{H}'^{(l_o)}_{am_o}(X, H') Y^{(l_o)}_{m_o}(ˆr)$$

## Step 1: Expansion of $\tilde{H}'^{(l_o)}_{am_o}(X, H')$

$$\tilde{H}'^{(l_o)}_{am_o}(X, H') = \theta H'^{(l_o)}_{am_o} + \sum_{l_f,m_f} \sum_{l_i,m_i} C(l_f, m_f, l_i, m_i, l_o, m_o) \sum_{b∈N_a} F'^{(l_f)}_{m_f}(x_{ba}) H'^{(l_i)}_{bm_i}$$

## Step 2: Substitution into the original equation

$$\tilde{H}'_a(X, H')(ˆr) = \sum_{l_o,m_o} \left(\theta H'^{(l_o)}_{am_o} + \sum_{l_f,m_f} \sum_{l_i,m_i} C(l_f, m_f, l_i, m_i, l_o, m_o) \sum_{b∈N_a} F'^{(l_f)}_{m_f}(x_{ba}) H'^{(l_i)}_{bm_i}\right) Y^{(l_o)}_{m_o}(ˆr)$$

## Step 3: Rearrangement of terms

$$\tilde{H}'_a(X, H')(ˆr) = \theta H'_a(ˆr) + \sum_{l_f,m_f} \sum_{l_i,m_i} \sum_{b∈N_a} F'^{(l_f)}_{m_f}(x_{ba}) H'^{(l_i)}_{bm_i} Y^{(l_f)}_{m_f}(ˆr) Y^{(l_i)}_{m_i}(ˆr)$$

## Step 4: Final form (Equation 14)

$$\tilde{H}'_a(X, H')(ˆr) = \theta H'_a(ˆr) + \sum_{b∈N_a} F'(x_{ba}, ˆr) H'_b(ˆr)$$

Where: $$F'(x, ˆr) = \sum_{l_f,m_f} F'^{(l_f)}_{m_f}(x) Y^{(l_f)}_{m_f}(ˆr)$$ $$H'_b(ˆr) = \sum_{l_i,m_i} H'^{(l_i)}_{bm_i} Y^{(l_i)}_{m_i}(ˆr)$$

---
# Detailed Derivation of Equations 15 and 16

Starting from Equation 14:

$$\tilde{H}'_a(X, H')(ˆr) = \theta H'_a(ˆr) + \sum_{b∈N_a} F'(x_{ba}, ˆr) H'_b(ˆr)$$

## Equation 15: Restricting to Real Components

1. Take the real part of both sides: $$\Re[\tilde{H}'_a(X, H')(ˆr)] = \Re[\theta H'_a(ˆr)] + \Re[\sum_{b∈N_a} F'(x_{ba}, ˆr) H'_b(ˆr)]$$
2. Distribute the real part over the sum: $$\Re[\tilde{H}'_a(X, H')(ˆr)] = \Re[\theta H'_a(ˆr)] + \sum_{b∈N_a} \Re[F'(x_{ba}, ˆr) H'_b(ˆr)]$$
3. Use the property of complex multiplication: $\Re[z_1z_2] = \Re[z_1]\Re[z_2] - \Im[z_1]\Im[z_2]$ $$\Re[\tilde{H}'_a(X, H')(ˆr)] = \theta\Re[H'_a(ˆr)] + \sum_{b∈N_a} (\Re[F'(x_{ba}, ˆr)]\Re[H'_b(ˆr)] - \Im[F'(x_{ba}, ˆr)]\Im[H'_b(ˆr)])$$

This is Equation 15.

## Equation 16: Transition to Real-Valued Spherical Representation

The authors argue that the function space covered by $\Re[F'(x, ˆr)]$ (and thus $\Re[H'(ˆr)]$) is the same as $\Im[F'(x, ˆr)]$ (and thus $\Im[H'(ˆr)]$). This allows them to remove the imaginary part without changing the resulting function space.

1. Define new real-valued functions: $$F^{sphere}(x, ˆr) = \Re[F'(x, ˆr)]$$ $$H^{sphere}(ˆr) = \Re[H'(ˆr)]$$
2. Substitute these into the equation: $$\tilde{H}^{sphere}_a(X, H)(ˆr) = \theta H^{sphere}_a(ˆr) + \sum_{b∈N_a} F^{sphere}(x_{ba}, ˆr) H^{sphere}_b(ˆr)$$

This is Equation 16.

## Key Points:

- The transition from complex to real functions doesn't change the expressiveness of the model.
- The resulting equation has the same structure as the original TFN, but uses only real-valued functions on the sphere.
- This demonstrates that the spherical representation can achieve the same expressiveness as the TFN using only real functions on S^2.



$$Y_l^m(\theta,\phi) = N_l^m P_l^m(\cos\theta) e^{im\phi}$$

- For m > 0: $Y_{l,m} = \frac{1}{\sqrt{2}}(Y_l^m + (-1)^m Y_l^{-m})$
- For m < 0: $Y_{l,m} = \frac{i}{\sqrt{2}}(Y_l^{-m} - (-1)^m Y_l^m)$
- For m = 0: $Y_{l,0} = Y_l^0$
