---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/hessian/","noteIcon":""}
---




A Hessian matrix is a square matrix of second-order partial derivatives of a scalar-valued function, or scalar field. It describes the local curvature of a function of many variables. Think of it as a multivariable version of the second derivative in single-variable calculus.

**Definition:**

For a function f(x₁, x₂, ..., xₙ) of n variables, the Hessian matrix **H** is an n x n matrix given by:

```
H =
| ∂²f/∂x₁²   ∂²f/∂x₁∂x₂ ... ∂²f/∂x₁∂xₙ |
| ∂²f/∂x₂∂x₁  ∂²f/∂x₂² ... ∂²f/∂x₂∂xₙ |
|  ...         ...       ...      ...  |
| ∂²f/∂xₙ∂x₁  ∂²f/∂xₙ∂x₂ ... ∂²f/∂xₙ²   |
```



Where:

- ∂²f/∂xᵢ∂xⱼ represents the second-order partial derivative of f with respect to xᵢ and xⱼ.
    

**Properties:**

- **Symmetry:** If the second-order partial derivatives are continuous, the Hessian matrix is symmetric, meaning ∂²f/∂xᵢ∂xⱼ = ∂²f/∂xⱼ∂xᵢ. This is due to Clairaut's theorem (equality of mixed partials).
    
- **Information about Curvature:** The eigenvalues of the Hessian matrix provide information about the curvature of the function at a given point.
    

**Uses of the Hessian:**

- **Optimization:** The Hessian plays a crucial role in optimizing functions of multiple variables.
    
    - **Finding Critical Points:** The first derivative (gradient) is set to zero to find critical points (potential maxima, minima, or saddle points).
        
    - **Classifying Critical Points:** The Hessian is evaluated at the critical points.
        
        - **Positive Definite Hessian (all eigenvalues positive):** The critical point is a local minimum. (Check only Det and Tr if there are only two variables involved.)
            
        - **Negative Definite Hessian (all eigenvalues negative):** The critical point is a local maximum.
            
        - **Indefinite Hessian (both positive and negative eigenvalues):** The critical point is a saddle point.
            
        - **Semi-definite Hessian (some eigenvalues are zero):** The test is inconclusive; further investigation is needed.


**Example:**

Let f(x, y) = x³ + y³ - 3xy.

The Hessian is:

```
H =
| 6x  -3 |
| -3  6y |
`
