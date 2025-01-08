---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l7-id-s-domains/","noteIcon":""}
---

---


**What is a domain?**

* **Structural Biology:** A domain is a segment of the polypeptide chain that folds into a compact, globular unit and may have a specific molecular function.
* **Genetics and Biochemistry:** A domain is the minimal fragment of a gene, typically identified through deletion experiments, that retains its function.
* **Modules:** Domains commonly found in many different proteins.


**Challenges in Domain Identification**

A key challenge is developing an objective algorithm to parse experimentally determined 3D protein structures into domains.  The core concept is that atomic interactions within a domain are more extensive than those between domains.

**Parsing a Structure into Domains**

Early algorithmic approaches focused on grouping residues to maximize intra-group contacts and minimize inter-group contacts.  This works well for contiguous domains, which require a single "cut" in the polypeptide chain. However, discontinuous domains, where parts of the chain fold together despite being separated linearly, require multiple cuts, making identification more complex. Discontinuous domains introduce a combinatorial challenge as there are multiple possible ways to parse the chain.

**Solutions and Algorithms**

* **Ignoring Covalent Structure:**  One solution is to ignore the covalent structure initially and focus solely on contact patterns. This requires examining numerous possible groupings, presenting a difficult optimization problem.
* **Hierarchical Partitioning:** This approach divides the structure into smaller substructures and iteratively combines them, building up a hierarchy. It begins with small, locally compact segments and progresses towards larger units, culminating in the complete structure.
* **Physical Criteria:** Methods also use physical criteria like rigid body motion of continuous chain segments, composition and conformation of linkers, and the presence of hydrophobic cores to define domain boundaries.
* **Graph-Based Methods:** Proteins can be represented as 3D graphs where residues are nodes and interactions are edges. The goal then becomes partitioning the graph to minimize inter-set interactions. This is computationally complex (NP-hard), so heuristic procedures are used for reasonable speed.
    * **STRUDL:** This graph-based method uses a residue exchange procedure. It iteratively moves residues between sets to minimize the contact area between the sets. It calculates a minimum contact density profile to identify domain boundaries.

**Comparisons and Limitations of Methods**

Different algorithms can lead to varying domain assignments, as seen in the comparison between STRUDL and CATH (Class, Architecture, Topology, Homologous superfamily) classifications. Some algorithms may incorrectly split single-domain proteins or group unrelated fragments together. The concept of "decorations" – small structural additions to the core domain – can also influence domain assignments.
![Screenshot 2025-01-07 at 07.29.06.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2007.29.06.png)



**Identifying Hydrophobic Cores**

Hydrophobic cores are crucial for domain stability and can be used to assist in domain identification.  Algorithms locate hydrophobic sites and group them based on proximity and contact patterns.

**Further Directions and Future Research**

* **Averaging Results:** Analyzing multiple domain assignments for a protein family and averaging the results can improve accuracy.
* **Domain-Domain Interfaces:** Understanding the interactions between domains is important for protein function.
* **Sequence-Based Prediction:** Predicting domain boundaries from sequence alone, without 3D structure, is a significant goal.  This involves considering factors like length, sequence similarity, secondary structure, and inter-linking regions.

**Domain Prediction from Sequence**

Predicting domains from sequence involves analyzing sequence length distributions, sequence similarity searches, and secondary structure predictions. Identifying linker regions and characteristics is also important. Linker indices and preference profiles can help predict potential domain boundaries.
![Screenshot 2025-01-07 at 07.35.50.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2007.35.50.png)

This  highlights a problem with single-linkage clustering when applied to multi-domain proteins. Single-linkage clustering groups proteins based on the similarity of their closest domains. Imagine three proteins like in the image above. 
Single-linkage clustering might group all three proteins together because Protein 1 and 2 share similarity through B/B', and Protein 2 and 3 share similarity through C/C'. However, Protein 1 and 3 are unrelated, sharing no common domains. This demonstrates that single-linkage clustering can create artificial groupings of multi-domain proteins, misrepresenting their true evolutionary relationships.

GEANNFAMMER: sufficient overlap -> Merge domains, iterate. 

[[Coursework/WiSe24-25/Strukturbioinf/Lecture Notes/UniDoc\|UniDoc]]


