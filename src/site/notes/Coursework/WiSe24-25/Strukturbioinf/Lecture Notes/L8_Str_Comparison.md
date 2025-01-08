---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l8-str-comparison/","noteIcon":""}
---

---
This lecture covers protein structure comparison and 3D alignment.

**Why compare protein structures?**

Unlike protein sequences, which can diverge significantly over evolutionary time, protein structures are much more conserved. Comparing structures can reveal distant evolutionary relationships that sequence analysis might miss.  Even proteins with only 15% sequence identity can share significant structural similarity.  This is because the three-dimensional structure is crucial for protein function.

Structure comparison also allows us to:

* **Analyze conformational changes upon ligand binding:**  Ligand binding can induce structural changes that facilitate catalysis, promote substrate binding at other sites, or allosterically regulate protein activity. Comparing bound and unbound structures helps us understand these mechanisms, crucial for drug design.
* **Analyze structural variation in protein families:** This tells us how much structures diverge as their sequences change, which depends on the protein fold and its inherent flexibility (structural plasticity). Multiple structure comparisons can pinpoint structurally conserved regions, like active sites or protein-protein interaction interfaces.
* **Identify common structural motifs:** Even proteins without evolutionary relationships (analogs) can exhibit global structural similarities due to constraints on secondary structure packing and physico-chemical requirements for protein folding. Analyzing these similarities helps us understand protein folding principles and common structural motifs, also known as super-secondary structures.


**Comparison in 3D**

The core problem is to find the optimal translation and rotation of one molecule onto another to maximize their overlap. This process, called superposition, aims to align equivalent residue centers. However, perfect superposition isn't always possible due to internal rotations or conformational changes. The difficulty of structural comparison varies. Comparing globins is relatively easy, while immunoglobulin comparisons are trickier, and subtle similarities like in G3P dehydrogenase's C-terminal domain are even more challenging to detect.

**Why is structure comparison harder than sequence comparison?**

* **Constraints:** Protein structures are more constrained by chemical and physical forces than sequences, limiting their possible conformations.
* **Optimal alignment definition:** There's no universally agreed-upon definition of an optimal 3D alignment.
* **Random structures:** Defining a "random" protein structure is difficult, making it hard to assess the significance of structural similarities and compare different methods statistically.
* **Theoretical understanding:** We lack a strong theoretical framework for how likely independent proteins are to have similar structures, unlike the well-established statistical models for sequence similarity.

**Consequences of these difficulties:**

* Assessing the statistical significance of structural similarity is challenging.
* Empirically determining the distribution of structural similarity scores and comparing different comparison methods is difficult.

**Definitions**

* **Structure comparison:**  Looking for similarities in the 3D structures of two proteins.
* **Structural alignment:** Establishing 1:1 equivalences (correspondences) between amino acid residues of two proteins based on their 3D structures.
* **Structure superposition:** Moving one structure onto another so that equivalent positions match best, usually by minimizing the Root Mean Square Deviation (RMSD).

**Multiple ways to compare structures**

Proteins can be described and compared at different levels (atom, residue, fragment, secondary structure element) and based on different features (geometry, topology, physio-chemical properties). The chosen approach depends on the goal of the comparison (e.g., similar secondary structure packing, similar topology).

**Structure description and features**

* **Levels:** Atom/atom group, residue, fragment, secondary structure element (SSE). The structure is described by elements of the chosen type. Using Cα (alpha carbon) atoms simplifies the comparison![Screenshot 2025-01-07 at 08.16.16.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2008.16.16.png), while using Cβ atoms makes it more sensitive to side-chain orientations.
* **Features:** Geometry (coordinates, relative positions), Topology (sequential order of residues along the backbone), Properties (physio-chemical properties of residues).

**Equivalences and Alignments**

An equivalence maps elements of one structure to elements of another.  An alignment is a co-linear equivalence, meaning the order of matched elements is preserved in both structures. This concept can be extended to multiple structures.  Unambiguous assignment of matching pairs leads to a single "best fit," but often, the assignment is ambiguous, requiring criteria like visual inspection, biochemical information, distance information, or secondary structure elements.

**Scoring Equivalences**

RMSD is the most common metric for quantifying structural similarity. It measures the average distance between corresponding atoms after optimal superposition.  A lower RMSD indicates higher structural similarity. Related structures typically have RMSD values below 3.5 Å. However, RMSD has pitfalls: it treats all atoms equally, best alignment doesn't always mean minimal RMSD, and its significance is size-dependent. Alternatives include aRMSD (calculated over aligned alpha carbons), bRMSD (over highest-scoring residue pairs), and wRMSD (weighted RMSD).
![Screenshot 2025-01-07 at 08.17.57.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2008.17.57.png)
T is a transform applied to B. 

**Optimal Alignment**

The goal is to find the highest number of atoms aligned with the lowest RMSD.  This involves balancing local regions with excellent alignments and the overall alignment quality. Sequence alignments inform which atoms correspond to each other.
![Screenshot 2025-01-07 at 08.20.55.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2008.20.55.png)



Let's delve deeper into the algorithms for protein structure comparison.

**1. Dynamic Programming (DP) and its limitations:**

Dynamic programming is highly successful for sequence alignment but faces challenges in structure comparison.  In sequence alignment, the score of an alignment is calculated incrementally, based on the scores of aligning individual residues or introducing gaps.  The optimal alignment is found by tracing back through the scoring matrix.  Crucially, the optimal alignment up to a given point is independent of subsequent alignment choices. This principle of optimality allows for efficient calculation.

However, in structure alignment, applying a rigid-body transformation (translation and rotation) to superimpose structures couples the positions of all aligned residues. This means aligning a pair of residues affects the relative positions of all other residues, violating the principle of optimality required for standard dynamic programming. Thus, simple dynamic programming cannot guarantee finding the globally optimal structure alignment.

**2. Iterative Methods (e.g., alternating superposition and alignment):**

These methods try to iteratively refine both the alignment and the superposition.  A common approach involves:

1. **Initial alignment:**  Start with an initial guess for the alignment, perhaps based on sequence similarity, secondary structure matching, or manual selection of a few corresponding residues.

2. **Superposition:**  Using the current alignment, find the optimal rigid-body transformation that minimizes the RMSD between the aligned residues.

3. **Scoring matrix:** Based on the superimposed structures, calculate a scoring matrix that reflects the distances between all pairs of residues in the two proteins.  Residues closer in space after superposition will receive higher scores.

4. **Alignment:** Use dynamic programming with the new scoring matrix to find an improved alignment.  This step treats the scoring matrix as fixed, temporarily ignoring the interdependence of residue positions due to the superposition.

5. **Iteration:** Repeat steps 2-4 until the alignment converges (i.e., no further changes occur) or a maximum number of iterations is reached.

While iterative methods don't guarantee a globally optimal solution, they often find good alignments in practice.

[[Coursework/WiSe24-25/Strukturbioinf/Lecture Notes/DDP\|DDP]]]


**4. Distance Matrix Methods (e.g., DALI):**

These methods represent protein structures as matrices of inter-residue distances.

1. **Distance matrix calculation:** Calculate the distance between all pairs of Cα atoms (or other representative atoms) within each protein.

2. **Submatrix comparison:** Break down the full distance matrices into smaller, overlapping submatrices.  Compare all pairs of submatrices between the two proteins to find regions with similar distance patterns.  This can be done efficiently using various techniques, such as hashing or indexing.

3. **Alignment construction:**  Assemble the matching submatrices into a consistent global alignment.  This step involves resolving overlaps and gaps between the matched regions.  DALI uses a Monte Carlo optimization (Metropolis algorithm) to find the best assembly.
![Screenshot 2025-01-07 at 08.37.38.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2008.37.38.png)
4. **Refinement:** The initial alignment can be further refined using iterative methods or other techniques.

Distance matrix methods are particularly effective at detecting similarities between proteins with different topologies or circular permutations, where the order of secondary structure elements differs.![Screenshot 2025-01-07 at 08.37.13.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2008.37.13.png)

**5. TM-align (combining rotation matrix and DP):**

TM-align addresses the computational cost of DALI by using a clever combination of dynamic programming and rotation matrices.

1. **Calculate inter-residue distances:** Similar to DALI, TM-align starts by calculating inter-residue distances within each protein.

2. **Generate a rotation matrix:**  It then uses a fast method based on singular value decomposition to calculate a rotation matrix that aligns the two structures.  This avoids the expensive Monte Carlo optimization used in DALI.

3. **Dynamic programming with the rotation matrix:** The rotation matrix is used to generate a scoring matrix for dynamic programming, which is then used to find the final alignment.

TM-align is significantly faster than DALI while achieving comparable accuracy.

**6. Foldseek (structural alphabet):**

Foldseek takes a different approach based on representing protein structures as sequences of structural letters.

1. **Structural alphabet:** Define a set of structural letters, each representing a specific local structural motif.

2. **Encode protein structures:**  Represent the 3D structure of each protein as a 1D sequence of structural letters.

3. **Sequence alignment:**  Use highly optimized sequence alignment algorithms to compare the structural letter sequences.  This allows for rapid comparison of large numbers of structures.

Foldseek sacrifices some detail compared to methods that work directly with 3D coordinates, but its speed makes it ideal for large-scale structure searches.  It is orders of magnitude faster than DALI.


These are just some of the most prominent algorithms for protein structure comparison.  The field continues to advance, with new methods being developed to improve both speed and accuracy. The choice of algorithm depends on the specific application and the trade-off between computational cost and the level of detail required.

