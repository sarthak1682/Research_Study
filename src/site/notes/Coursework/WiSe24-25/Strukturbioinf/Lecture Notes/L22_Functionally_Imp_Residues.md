---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l22-functionally-imp-residues/","noteIcon":""}
---

---
[[L22_SbioInf_MM.canvas|L22_SbioInf_MM]]

**Slide 2: Finding Functionally Important Sites - The Obvious Method**

*   **Explanation:** This slide presents the most intuitive approach: conservation. If a particular amino acid position is highly conserved across many related proteins, it's a strong indication that this position is important for the protein's function or structure. Mutations at that site are likely to be detrimental, so they are rarely seen in evolution. The arrows highlight these conserved residues.



**Slide 4: Automated Selection of Specificity-Determining Positions (SDPs)**

*   **Content:**
    *   **Input:**
        *   Multiple sequence alignment (MSA)
        *   Specificity groups (i.e., groups of proteins within the family that have distinct functions)
    *   **Output:** Specificity-determining positions (SDPs)
    *   **Description:** SDPs are positions in the MSA that best discriminate between the specificity groups. They are conserved *within* a group but *differ* between groups.

*   **Explanation:** This slide introduces a more sophisticated, computational approach.  Instead of just looking for overall conservation, this method identifies positions that are crucial for *differences* in function within a protein family.  For example, a family of enzymes might all catalyze similar reactions, but on different substrates. SDPs would be the residues responsible for that substrate specificity.

**Slide 5: Method - Z-scores**

*   **Title:** "Method"
*   **Content:**
    *   Calculates measures of association between amino acid distribution at a position and the specificity.
        *   Relative entropy (Sp)
        *   Mutual information (Ip)
    *   Calculates Z-scores based on randomly shuffled data.  The formula for the Z-score is given:  Z<sub>i</sub><sup>l</sup> = (I<sub>i</sub> - <I<sub>i</sub><sup>exp</sup>>) / σ(I<sub>i</sub><sup>exp</sup>)
    *   Calculates the statistical significance of the Z-score.


**Slide 6: Relative Entropy (Sp)**

*   **Title:** "Relative entropy Sp at position p"
*   **Content:**
    *   Formula: Sp = Σ<sub>i=1</sub><sup>N</sup> Σ<sub>α=1</sub><sup>20</sup> q<sub>p</sub>(α,i) log(q<sub>p</sub>(α,i) / q<sub>p</sub>(α))
    *   Definitions:
        *   α: Residue type (1 to 20, representing the 20 standard amino acids)
        *   i: Specificity group (1 to N, where N is the total number of groups)
        *   q<sub>p</sub>(α,i): Ratio of the count of residue α at position p in group i to the size of group i.
        *   q<sub>p</sub>(α): Frequency of residue α in the whole alignment column p.
    *  
![Screenshot 2025-02-09 at 01.21.57.png](/img/user/Attachments/Screenshot%202025-02-09%20at%2001.21.57.png)
**Slide 7: Mutual Information (Ip)**

*   **Title:** "The mutual information Ip at position p"
*   **Content:**
    *   Formula: Ip = Σ<sub>i=1</sub><sup>N</sup> Σ<sub>α=1</sub><sup>20</sup> f<sub>p</sub>(α,i) log(f<sub>p</sub>(α,i) / (f<sub>p</sub>(α)f(i)))
    *   Definitions:
        *   f<sub>p</sub>(α,i): Ratio of the number of occurrences of residue α in group i at position p to the length of the whole alignment column.
        *   f<sub>p</sub>(α): Frequency of residue α in the whole alignment column.
        *   f(i): Fraction of proteins belonging to group i.
    *   Explanation: A high Ip means that the amino acid at position p is strongly associated with a particular specificity group.
I_p_ _is always nonnegative, I__p__=0 if and only if α and i are statistically independent._ _The larger I__p__, the stronger α and i are associated in position p of the MSA.




**Slide 9: Sequence Variation and Function - Limitations of Conservation**

*   **Content:**
    *   Functional sites have fewer mutations.
    *   Amino acid differences at functional sites can be described by conservation (profiles, HMMs).
    *   Methods can detect local sequence motifs (INTERPRO).
    *   Fundamental to functional annotation...
    *   ...but limited:
        *   Many functions involve large interfacial areas, not just short motifs.
        *   Functional analogies can be misleading, especially below 40% sequence identity.
    *   Circumventing limitations requires examining a protein structure's physical features.

**Slide 10: Physical and Compositional Heterogeneity of Functional Sites**

*   **Content:**
    *   Protein-ligand interactions are diverse.
    *   Geometric and electrostatic complementarity are universal features.
    *   Small ligands bind in cavities and areas of increased roughness.
    *   Protein-protein interactions:
        *   Typically involve large, accessible, planar sites.
        *   Solvation potential, interface propensities, and protrusion are not easily distinguished *a priori*.
    *   Some generalizations:
        *   Stable protein-protein interactions: lack of charged groups, excess of hydrophobic residues.
        *   Transient protein-protein interactions: composition similar to the rest of the protein surface.
    *   Mutational analysis is slow and expensive.


**Slide 11: Introduction to Evolutionary Trace (ET)**

* **Content**:
    
*  the goals of ET:
	* Identifies active sites.
	* Looks for conserved residues in branches of a phylogenetic tree.
	* Maps functionally important residues (FIR) onto the surface of the protein structure.
* **Explanation:** This introduces a key method: the Evolutionary Trace (ET) method. This method combines sequence and structural information to identify functionally important residues. The core idea is to trace the evolutionary history of a protein family and look for patterns of conservation that correlate with function.

**Slide 12: Hypotheses Underlying the Evolutionary Trace Method**

* **Title**: Based on two hypotheses
* **Content**:
    * **Hypothesis 1 (Common Functions):** If a function is conserved from an ancestral protein, it will occur at or near the same structural site in descendant proteins. This site will have low mutation rates within subgroups that share the function.
    * **Hypothesis 2 (Functional Divergence):** If there's a functional difference between related proteins, it's likely due to mutations at or near residues involved in that function.  These mutations define new functional branches and are under selective pressure to remain conserved.
* **Explanation**: This slide clarifies the assumptions behind the ET method. It's based on the idea that evolution is relatively conservative: functional sites tend to stay in the same place structurally, and changes in function are often due to a small number of key mutations.

**Slide 13: Protein Family Characteristics**

*   **Title:** "Protein family:"
*   **Content:**
    *   Should retain its fold.
    *   Conserve the location of functional sites.
    *   Have a lower mutation rate at these sites, punctuated by mutations causing divergence.


**Slide 14: The Evolutionary Trace (ET) Method - Details**

*   **Content:**
    *   Connects mutations that alter function with patterns of conservation.
    *   Finds the position of functionally important residues.
    *   Functional resolution can be adjusted (specificity vs. sensitivity).
    *   Can distinguish internal (structural) and external (binding/enzymatic) residues.
*   **Explanation:** This slide elaborates on the ET method. It can be tuned to focus on either *essential* residues (conserved across the entire family) or *specificity-determining* residues (conserved within subgroups). It also highlights the ability to distinguish between residues important for overall structure and those directly involved in function.

**Slide 15: Derivation of the Evolutionary Trace - Example**

*   **Content:** A visual example showing how the evolutionary trace is derived.  It includes:
    *   **Functional Groups:** Sets of related sequences.
    *   **Consensus Sequences:**  Representations of the conserved residues within each group.
    *   **Trace:**  A combined representation showing both conserved and class-specific positions.
    *   **Mapping:**  The trace residues are mapped onto a 3D protein structure.


**Slide 16: Partition Identity Cutoff (PIC)**

* **Title:** In the absence of functional information
* **Content**
  * Clustering proteins by sequence
  * Cluster defined by  Early and later nodes (larger and smaller resp.)
  * Partition identity cutoff: The minimum percentage identity within a cluster is bounded by
PIC


**Slide 17: Example Tree with Ranks**

*   **Explanation:** This slide shows how the phylogenetic tree is used to assign ranks to residues.  A residue that is conserved across the entire tree has a low rank (e.g., rank 1).  A residue that becomes class-specific only when the tree is divided into many subgroups has a higher rank.  The rank reflects the evolutionary importance of the residue.

**Slide 18: Functional Resolution**

*   **Title:** "Functional resolution"
*   **Content:**
    *   Defined as the number of clusters generated by a partition of the family.
    *   Low PIC (Partition Identity Cutoff) -> few large clusters, low resolution.
    *   High PIC -> many small clusters, high resolution.
    *   Alternative partitions can be chosen based on functional knowledge.


**Slide 19-22: Trace Residues and Active Sites**

![Screenshot 2025-02-06 at 01.03.41.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2001.03.41.png)

![Screenshot 2025-02-06 at 01.03.47.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2001.03.47.png)

![Screenshot 2025-02-06 at 01.03.56.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2001.03.56.png)

![Screenshot 2025-02-06 at 01.04.14.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2001.04.14.png)

**Residues with lower numbered ranks are considered to be more important than** those with higher numbered ranks.



**Slide 24: ET as a Functional Filter - Subgroup Analysis**
![Screenshot 2025-02-06 at 01.06.30.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2001.06.30.png)

* **Explanation:** For large and diverse families, analyzing the entire family at once may miss important details. Subgroup analysis allows focusing on specific branches of the evolutionary tree, revealing functional sites that are unique to those subgroups.


**Slide 26: Sequence Identity Dendrogram of SH2 Domains**

*   **Explanation:** This slide shows the evolutionary relationships among the SH2 domains, and how the PIC is used to create different partitions (groupings) of the sequences.

**Slide 27: Evolutionary Trace of SH2 Domains Mapped to Structure**

*   **Content:**  Multiple views of the Src SH2 domain structure, with trace residues highlighted for different partitions (A1 to G1).
*   **Explanation:** This slide shows the results of the ET analysis for the SH2 domain family.  As the PIC increases (from A1 to G1), the trace becomes more refined, and a cluster of residues emerges on one face of the protein. This cluster corresponds to the known binding site of the SH2 domain.

**Slide 28: Comparison of ET and Known Structure (SH2)**

*   **Content:** Compares the ET predictions to the known structural epitope (the residues that are within 4 A° of the ligand,).
*   **Explanation:** This slide validates the ET method by showing that the predicted functional site (based on the ET analysis) overlaps significantly with the experimentally determined binding site.  It provides quantitative measures of specificity and sensitivity.

do the same with SH3


**Slide 37: Large-Scale Application of ET - Bottlenecks**

*   **Content:**
    *   Selection of homologues is complicated by gaps in the alignment.
    *   Visual interpretation of results is subjective and requires expertise.


**Slide 38: Treatment of Gaps**

*   **Content:**
    *   Gap-tolerant trace: gaps are treated as a 21st amino acid type.
    *   Gaps are not meant to carry biophysical meaning.
    *   Gaps often occur in blocks, suggesting functional importance.
    *   Ranking gapped positions eliminates "holes" in the analysis.


**Slide 39: Away from Visual Interpretation**

*   **Title:** "Away from visual interpretation"
*   **Content:**
    *   Use two statistics:
        *   Overall number of clusters
        *   Size of the largest cluster
    *   Estimate the distributions of these statistics by random sampling.
    *   Measure the significance of the actual ET-generated values.

**Slide 40: Comparing Clusters - Trace vs. Random**

*   **Explanation:** This slide illustrates the difference between clusters formed by functionally important residues (identified by ET) and random clusters.  Trace residues tend to form a few large, well-defined clusters, while random residues form many small, scattered clusters.

**Slide 41: Overlap Statistics**

*   **Content:**  Describes four different statistics (TCR, LCO, AO, HD) for quantifying the overlap between predicted functional sites and known functional sites.
![Screenshot 2025-02-06 at 01.17.46.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2001.17.46.png)



**Slide 42: Trace Clusters Overlap Significantly with Functional Sites**

*   **Content:**  A bar graph showing the performance of the different overlap statistics.
*   **Explanation:** This slide presents results demonstrating that the ET method performs well in identifying functional sites.  The overlap statistics are significantly higher for trace clusters than for random clusters.

**Slide 43: 3D Cluster Analysis**
*   **Explanation:** This slide introduces a more advanced method that goes beyond the traditional ET approach.  3D cluster analysis aims to identify functional sites directly from the 3D structure and sequence alignment, without relying on a phylogenetic tree. This is useful when the phylogenetic tree may not accurately reflect the functional relationships between proteins.

**Slide 44: Similarity Deviation Score**

*   **Title:** "Similarity deviation score"
*   **Content:**
    *   Detects residue clusters with deviations in their regional sequence similarity.
    *   Facilitates assignment of functions not adequately represented in the "apparent phylogenetic tree."

**Slide 46: 3D Cluster Analysis - Steps (Diagram)**


*   **Explanation:** This slide provides a visual representation of the 3D cluster analysis process:
    1.  **Identify spatial neighbors:** For each residue, identify its neighbors within a defined radius in the 3D structure.
    2.  **Extract regional alignments:** Extract the corresponding sequence segments from the multiple sequence alignment.
    3.  **Calculate similarity matrices:** Calculate two similarity matrices: one for the entire sequences (global) and one for the regional alignments (local).
    4.  **Calculate similarity deviation score:**. Compare the local and global similarity matrices to calculate the similarity deviation score for each residue.

