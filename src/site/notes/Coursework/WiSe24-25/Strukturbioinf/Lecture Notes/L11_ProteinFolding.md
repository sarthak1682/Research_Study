---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l11-protein-folding/","noteIcon":""}
---

---
[[L11_SbioInf_MM.canvas|L11_SbioInf_MM]]



This presentation discusses protein folding and ab initio structure prediction. Let's break down the key concepts presented.


**Slide 5: The Folding Problem and Ab Initio Prediction**

 the central question: can we predict protein structures from sequence alone (ab initio)?


**Slide 8 & 9: Molecular Mechanics View**

This model incorporates bonded terms (bonds, angles) and non-bonded terms (van der Waals forces, electrostatics) to describe interactions within the molecule.

**Slide 10: Central Postulate of Molecular Mechanics**

The key idea here is the relationship between a protein's structure and its energy.  The structure with the lowest energy is the most stable and represents the native state. The potential energy surface, a multi-dimensional representation of energy as a function of atomic coordinates, is a crucial concept.  The minima on this surface correspond to stable conformations.

**Slide 11 & 12: Computational Structure and Molecular Mechanics Definition**

  The goal is to find the energy minima on the potential energy surface. This involves optimizing the geometry of the molecule, allowing bond lengths, angles, etc., to adjust until they reach their "natural" values, corresponding to the lowest energy state.

**Slide 13-15: Energy Terms in Molecular Mechanics**

These slides detail specific energy terms in the molecular mechanics force field:

* **Bond stretching:**  The energy associated with deviations from ideal bond lengths.
* **Angle bending:** The energy associated with deviations from ideal bond angles.
* **Bond twisting (Torsion):** The energy associated with rotation around bonds.

**Slide 16: Van der Waals Energy**

This slide describes the van der Waals interaction, a weak attractive force between atoms at a specific distance range, becoming repulsive at very short distances. The equation shows how this energy depends on the distance between atoms and their van der Waals radii.
![Screenshot 2025-01-07 at 12.01.12.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2012.01.12.png)

 The main idea is that even nonpolar molecules can have temporary, fluctuating dipoles that induce dipoles in neighboring molecules, leading to weak attractive forces.



**Slide 20 & 21: Empirical Potential Energy Function**

 mathematical function used in molecular mechanics to describe the total energy of a molecule. It’s a sum of the various energy terms discussed earlier (bonds, angles, dihedrals, electrostatics, van der Waals). 

**Slide 22: Assumptions of Molecular Mechanics**

 energy contributions from different interactions are additive; the interaction between two atoms is independent of their environment (transferability); and quantum mechanical effects are negligible as long as no bonds are broken.

![Screenshot 2025-02-07 at 18.23.12.png](/img/user/Attachments/Screenshot%202025-02-07%20at%2018.23.12.png)
**Slide 25: Hypotheses on Protein Folding**

This slide presents some hypotheses about the protein folding process, including the idea that secondary structures may form early in the process and the role of hydrophobic collapse (hydrophobic (water-fearing) amino acid residues cluster together to minimize their exposure to water). It mentions the nucleation-propagation mechanism of helix formation (A small, specific region of the protein forms a stable **"nucleus"** of secondary structure (e.g., α-helix or β-sheet), Once the nucleus forms, the rest of the protein rapidly folds around it.).

**Slide 26: Three Stages of Unassisted Protein Folding**

This slide illustrates a simplified view of protein folding, involving three stages: unfolded, molten globule (a partially folded intermediate), and native state.


**Slide 37: Exploring the Energy Landscape**

This slide visually compares different methods for exploring the energy landscape, including gradient-based minimization, Metropolis Monte Carlo, and Molecular Dynamics. It highlights the trade-off between accuracy and speed. Molecular Dynamics simulates the actual physical movements of atoms, but it's computationally demanding. Monte Carlo randomly samples conformational space, and gradient-based minimization moves downhill on the energy surface.


Slide 40: 
- Key distinguishing features of protein native states include:

	- Hydrophobic patterning (polar/nonpolar distribution)
	
	- Extensive hydrogen bonding network
	
	- Tight side-chain packing
	
	- Specific backbone and side-chain torsional angles


**Slide 46: Molecular Dynamics**

molecular dynamics simulations calculate the motions of atoms over time based on their interactions. Key terms are "snapshot" (atomic coordinates at a specific time) and "trajectory" (a series of snapshots).

**Slide 47 & 48: Simulations of the Villin Headpiece**

These slides discuss the villin headpiece, a small, fast-folding protein, as a model system for studying protein folding via molecular dynamics..Folding time is on the order of 10 microseconds

**Slide 49: Overview of Protein Design**

de novo design, designing protein-protein interactions, and designing ligand-binding proteins.  
![Screenshot 2025-02-07 at 18.29.06.png](/img/user/Attachments/Screenshot%202025-02-07%20at%2018.29.06.png)
**Slide 50: Some Facts about Proteins**

This slide lists some general principles regarding protein structure and stability, including the location of hydrophobic and hydrophilic residues, the role of conserved residues( tend to lie inside, or near the active site), and the relationship between free energy and protein stability. The equation given is a more general form of the potential energy function.

