---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l12-docking/","noteIcon":""}
---

---
[[L12_SbioInf_MM.canvas|L12_SbioInf_MM]]


**Slide 2: What is docking?**

Molecular docking is a computational technique used to predict the preferred orientation of one molecule (ligand) to a second (receptor) when bound to each other to form a stable complex.   It primarily aims to predict:

* **Binding Mode:** The specific orientation of the ligand within the receptor's binding site.
* **Binding Affinity:** The strength of the interaction between the ligand and receptor.

The underlying assumption is that molecules that "dock" well computationally are likely to bind to each other in reality.  Studying the structures of existing complexes (co-crystal structures, where both the receptor and ligand are visualized in their bound state through techniques like X-ray crystallography) provides invaluable insights into the nature of these interactions.  These structures serve as training and validation sets for docking algorithms.

**Slide 3: Why do we want protein docking?**

Docking serves several key purposes:

* **Predicting Protein-Protein Interactions:** Understanding which proteins interact is crucial for mapping biological pathways and understanding disease mechanisms.
* **Identifying Binding Sites:** Docking can pinpoint the specific regions on a protein's surface where interactions occur.
* **Drug Discovery:** A primary application is predicting how potential drug molecules (ligands) interact with target proteins (receptors), accelerating drug development.
* **Protein Engineering:**  Docking can guide the design of modified proteins with altered binding properties or novel functions.

**Slide 4: The docking problem**

This slide formalizes the docking problem:

* **Input:**  3D structures of the molecules to be docked (typically obtained from experimental methods or computational modeling).
* **Tasks:**
    * **Binding Prediction:** Determining if the molecules are likely to interact and form a stable complex.
    * **Affinity Estimation:** Quantifying the strength of binding.
    * **Structure Prediction:** Predicting the 3D structure of the resulting complex.
    * **Function Inference:** Sometimes, the docking results can shed light on the biological function of the interaction.

**Slide 5: Forces governing biomolecular recognition**

Several forces govern how biomolecules interact:

* **Van der Waals forces:** Weak attractive forces between molecules at close proximity.
* **Electrostatic interactions:** Attractive or repulsive forces between charged groups.
* **Hydrophobic interactions:** The tendency of nonpolar molecules to cluster together in an aqueous environment.
* **Hydrogen bonds:** Relatively strong interactions between a hydrogen atom bonded to an electronegative atom (like oxygen or nitrogen) and another electronegative atom.
* **Salt bridges:** Ionic bonds between oppositely charged groups.

These forces act at short ranges, and surface complementarity (how well the shapes of the two molecules match) is essential for tight binding.

**Slide 6: Surface complementarity**

This slide visually illustrates the concept of surface complementarity, using the analogy of puzzle pieces fitting together.  The "T" represents the transformation (rotation and translation) required to bring the ligand into its optimal binding pose with the receptor.

**Slide 7: Geometric Docking Algorithms**

Geometric docking algorithms primarily focus on shape complementarity. They search for the best fit between the ligand and receptor, considering:

* **Molecular Surface Complementarity:**  How well the shapes of the molecules match.
* **Hydrogen Bond Complementarity:** Matching hydrogen bond donors and acceptors.

These algorithms can be applied to protein-protein, protein-ligand (including protein-drug), and even DNA/RNA interactions.

**Slide 8: Issues to be examined when evaluating docking methods**

Several factors determine the effectiveness of a docking method:

* **Rigidity vs. Flexibility:**  Whether the molecules are treated as rigid bodies or if flexibility (e.g., side-chain rotations, backbone movements) is incorporated.  Flexibility adds complexity but is often essential for accurate predictions.
* **Prior Knowledge of the Active Site:** Some methods require prior knowledge of the binding site on the receptor, while others can predict it.
* **Performance with Unbound Structures:** How well the method performs when using structures of the molecules in their unbound (free) conformations, which is more challenging than using bound structures.
* **Speed:**  Especially important for screening large libraries of potential ligands (e.g., in virtual drug screening).

**Slide 9: Bound docking**

Bound docking is a simpler scenario where the starting point is a known complex structure. The molecules are separated and then re-docked to see if the algorithm can reproduce the original complex.  This is a useful initial test for a docking method.

**Slide 10: Unbound docking**

Unbound docking is more realistic and challenging, as it uses the structures of the molecules in their unbound conformations.  Conformational changes upon binding and experimental errors in the structures can complicate the process.

**Slide 11: Difficulties**


* **Rigidity:**  Biological molecules are often flexible, making it difficult to predict their bound conformations.
* **Search Space:** The vast number of possible orientations and conformations creates a huge search space.
* **Representation of Docking Surface:**  Accurate representation of the molecular surfaces is crucial.


**Slide 13: The stages of protein-protein docking**


1. **Input Coordinates:** Start with the 3D structures of the two proteins.
2. **Rigid-Body Search:**  Explore different orientations of the proteins relative to each other, treating them as rigid bodies.
3. **Generate Possible Complexes:**  Identify potential docking poses based on shape complementarity and other criteria.
4. **Rerank by Energy:**  Evaluate the energy of the different poses to prioritize those that are more likely to be stable.
5. **Introduce Flexibility:**  Refine the top-ranking poses by allowing for flexibility in the protein structures.
6. **Refine and Rerank:** Further optimize the structures and re-evaluate their energies.
7. **Output List of Complexes:**  Produce a ranked list of predicted complexes.  Experimental information can be incorporated at various stages to guide the process.


**Slide 14: Protein flexibility types**

This slide illustrates different types of protein flexibility:

* **Shear motion:**  Sliding of domains or subunits relative to each other.
* **Hinge motion:**  Rotation around a flexible region (hinge).
* **Flexible loop:**  Movement of loops on the protein surface.

**Slide 15: A general scheme of flexible docking**


![Screenshot 2025-01-07 at 12.17.41.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2012.17.41.png)


**Slide 16: Protein-Ligand Docking**

Protein-ligand docking, particularly with small drug-like molecules, often involves a flexible ligand and a (mostly) rigid protein receptor. The search space is immense due to the numerous possible ligand conformations and binding sites on the protein.

**Slide 17: Examples of modelled protein-ligand complexes**
![Screenshot 2025-01-07 at 12.33.41.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2012.33.41.png)



**Slide 19: How "DOCK" works**

A brief overview of the DOCK software, a widely used docking program. It involves generating a molecular surface for the receptor's active site, generating spheres to represent the site, matching these spheres to ligand atoms, and finally scoring the different poses.



