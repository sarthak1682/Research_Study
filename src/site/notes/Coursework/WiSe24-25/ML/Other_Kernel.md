---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/ml/other-kernel/","noteIcon":""}
---

---

## 2. Mercer's Theorem

Mercer's theorem provides the theoretical foundation for kernel methods by establishing when a function can be used as a valid kernel.

### Key Points:
1. A symmetric function k(xi, xj) = k(xj, xi) from L₂ can be expanded as:
   ```
   k(xi, xj) = Σ λₕφₕᵀ(xi)φₕ(xj)
   ```
   where:
   - λₕ > 0 are positive coefficients
   - φₕ are basis functions

2. Necessary and sufficient condition:
   ```
   ∫∫ k(xi, xj)g(xi)g(xj) dxidxj > 0
   ```
   for all g ≠ 0 where ∫ g²(xi)dxi < ∞

### Properties of Mercer Kernels:
- They are positive-definite kernels
- For kernel matrix K: aᵀKa > 0 for all vectors a ≠ 0
- All eigenvalues of the kernel matrix are positive
- Results extend to positive-semidefinite case

## 3. Common Kernel Types

### Linear Kernel:
```
k(xi, xj) = xiᵀxj
```
- Kernel matrix: K = XXᵀ
- X is the design matrix (N × M)

### Polynomial Kernels:
1. Type 1: k(xi, xj) = (xiᵀxj)ᵈ
   - Basis functions are ordered polynomials of order d
2. Type 2: k(xi, xj) = (xiᵀxj + R)ᵈ
   - Includes polynomials of order d or smaller
   - R is a tuning parameter

### Gaussian (RBF) Kernel:
```
k(xi, xj) = exp(-1/(2σ²)||xi - xj||²)
```
- Corresponds to infinitely many Gaussian basis functions
- Most widely used kernel in practice

### Sigmoid Kernel:
```
k(xi, xj) = sig(xiᵀxj)
```
- Also known as neural network kernel

## 4. Neural Tangent Kernel

For functions of the form:
```
f(xi) = φᵀ(xi)w
f(xj) = φᵀ(xj)w
```

The kernel can be written as:
```
k(xi, xj) = φ(xi)ᵀφ(xj) = (∂f(xi)/∂w)ᵀ(∂f(xj)/∂w)
```

This generalizes to nonlinear models like neural networks.

## 5. Valid Kernel Conditions

### Required Properties:
1. Symmetry: k(xi, xj) = k(xj, xi)
2. Functions of ||xi - xj|| are valid candidates
3. Functions of xiᵀxj are valid candidates

### Example of Invalid Kernel:
```
k(xi, xj) = xiᵀxj + α||xi||²
```
This violates the symmetry condition.

## 6. Representer Theorem

For a loss function minimization problem:
```
Σ loss(yi, f(xi)) + Ω(||f||φ)
```

Where:
- Ω is strictly monotonically increasing
- ||f||φ is a norm in reproducing kernel Hilbert space (RKHS)
- ||f||φ = √(f,f)φ includes ||f||φ = √wᵀw

The solution can be represented as:
```
f(xi) = Σ vik(xi, xj)
```

This theorem guarantees that kernel solutions exist for all considered cost functions in the optimization problem.