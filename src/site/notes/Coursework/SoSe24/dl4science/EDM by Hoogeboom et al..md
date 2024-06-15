---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/edm-by-hoogeboom-et-al/","noteIcon":""}
---

---

## Summary to be submitted

The EDM (E(3) Equivariant Diffusion Model) generates molecules by defining a noising process on node position (continuous) and features (discrete), which it later tries to denoise with an equivariant neural network. It performs significantly better than the contemporary state-of-the-art, thus establishing a new one. They predict bond types from distance between pairs of atoms and then compare stability with their competitors, G-Schnet and E-NF, and with their own architecture without the equivariance properties, where EDM outperforms every single one of them. EDM also generates valid and unique molecules at a very high rate, which is explained by its effective scaling and precise distributions (also reflected in much lower NLL values). EDM can also take conditional property information into account. Stability suffers a bit (98 vs 81 percent) when tested on a bigger dataset (GEOM-Drugs) but it still manages to capture the energy distribution for the molecules well enough, whereas other methods tend to produce a little too-many low-energy compounds. The authors also hint that further training (/scaling) and increasing expressivity of model can enhance the performance even on a large dataset like GEOM-Drugs. 