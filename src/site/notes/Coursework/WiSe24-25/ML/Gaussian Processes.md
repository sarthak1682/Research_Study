---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/ml/gaussian-processes/","noteIcon":""}
---

---
# Understanding Gaussian Processes: From Prior to Prediction

## Key Mathematical Terms and Notation

- **w**: Weight vector for basis functions
- **φ(x)**: Basis function vector
- **N(0,I)**: Normal distribution with zero mean and unit covariance
- **k(x,x')**: Kernel function (covariance function) between inputs x and x'
- **Σ**: Covariance matrix
- **μp(x)**: Posterior mean function
- **kp(x,x')**: Posterior covariance function
- **vpen**: Penalized version of weights (K⁻¹y)
- **K**: Kernel matrix
- **σ²**: Noise variance

## 1. Prior Distribution

### Prior Mean Function
The Gaussian Process starts with defining a prior distribution over functions. Key characteristics:

1. The prior distribution of basis function weights (w) follows:
   - Zero mean
   - Unit covariance
   - Mathematically expressed as: w ~ N(0,I)

2. The prior mean function is zero everywhere:
   - E[φ(x)] × 0 = 0
   - This represents our initial state of uncertainty about the function

### Prior Covariance

The covariance matrix between functional values at two input points (x₁, x₂) is given by:

```
Σ(f(x₁),f(x₂)) = [ k(x₁,x₁)  k(x₁,x₂) ]
                  [ k(x₂,x₁)  k(x₂,x₂) ]
```

Where:
- k(x₁,x₂) represents the kernel function evaluating covariance between points x₁ and x₂
- Special case: var_prior(f(x₁)) = k(x₁,x₁)

## 2. Prediction

### Mean Prediction
The posterior mean prediction at a point x is calculated as:

```
μp(x) = Σᵢ₌₁ᴺ vᵢᵖᵉⁿk(xᵢ,x)
```

Where:
- vᵖᵉⁿ = K⁻¹y (assuming zero noise in measurements)
- N is the number of training points
- k(xᵢ,x) is the kernel value between the prediction point and training point i

### Uncertainty in Prediction

The posterior covariance kernel becomes:
```
kp(x₁,x₂) = k(x₁,x₂) - kᵀ(x₁)K⁻¹k(x₂)
```

Special case for variance:
```
var_post(f(x₁')) = var_prior(f(x₁')) - kᵀ(x₁')K⁻¹k(x₁')
```

For noisy measurements, modify K:
- K ← K + σ²I
- Where σ² is the noise variance

## 3. Practical Considerations and Limitations

### Strengths
1. Works well with data on low-dimensional manifolds
2. Provides uncertainty estimates in predictions
3. "Knows when it doesn't know" - explicit uncertainty quantification
4. Useful in safety-critical applications (e.g., robotics)

### Dilemma and Limitations

1. **Bandwidth-Complexity Trade-off**:
   - Complex functions (high bandwidth) require many fixed basis functions
   - Gaussian kernel should have small width for complex functions
   - Small kernel width leads to near-zero predictions for test points different from training data
   
2. **Data Requirements**:
   - Needs large training datasets for complex functions
   - Kernel models don't handle large datasets efficiently

3. **Practical Compromise**:
   - Often must assume low bandwidth functions
   - Use larger kernel width
   - This reduces to simpler cases (I/III) which may not capture complex patterns

## 1. Computational Complexity

The computational efficiency of kernel methods depends on the relationship between N (number of data points) and Mφ (dimensionality of feature space):

### When N >> Mφ:
- Working with basis functions is more efficient
- Computational cost: O(Mφ³ + Mφ²N) operations
  
### When Mφ >> N:
- Kernel version is more efficient
- Computational cost: O(N³ + N²Mφ) operations
- For known a priori kernels: O(N³) operations

### Best Practices for Implementation

1. **Kernel Selection**:
   - Choose based on expected function smoothness
   - Consider computational constraints
   - Balance between expressiveness and overfitting

2. **Noise Handling**:
   - Always include noise term (σ²I) in real applications
   - Tune noise parameter based on data quality

3. **Scalability Considerations**:
   - Consider sparse approximations for large datasets
   - Use structured kernels when possible
   - Balance computational cost with model accuracy
