---
{"dg-publish":true,"permalink":"/coursework/so-se24/mof-ml/saddle-point/","noteIcon":""}
---



**Saddle Point:**

A saddle point is a critical point of a function where the function has a local maximum in one direction and a local minimum in another direction. It's like the center of a saddle on a horse, where you can go up in one direction and down in another.

- **Identifying Saddle Points:**
    
    1. **Find Critical Points:** Find the critical points by setting the gradient equal to zero: ∇f = **0**
        
    2. **Evaluate the Hessian:** Calculate the Hessian matrix (the matrix of second-order partial derivatives) at each critical point.
        
    3. **Check Eigenvalues:** Examine the eigenvalues of the Hessian. If the Hessian has both positive and negative eigenvalues, the critical point is a saddle point.
        
- **Intuition:** A positive eigenvalue indicates a concave-up shape in the corresponding eigenvector direction, while a negative eigenvalue indicates a concave-down shape. The presence of both indicates the saddle shape.
    
- **Example:** Consider f(x, y) = x² - y². The gradient is ∇f = (2x, -2y). The only critical point is (0, 0). The Hessian is:
    
    ```
    H =
    |  2   0 |
    |  0  -2 |
    ```
    
    
    
    The eigenvalues are 2 and -2. Since there's a positive and a negative eigenvalue, the point (0, 0) is a saddle point.