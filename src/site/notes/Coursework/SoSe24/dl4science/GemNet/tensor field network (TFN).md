---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/tensor-field-network-tfn/","noteIcon":""}
---

---
Links: 
[openreview.net/pdf?id=6NFBvWlRXaG](https://openreview.net/pdf?id=6NFBvWlRXaG) Dym and Maron: Universality of TFN
[20181208\_tensorfieldnetworks\_neurips\_mol\_and\_mat.pdf](https://blondegeek.github.io/pdfs/20181208_tensorfieldnetworks_neurips_mol_and_mat.pdf): slides from Thomas et al. (OG Authors)
[Equivariant Neural Networks | Part 3/3 - Transformers and GNNs - YouTube](https://www.youtube.com/watch?v=RBKERHaiEKY&t=348s) from 05:48 to 13:08
[tensor-field-networks/tutorials/tutorial.ipynb at master · UPEIChemistry/tensor-field-networks · GitHub](https://github.com/UPEIChemistry/tensor-field-networks/blob/master/tutorials/tutorial.ipynb) tutorial
[[2006.10503] SE(3)-Transformers: 3D Roto-Translation Equivariant Attention Networks](https://arxiv.org/abs/2006.10503)

----


continous filters from SchNet and basis functions from harmonic nets: rotation eq. 
based on steerability (?)
inputs, outputs: N-Dim tensor fields

filters are made out of spherical harmonics


[[Coursework/SoSe24/dl4science/GemNet/tensors\|tensors]]

[[Coursework/SoSe24/dl4science/GemNet/spherical harmonics\|spherical harmonics]]

[[Coursework/SoSe24/dl4science/GemNet/wigner-D matrix\|wigner-D matrix]]

[[Coursework/SoSe24/dl4science/GemNet/SO(3)\|SO(3)]]
[[Coursework/SoSe24/dl4science/GemNet/repr. of SO(3)\|repr. of SO(3)]] (also SO(3) vs S2)

Can construct tensors based  on a combo of  SPherical harmonics and can know how to transform with WD Matrix


[[Coursework/SoSe24/dl4science/GemNet/CG Coeff\|CG Coeff]]

[[fibres\|fibres]]

full layer 

a is the centre point, b all other points in the point cloud


![Screenshot 2024-06-29 at 00.15.09.png](/img/user/Attachments/Screenshot%202024-06-29%20at%2000.15.09.png)


Summary:
1) continuous point conv. that takes all the point into account
2) filters are constrained to be learnable radial net combined with spherical harmonics
3) Tensor Alg. combines vectors


### Relevance to GemNet
In order to show the equivalence of the TFN to spherical representations, we first need to define this model.
Following Dym & Maron , we split the model into two parts: 
1) Embedding functions Ffeat that lifts the input into an equivariant representation, and 
2) pooling functions Fpool that aggregate the results of multiple embedding functions on each point and computes the model output.


![Screenshot 2024-06-28 at 22.15.34.png](/img/user/Attachments/Screenshot%202024-06-28%20at%2022.15.34.png)


![IMG_2B7D0F756321-1.jpeg](/img/user/Attachments/IMG_2B7D0F756321-1.jpeg)


Note: there aren't "multiple" embedding and pooling functions but 2 of them paired together f_pool^1, f_feat^1 etc. 

![Screenshot 2024-06-28 at 22.31.56.png](/img/user/Attachments/Screenshot%202024-06-28%20at%2022.31.56.png)
where D ∈ N denotes the function’s maximum polynomial degree, K(D) ∈ N is chosen such that Theorem 1 is fulfilled
	D is the degree of complexity, K(D) is how many pieces you need to put together to achieve that complexity.

	- **Degree DD**: Specifies the maximum polynomial degree. It defines how complex the function can be in terms of the highest power of the variables it includes. Higher DD means the function can model more complex relationships.
- **Function K(D)K(D)**: Ensures that there are enough components in the function space to accurately represent any polynomial of degree DD. It ensures the richness of the function space, allowing it to capture all necessary details for that degree.


#### Codomain WTnWTn​

- The codomain WTnWTn​ indicates that the output of the functions in G′G′ lies in a space that respects the symmetries of the SO(3)SO(3) group. This means that the output vectors or features are structured in a way that rotations of the input result in predictable changes to the output.


[[Coursework/SoSe24/dl4science/GemNet/repr. of SO(3)\|repr. of SO(3)]]

[[Coursework/SoSe24/dl4science/GemNet/FTFN pool\|FTFN pool]]

[[Coursework/SoSe24/dl4science/GemNet/Embedding Function\|Embedding Function]]

[[Coursework/SoSe24/dl4science/GemNet/The main Update\|The main Update]]
