---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l13-homology-modelling/","noteIcon":""}
---

---






**Slide 7: Basis of Homology Modeling**

1.  A protein's 3D structure is uniquely determined by its amino acid sequence.
2.  Structure is more evolutionarily conserved than sequence. A small change in sequence doesn't usually mean a big change in structure.


The graph illustrates this, showing that even at low sequence identities (e.g., 20%), there can still be significant structural similarity.

**Slide 8: Homology Modeling Zones**

This graph defines the "safe" and "twilight" zones for homology modeling.

*   **Safe Zone:**  High sequence identity (>30%) generally results in reliable models.
*   **Twilight Zone:** Low sequence identity (10-30%) makes modeling more challenging and requires more careful evaluation of the model. This zone is called 'twilight' because it is difficult to be sure of the relation between query and template.


**Slide 9: Evolution of Protein Structure Families**
As sequence identity increases, the RMSD (root-mean-square deviation, a measure of structural difference) of the core decreases.  A highly conserved core indicates a strong structural similarity.
for proteins > 60% identical residues, the core contains > 90 % of all residues deviating less than 1.0 Å.


**Slide 10: Homology Modeling Definition**
 alternative names: comparative protein modeling, modeling by homology, and knowledge-based modeling. The most successful method for predicting protein structure from sequence.


**Slide 12: Steps in Homology Modeling 
1.  **Template Identification and Alignment:**  Find a suitable template structure and align the target sequence to it.
2.  **Backbone Generation:** Build the backbone of the target model based on the aligned template structure.
3.  **Loop and Side Chain Modeling:** Model the loops (regions not present in the template) and the side chains of the amino acids.
4.  **Model Optimization:** Refine the model using energy minimization and other techniques to improve its accuracy.



**Slide 14: Template Recognition and Initial Alignment**

This slide details the first step:

*   **Safe Zone Alignment:** Emphasizes the importance of selecting a template with sufficient sequence identity.
*   **Tools:**  Lists commonly used sequence alignment tools like BLAST and FASTA.
*   **Alignment Example:**  Demonstrates a simple sequence alignment, highlighting the importance of aligning residues with similar properties and minimizing gaps.

**Slide 15: Alignment Correction**

This slide stresses that the initial alignment might not be optimal. Multiple sequence alignment and structural considerations can help improve the alignment accuracy.  The example illustrates how a seemingly worse alignment based on sequence alone can lead to a better model if it minimizes structural gaps.

**Slide 16: Backbone Generation**


*   **Coordinate Copying:**  Copy coordinates from aligned template residues.
*   **Backbone-Only Copying:** If residues differ, only copy the backbone (N, Cα, C, and O) atoms.
*   **Side Chain Copying:** Copy side chains only for identical residues.
*   **Template Selection:** Prioritize the best template if multiple are available.
*   **Combine Resolved Regions:** Use the best resolved regions from multiple templates if possible.

**Slide 17: Loop Modeling**


*   **Gaps:** Gaps in the alignment represent insertions or deletions in the target sequence compared to the template.
*   **Loop Conformation:**  Predicting the conformation of loops is difficult even without gaps, as loop regions are flexible.
*   **Loop Modeling Approaches:**  Lists two main approaches:
    *   **Knowledge-based:** Use known loop structures from the PDB.
    *   **Energy-based:** Use energy functions to evaluate and optimize the loop conformation.




**Slide 23: Energetically Favourable Side-Chain Conformations**

It explains the energetic basis of rotamer preferences using ethane and valine as examples. Staggered conformations are generally preferred due to reduced steric clashes. Favoured Conf: Rotamers
![Screenshot 2025-01-07 at 12.54.38.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2012.54.38.png)


**Slide 24: Building Side Chains**
*   **Copy from Template:** For identical residues.
*   **Partial Similarity:**  Use parts of the template side chain for similar residues.
*   **Substitution:** For different residues, build side chains from rotamer libraries. The different rotamers available are labeled *χ*1, *χ*2, etc. and show the angles around bonds in the side chain. Different rotamers are energetically different and favored depending on the backbone conformation.

**Slide 25: Side-Chain Modeling**

*   **Rotamer Conservation:** Rotamers are conserved in closely related proteins.
*   **Rotamer Variation:** Rotamers may differ in distantly related proteins.
*   **Knowledge-Based Approaches:** Use libraries of common rotamers and energy functions to score them.
*   **Backbone Influence:** Certain backbone conformations favor specific rotamers, reducing the search space.




**Slide 28: Prediction Accuracy for Rotamers**


*   **High Accuracy in Core:**  High accuracy for residues in the hydrophobic core due to well-defined packing interactions.
*   **Low Accuracy on Surface:** Lower accuracy for surface residues due to greater flexibility and influence of crystal contacts. Energy functions used to score rotamers can easily handle the hydrophobic packing in the core (mainly Van der Waals interactions), but not complicated electrostatic interactions on the surface.


**Slide 29: Model Optimization**

This slide details model optimization:

*   **Iterative Procedure:** Iterate between rotamer prediction and backbone adjustments.
*   **Energy Minimization:**  Use energy minimization to refine the entire protein structure (computationally challenging).
*   **Simplifications:** Restrain atom positions and use a limited number of energy minimization steps to reduce the computational cost.



**Slide 31: Errors in Homology Models**


*   **High Identity:** >90% : Models are nearly as good as crystal structures.
*   **Medium Identity:**  50-90% : Errors up to 1.5 Å RMSD.
*   **Low Identity:** 25-50% : Large errors are possible.
*   **Template Errors:**  Errors in the template structure propagate to the model.

**Slide 32: Model Validation**


*   **Bond Lengths, Angles, Torsions:** Verify normal values, but usually not a concern for homology models.
*   **Residue Distributions:**  Check the distribution of polar and nonpolar residues.
*   **Atom Contact Potentials:** Assess the energy of atom interactions.
*   **Atom Contact Directions:** Evaluate the relative orientations of interacting atoms.


**Slide 36: Limiting Steps**
. At high sequence identity, speed is the main constraint.  As sequence identity decreases, alignment accuracy and the ability to detect homology become more crucial.

**Slide 37: Applications of Comparative Protein Modeling**
![Screenshot 2025-01-07 at 13.01.59.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2013.01.59.png)

![Screenshot 2025-01-07 at 13.02.27.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2013.02.27.png)


