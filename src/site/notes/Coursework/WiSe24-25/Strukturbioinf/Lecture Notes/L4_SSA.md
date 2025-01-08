---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l4-ssa/","noteIcon":""}
---

---

**The Problem:**

We can determine the 3D structure of proteins experimentally, often using X-ray crystallography. (Task: label the secondary structure state for each residue based on atomic coordinates)  The output is a list of atomic coordinates, typically stored in a PDB (Protein Data Bank) file.  While alpha-helices and beta-strands are visually identifiable in a 3D structure, we need an objective and consistent way to define and assign them.  Different definitions exist, each capturing various aspects of the protein's reality.

**Why is secondary structure assignment needed?**

* **Visualization:** Secondary structure simplifies the representation of complex protein structures.
* **Fold classification:** Databases like SCOP, CATH, and FSSP use secondary structure for classifying protein folds.
* **Sequence alignment improvement:**  Knowledge of secondary structure can help refine sequence alignments.
* **Structure comparison:** Fast methods for comparing protein structures often rely on secondary structure.
* **Comparative modeling & Threading:** Secondary structure is crucial for these homology-based structure prediction methods.

**Different schemes of secondary structure assignment:**

Ideal assignment schemes should agree between proteins of similar structure and be predictable from amino acid sequence.

**History:**

* Pauling and colleagues correctly predicted the idealized alpha-helix, pi-helix, and beta-sheet structures based on intra-backbone hydrogen bonds (1951).  However, they incorrectly believed 3<sub>10</sub> helices wouldn't occur in proteins.
* Initially, crystallographers assigned secondary structure by visual inspection, lacking consistency.
* Kabsch and Sander (1983) introduced the first objective method: DSSP.

**Intra-molecular Hydrogen Bonds in a Protein:**

Hydrogen bonds are crucial for stabilizing secondary structure.  They form between the backbone amide hydrogen and carbonyl oxygen atoms.
![Screenshot 2025-01-07 at 05.04.14.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2005.04.14.png)
**Alpha-helix (α-helix):**

A tightly coiled structure where the backbone forms a right-handed spiral. Hydrogen bonds occur between the carbonyl oxygen of residue *i* and the amide hydrogen of residue *i+4*. The 3<sub>10</sub> helix has *i+3* bonding, and the pi-helix has *i+5* bonding.


**Hydrogen Bond Models:**

Various models exist to computationally identify hydrogen bonds, including angle-distance, Coulombic, and empirical calculations.

* **Angle-distance:**  Assigns hydrogen bonds based on the N-H…O angle (q) and the H…O distance (r<sub>ho</sub>). Typically, q > 120° and r<sub>ho</sub> < 2.5Å.
* **Coulomb:**  Calculates the electrostatic energy of the interaction between partially charged atoms involved in the hydrogen bond. A threshold energy value (e.g., -0.5 kcal/mol) determines whether a bond exists. E < -0.5. ![Screenshot 2025-01-07 at 05.08.00.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2005.08.00.png)
* **Empirical:**  Uses pre-defined parameters to evaluate the hydrogen bond potential.

**Assignment Methods:**

* **DSSP:**  The most widely used method, with over 15,000 citations.
* **STRIDE:** Aimed to reproduce crystallographer assignments, uses empirical hydrogen bond calculation and phi-psi torsion angles.
* **DEFINE & P-Curve:** Less frequently used alternatives.


**DSSP Algorithm (Define Secondary Structure of Proteins):**

1. **Hydrogen Bonds:** Identifies hydrogen bonds using a Coulombic model.

2. **Elementary H-bonding Patterns:** Defines basic structural elements:
    * **Turns (n-turn):** Single hydrogen bond between residues *i* and *i+n* (*n* = 3, 4, or 5).
	    * CO(i), CN(i+n)
    * **Bridges:** Two non-overlapping triplet hydrogen bond patterns between strands:
        * **Parallel:** Hydrogen bonds between  {Hbond(i-1,j) and Hbond(j,i+1)} or {Hbond(j-1,i) and Hbond(i,j+1)}
        * ![Screenshot 2025-01-07 at 05.37.42.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2005.37.42.png)
        * **Antiparallel:** Hydrogen bonds between Antiparallel Bridge(i,j) = Hbond(i,j) and Hbond(i,j)] or Hbond(i-1,j+1) and Hbond(j-1,i+1) ![Screenshot 2025-01-07 at 05.37.58.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2005.37.58.png)


1. **Cooperative Patterns:**  Combines elementary patterns to define higher-order structures:
    * **Helices (n-helix):** Two consecutive n-turns form a minimal helix.  Longer helices are classified: 3<sub>10</sub> ("G"), α ("H"), π ("I").![Screenshot 2025-01-07 at 05.39.09.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2005.39.09.png)
	    * most helices are right handed (+ve chirality)
    * **Ladders:** One or more consecutive bridges of the same type (anti-parallel)
    * **Sheets:** One or more ladders connected by shared residues. Single bridges are denoted "B," and extended ladders (β-strands) are denoted "E." (most sheets are left-handed, -ve chirality)

2. **Irregularities:**  Accounts for imperfections in ideal secondary structure elements.
    * **Helices:** Overlapping helices, missing hydrogen bonds (kinks due to Proline).
    * **Ladders/Sheets:** Bulge-linked ladders where two ladders are connected by a single residue on one strand and less than 5 residues on the other. 

3. **Geometric Structure:** Provides further structural details.
    * **Bends ("S"):** Regions with high curvature (at least 70°).
    * **Chirality:** The handedness of the helix (most are right-handed, or positive).
    * **Disulfide Bonds** and **Chain breaks:** Provide additional information about protein connectivity.

4. **Solvent Exposure:** Calculates the accessible surface area of each residue using a "rolling sphere" model.


**DSSP Structure Summary:**

The final DSSP output represents the secondary structure assignment as a single line aligned with the sequence, using a one-letter code for each residue:

* **H:** 4-helix (α-helix)
* **B:** Residue in isolated β-bridge
* **E:** Extended strand, participates in β-ladder
* **G:** 3-helix (3<sub>10</sub> helix)
* **I:** 5-helix (π-helix)
* **T:** H-bonded turn
* **S:** Bend
* **" " (blank):** Unclassifed (e.g., loop)

In case of overlapping structural elements, a priority order (H > B > E > G > I > T > S) is applied.

**HSSP (Homology-derived Secondary Structure of Proteins):**

A database that expands the information available by using sequence homology to infer secondary structure for proteins without experimentally determined structures.

**STRIDE:**

An alternative method aiming to mimic crystallographers' assignments, employing empirical hydrogen bond calculation and torsion angle criteria.

