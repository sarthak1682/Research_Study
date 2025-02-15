---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/ml/manifold/","noteIcon":""}
---

---
A manifold is essentially a geometric structure that locally looks like a flat Euclidean space (think of a surface that's smooth enough to appear flat when you zoom in really close), but globally might be curved or twisted. Here are some intuitive examples:

1. A sheet of paper:

- While it exists in 3D space, it's intrinsically 2-dimensional
- When flat, it's a linear subspace
- When curved (like rolled or crumpled), it becomes a nonlinear manifold
- But locally, you can still "flatten" any small piece of it

2. The surface of Earth:

- While we need 3D coordinates to describe points on it
- It's actually a 2D manifold (you only need latitude and longitude)
- Locally appears flat (which is why local maps work)
- Globally is curved (nonlinear)

The relationship with nonlinear subspaces:

- A linear subspace is like a flat sheet: it's the simplest type of manifold
- A nonlinear subspace (manifold) is like a curved sheet: it can bend and twist through the higher-dimensional space
- Both restrict where data points can lie, but:
    - Linear subspaces restrict points to flat surfaces
    - Manifolds allow points to lie on curved surfaces

In machine learning:

- Real data often lies on manifolds rather than linear subspaces
- Example: face images
    - Live in high-dimensional pixel space
    - But variations between faces follow smooth, nonlinear patterns
    - You can't get valid face images by linear combinations of pixel values
    - But you can get them by moving along the "face manifold"


---
A little more math

1. Topological Manifold:

- An n-dimensional topological manifold M is a topological space that is:
    - Hausdorff (distinct points have disjoint neighborhoods)
    - Second countable (has a countable base)
    - Locally homeomorphic to ℝⁿ (every point has a neighborhood that can be continuously and bijectively mapped to an open subset of ℝⁿ)

2. Charts and Atlases:

- A chart (U,φ) consists of:
    - U: an open subset of M
    - φ: a homeomorphism from U to an open subset of ℝⁿ
    - φ is called a coordinate system or local parameterization
- An atlas is a collection of charts that cover the entire manifold

3. Smooth (Differentiable) Manifold:

- When charts overlap (U₁∩U₂ ≠ ∅), we have transition maps:
    - φ₂∘φ₁⁻¹: φ₁(U₁∩U₂) → φ₂(U₁∩U₂)
- If all transition maps are C^k (k times differentiable), we have a C^k manifold
- If k = ∞, we have a smooth manifold

4. Tangent Space:

- At each point p ∈ M, there's a tangent space T_p M
- T_p M is a vector space that best approximates M near p
- Dimension of T_p M equals the dimension of the manifold

5. Riemannian Manifold:

- A smooth manifold with a Riemannian metric g
- g assigns an inner product to each tangent space
- Allows measurement of distances and angles on the manifold

In machine learning context:

- Data manifold hypothesis: high-dimensional data often lies near a lower-dimensional manifold
- The dimension of the manifold (n) is much smaller than the ambient space dimension
- Learning tasks involve:
    - Discovering the manifold structure
    - Finding efficient representations in the lower-dimensional space
    - Making predictions that respect the manifold geometry