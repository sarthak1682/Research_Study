---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l9-str-classification/","noteIcon":""}
---

---
[[L9_SBioInf_MM.canvas|L9_SBioInf_MM]]

**Slide 2: Fold Space and Protein Evolution**

* **Limited Fold Space:**  While the theoretical possibilities are vast, the actual number of observed protein folds is surprisingly limited.  
* **Estimates of Unique Folds:**  Scientists estimate that the number of unique protein folds is somewhere between 1,000 and 10,000. 
* **Limitation of Fold Space – Divergent Evolution:**  This is a process where a protein with a specific fold duplicates, and the copies evolve to perform different functions while retaining the same basic fold.  This explains why **one fold can be associated with multiple functions**.
* **Limitation of Fold Space – Convergent Evolution:**  This occurs when unrelated proteins evolve independently to adopt similar folds because those folds are particularly stable or advantageous under specific biophysical constraints.
*  Divergent and convergent evolution are not mutually exclusive

**Slide 3: Divergent Evolution**

* **Shared Common Ancestor:**  Most folds likely originated from a smaller group of ancestral proteins.
* **Duplication and Reuse:** Once a stable fold evolved, it was duplicated and reused for different functions through evolutionary processes.
* **Modification of Existing Folds:**  It's easier for evolution to modify an existing fold than to create a completely new one from scratch.
* **Similar Structures, Different Functions:**  As a result of divergent evolution, proteins with similar folds can have very different functions.
* **Functional Versatility:**  This adaptability of folds suggests that many theoretically possible folds may never be observed because organisms haven't needed them.

**Slide 4: Convergent Evolution**


* **Biophysically Favored Folds:** Certain folds are inherently more stable or efficient to pack, making them more likely to arise through evolution, even independently.
* **Overrepresentation in PDB:**  The Protein Data Bank (PDB), a repository of protein structures, shows an overrepresentation of certain folds, supporting the idea of convergent evolution.
* **No Sequence Similarity:** Convergent evolution leads to similar folds in proteins that have no significant sequence similarity, meaning they are not related by common ancestry.
* **Protein Folding Models:**  Computational models of protein folding also suggest that some folds are more favorable biophysically.



**Slide 7: Structural Classification by Fold**

* **2000+ Known Folds:**  The current estimate.
* **Many Sequences, Same Fold:** Different amino acid sequences can fold into the same overall structure.

**Slide 8: Fold Comparison**

This slide lists the different methods used for comparing and classifying protein folds.

* **Method 1 (Expert Examination – SCOP):**  Manual classification by experts, relying on visual inspection and structural comparisons.
* **Method 2 (Double Dynamic Programming – CATH):**  A computational approach using sequence and structure comparison algorithms.
* **Method 3 (Distance Matrix Method – FSSP):**  A computational method based on comparing distances between residues in the 3D structures.
* **Method 4 (Vector Alignment – MMDB):**  Another computational method aligning structural vectors representing secondary structure elements.

**Slide 9: SCOP**

This slide introduces the SCOP (Structural Classification of Proteins) database.

* **Evolutionary Relationships:** SCOP classification is based on evolutionary relationships between proteins.
* **Visual Comparison & Automated Alignments:**  Experts use both visual inspection and computational tools to classify proteins.
* **Links to Data:** SCOP provides links to coordinates, images, and sequence data for classified proteins.

**Slide 10: SCOP Hierarchy**

This slide explains the hierarchical organization of the SCOP database.

* **Class:** Based on secondary structure composition (all alpha, all beta, alpha/beta, alpha+beta).
* **Fold:**  Similar core structures, regardless of evolutionary relationship.
* **Superfamily:** Probable common evolutionary origin based on structural and functional similarities.
* **Family:**  Clear common evolutionary origin based on sequence similarity.

**Slide 11: SCOP Classification**

![Screenshot 2025-01-07 at 11.29.42.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2011.29.42.png)



**Slide 13: SCOP Hierarchy (Detailed)**

alpha/beta: principally single beta-sheet with alpha-helices joining the individual strands
alpha+beta: both units largely separated, anti || strands usually joined by hairpins

**Slide 14: SCOP2 Prototype**

This slide introduces SCOP2, a newer version of the SCOP database.

* **Network Organization:**  Uses a network (directed acyclic graph) instead of a strict hierarchy.
* **Four Relationship Categories:** Protein types, evolutionary events, structural classes, and protein relationships (structural, evolutionary, other).
* **Separation of Relationships:**  Separates structural and evolutionary relationships.
* **New Category (IR):** Introduces a new category for non-hierarchical relationships, including cases where proteins with different folds share large substructures or motif.



**Slide 18: CATH

This slide details the five levels of the CATH hierarchy.

* **Protein Chains:** Individual protein entries.
* **Homologous Superfamily:**  Proteins with highly similar structures and functions.
* **Topology:**  Topological connections and number of secondary structures.
* **Architecture:** Gross orientation of secondary structures.
* **Class:**  Secondary structure content.



CATH Update Strategy
1. **Identify Close Relatives Using Pairwise Sequence Alignments:** The first step involves comparing the amino acid sequence of a new protein structure against the sequences of proteins already classified in CATH. Pairwise sequence alignment algorithms, like BLAST, are used to identify close homologs. If a close match is found, the new protein is likely to share the same fold and superfamily as its match.
    
2. **Detect Distant Relatives Using Sequence Profiles and Structure Comparisons:** For proteins without close sequence homologs, more sensitive methods are used. Sequence profiles (like those used by PSI-BLAST or HMMER) can detect more distant evolutionary relationships by considering conserved patterns of amino acids. If a potential match is found, structural comparison tools (like SSAP) are used to confirm that the proteins share a similar fold.
    
3. **Examine Unclassified Structures and Determine Domain Boundaries:** Proteins that remain unclassified after sequence-based searches undergo domain boundary assignment. A protein can consist of multiple domains, each with its own independent fold. Identifying these domains is crucial for accurate classification. This step involves both automated methods (like DBS) and manual inspection.
    
4. **Reiterate Steps 2 and 3:** The process of searching for distant relatives and defining domain boundaries can be iterative. New structural information and improved algorithms may reveal previously undetected relationships.
    
5. **Manual Assignment to Existing or New Architectures:** The final step involves assigning the protein to an existing architecture within CATH or creating a new architecture if no suitable match is found. This step requires expert knowledge and manual curation, ensuring the quality and consistency of the classification.


CATH/SCOP Disagreements: 
- **Domain Boundary Definition:** One of the most common discrepancies is in how domains are defined. SCOP and CATH may use different criteria for dividing a protein into domains, leading to different classifications. For example, in some cases, SCOP might consider a region a single domain, while CATH divides it into two.
    
- **Class Assignment Based on Secondary Structure Content:** The two databases can also disagree on the class assignment, particularly for proteins with mixed alpha/beta structures. SCOP might classify a protein as mainly alpha or mainly beta if one type of secondary structure is dominant, even if other secondary structures are present. CATH, on the other hand, might consider the presence of even small stretches of a different secondary structure significant, leading to an alpha+beta or alpha/beta classification.
    
- **Treatment of Small Proteins and Multi-domain Proteins:** There can be differences in how small proteins (with limited secondary structure) and multi-domain proteins are classified. SCOP has a separate class for "small proteins," while CATH might classify them based on their predominant secondary structure or closest structural relatives. Similarly, differences can arise in how regions within multi-domain proteins are classified, especially when domains are intertwined or have ambiguous boundaries. 

**Underlying Reasons for Disagreements:**

- **Manual vs. Automated Approaches:** SCOP relies more on expert manual curation, while CATH uses more automated methods. This can lead to differences in interpretation and judgment.
  

