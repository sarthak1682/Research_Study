---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l19-contact-prediction/","noteIcon":""}
---

---
[[L19_SBioInf_MM.canvas|L19_SBioInf_MM]]

**Slide 2: General Strategy for Machine Learning Protein Structures**

* **Primary sequence:** The starting point, representing the amino acid sequence of the protein.
* **Secondary Structure Prediction:**  Predicting local structural elements like alpha-helices and beta-sheets from the primary sequence.  Well-established methods like PSI-PRED and Jpred are commonly used.
* **Contacts and Solvent Accessibility Prediction:** Predicting which residues are in contact and which are exposed to the solvent.  These are important constraints for 3D structure prediction.
* **Contact Map:** A 2D representation of protein contacts. A dot at (i,j) indicates a contact between residue i and residue j.
* **Topology:** Simplified representation of secondary structure elements and their arrangement.
* **3D Structure:** The ultimate goal, the three-dimensional arrangement of atoms in the protein.


**Slide 3: Decompose the Structure Prediction Problem**

 1) predicting structural features, 2) predicting contact maps from these features, and 3) predicting the 3D structure from the 2D contact map.

**Slide 4: What is a Contact?**

This slide visually defines a contact.

* **Left:** A 3D structure of a protein, with a zoomed-in region highlighted.
* **Right:** The zoomed-in region, showing the atoms of several residues. A contact is typically defined as a spatial proximity between two residues that are not immediately adjacent in the sequence.  The specific distance threshold (e.g., 8 Å between Cβ atoms/Seq Gap > 7 Residues) can vary.

**Slide 5: What are we trying to do?**

This slide clarifies the objective of contact prediction.  The goal is to predict contacts between residues that are far apart in the sequence but close in the folded 3D structure.  A typical definition is provided: Cβ-Cβ distance < 8 Å and a sequence separation > 7 residues (to exclude trivial contacts).

**Slide 6: We can build the correct structure from the correct contact map**

This slide emphasizes the importance of contact maps. If a perfectly accurate contact map is known, it can be used to reconstruct the 3D structure with reasonable accuracy, as demonstrated by the low RMSD (Root Mean Square Deviation) value between the model and the actual structure.

**Slide 7: Why predict contact maps?**

* **Fundamental to protein structure:** Contacts are essential for stabilizing the folded protein.
* **Intermediate step in structure prediction:** Contact maps provide valuable constraints for 3D structure prediction.
* **Enables _de novo_ structure prediction:** Along with secondary structure prediction and folding algorithms, accurate contact maps can facilitate predicting structures without relying on templates.
* **Protein structure comparison:** Contact maps can be used to compare protein structures in a sequence-independent way.

**Slide 8: Distance and contact maps**

* **Symmetric square matrix:** Both are represented as N x N matrices, where N is the length of the protein sequence.
* **Distance map:**  C(i,j) represents the spatial distance between residues i and j.
* **Contact map:** C(i,j) = 1 if the distance is below a threshold, 0 otherwise.
* **Contact definitions:** Different distance thresholds can be used (e.g., 6-12 Å for Cα-Cα or Cβ-Cβ).  A shorter threshold (4.5 A) might be used for any-atom contacts.
* **Rotation and translation invariant:**  Contact maps are invariant to rotations and translations of the protein structure, which is a useful property.
* **Coarse-grained maps:** Contact maps can also be defined for secondary structure elements.

**Slide 9: A structure A and its mirror image B**
: distance matrices (and contact maps) don't contain information about "handedness" or chirality.  Two structures that are mirror images of each other will have the same distance matrix. This is a limitation of using only distance information for structure prediction.

**Slide 10: Contact map of HSP-60 protein fragment**

This slide shows an example of a real contact map for a fragment of the HSP-60 protein. The diagonal represents the sequence.  Dots indicate contacts.  The different patterns correspond to different secondary structure elements (alpha-helices, parallel and antiparallel beta-sheets).

**Slide 11: Approaches to predict contact maps**

This slide introduces the two main approaches for contact map prediction: correlated mutations and machine learning.

**Slide 12: Correlated mutation analysis**

This slide introduces the concept of correlated mutations. The idea is that if two residues are in contact and one mutates, the other may also mutate to compensate and maintain the interaction.  By analyzing patterns of covariation in multiple sequence alignments, we can infer contacts.

- **Orthologs**: Genes (or proteins) in different species that evolved from a common ancestral gene through speciation. They usually retain similar functions across species.
- **Sequence variability**: Changes in the amino acid sequence of a protein over evolutionary time due to mutations, insertions, or deletions. It is restricted by the need to conserve the proper protein fold and function. 


**Slide 13: The Rational Basis of the Correlated Mutations Concept**

This slide explains the rationale behind correlated mutation analysis.- **Functional Constraints & Conservation**:
    
- Some residues are highly conserved because they are essential for protein function.
- Functional constraints limit the rate at which mutations can occur at these critical sites.
- **Structural Stability & Compensatory Mutations**:
    
    - If a mutation occurs at one residue and destabilizes the protein, evolution may select for a compensatory mutation at a contacting residue to restore stability.
    - This creates a pattern where two residues mutate together over evolutionary time, known as **coevolution**.



**Slide 14: Correlated mutation analysis (continued)**

This slide provides a specific example of how correlated mutation analysis works.  Panel A shows two alpha-helices.  Panel B shows a multiple sequence alignment. Arrows connect correlated substitutions. Panel C shows the most parsimonious evolutionary pathway, suggesting that positions 1 and 3 are likely in contact.![Screenshot 2025-02-05 at 19.16.39.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2019.16.39.png)



**Slide 15: From putative correlated mutations to predicted contacts**

This slide explains how to go from correlated mutations to predicted contacts.  A mutation matrix captures the similarity of amino acids at each position in a multiple sequence alignment. Correlation coefficients between mutation matrices at different positions are calculated. If the correlation is above a threshold, a contact is predicted.  The accuracy is evaluated by comparing predicted contacts with those observed in known structures.

**Slide 16: Correlated mutation score between positions (i,j)**

This slide provides the mathematical formula for calculating the correlated mutation score (Pearson correlation) between positions i and j. The formula incorporates weights to down-weight highly similar sequences and accounts for the average similarity and standard deviation of similarity scores.

[[Coursework/WiSe24-25/Strukturbioinf/Lecture Notes/CM_ij_Calc\|CM_ij_Calc]]


**Slide 19: Accuracy vs. Number of Predicted Contacts**

These graphs show the trade-off between the number of predicted contacts and the accuracy of the prediction.  A higher correlation cutoff (rc) leads to fewer predicted contacts but higher accuracy.

**Slide 20: Observed Minus Expected Squared (OMES)**
[[Coursework/WiSe24-25/Strukturbioinf/Lecture Notes/OMES\|OMES]]


**Slide 21: Mutual information**

![Screenshot 2025-02-05 at 20.45.54.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2020.45.54.png)
**Slide 22: Prediction of contact maps with neural networks and correlated mutations**

This slide describes a method that combines neural networks with correlated mutations for contact map prediction. It uses a variety of input features, including evolutionary information, sequence conservation, correlated mutations, and predicted secondary structures.

**Slide 23: Neural network architecture for contact map prediction**

This slide details the architecture of the neural network used in the previous method. It explains the input encoding, including frequencies of residue pairs and secondary structure information.

**Slide 24: PROFcon: novel prediction of long-range contacts**

This slide introduces PROFcon, a method for predicting long-range contacts using neural networks. It incorporates alignments, predicted secondary structure and solvent accessibility, information about the region between residues, and average protein properties.


**Slide 26: PROFcon accuracy versus sequence separation**

This graph shows the accuracy of PROFcon as a function of sequence separation.  The number of predicted contacts considered is a fraction of the protein length (L/5, L/10, L/20).

**Slide 28: Deriving folded three-dimensional structure from contact map**

This slide outlines the steps involved in deriving a 3D structure from a predicted contact map. It includes building a multiple sequence alignment, calculating co-occurrence frequencies, deriving predicted contacts, generating approximate 3D coordinates, refining the coordinates using molecular dynamics, and ranking the generated models.


**Slide 29: Influence of indirect correlations**

This slide discusses the problem of indirect or transitive correlations in correlated mutation analysis.  Indirect correlations can arise when two residues don't directly interact but are both in contact with a third residue. These correlations can confound structure prediction. Global probability models attempt to address this issue.

**Slide 30: Problem: functional vs phylogenetic correlations in multiple alignment**

This slide illustrates the challenge of distinguishing between functional and phylogenetic correlations in multiple sequence alignments.  Functional correlations (due to convergent evolution) can be mistaken for structural contacts.
**Homoplasy:** Similarity due to factors other than common ancestry (e.g., chance, convergent evolution
Phylogenetics is **the study of evolutionary relationships among biological entities** – often species, individuals or genes (which may be referred to as taxa)
![Screenshot 2025-02-05 at 20.55.33.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2020.55.33.png)

The unusual substitution pattern found at sites 5 and 6 indicates functional convergence.

**Slide 31: Prediction of disulfide-bonded cysteines**

This slide briefly presents a specialized application of contact prediction: predicting disulfide bonds between cysteine residues.  It uses a probabilistic model to predict the bonding states of cysteines.

**Slide 32: Relative contact order**

This slide defines relative contact order (CO), a measure of protein topological complexity. CO is the average sequence separation between contacting residues, normalized by the protein length.
![Screenshot 2025-02-05 at 20.56.41.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2020.56.41.png)



**Slide 33: Relationship between protein folding kinetics and topological complexity**

This slide shows a correlation between protein folding rates and relative contact order. Proteins with higher CO tend to fold more slowly.

**Slide 34: Key steps in template-free structure prediction**

This slide summarizes the key steps in template-free structure prediction, a challenging problem in structural biology. The steps include building a multiple sequence alignment, predicting local structure, predicting residue contacts, assembling 3D models, and refining and ranking the models.
 