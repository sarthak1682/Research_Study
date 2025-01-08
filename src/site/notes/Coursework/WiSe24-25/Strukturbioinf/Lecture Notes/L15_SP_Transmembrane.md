---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l15-sp-transmembrane/","noteIcon":""}
---

---


**Slide 2: Diverse Functions of Membrane Proteins**

This slide emphasizes the importance of membrane proteins, stating that they comprise approximately 30% of all proteins in a cell. It illustrates their diverse functions with examples like electron and proton transporters, channels, receptors, and enzymes, all situated within a cell membrane.
![Screenshot 2025-01-08 at 08.18.26.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2008.18.26.png)
**Slide 3: Schematic Diagram of Typical Membrane Proteins**

This slide provides a detailed schematic of a biological membrane, showing various types of membrane proteins:

* **Integral proteins:** Embedded within the hydrophobic core of the membrane.  They can span the entire membrane (transmembrane) or be partially embedded.
* **Peripheral proteins:** Associated with the membrane surface, often interacting with integral proteins or lipid head groups.
* **Glycoproteins and Glycolipids:**  Proteins and lipids with attached carbohydrate chains, often found on the exterior surface of the membrane.

The slide also highlights the phospholipid bilayer structure of the membrane, with its hydrophilic heads and hydrophobic tails. It differentiates between two main structural motifs of integral membrane proteins: alpha-helical bundles (common in many transmembrane proteins) and beta-barrels (often found in porins).

**Slide 4: Amino Acid Sequence and Transmembrane Disposition of Glycophorin A**

This slide zooms in on a specific example: glycophorin A, a transmembrane protein found in the erythrocyte plasma membrane. It shows the amino acid sequence and how it's arranged within the membrane. The single alpha-helix that spans the membrane is clearly depicted, along with the extracellular glycosylation.  Note the hydrophobic residues within the membrane region.

**Slide 5: Transmembrane Helix**

This slide focuses on the characteristics of a typical transmembrane alpha-helix. It highlights that these helices are approximately 20 amino acids long and consist primarily of hydrophobic residues, which is crucial for their stability within the membrane's hydrophobic core.

**Slide 6: Overall Structure of Bacteriorhodopsin**

This slide presents bacteriorhodopsin, another example of a transmembrane protein, this time with multiple transmembrane alpha-helices. The helices are labeled A-G, and the retinal pigment crucial to bacteriorhodopsin's function is indicated. This illustrates that transmembrane proteins can adopt more complex structures than a single helix.

**Slide 7: Transmembrane Helix Prediction**

This slide shifts to the computational aspect: predicting transmembrane helices from amino acid sequences.  It lists key properties of TM helices that inform these predictions:

* **Apolarity:** Predominantly hydrophobic amino acid composition.
* **Length:** Typically 12-35 residues.
* **Loop Length:** Short loops between TM helices (less than 60 residues).
* **Positive-Inside Rule:**  A tendency for positively charged residues (arginine and lysine) to be located on the cytoplasmic side of the membrane.

The slide mentions that these properties are utilized in Hidden Markov Models (HMMs), a powerful statistical tool for sequence analysis, and introduces TMHMM, a widely used TM helix prediction server with 78% accuracy.

**Slide 8: The Four Major Geometries of Pair-wise TMD Interactions**

This slide details how transmembrane domains (TMDs) can interact. It shows four possibilities based on parallel/antiparallel orientations and left/right-handed helix packing. It highlights “knobs-into-holes” packing and the importance of small residues fitting into the grooves of other helices in right-handed bundles. It also indicates the characteristic amino acid patterns (heptad repeats) and the periodicity within the transmembrane region.

(j,i + 7) for l-handed, i, i+4 for r-handed
![Screenshot 2025-01-08 at 08.31.36.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2008.31.36.png)


**Slide 10: mpstruc Database**
exists

**Slide 11: Ligand-Activated Ion Channel Gating**

![Screenshot 2025-01-08 at 08.36.56.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2008.36.56.png)
**Slide 12: Structural Elements of the K+ Channel Pore**

![Screenshot 2025-01-08 at 08.38.02.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2008.38.02.png)
**Slide 13: AQP1 Water Channel**

This slide focuses on the AQP1 water channel, another important type of membrane protein. It shows both the monomeric structure and the tetrameric assembly of AQP1.  The alignment of AQP1 sequences from different organisms (bacteria, human, and spinach) indicates conserved regions crucial for water transport. The different regions (M1-M8) are marked along with the pore-forming NPA motifs.

**Slide 14: Voltage-Modulated and Mechanosensitive Channel**

This slide discusses another type of ion channel that’s regulated by voltage and mechanical stimuli. The slide shows the structure of the mechanosensitive channel MscS (MscS is from *E. coli*). It presents three different views of the channel: a single subunit, a top-down view of the heptameric assembly, and a side view of the heptamer. The different transmembrane helices and cytoplasmic domains are labeled.

**Slide 15: Structural States Defined for a Typical Helical Transmembrane Protein**

This slide illustrates how the amino acid sequence of a transmembrane protein can be segmented into different structural states, such as "tail," "helix," "loop," etc. The slide provides a schematic diagram of a typical helical transmembrane protein, its amino acid sequence, a simplified sequence representing the different structural states, and the topology of these states within the membrane.
![Screenshot 2025-01-08 at 08.40.35.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2008.40.35.png)
**Slide 16: Structure of *N. meningitidis* OpcA**

This slide shows the structure of OpcA, a beta-barrel protein from *Neisseria meningitidis*. The color-coding indicates the B-factors, a measure of atomic flexibility, with blue representing lower flexibility and red representing higher flexibility. The structure highlights the beta-strands and the location of bound Zn2+ ions. The green highlights the hydrophobic girdles of aromatic residues.
![Screenshot 2025-01-08 at 08.40.43.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2008.40.43.png)

**Slide 18: Hydro-pathy/phobicity/philicity**

This slide introduces the concepts of hydrophobicity, hydrophilicity, and hydropathy:

* **Hydrophobicity:**  The tendency of a molecule or amino acid to repel water ("water fearing").
* **Hydrophilicity:**  The tendency of a molecule or amino acid to attract water ("water loving").
* **Hydropathy:**  A combined term that encompasses both hydrophobicity and hydrophilicity.

These properties are crucial for predicting membrane protein structure as hydrophobic regions tend to reside within the membrane, while hydrophilic regions are typically exposed to the aqueous environment.



**Slide 21: Hydrophobicity and Hydrophilicity (Kyte-Doolittle)**

This slide specifically presents the Kyte-Doolittle hydropathy scale, showing the values assigned to each amino acid. Positive values indicate hydrophobicity, while negative values indicate hydrophilicity.
![Screenshot 2025-01-08 at 08.42.38.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2008.42.38.png)




**Slide 23: Hydropathy Calculations**

example of hydropathy calculation using a sliding window of size 7 and the Kyte-Doolittle scale.

**Slide 24: A Hydropathic Index Plot**


![Screenshot 2025-01-08 at 08.43.05.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2008.43.05.png)




**Slide 31:  Positive Inside Rule Visualization**

This slide visualizes the positive-inside rule. It shows the log ratio of hydrophilic to hydrophobic residues flanking the transmembrane region. Positive values outside and negative values inside the membrane show the greater positive charge inside.

![Screenshot 2025-01-08 at 08.45.10.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2008.45.10.png)



**Slide 34-35: Transmembrane helix propensity and position**

These slides offer further insight into the amino acid composition of transmembrane helices. One table shows the propensity of different amino acids to be found in the central (Pm) and terminal (Pe) regions of transmembrane helices.  The other shows the amino acid composition at different positions within the transmembrane helix. This position-specific analysis helps to refine transmembrane helix predictions.
![Screenshot 2025-01-08 at 08.57.07.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2008.57.07.png)
**Slide 36: Prediction of Transmembrane Helices by a Neural Network**

This slide introduces the concept of using neural networks for transmembrane helix prediction. The diagram illustrates how a neural network takes the protein sequence as input and predicts the location of transmembrane helices.

**Slide 37: Two-Level System of Neural Networks**

This slide expands on the neural network approach, showing a two-level system. The first level uses local sequence information and the second level incorporates global information.
![Screenshot 2025-01-08 at 08.58.39.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2008.58.39.png)
**Slide 38: Training Data**

This slide lists the types of data used to train the neural network: known 3D structures, antibody binding data, and proteolysis data. 

**Slide 39: A Collection of Well-Characterized Integral Membrane Proteins**

This slide exemplifies the type of curated data used for training and benchmarking prediction methods.  It shows a Swiss-Prot-like entry for ATP6 from *E. coli*, highlighting the experimentally determined features, including the transmembrane segment.

**Slide 40-41: TMHMM Introduction and Features**

These slides introduce TMHMM, a widely used hidden Markov model-based method for predicting transmembrane helices. The key features are: it's based on HMMs, **uses topology constraints, distinguishes well between soluble and membrane proteins, and has an accuracy of about 77%**. The limitation of having issues with signal peptides is also noted.

**Slide 42: HMM in General**

This slide provides a general introduction to HMMs, explaining their key characteristics: hidden states, emission probabilities, and transition probabilities.

**Slide 43: Alignment Matrix and Weight Matrix**

This slide shows the relationship between alignment matrices and weight matrices used in sequence analysis. It uses a simplified DNA sequence example to illustrate how weight matrices can be derived from alignments and used for scoring sequences.

**Slide 44-46: Regular Expressions, HMM, Probabilities and Log-Odds**

These slides build up the concept of HMMs and how they’re applied to sequence analysis, specifically focusing on log-odds scores. Slide 44 shows a regular expression which finds sequences with a particular pattern. Slide 45 introduces a simple hidden Markov model, showing the states, emission probabilities, and transition probabilities. Slide 46 demonstrates how HMMs can differentiate between likely and unlikely sequences by calculating probabilities and log-odds scores.  The example is based on a simple motif alignment, showing how a consensus sequence and exceptional/non-consensus sequences are scored.

**Slide 47: Log-Odds Score**

![Screenshot 2025-01-08 at 09.07.37.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2009.07.37.png)

**Slide 48: Probabilities Turned into Log-Odds**

This slide uses the previous motif example to show how probabilities from an HMM are converted into log-odds scores.

**Slide 49: Example HMM for 5' Splice Sites**

This slide provides a practical example of an HMM applied to a biological problem: identifying 5' splice sites in DNA. It shows the states, probabilities, and how a sequence is scored using the Viterbi algorithm (shown as “parsing”) and posterior decoding.

**Slide 50: HMM Advantages**

This slide lists the advantages of using HMMs for transmembrane helix prediction, such as the ability to model helix length, hydrophobicity, charge bias, and grammatical constraints.

**Slide 51: Globular Portions**

This slide discusses how globular portions of membrane proteins are handled in TMHMM. Since these portions don’t have the strong sequence biases seen in TM helices, they are modeled using a simpler approach with a single "globular" state.

**Slide 52-55: TMHMM Architecture and States**

These slides explain the architecture of the TMHMM in detail.  They explain the different states of the HMM, which correspond to different regions of a membrane protein (helix core, helix caps, cytoplasmic loops, non-cytoplasmic loops, and globular regions). Slide 54 explains how the helix is modeled and Slide 55 explains how the loops and caps are modeled.


**Slide 56-57: Training Set and Cross-Validation**

These slides explain how the TMHMM is trained and evaluated. It mentions a dataset of 160 proteins with experimentally determined TM helices, the use of 10-fold cross-validation, and the importance of ensuring no sequence similarity between the cross-validation subsets.  Jack-knife resampling is also mentioned.

**Slide 58: TMHMM Prediction**

This slide shows an example of a TMHMM prediction for gluconate permease 3 from *E. coli*. The plot shows the probability of each residue being in a transmembrane helix, inside the cell, or outside the cell.

**Slide 59: Prediction Errors**

This slide lists the types of errors that can occur in transmembrane helix prediction: over-prediction, under-prediction, false merges, false splits, and inverse topology.



**Slide 62-65: TMHMM Performance and Comparison**

membrane-spanning regions (MSRs), **signal peptides and soluble proteins.**

**Slide 66: Packing of Transmembrane Helices**

This slide illustrates how transmembrane alpha-helices can pack together within the membrane, forming aqueous channels or other functional structures.


**Slide 68-69: Amphiphilicity/Amphipathicity**

These slides introduce the concept of amphiphilicity (or amphipathicity), where a protein domain has both hydrophilic and hydrophobic regions. This property is crucial for membrane-associated proteins.

**Slide 70: Helical Wheel for Prion Protein**

This slide shows a helical wheel plot for a segment of the prion protein. Helical wheel plots are a way to visualize the distribution of hydrophobic and hydrophilic residues within an alpha-helix.

**Slide 71-72: Hydrophobic Moment**

These slides explain the concept of the **hydrophobic moment**, a quantitative measure of amphiphilicity developed by David Eisenberg. Slide 72 shows the hydrophobic moment formula and a graphical representation of how it’s calculated.

**Slide 73: A Gallery of Beta-barrel Membrane Protein Structures**

This slide showcases the diversity of beta-barrel membrane protein structures, including maltoporin, FebA, TolC, and alpha-hemolysin.

**Slide 74: Protein Localization in Bacteria**

This slide reviews bacterial protein localization, highlighting the different compartments where membrane proteins can be found (cytoplasmic membrane, periplasm, outer membrane, etc.).

**Slide 75-76: Architecture and Structure of a Beta-Barrel Membrane Protein**

These slides focus on the architecture of beta-barrel membrane proteins, using OmpX as an example. They show how the beta-strands are arranged to form a barrel and highlight the distribution of amino acids within the barrel. Slide 75 shows the arrangement of amino acids in a B-barrel as a function of distance from the membrane and slide 76 shows different views of the OmpX protein.

**Slide 77: Beta-Barrels: Construction Rules**

This slide summarizes the key structural rules governing beta-barrel formation, including the number of strands, tilt angle, strand connections (turns and loops), and the distribution of amino acid sidechains.



**Slide 79: Abundance of Amino Acids in Beta-Barrels**

This slide compares the amino acid composition of beta-barrels to the overall genomic abundance, showing that the external surfaces are enriched in aromatic residues while the internal residues are enriched in small and polar amino acids.


**Slide 81: Beta-Barrel Finder**

This slide briefly mentions a tool called "Beta-barrel finder" which uses hydropathy analysis, secondary structure prediction, amphipathicity analysis, and similarity searches to identify beta-barrel proteins.

**Slide 82: Neural Network-Based Predictor**

This slide shows the output of a neural network-based predictor for two beta-barrel proteins.

**Slide 83: Suite of Predictors for TM Proteins**

This slide shows a flow chart depicting a suite of predictors that incorporates various methods for predicting both alpha-helical and beta-barrel membrane proteins, including signal peptide prediction.

**Slide 84-86: Re-entrant Regions**

These slides address the challenge of predicting re-entrant regions in membrane proteins, which are segments that dip into the membrane but don't completely cross it. Slide 84 shows the structure of the glycerol channel GlpF and highlights the 'half TM helices'. Slide 85 shows several examples of these segments with different structural motifs and Slide 86 shows examples of interface helix and loop regions where these segments are found.
![Screenshot 2025-01-08 at 09.29.23.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2009.29.23.png)
**Slide 87: TOP-MOD**

This slide shows the architecture of TOP-MOD, an HMM model designed to predict membrane protein topology, including re-entrant regions.


**Slide 89: Protein Structure Prediction Workflow**

This slide presents a broader overview of protein structure prediction methods, including homology modeling, fold recognition, de novo folding, and molecular dynamics. It shows how these methods can be applied to the challenging problem of membrane protein structure prediction.![Screenshot 2025-01-08 at 09.30.17.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2009.30.17.png)


