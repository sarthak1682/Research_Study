---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l17-coiled-coils/","noteIcon":""}
---

---


**Slide 2: Coiled coils**

This slide defines coiled coils and highlights their key features:

* **Definition:** Coiled coils are a common and versatile protein structural motif.
* **Structure:** They are formed by bundles of α-helices that twist around each other, forming a superhelix.  Think of it like two or more spiral staircases wrapping around each other.
* **Stability:** The stability comes primarily from the "knobs-into-holes" packing.  Hydrophobic (water-fearing) amino acid side chains ("knobs") on one helix fit into spaces ("holes") on the other helix.  This creates a hydrophobic core that's shielded from the surrounding water, which was first proposed by Francis Crick.

**Slide 3: Structure of a coiled coil**

This slide visualizes the structure in more detail:

* **Heptad Repeat:** The image shows a single α-helix with amino acid side chains labeled 'a' through 'g.' This represents the heptad repeat, a characteristic seven-residue pattern often found in coiled coils.
* **'a' and 'd' Positions:**  The 'a' and 'd' positions (shaded red) are typically occupied by hydrophobic amino acids.  These form the "knobs" that interact with the "holes" in the neighboring helix, creating the hydrophobic core.
* **Supercoiling:** The image shows how two α-helices wrap around each other.  The hydrophobic interactions between the 'a' and 'd' residues drive this supercoiling.
* **Aqueous Environment:** The other amino acids ('b,' 'c,' 'e,' 'f,' 'g') are often hydrophilic (water-loving) and face the outside, interacting with the surrounding water.
* **Atomic Structure:** The rightmost image shows a coiled coil's atomic structure determined by X-ray crystallography, confirming the knobs-into-holes packing. The red side chains highlight the hydrophobic residues.
![Screenshot 2025-01-08 at 10.40.56.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2010.40.56.png)


**Slide 4: Coiled Coil Motifs in Known Proteins**

This table lists examples of proteins containing coiled coils, their features, and functions:

* **Parallel/Antiparallel:** The table classifies coiled coils as parallel (helices run in the same direction) or antiparallel (helices run in opposite directions).
* **Number of Strands:** Coiled coils can be two-, three-, or even four-stranded.
* **Structural Features:** This column describes specific structural characteristics of the coiled coil, like stutters (insertions of residues) or skips (deletions of residues) in the heptad repeat, which can affect the supercoiling.
* **Function:** This column explains the role of the coiled coil in the protein's function.  Common functions include:
    * Dimerization/Oligomerization: Bringing together multiple protein subunits.
    * DNA binding (e.g., bZIP proteins).
    * Structural support (e.g., tropomyosin).
    * Membrane fusion (e.g., influenza hemagglutinin).


**Slide 6: Structural and Functional Diversity**



* **Varying number of helices:** From two to more than twenty.
* **Different shapes:** Fibers, levers, tubes, funnels, sheets, spirals, and rings.
* **Supercoiling direction:** Left-handed and right-handed.
* **Local variations in structure:** Departures from a perfect α-helix, such as 3<sub>10</sub>-helices, π-turns, and short β-strands.

**Slide 7: PKN1 Coiled Coil**

This slide focuses on the coiled coil domain of protein kinase C-related kinase 1 (PKN1):

* **Sequence:** The top shows the amino acid sequence of the PKN1 coiled-coil domain, highlighting the heptad repeat ('a' and 'd' positions).![Screenshot 2025-01-08 at 10.42.26.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2010.42.26.png)
* **Structure:** The bottom image displays the 3D structure of the PKN1 coiled coil bound to RhoA proteins.  This illustrates how coiled coils can mediate protein-protein interactions.
![Screenshot 2025-01-08 at 10.42.33.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2010.42.33.png)
**Slide 8: Parameters of Coiled Coils**

This slide summarizes the key parameters that define coiled coils:

* **Pitch:** The distance along the superhelix axis for one complete turn.
* **Pitch Angle:** The angle between the helices and the superhelix axis.
* **Number of Helices:** Coiled coils can consist of 2, 3, 4, or even 5 helices.
* **Orientation:**  The helices can be parallel or antiparallel.
* **Heptad Repeat:** The 'a' and 'd' positions are generally hydrophobic, while the other positions are typically hydrophilic.

**Slide 9: Global Parameters**

This slide visually explains the pitch and pitch angle of a coiled coil.
![Screenshot 2025-01-08 at 10.43.31.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2010.43.31.png)
**Slide 10: Periodicity of Hydrophobic Residues**

This slide illustrates how the periodicity of hydrophobic residues in the heptad repeat leads to supercoiling.  It also shows that all known naturally occurring coiled coils have left-handed supercoiling.
![Screenshot 2025-01-08 at 10.43.56.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2010.43.56.png)
**Slide 11: Side Chain Interactions**

This slide demonstrates the "knobs-into-holes" packing in both parallel and antiparallel coiled coils. It also compares this to the "ridges-into-grooves" packing sometimes seen in globular proteins.

**Slide 12: Discontinuities**

This slide shows how variations in the heptad repeat, such as skip residues (deletions) or stutters (insertions), can introduce discontinuities in the coiled coil, affecting its overall structure.

**Slide 13: Parallel vs. Antiparallel**

This slide compares parallel and antiparallel coiled coils.  Most naturally occurring coiled coils are parallel.  The slide also shows how electrostatic interactions between residues can contribute to coiled-coil stability.

**Slide 14: Antiparallel Examples**

This slide presents examples of proteins with antiparallel coiled-coil domains. These are less common than parallel coiled coils.

**Slide 15: Functions**

This slide summarizes the key functions of coiled coils:

* **Oligomerization:** Bringing together protein subunits.
* **Signal transduction:** Relaying signals within cells.
* **Molecular recognition:** Interacting with other molecules.
* **Mechanical stability:** Providing structural support.


Let's revisit the coiled-coil prediction algorithms, starting with COILS.

**COILS (Slides 17-22)**

* **Core Idea:** COILS predicts coiled coils based on the characteristic heptad repeat (abcdefg) and the preference for hydrophobic residues at positions 'a' and 'd'.  It compares a sequence's amino acid composition within a sliding window to the expected frequencies of amino acids in known coiled coils.

* **Algorithm (Slide 19):**
    1. **Sliding Window:** A window of 28 residues (4 heptads) moves along the protein sequence.  28 is chosen because it's the minimum length that reliably forms a coiled coil.

    2. **Heptad Frames:** The window is assigned all possible heptad repeat frames (7 possibilities because any of the 'a' through 'g' positions can start the heptad).

    3. **Relative Frequencies (Slide 18):** For each residue in each frame, COILS looks up its relative frequency at that particular heptad position from a pre-calculated table (derived from known coiled-coil structures).  This table tells us how often we expect to see a given amino acid at a given position in a real coiled coil.

    4. **Geometric Average:** For each frame, COILS calculates the geometric average of the relative frequencies of all residues within the window.  The geometric mean is less sensitive to extreme values than the arithmetic mean, which is useful here since a single non-hydrophobic residue at an 'a' or 'd' position can disrupt a coiled coil.

    5. **Scoring:** For each residue, COILS gets a set of 196 preliminary scores (7 frames * 28 positions).

    6. **Probability (Slide 20):**  COILS compares the distribution of scores in known coiled coils and globular proteins (non-coiled coils). It then calculates the probability that a given score indicates a coiled coil.

    7. **Output (Slide 21):** COILS outputs the probability of each residue being part of a coiled coil.

* **Problems (Slide 22):** COILS can have a high false-positive rate, especially for sequences rich in lysine (Lys).  Lysine is sometimes found at all heptad positions, and poly-Lysine sequences can score highly even if they don't actually form coiled coils.

**Paircoil (Slides 23-25)**

* **Core Idea:** Paircoil improves upon COILS by considering pairwise correlations between residues in the heptad repeat. This means it doesn't just look at individual amino acid frequencies but also at how often certain pairs of amino acids occur together at specific distances within the heptad.

* **Algorithm:**
    1. **Pairwise Probabilities:** Paircoil uses a database of known coiled coils to calculate the probability of finding a specific pair of amino acids at a given distance (1, 2, or 4 positions apart in the heptad).

    2. **Normalization:**  These pairwise probabilities are normalized by dividing by the frequencies of the individual amino acids in the general protein database (Genpept).  This corrects for biases due to the overall amino acid composition.

    3. **Propensity (Slide 25):** For each residue, Paircoil calculates a "propensity" score based on the normalized probabilities of pairs involving that residue and its neighbors at distances 1, 2, and 4. The propensity reflects the likelihood of that residue being part of a coiled coil, considering the influence of its surrounding residues.

    4. **Windowing:** Similar to COILS, Paircoil uses a sliding window (30 residues), but the scoring within the window is based on the residue propensities rather than just single-residue frequencies.

    5. **Output:** Paircoil outputs a score for each residue, reflecting the likelihood of it being part of a coiled coil.

**Multicoil (Slides 26-30)**

* **Core Idea:** Multicoil extends Paircoil to distinguish between two-stranded and three-stranded coiled coils. It does this by using two separate scoring matrices, one based on two-stranded coiled coils and one based on three-stranded coiled coils.

* **Algorithm:**
    1. **Dual Scoring:**  Multicoil runs Paircoil twice, once with each scoring matrix.

    2. **Multidimensional Score Vector:**  Each residue now gets a two-dimensional score vector, representing its likelihood of being in a two-stranded and a three-stranded coiled coil.

    3. **Classification:**  The relative magnitudes of the two scores are used to classify the residue as two-stranded, three-stranded, or non-coiled coil.

    4. **Probability Output:**  Multicoil outputs the probability of each residue belonging to each class.

**MARCOIL (Slide 31)**

* **Core Idea:** MARCOIL uses a hidden Markov model (HMM) to predict coiled coils. HMMs are good at modeling sequential data, making them suitable for capturing the repeating patterns of coiled coils.

* **Algorithm:**1. 
	* **States:** MARCOIL defines a set of 64 distinct states within its HMM. These states can be categorized as follows:
    
    - **State 0:** This is the "background" state, representing regions that are not part of a coiled coil.
        
    - **States 1-9:** These states correspond to the nine positions that model a coiled-coil heptad repeat and its flanking regions. To understand this, let's break it down further:
        
        - **States 1-4:** These represent the N-terminal flanking region and the first four positions of a coiled coil heptad. They capture the transition from a non-coiled coil region into the coiled-coil structure.
            
        - **State 5:** This state represents the core heptad repeat positions. It is further divided into seven sub-states, 5athrough 5g, corresponding to each position within the heptad (a, b, c, d, e, f, g).
            
        - **States 6-9:** These represent the last four positions of a coiled-coil heptad and the C-terminal flanking region. They capture the transition out of the coiled-coil structure back to a non-coiled coil region.




