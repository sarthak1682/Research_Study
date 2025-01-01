---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gradient/","noteIcon":""}
---



**Gradient:**

The gradient of a scalar-valued function (a function that outputs a single number) is a vector that points in the direction of the greatest rate of increase of the function at a specific point. Its magnitude represents the rate of increase in that direction. Think of it as the slope in multiple dimensions.

- **Definition:** For a function f(x₁, x₂, ..., xₙ), the gradient, denoted as ∇f or grad(f), is the vector:
    
    ```
    ∇f = (∂f/∂x₁, ∂f/∂x₂, ..., ∂f/∂xₙ)
    ```
    
    Use code [with caution](https://support.google.com/legal/answer/13505487).
    
    where ∂f/∂xᵢ represents the partial derivative of f with respect to xᵢ.
    
- **Properties:**
    
    - **Direction of Steepest Ascent:** The gradient points in the direction of the steepest ascent of the function. Moving in the opposite direction of the gradient leads to the steepest descent.
        
    - **Magnitude:** The magnitude of the gradient, ||∇f||, represents the rate of change of the function in the direction of the steepest ascent.
        
    - **Orthogonal to Level Curves/Surfaces:** The gradient is always perpendicular to the level curves (in 2D) or level surfaces (in 3D) of the function. Level curves/surfaces are sets of points where the function has a constant value.
        
- **Example:** If f(x, y) = x² + y², then ∇f = (2x, 2y). At the point (1, 1), the gradient is (2, 2), pointing in the direction of greatest increase of f.







