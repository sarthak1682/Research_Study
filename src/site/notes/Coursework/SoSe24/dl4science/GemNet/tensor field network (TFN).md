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



continous filters from SchNet and basis functions from harmonic nets: rotation eq. 
based on steerability (?)
inputs, outputs: N-Dim tensor fields


[[Coursework/SoSe24/dl4science/GemNet/tensors\|tensors]]

[[Coursework/SoSe24/dl4science/GemNet/spherical harmonics\|spherical harmonics]]

[[Coursework/SoSe24/dl4science/GemNet/wigner-D matrix\|wigner-D matrix]]

Can construct tensors based  on a combo of  SPherical harmonics and can know how to transform with WD Matrix


[[Coursework/SoSe24/dl4science/GemNet/CG Coeff\|CG Coeff]]
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

[[repr. of SO(3)\|repr. of SO(3)]]

