---
{"dg-publish":true,"permalink":"/zotero-storage/gcyvdt-6-p/tfn-notes/","noteIcon":""}
---

---
> [!PDF|] [[Thomas et al. - 2018 - Tensor field networks Rotation- and translation-e.pdf#page=1&selection=59,51,59,71|Thomas et al. - 2018 - Tensor field networks Rotation- and translation-e, p.1]]
>  locally equivariant

local? 


> [!PDF|] [[Thomas et al. - 2018 - Tensor field networks Rotation- and translation-e.pdf#page=2&selection=0,0,29,0|Thomas et al. - 2018 - Tensor field networks Rotation- and translation-e, p.2]]
> Equivariance confers three main benefits: First, this is more efficient than data augmentation to obtain 3D rotation-invariant output, making computation and training less expensive. This is significantly more important in 3D than in 2D: Without equivariant filters like those in our design, achieving an angular resolution of δ would require a factor of O(δ−1) more filters in 2D but O(δ−3) more filters in 3D.2 

- the scaling of the problem with angular resolution (δ).
    
- **2D:** Imagine rotating an image in 2D. To achieve an angular resolution of δ, you'd need to consider rotations in increments of δ. The number of possible rotations (and thus the number of filters you'd need in a non-equivariant approach) scales linearly with 1/δ, which is written as O(δ⁻¹). If you double the resolution (halve δ), you double the number of filters.
    
- **3D:** Now imagine rotating a 3D object. You have three axes of rotation to consider. The number of possible rotations scales with the cube of the inverse of the angular resolution, O(δ⁻³). This is a much faster increase. If you double the resolution (halve δ), you multiply the number of required filters by 2³ = 8!


---

# Theory

[[zotero_storage/GCYVDT6P/Group Representations and Equivariance in 3D\|Group Representations and Equivariance in 3D]]
