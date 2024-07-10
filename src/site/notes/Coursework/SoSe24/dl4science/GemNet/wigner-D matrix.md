---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/wigner-d-matrix/","noteIcon":""}
---

---
diff. types of features when dealing with rot.
WD Matrices tell us how these types transform under rot.
irreducible repr. of group SO(3)

they can be decomposed into a block-diagonal form, basis functions (orthonormal subspaces of spherical harmonics) corr. to WD MAtrices
![Screenshot 2024-06-29 at 00.09.00.png](/img/user/Attachments/Screenshot%202024-06-29%20at%2000.09.00.png)

![Screenshot 2024-07-01 at 19.52.03.png](/img/user/Attachments/Screenshot%202024-07-01%20at%2019.52.03.png)
any function on SO(3) can be represented as a wieghted sum of wigner-d functions


Title: Wigner-D Matrices in 3D Rotational Equivariance

1. Definition:
    - Wigner-D matrices D^l(R) are representations of the rotation group SO(3)
    - They describe how spherical harmonics transform under 3D rotations
2. Key Properties:
    - Size: (2l+1) × (2l+1) matrices for each l
    - Unitary: D^l(R)^† D^l(R) = I
    - Composition: D^l(R1R2) = D^l(R1) D^l(R2)
3. Role in Equivariant Networks:
    - Enable rotation of feature vectors in a basis-independent way
    - Preserve equivariance in neural network layers
    - Allow for efficient computation of rotated filters
4. Practical Use:
    - Transform spherical harmonic coefficients under rotation
    - Crucial for maintaining rotational equivariance in 3D deep learning models
5. Advantage:
    - Eliminates need for data augmentation with rotations
    - Ensures consistent predictions regardless of 3D orientation

This concise overview highlights the essential aspects of Wigner-D matrices and their importance in rotationally equivariant neural networks, suitable for a presentation slide.


----
Example

![Screenshot 2024-07-06 at 18.41.48.png](/img/user/Attachments/Screenshot%202024-07-06%20at%2018.41.48.png)
### Conclusion

In this example, we've used the Wigner D-matrix implicitly through the rotation matrix \( R(\theta) \), which corresponds to \( D^{(1)}_{m'm}(\theta, 0, 0) \) for the spin-1 representation (vectors). The application of \( R(\theta) \) to the vector \( \vec{v} \) shows how the components of \( \vec{v} \) transform under the rotation by angle \( \theta \) around the z-axis. This demonstrates how Wigner matrices are used practically to transform vectors (and other tensors) under rotations in three-dimensional space.

----
How does this allow one to follow the rules of equivariance? 

f(R * ψ) = D^(l)(R) * f(ψ)

How do they do that? 
Overall, Wigner-D matrices provide the "rules" for how each basis function in the state vector transforms under a rotation. By combining these transformations, they ensure the entire state vector (and any function operating on it) transforms consistently, satisfying equivariance.