---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/ml/math-kernel/","noteIcon":""}
---

---
# Mathematical Derivation of Kernel Methods

## Key Terms and Notation

- **y**: Vector of target values (labels) where yi is the i-th observation
- **w**: Vector of weights for the basis functions
- **x**: Input vector where xi is the i-th input data point
- **φj(x)**: The j-th basis function applied to input x
- **Φ**: Design matrix where (Φ)i,j = φj(xi)
- **λ**: Regularization parameter (controls the trade-off between fit and complexity)
- **N**: Number of data points
- **M𝜙**: Number of basis functions
- **K**: Kernel matrix where Ki,j = k(xi, xj)
- **v**: Dual weights vector (coefficients in the kernel representation)

## 1. The Regularized Cost Function

### Original Form
The penalized least squares cost function combines the error term and regularization:

```
cost^pen(w) = Σ(yi - Σwjφj(xi))² + λΣwj²
             i=1..N    j=1..M𝜙      j=1..M𝜙
```

### Matrix Form
```
cost^pen(w) = (y - Φw)ᵀ(y - Φw) + λwᵀw
```

This form has two components:
1. Data fit term: (y - Φw)ᵀ(y - Φw)
2. Regularization term: λwᵀw

## 2. Finding the Minimum: Implicit Solution

### Take the Derivative
```
∂cost^pen(w)/∂w = -2Φᵀ(y - Φw) + 2λw = 0
```

### Solve for w
```
Φᵀ(y - Φw) = λw
Φᵀy - ΦᵀΦw = λw
Φᵀy = (ΦᵀΦ + λI)w
```

### Implicit Solution
```
wpen = (1/λ)Φᵀ(y - Φwpen)
```

## 3. The Kernel Transformation

### Key Insight
The solution can be written as a linear combination of transformed input vectors:
```
wpen = Φᵀv = Σvi𝜙(xi)
      i=1..N
```

Where v = (v1, ..., vN)ᵀ are the new coefficients.

### Prediction Function
```
f(x') = 𝜙(x')ᵀwpen 
      = 𝜙(x')ᵀΦᵀv 
      = Σvik(xi,x')
       i=1..N
```

Where k(xi,x') = 𝜙(xi)ᵀ𝜙(x') is the kernel function.

## 4. Kernel Form of Cost Function

### Substituting the Kernel Representation
```
cost^pen(v) = (y - ΦΦᵀv)ᵀ(y - ΦΦᵀv) + λvᵀΦΦᵀv
            = (y - Kv)ᵀ(y - Kv) + λvᵀKv
```

Where K = ΦΦᵀ is the kernel matrix with elements ki,i' = k(xi,xi')

### Explicit Form
```
cost^pen(v) = Σ(yi - Σvi'k(xi,xi'))² + λΣΣvivi'k(xi,xi')
             i=1    i'=1               i=1 i'=1
```

## 5. Final Solution

### Take Derivative with Respect to v
```
∂cost^pen(v)/∂v = 2K(Kv - y) + 2λKv = 0
```

### Solve for v (assuming K is full rank)
```
K(Kv - y) + λKv = 0
K(Kv + λv - y) = 0
Kv + λv = y
(K + λI)v = y
```

### Final Solution
```
vpen = (K + λI)⁻¹y
```

## Important Properties

1. The solution depends only on dot products of basis functions (kernels), not the basis functions themselves.
2. The final predictor is a weighted sum of N kernels.
3. Not all functions expressible as Σwjφj(x') can be written in kernel form - only those that minimize the cost function for the specific training data.
4. The kernel matrix K must be positive semi-definite.
5. The regularization parameter λ ensures numerical stability and prevents overfitting.

## Computational Advantage

The kernel method allows us to:
1. Work with potentially infinite-dimensional feature spaces
2. Avoid explicit computation of basis functions
3. Operate in the dual space with N variables instead of M𝜙 variables
4. Compute predictions using only kernel evaluations

This makes kernel methods particularly powerful for problems where the feature space is very high-dimensional or even infinite-dimensional, while keeping computations tractable.