---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l16-signal-peptide-cell-localization/","noteIcon":""}
---

---
[[L16_SbioInf_MM.canvas|L16_SbioInf_MM]]

Cellular localization refers to where a protein resides within a cell (e.g., cytoplasm, nucleus, mitochondria). ==Signal peptides are short amino acid sequences within a protein that act as "zip codes," directing the protein to its correct location==.  Predicting these signals is crucial for understanding protein function.

**Slide 2: Peptide Signals: Transport and Localization**

* **Key Concept:** Proteins have intrinsic signals that govern their transport and localization within the cell. 
* **Examples:** The slide lists several types of ==N-terminal signal peptides (located at the beginning of the protein sequence)==:
    * ==**SPs (Secretory Signal Peptides):**  Direct proteins to the secretory pathway, ultimately leading to secretion outside the cell or insertion into the cell membrane.==
    * ==**cTPs (Chloroplast Transit Peptides):** Target proteins to chloroplasts.==
    * ==**mTPs (Mitochondrial Targeting Peptides):** Target proteins to mitochondria.==
* **NLS (Nuclear Localization Signals):** These signals, not always at the N-terminus, direct proteins to the nucleus.

**Slide 3: N-terminal Secretory Signal Peptides (SPs)**

This slide illustrates the mechanism of protein secretion via the endoplasmic reticulum (ER):

1. **Ribosome Binding:**  mRNA binds to free ribosomes in the cytoplasm.
2. **Signal Peptide Recognition:** As the ribosome translates the mRNA, the emerging signal peptide (SP) is recognized by a signal recognition particle (SRP).
3. **SRP Binding:** The SRP binds to both the signal peptide and the ribosome, temporarily halting translation.
4. **ER Docking:** The SRP-ribosome complex docks onto the ER membrane at the SRP receptor.
5. **Translocation:** The ribosome is transferred to a protein channel called the translocon. Translation resumes, and the growing polypeptide chain is threaded through the translocon into the ER lumen.
6. **Signal Peptidase Cleavage:** An enzyme called signal peptidase cleaves off the signal peptide.
7. **Protein Folding and Secretion:** The protein folds into its mature form within the ER lumen and is then transported through the secretory pathway, ultimately being secreted out of the cell.

**Slide 4: Signal Peptide and Signal Anchor**

This slide compares signal peptides (SPs) and signal anchors:

* ==**Signal Peptide:**  Cleaved after translocation, releasing the mature protein into the ER lumen (or extracellular space).==
* ==**Signal Anchor:** Not cleaved.  It becomes a transmembrane domain, anchoring the protein within the membrane. The protein remains embedded in the membrane.==

**Slide 5: Signal Peptides and Signal Anchors (Properties)**

* Found in both prokaryotic and eukaryotic cells.
* Control entry into the secretory pathway.
* Located at the N-terminus, typically 15-40 amino acids long.
* Cleaved from the mature protein during translocation.

**Slide 6: Secretory Signal Peptide: Properties**

This slide describes the characteristic regions within a typical secretory signal peptide:

* ==**n-region:**  A short, positively charged region near the N-terminus.==
* ==**h-region:** A central hydrophobic region.==
* ==**c-region:**  A more polar, uncharged region near the cleavage site.==
* ==**Cleavage site==:** The site where signal peptidase cleaves the signal peptide from the mature protein. Specific amino acid patterns are found near this site, often small and neutral at positions -3 and -1.
* **Variations:**  The exact characteristics of signal peptides can vary between eukaryotes, gram-positive bacteria, and gram-negative bacteria.

**Slide 7: N-terminal Secretory Signal Peptides (SPs) (Comparison)**

This table summarizes the differences in SPs between the three domains of life:

* **Length:** Gram-positive SPs are generally longer.
* **n-region:**  Eukaryotic n-regions are slightly arginine-rich; gram-positive ones are lysine- and arginine-rich.
* **h-region:** Eukaryotic h-regions are short and very hydrophobic; gram-positive ones are longer and less hydrophobic.
* **c-region:** Variations in amino acid composition.
* **-3, -1 Positions:** Almost exclusively alanine in gram-positive bacteria.
* **+1 to +5 Region:** Specific amino acid enrichment in gram-negative bacteria.

**Slide 8: Sequence Logos**

* **Sequence logos** provide a visual representation of the amino acid conservation at each position within a set of aligned sequences. The height of the stack of letters indicates the degree of conservation at that position. The height of each individual letter within the stack represents the relative frequency of that amino acid at that position.  In this case, the logos illustrate the sequence conservation patterns around the cleavage site of eukaryotic signal peptides.  Hydrophobic residues are prevalent in the h-region, while small and neutral residues are often seen at the -3 and -1 positions relative to the cleavage site.



**Slide 11: SignalP Output**

Explanation of the ==different score==s produced by the SignalP software:

* **C-score:** Raw cleavage site score; peaks at the position immediately after the predicted cleavage site.
* **S-score:** Signal peptide score; high for positions within the signal peptide and low after the cleavage site.
* **Y-score:** Combined cleavage site score; combines the C-score and the slope of the S-score to provide a more accurate prediction of the cleavage site.

**Slide 12: How to Predict Signal Peptides (SPs)?**

Example of SignalP output for a secretory protein (EGFR). The scores are plotted along the protein sequence. The output also includes the predicted cleavage site location.




**Slide 14: And What About Signal Anchors?**

* **Signal Anchors:**  A type of "uncleaved signal peptide". They initiate translocation into the ER but are not cleaved by signal peptidase.
* **Result:** The protein becomes a type II membrane protein, anchored to the membrane by the signal anchor sequence, which acts as a transmembrane domain.

**Slide 15: And What About Signal Anchors? (Prediction Challenges)**

Prediction methods sometimes confuse signal peptides, signal anchors, and membrane anchors. This slide shows the distribution of SignalP S-scores for these three types of sequences, illustrating the overlap.

**Slide 16: Large-Scale Application**

Application of SignalP to the *Haemophilus influenzae* genome to predict the number of secretory proteins.  Approximately 15-20% of the proteins were predicted to have cleavable signal peptides.

**Slide 17: Architecture of Hidden Markov Model (HMM)**

Schematic representation of the HMM used in SignalP for signal peptide and signal anchor prediction.![Screenshot 2025-01-08 at 10.20.29.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2010.20.29.png)

**Slide 20: Predicting Subcellular Localization of Proteins**

This slide sets the stage for understanding how proteins are directed to their correct locations within a eukaryotic cell:

* **The Central Dogma and Protein Synthesis:** Most proteins are encoded in the nuclear genome and synthesized by ribosomes in the cytosol (the fluid part of the cytoplasm).
* **The Need for Sorting:** Many proteins must then be transported to specific subcellular compartments (organelles) like the mitochondria, chloroplasts, nucleus, or the secretory pathway (ER, Golgi, lysosomes, etc.).
* **N-terminal Targeting Sequences:** The sorting process often relies on specific amino acid sequences at the beginning (N-terminus) of the protein. These sequences act as "address labels" or "zip codes."

**Slide 21: Targeting Sequences**

This slide delves into the specifics of these targeting sequences:

* **Signal Peptides (SPs):**  Already discussed in detail, these target proteins to the secretory pathway.
* **Mitochondrial Targeting Peptides (mTPs):**
    * Rich in arginine, alanine, and serine.
    * Lack negatively charged amino acids (aspartate and glutamate).
    * Have weak consensus sequences, meaning there's no single, highly conserved sequence.  However, a conserved arginine at position -2 or -3 relative to the cleavage site is common.
    * Cleaved by Mitochondrial Processing Peptidase (MPP). Some are further cleaved by Mitochondrial Intermediate Peptidase (MIP).
* **Chloroplast Transit Peptides (cTPs):**
    * Secondary structure is not well-defined.
    * Limited sequence conservation around the cleavage site.
    * Key features: low content of acidic residues; high content of hydroxylated residues (serine, threonine, tyrosine).
    * Cleaved by Stromal Processing Peptidase (SPP).
    * Thylakoid proteins (proteins within the thylakoid membranes of chloroplasts) have a two-part targeting sequence, with the second part becoming active after the first part is cleaved.



**Slide 23: TargetP**

* **Integrated Prediction:** TargetP is a software tool that integrates and extends existing prediction methods for SPs (SignalP) and cTPs (ChloroP).
* **Subcellular Localization Prediction:** It predicts the localization of a protein to one of four compartments: chloroplast, mitochondrion, secretory pathway, or "other."

**Slide 24: TargetP Architecture**

* **Neural Networks:** TargetP uses a two-layer system of feed-forward neural networks.
* **Decision-Making Unit:** On top of the neural networks, there's a decision-making unit that considers cutoff values and a reliability class (RC) to generate the final prediction.  The RC value indicates the confidence level of the prediction.  The non-plant version of TargetP does not predict cTPs.

**Slide 25: Phobius**

This slide introduces Phobius, a more sophisticated prediction method:

* **Combined Prediction:** Phobius combines transmembrane (TM) topology and signal peptide prediction in a single tool.  This is important because transmembrane helices and signal peptides can sometimes have similar sequence features, leading to mispredictions if considered in isolation.
* **Hidden Markov Model (HMM):** Phobius uses an HMM, a statistical model that represents the different sequence regions (signal peptide, transmembrane helix, cytoplasmic loop, non-cytoplasmic loop) as a series of interconnected states. The HMM learns the probabilities of transitioning between these states and emitting specific amino acids in each state.
* **Improved Accuracy:**  By jointly modeling TM topology and signal peptides, Phobius reduces errors compared to using separate predictors like TMHMM (for transmembrane helices) and SignalP (for signal peptides).  Specifically, the false positive rates for both signal peptides and transmembrane helices are significantly reduced.

**Slide 26: Overview of the Phobius Model**

This slide provides a schematic overview of the Phobius HMM.  It visually represents the different states and their connections:

* **Non-cytoplasm:** Represents regions outside the cytoplasm (e.g., ER lumen, extracellular space).
* **Membrane:** Represents transmembrane helices.
* **Cytoplasm:** Represents cytoplasmic regions.
* **Signal Peptide:**  The signal peptide model (n-region, h-region, c-region) is integrated into the overall model.
* **Loops:**  The model includes states for both cytoplasmic and non-cytoplasmic loops of varying lengths.
* **Globular Domains:**  Represents globular domains outside the membrane.
![Screenshot 2025-01-08 at 10.32.39.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2010.32.39.png)
**Slide 27: The TM Helix Submodel**

This slide zooms in on the part of the Phobius HMM that models transmembrane helices.

* **Three States:** Each helix is represented by three states:
    * *Helix cyt./non-cyt. end:* Models the cytoplasmic or non-cytoplasmic end of the helix.
    * *Helix core:* Models the central hydrophobic core of the helix.
    * *Helix non-cyt./cyt. end:* Models the other end of the helix.
* **Transitions:** The arrows indicate the allowed transitions between states.  The model captures the fact that a helix starts on one side of the membrane, traverses the membrane through the hydrophobic core, and then ends on the other side.
![Screenshot 2025-01-08 at 10.35.00.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2010.35.00.png)
**Slide 28: The Signal Peptide Submodel**

This slide focuses on the signal peptide part of the Phobius HMM:

* **Integration:**  The signal peptide submodel is seamlessly integrated into the overall topology model.
* **States:** The classic n-region, h-region, and c-region of the signal peptide are represented as distinct states.
* **Cleavage Site:**  The model explicitly includes a state for the cleavage site.
* **Loops:** States for short and long non-cytoplasmic loops are also present, acknowledging that the signal peptide can be followed by a loop region before the mature protein starts.
![Screenshot 2025-01-08 at 10.34.51.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2010.34.51.png)
**Slide 29: The Cytoplasmic and Short Non-cytoplasmic Loop Submodels**

This slide details how Phobius models loop regions:

* **Globular/Loop Distinction:**  Phobius distinguishes between globular domains and loop regions.
* **Loop Lengths:** The model allows for loops of different lengths.
* **Helix Ends:**  The loop submodels connect to the helix end states, allowing for transitions between loops and transmembrane helices.
![Screenshot 2025-01-08 at 10.34.45.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2010.34.45.png)
In summary, these last few slides illustrate the power and complexity of the Phobius HMM. By integrating signal peptide and transmembrane helix prediction within a single probabilistic framework, Phobius achieves higher accuracy and a more nuanced understanding of protein topology.

