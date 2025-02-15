---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l25-protein-evo/","noteIcon":""}
---

---
[[L25_SbioInf_MM.canvas|L25_SbioInf_MM]]


**Slide 3: Darwinian Theory of Evolution**

*   **Key Concepts:**
    *   **Undirected, random variation:** Mutations occur randomly, providing the raw material for evolution.
    *   **Natural selection:**  Beneficial variations are more likely to be passed on (fixation), while harmful ones are eliminated (deleterious variation).
    *   **Gradual accumulation:**  Evolution happens through the accumulation of many small changes over long periods.


**Slide 4: The Tree of Life**

*   **Key Concepts:**
    *   **Phenotype comparison:** Early methods of classifying life relied on observable characteristics (like structures).
    *   **Molecular phylogeny:**  A more accurate way to understand evolutionary relationships, using molecular data.
        *   **rRNA molecules:**  Pioneered by Woese, using ribosomal RNA to build evolutionary trees.  Revealed the three domains of life: Bacteria, Archaea, and Eukarya.
        *   **Protein sequence-based trees:**  Can be different from rRNA trees due to phenomena like horizontal gene transfer (where genes are transferred between organisms not through direct descent).

**Slide 5: Neutral Theory**

*   **Key Concepts:**
    *   **Selectively neutral mutations:** A significant portion of fixed mutations have no noticeable effect on the organism's fitness (neither beneficial nor harmful).
    *   **Random drift:**  The frequency of these neutral mutations changes randomly over time.
    *   **Molecular clock:**  A consequence of neutral theory, suggesting that mutations accumulate at a roughly constant rate.
*   **Overview:** This contrasts with Darwinian selection.  Neutral theory proposes that much of molecular evolution is *not* driven by adaptation, but by random chance.

**Slide 6: Molecular Clock Hypothesis**

*   **Key Concepts:**
    *   **Historical context:** Based on early protein sequence data from the 1960s (globins, cytochromes, fibrinopeptides).
    *   **Variable rates:**  Some proteins evolve faster than others.
    *   **Constant rate for a given protein:**  Pauling, Margoliash, and others proposed that *for a specific protein*, the rate of evolution is approximately constant over time.


**Slide 7: Molecular Clock Graph (Dickerson, 1971)**

*   **Title:** Dickerson (1971)
*   **Axes:**
    *   **X-axis:** Millions of years since divergence.
    *   **Y-axis:** Corrected amino acid changes per 100 residues (m).
*   **Data:** Shows the relationship between divergence time and amino acid changes for three different proteins:
    *   **Fibrinopeptides:** Evolve rapidly (steep slope).
    *   **Hemoglobin:** Evolves at an intermediate rate.
    *   **Cytochrome c:** Evolves very slowly (shallow slope).
*   **Key Observation:** The approximately linear relationship for each protein supports the molecular clock hypothesis. The different slopes show that different proteins evolve at different rates.

**Slide 8: Molecular Evolution**

*   **Definition:** The study of changes in genes and proteins across different branches of the tree of life.
*   **Two Steps of Protein Evolution:**
    1.  **Mutation:** Changes in the DNA sequence that codes for the protein.
    2.  **Fixation:** The new variant becomes established in the population.
*   **Fitness Effect:** The probability of fixation depends on how the mutation affects the organism's fitness.
*   **Types of Variants:**
    *   **Neutral/Nearly neutral:**  Governed by genetic drift.
    *   **Deleterious:**  Removed by purifying selection.
    *   **Advantageous:**  Favored by positive selection.

**Slide 9: Detecting Natural Selection**

*   **Key Concept:** Comparing the rates of synonymous and non-synonymous substitutions.
    *   **Synonymous substitutions (Ks):**  DNA changes that *do not* change the amino acid sequence (often neutral).
    *   **Non-synonymous substitutions (KA):**  DNA changes that *do* change the amino acid sequence (more likely to affect function).
*   **Comparing Genes:**
    *   **Orthologs:**  Genes in different species derived from a common ancestor (e.g., human hemoglobin and mouse hemoglobin).
    *   **Paralogs:**  Genes within the same species that arose from gene duplication.
*   **KA/Ks Ratio:**  The key statistic for detecting selection.

**Slide 10: Possible Results (KA/Ks Ratio)**

*   **Interpretations of KA/Ks:**
    *   **KA/Ks = 1 (Neutral selection):**  Synonymous and non-synonymous changes occur at the same rate.  Suggests the gene is not under strong selection (or is a pseudogene).
    *   **KA/Ks < 1 (Negative/Purifying selection):**  Synonymous changes are more frequent.  Indicates that most amino acid changes are harmful and are being removed.
    *   **KA/Ks > 1 (Positive/Disruptive selection):**  Non-synonymous changes are more frequent.  Suggests that changes in the amino acid sequence are being favored, possibly due to adaptation to different functions.
*   **Example:**  Compares human and mouse genes.  Highly conserved genes (low KA/Ks) are involved in essential cellular functions.  Genes with high KA/Ks are often involved in defense and immunity.

**Slide 11: Purifying Selection**

*   **Definition:** Selection against deleterious mutations.
*   **Factors Influencing Protein Evolution Rate:**
    *   **Overall protein importance:**  More important proteins evolve more slowly.
    *   **Structural constraints:**  Changes that disrupt protein structure are less likely to be tolerated.
    *   **Pleiotropy:**  Genes that affect multiple traits (are pleiotropic) are often more constrained.
    *   **Protein expression:** Highly expressed proteins often evolve more slowly.

**Slide 12: Functional (Fitness) Density**


*   **Key Concept:**  The proportion of sites in a protein that are important for its function (Zuckerkandl, 1976).
*   **Selection Acts on More Than Just Function:**  Can also affect things like translational efficiency.
*   **Considerations:**
    *   Proportion of sites under selection.
    *   Strength of selection at those sites.
*   **Definition of Fitness Density:** How much a mutation changes the protein's fitness compared to the wild type.
*   **Complication:** Compensatory mutations (where one mutation compensates for the effect of another).

**Slide 13: Mutation Effects and Conservation**

* 
*   **Visualizations:** Shows two 3D models of a DNA repair enzyme.
    *   **Left:** Colored by "mutability" (how much a mutation at that site abolishes function).  Red = most mutable, blue = least mutable.
    *   **Right:** Colored by evolutionary conservation (variability among homologous proteins).  Red = most conserved, blue = least conserved.
*   **Key Observation:**  The least mutable sites (left) are generally the most conserved sites (right).  Active site residues (indicated by the arrow) are both highly conserved and highly sensitive to mutations.

**Slide 14: Gene Dispensability and Evolution Rate**

*   **Key Concepts:**
    *   **Gene dispensability:** How much an organism can tolerate the loss of a gene (tested by experimental knockout).
    *   **Nearly neutral mutations:**  A major driver of evolutionary change.
    *   **Hypothesis:**  More dispensable proteins can tolerate more nearly neutral mutations, and thus evolve faster.
*   **Graph:** Shows the relationship between gene dispensability (lethal, defective growth, normal growth) and the rate of protein evolution.  Proteins from genes with lethal knockouts evolve slowest, and those with normal growth evolve fastest.

**Slide 15: Problems with Gene Dispensability**

*   **Limitations:**
    *   Mainly useful for comparing essential vs. non-essential genes.
    *   Explains only a small fraction of the variation in evolutionary rates.
    *   Fitness is measured under artificial lab conditions.
    *   Measures fitness for the *entire* gene, but evolution acts on point mutations.
    *   Dispensability is more correlated with the *propensity of gene loss (PGL)*.

**Slide 16: Protein Structure and Stability**

*   **Key Points:**
    *   Mutations often affect protein stability and activity.
    *   Most mutations are destabilizing.
    *   Even small reductions in folding efficiency can lead to aggregation and toxicity.
    *   Selection acts to maintain the stability of proteins.

**Slide 17: Classification of Extremophiles**
 
*   **Content:**  A table listing different types of extremophiles (organisms that thrive in extreme environments), categorized by the environmental parameter they tolerate (temperature, pressure, salinity, pH, etc.).
*   **Examples:** Provides specific examples of organisms for each category (e.g., *Pyrolobus fumarii* for hyperthermophiles).
* **Importance** This slide sets the stage for the discussion on thermophiles by introducing the wide range of extremophiles.

**Slide 18: Temperature Limits for Life**
 
*   **Content:** A graphic showing the temperature ranges tolerated by different groups of organisms.
*   **Key Groups:**
    *   **Mesophiles:**  Grow at moderate temperatures.
    *   **Thermophiles:**  Grow at high temperatures.
    *   **Hyperthermophiles:** Grow at very high temperatures (e.g., sulfur-dependent archaea).
    *   **Psychrophiles:** Grow at low temperatures.
*   **Overview:**  Illustrates the diversity of life in terms of temperature tolerance, focusing on thermophiles.

**Slide 19: Sequences from Thermophilic Organisms are Shorter**

  
*   **Content:** A heatmap comparing the proteomes (sets of proteins) of thermophilic and mesophilic organisms.
*   **Key Observation:**  The heatmap shows a pattern indicating that proteins from thermophiles tend to be shorter than their homologs in mesophiles.  This is one adaptation to high temperatures.

**Slide 20: Thermophilic Deletions in Exposed Loops**
 *   **Content:** A graph comparing the likelihood of gaps (deletions) in protein sequences from thermophiles and mesophiles, categorized by secondary structure (helix, strand, loop) and location (buried, exposed).
*   **Key Observation:** Thermophiles show a higher likelihood of deletions in *exposed loops*.  This suggests that shortening loops, which are often on the surface of the protein, is a strategy for increasing thermostability.

**Slide 21: Salt Bridges**
 
*   **Content:**  A diagram of a salt bridge between two amino acid residues (glutamic acid and arginine) in a protein.
*   **Key Concept:**  Salt bridges are electrostatic interactions between oppositely charged amino acid side chains.  They contribute to protein stability, especially in thermophiles.

**Slide 22: Factors Determining Thermophilic Protein Stability**

*   **Summary of Adaptations:**
    *   Shorter sequences.
    *   More deletions in exposed loops.
    *   Greater content of charged residues (to form salt bridges).
    *   More prevalent intra-helical salt bridges.
*   **Overview:** This slide summarizes the key structural features that make proteins from thermophiles more stable at high temperatures.

**Slide 23: Evolutionary Rates and Disease**
	
*   **Key Ideas:**
    *   Disease-causing mutations create selective pressure.
    *   We can use variation in evolutionary rates to predict the severity of medically important phenotypes.  Sites that are highly conserved are more likely to be functionally important, so mutations at those sites are more likely to cause disease.

**Slide 24: Possible Approaches**
 
*   **Strategies for Predicting Disease-Causing Mutations:**
    *   **Sequence homology:** Mutations are more likely to be harmful at positions that are highly conserved across evolution.
    *   **Structure:**  Disease-causing mutations often share common structural features that distinguish them from neutral substitutions.

**Slide 25: Amino Acid Mutation Frequencies**
 
*   **Content:**  Four matrices showing amino acid mutation frequencies:
    *   **(a) Expected:**  Based on codon frequencies (what you'd expect by chance).
    *   **(b) Nonsynonymous benign:**  From SNPs (single nucleotide polymorphisms) that don't cause disease.
    *   **(c) Disease:**  From mutations known to cause genetic diseases.
    *   **(d) Interspecies (PAM1):**  From comparisons between species.
*   **Key Observation:**  The patterns in the matrices are different.  Disease-causing mutations (c) are less likely to be conservative (close to the diagonal) than benign SNPs (b) or interspecies differences (d).

**Slide 26: Relative Mutation Probabilities**

*   **Content:** Two graphs:
    *   **(a) Conservation:** Shows how the probability of different types of mutations (disease, synonymous, nonsynonymous benign) changes with evolutionary conservation (measured by relative entropy).  Highly conserved sites are more likely to have disease-causing mutations.
    *   **(b) Solvent Accessibility:** Shows how mutation probabilities change with solvent accessibility.  Buried sites are more likely to have disease-causing mutations.

**Slide 27: Mutations in OMIM and dbSNP**

*   **Content:**  A scatter plot comparing the frequency of different types of mutations in the OMIM database (disease-causing mutations) and the dbSNP database (common polymorphisms).
*   **Key Observation:**  Mutations that cause large changes in hydrophobicity are more frequent in OMIM (disease) than in dbSNP (benign).

**Slide 28: Summary (Structural Features and Disease)**
 
*   **Structural Features Associated with Disease-Causing Mutations:**
    *   Size changes in the hydrophobic core.
    *   Introduction of buried charged residues.
    *   Disruption of protein-protein interactions.
    *   Disruption of hydrogen-bonding networks.
    *   Interference with DNA binding.
    *   Breaking disulfide bonds.
    *   Mutation of catalytic residues.
    *   Mutation of metal-binding residues.
    *   Disrupting quaternary structure (how protein subunits assemble).
    * **Summary** Lists the ways mutations can lead to disease by affecting protein structure.

**Slide 29: PolyPhen Protocol**
 
*   **Content:**  A flowchart describing the PolyPhen method for predicting the impact of amino acid substitutions.
*   **Key Steps:**
    *   Gathers data from various databases (SWISS-PROT, OMIM, HGBASE, CHAK, HSSP).
    *   Identifies disease-causing mutations and polymorphisms.
    *   Maps these variations onto protein structures.
    *   Searches for substitutions between proteins and their homologs in other species.
*   **Goal:** To predict whether a given amino acid substitution is likely to be harmful.

**Slide 30: SIFT**
  
*   **Key Idea:**  SIFT uses sequence conservation to predict whether an amino acid substitution will be tolerated.  Highly conserved positions are less likely to tolerate substitutions.

**Slide 31: Protein Designability**
 
*   **Key Concept:** The number of different amino acid sequences that are compatible with a given protein structure.
*   **Variability:** Designability varies greatly across different protein structures.
*   **Diagram:**  A hierarchical diagram showing the relationship between fold, superfamily, and family.

**Slide 32: Structure Occupancy**

*   **Title:** Structure occupancy in a complete enumeration of compact lattice polymers and the concept of designability
*   **Content:**  A graph showing the distribution of the number of sequences per structure in a simplified model (lattice polymers).
*   **Key Observation:**  A small number of structures are highly "designable" (many sequences can fold into them), while most structures are not.

**Slide 33: Designability and Evolutionary Rate**
 
*   **Diagram:**  Shows the relationship between designability, mutational tolerance, and evolutionary rate.
*   **Key Idea:**  Highly designable proteins (those with many possible sequences) are more tolerant to mutations and tend to evolve more slowly.

**Slide 34: Designability and Disease Frequency**
 
*   **Content:**  A table comparing the designability of proteins associated with disease and non-disease proteins.
*   **Key Observation:** Disease proteins tend to be *less* designable than non-disease proteins.  Proteins associated with common diseases are less designable than those associated with rare diseases.

**Slide 35: Position in Biological Networks**
 
*   **Key Concepts:**
    *   Protein structure is constrained by the need to interact with other proteins.
    *   Interactions increase fitness density and reduce evolutionary rate.
*   **Diagram:**  Shows a protein interacting with multiple other proteins, and a network diagram representing these interactions.

**Slide 36: Evolutionary Rate in Protein Interaction Network**
 
*   **Content:** A graph and a causal model.
    *   **Graph:** Shows a negative correlation between the number of protein interactions and the evolutionary rate (K).
    *   **Causal Model:**  Explores two hypotheses:
        1.  Interactions impose structural constraints (direct effect).
        2.  Proteins with more interactions have a greater effect on fitness (indirect effect).
*   **Conclusion:** The second hypothesis is rejected; the effect of interactions on evolutionary rate is not mediated by protein fitness effect.

**Slide 37: Biases in Interaction Data**

*   **Key Points:**
    *   The apparent relationship between interaction number and evolutionary rate is largely due to biases in the data (more interactions are counted for abundant proteins).
    *   The strongest correlation is between evolutionary rate and protein *abundance*.

**Slide 38: No Simple Dependence**
*   **Content:**  A humorous image of a hand stamping a document, emphasizing the conclusion.
*   **Key Idea:**  There's no straightforward relationship between the number of interactions and evolutionary rate, except perhaps for proteins with a very large number of interactions.

**Slide 39: Transient vs. Obligate Interactions**

*   **Key Distinction:**
    *   **Obligate interactions:**  Stable complexes where the subunits are always found together.
    *   **Transient interactions:**  Temporary interactions.
*   **Evolutionary Consequences:**
    *   **Obligate:**  Residues in the interface evolve slowly and coevolve with their partners.
    *   **Transient:**  Interface residues evolve faster, with less evidence of coevolution.

**Slide 40: Multi-protein Complexes and Selection**
 
*   **Content:**  Four graphs examining the relationship between protein complex membership and evolutionary rate (dN/dS).
*   **Key Observations:**
    *   Proteins in complexes tend to evolve more slowly.
    *   The more complexes a protein participates in, the slower it tends to evolve.

**Slide 41: Interactions and Ortholog Probability**
 
*   **Content:**  Four graphs showing the relationship between the number of protein interactions and the probability of finding an ortholog in another species.
*   **Key Observation:**  Proteins with more interactions are more likely to have orthologs in other species (they are more conserved).

**Slide 42: Centrality and Lethality**
 
*   **Content:** A network diagram and two graphs.
    *   **Network:**  Shows a protein interaction network, with highly connected proteins ("hubs") highlighted.
    *   **Graphs:**
        *   Shows a power-law distribution of the number of connections per protein.
        *   Shows that proteins with more connections are more likely to be essential (lethal if knocked out).
*   **Key Idea:**  "Hub" proteins, which are central to the network, are often essential for survival.

**Slide 43: Gene Expression and Evolution Rate**
 
*   **Content:** A graph showing a strong negative correlation between gene expression level and the rate of protein evolution.
*   **Key Observation:** Highly expressed proteins evolve more slowly.

**Slide 44: Expression Breadth and Level**
 
*   **Key Concepts:**
    *   **Expression breadth:**  The number of different tissues in which a gene is expressed.
    *   **Expression level:**  The amount of mRNA or protein produced.
*   **Observations:**
    *   Broadly expressed proteins evolve more slowly.
    *   Alternatively spliced exons evolve faster.
    *   Expression breadth and level are correlated.
    *   In mammals, breadth is a better predictor than level.
    *   In yeast (which lacks tissue-specific expression), expression level explains a large fraction of the variation in evolutionary rate.

**Slide 45: Summary: Purifying Selection**
 
*   **Four Key Factors:**
    1.  Gene dispensability
    2.  Protein structure and stability
    3.  Pleiotropy (involvement in multiple interactions and processes)
    4.  Expression level
*   **Strongest Predictor:** Expression level (especially in unicellular organisms).
*   **Possible Explanation:** Selection for robustness against mistranslations (errors in protein synthesis). Highly expressed proteins need to be more robust to errors.

**Slide 46: Positive Selection**
 
*   **Key Concept:** Selection for advantageous protein changes.
*   **Observations:**
    *   Can drive a significant fraction (20-45%) of amino acid substitutions.
    *   The proportion of adaptive substitutions is relatively constant across the genome.
    *   Fast-evolving genes have more *both* adaptive and neutral substitutions.
    *   Neutral evolution may play a role in adaptation by allowing exploration of sequence space.
    *   Genes with high fitness density may be less likely to contribute to adaptation.

**Slide 47: Positive Selection (Examples)**
 
*   **Driving Forces:**
    *   **Arms races:**  Between competitors (e.g., host-parasite interactions).
    *   **Compensatory substitutions:**  One mutation compensates for the effect of another.
    *   **Adaptation:**  To new or changing environments.
*   **Examples:**
    *   Immunity genes (evolving rapidly due to host-pathogen interactions).
    *   Proteins involved in sensory perception, brain size, and language processing (in primates).
    *   Genes expressed in the central nervous system of primates.

**Slide 48: Detecting Positive Selection (Detailed Example)**
 
*   **Content:**  A complex diagram illustrating how positive selection can be detected by comparing protein sequences from different species.
*   **Key Concepts:**
    *   **dN/dS ratio:**  Compares the rate of non-synonymous (dN) and synonymous (dS) substitutions.
    *   **dN/dS < 1:**  Purifying (negative) selection.
    *   **dN/dS = 1:**  Neutral evolution.
    *   **dN/dS > 1:**  Positive selection.
*   **Example:**  Shows a hypothetical scenario of a virus interacting with a host receptor.  Positive selection favors changes in the receptor that prevent viral binding, and the virus evolves to overcome these changes (an "arms race").

**Slide 49: Distribution of dN/dS Values**
 
*   **Content:**  A histogram showing the distribution of dN/dS values for a large set of human and mouse orthologous genes.
*   **Key Observation:**  Most genes have dN/dS < 1 (purifying selection), but a small number have dN/dS > 1 (positive selection).  Specific genes with high dN/dS are labeled.

**Slide 50: Selection on NPC1** 
*   **Content:** A diagram of the NPC1 protein, showing its membrane topology and regions under different selective pressures.
*   **Key Points:**
    *   NPC1 is involved in cholesterol transport and is also a receptor for Ebola virus.
    *   The diagram shows regions under strong negative selection (blue) and sites under positive selection (red).
    *   Positive selection is likely driven by the interaction with filoviruses (Ebola, Marburg).

**Slide 51: High-Throughput Methods** 
*   **Content:** A table listing different protein variables (dispensability, functional density, expression, etc.) and examples of high-throughput methods used to measure them.
*   **Key Idea:**  Modern genomics allows us to measure these variables on a large scale, providing data for studying protein evolution.

**Slide 52: Variables Associated with Evolution Rate**

*   **Title:** Table 1. Variables that have been associated with protein evolutionary rates, using different surrogates
*   **Content:** A table summarizing various factors that have been correlated with protein evolutionary rates, along with the surrogates used to measure them and comments on the strength and reliability of the associations.
*   **Key Factors:**  Expression levels, expression breadth, essentiality, dispensability, density of contact functions, cost of biosynthesis, functional category, modularity, intronic structure.
* **Importance** Very important slide, because it summarizes key ideas and results from the presentation.

**Slide 53: Interdependence of Factors** 
*   **Content:** A diagram showing the complex relationships between different factors that influence protein evolution (mutation rate, recombination rate, expression level, protein interactions, gene dispensability).
*   **Key Idea:**  These factors are not independent; they influence each other in complex ways.

**Slide 54: Simplified Relationship Diagram**
 
*   **Content:** A simplified diagram showing the relationships between functional density, modularity, dispensability, protein expression, and evolutionary rate.

**Slide 55: Correlations Between Genomic Variables**

*   **Title:** Table 1. The correlations between the seven genomic variables. (Asterisks denote the correlations that are significantly different from zero, p<0.05.)
* **Content** A correlation matrix showing the relationships between various genomic variables.
* **Variables:** NP (number of paralogs), PPI (number of physical interactions), GI (number of genetic interactions), PGL (propensity of gene loss), ER (evolution rate), EL (expression level), KE (fitness effect of gene knockout).

**Slide 56: Principal Component Analysis**

*   **Title:** Contributions of the quantitative genome-related measures to the first three principal components
*   **Content:**  Two plots showing the results of a principal component analysis (PCA) of the genomic variables.
*   **Key Idea:** PCA helps to identify the major axes of variation in the data and how the different variables contribute to these axes.(Status, Adapatability, Reactivity)

**Slide 57: Phenomic and Evolutionary Variables**

*   **Content:**  A diagram showing the relationships between "phenomic" variables (related to the organism's phenotype) and "evolutionary" variables.

**Slide 58: Gene Status**
 
*   **Content:**  A graph showing the relationship between "phenomic" variables and "evolutionary" variables, defining a concept of "gene status."
*   **Key Idea:**  Genes can be characterized by their position along this axis, reflecting their evolutionary and functional properties.

**Slide 59: Evolution by Gene Duplication**
 
*   **Key Concepts:**
    *   **Ohno, 1970:**  Proposed that gene duplication is a major driver of evolution.
    *   **Neofunctionalization:**  After duplication, one copy can acquire a new function while the other maintains the original function.
    *   **Challenge to Gradualism:**  Duplication provides a mechanism for larger evolutionary changes, challenging the idea that evolution always proceeds through tiny, incremental steps.

**Slide 60: Mechanisms of Gene Duplication**
 
*   **Content:**  Diagrams illustrating different mechanisms of gene duplication:
    *   **Retrotransposition:**  An RNA intermediate is reverse-transcribed into DNA and inserted into the genome.
    *   **Segmental Duplication (unequal crossing over):**  Misalignment during recombination leads to duplication of a segment of DNA.
    *   **Segmental Duplications (non-homologous):** Replication errors.![Screenshot 2025-02-11 at 00.04.51.png](/img/user/Attachments/Screenshot%202025-02-11%20at%2000.04.51.png)
1. Retrotransposition:

- This process begins with a DNA sequence being transcribed into mRNA
- The mRNA is then reverse transcribed back into DNA by reverse transcriptase
- This DNA copy is then integrated back into the genome at a new location
- Notable characteristic: The new copy lacks introns since it came from processed mRNA

2. Segmental Duplication through Unequal Crossing Over:

- Occurs during recombination between similar but misaligned sequences
- Often happens between repeated elements like Alu sequences
- Results in tandem duplication where the duplicated segment appears next to the original
- One chromosome ends up with an extra copy while the other loses a copy

1. Non-homologous Segmental Duplication:

- Caused by replication errors during DNA synthesis
- Can occur when the replication machinery skips or re-replicates a segment
- Results in tandem duplication of the affected segment
- Does not require sequence similarity like unequal crossing over does


**Slide 61: Evolutionary History with Duplication**

*   **Content:** A diagram showing how gene duplication and speciation events can lead to a complex pattern of orthologs and paralogs.

**Slide 62: Globin Family**

*   **Content:**  A diagram showing the evolutionary history of the globin gene family, with multiple duplication events leading to different globin genes (myoglobin, alpha-globin, beta-globin, etc.).

**Slide 1: Gene loss**![Screenshot 2025-02-11 at 00.14.08.png](/img/user/Attachments/Screenshot%202025-02-11%20at%2000.14.08.png)

*   **Concept:** This slide visually illustrates how genes can be lost during evolution in different lineages. It sets the stage for discussing gene loss as an evolutionary process.

**Slide 2: Orthologous and paralogous relationships between three ancestral genes and their descendants in three species**

*   **Image:** A more complex gene tree diagram is presented.
    *   At the top is the "Family ancestor" with three genes labeled X, Y, and Z.
    *   "LCA" denotes the Last Common Ancestor.
    *   Numbers 1, 2, and 3 likely indicate gene duplication events.
    *   The tree branches out into three species A, B, and C.
    *   The labels (XA, XB, XC, etc.) represent gene copies in each species.
    *   **Color-coding:** The consistent colors (e.g., all 'X' genes in shades of green, 'Y' in orange, 'Z' in blue) help track the origin of each gene copy.
*   **Concept:** This slide illustrates:
    *   **Speciation:** The branching of the tree represents speciation events, leading to different species (A, B, C).
    *   **Gene Duplication:**  Events 1, 2, and 3 show gene duplication within lineages. For example, gene Y in the LCA leads to YA1 and YA2 after duplication 1.
    *   **Orthologs:** Genes in different species that originated from a single gene in the last common ancestor (speciation event). For example, XA, XB, and XC are orthologs of ancestral gene X.
    *   **Paralogs:** Genes within the same species (or genome) that originated from gene duplication events. For example, YA1 and YA2 in species A are paralogs.
    *   The slide visually clarifies the relationships between gene copies arising from both speciation and duplication.
![Screenshot 2025-02-11 at 00.16.25.png](/img/user/Attachments/Screenshot%202025-02-11%20at%2000.16.25.png)
**Slide 3: Homology terms and definitions**

*   **Table:** It is divided into two main sections: "Homologs" and "Paralogs".
    *   **Homologs (Genes sharing a common origin):**
        *   **Orthologs:** Defined as genes originating from a single ancestral gene in the last common ancestor of the compared genomes (speciation).
        *   **Pseudoorthologs:** Genes that are actually paralogs but appear orthologous due to differential gene loss.
        *   **Xenologs:** Homologous genes acquired through horizontal gene transfer (XGD).
        *   **Co-orthologs:**  Multiple genes in one lineage that are collectively orthologous to one or more genes in another lineage due to lineage-specific duplications. Inparalogs are mentioned as members of co-orthologous sets relative to speciation.
    *   **Paralogs (Genes related by duplication):**
        *   **Inparalogs (symparalogs):** Paralogs arising from duplication *after* a speciation event. Defined relative to a speciation event.
        *   **Outparalogs (alloparalogs):** Paralogs arising from duplication *before* a speciation event. Also defined relative to a speciation event.
        *   **Pseudoparalogs:** Homologous genes that appear as paralogs in genome analysis but are a result of vertical inheritance and horizontal gene transfer (HGT).
*   **Concept:** This slide is a glossary of important terms in evolutionary and comparative genomics. It provides precise definitions to understand gene relationships and evolutionary history.

**Slide 4: Pseudogenes: definition**

*   **Bullet Points:**
    *   **Definition:** Pseudogenes are nonfunctional DNA sequences derived from functional genes, exhibiting degenerative features like premature stop codons and frameshift mutations that prevent their expression.
    *   **Similarity to Paralogs:** They are characterized by close similarity to one or more paralogous genes but are non-functional.
    *   **Lack of Function:** The lack of function results from failures in transcription or translation, or production of a protein with a non-functional repertoire compared to the normal paralog.
    *   **Nucleotide Sequence Differences:** A key feature is that their nucleotide sequences differ from functional paralogs at crucial points, leading to their non-functionality.

*   **Concept:** This slide clearly defines what pseudogenes are, emphasizing their origin from functional genes, their non-functionality, and the molecular basis of this non-functionality.

**Slide 5: Nonprocessed (conventional) pseudogenes**

*   **Diagram:** A schematic diagram illustrates the process.
    *   **Gene Duplication:** Starts with "Gene duplication" of gene A, resulting in two identical copies.
    *   **Selection Pressure:** "Selection pressure" acts on only one copy (the "top" one in the diagram) to maintain the "Original function".
    *   **Sequence Divergence:** The "bottom" copy is under less selection pressure and undergoes "Sequence divergence". This divergence can be "Slow" or "Rapid".
    *   **Outcomes of Divergence:**
        *   **No function (ΨA):**  The diverged copy accumulates deleterious mutations (represented by vertical bars) and becomes a nonfunctional pseudogene (ΨA).  It may still be transcribed for a while but eventually becomes transcriptionally silent.
        *   **Related function (A2):** In some cases, mutations might lead to a different expression pattern or a new, advantageous property (A2). This is an example of gene duplication leading to new function (neofunctionalization or subfunctionalization, though not explicitly stated here).
    *   **Tandem Gene Duplication:**  The bottom text mentions that in tandem duplications, sequence exchanges can occur between copies, slowing down divergence.
*   **Bullet Points:** Summarize the key points of the diagram.
*   **Concept:** This slide explains the "birth-and-death" model of gene evolution where duplication provides raw material for divergence.  It focuses on how nonprocessed pseudogenes arise from gene duplication and subsequent functional loss in one copy, while the other copy retains the original function.

**Slide 6: Processed pseudogenes**

*   **Diagram:**  A step-by-step diagram illustrates the process:
    *   **Functional gene (DNA):** Starts with a functional gene in the DNA.
    *   **transcription/splicing:** The gene is transcribed and spliced to produce mRNA.
    *   **RNA:**  The mRNA molecule is produced.
    *   **reverse transcription:** The mRNA is reverse transcribed into DNA (cDNA).
    *   **DNA (cDNA):** The cDNA is generated.
    *   **re-integration:** The cDNA is re-integrated into the genome at a new location.
    *   **pseudogene:** The re-integrated cDNA becomes a processed pseudogene.
*   **Text Description:**  Explains that processed pseudogenes arise from the integration of a cDNA copy of mRNA back into the genome.
    *   **Reverse Transcription:**  The process of copying mRNA to DNA.
    *   **cDNA:** Complementary DNA.
    *   **Integration Location:** cDNA can integrate into the same or a different chromosome than the original gene.
*   **Concept:** This slide details the mechanism of processed pseudogene formation, highlighting the involvement of mRNA, reverse transcription, and genomic re-integration. Processed pseudogenes lack introns and often have poly-A tails, characteristics derived from their mRNA origin


**Slide 7: Evolution of new protein functions**

*   **List of Mechanisms (with brief descriptions):**
    *   **gene recruitment (function depends upon environmental factors):**  An existing gene is "recruited" to perform a new function, often in response to environmental changes.
    *   **gene duplication:** Duplication provides an extra copy of a gene that can then evolve a new function while the original copy maintains its role.
    *   **incremental mutations:** Gradual accumulation of mutations in a gene can lead to changes in its protein product and potentially new or modified functions.
    *   **gene fusion:** Combining parts of two or more genes to create a new gene with a novel function.
    *   **oligomerisation:**  Proteins assembling into oligomers (multimeric complexes) can gain new functions through subunit interactions and allosteric regulation.
    *   **post-translational modification:** Chemical modifications to a protein after translation can alter its activity, localization, or interactions, effectively leading to functional diversification.
![Screenshot 2025-02-11 at 00.21.26.png](/img/user/Attachments/Screenshot%202025-02-11%20at%2000.21.26.png)




**Slide 8: Evolution by gene duplication and domain insertion**
![Screenshot 2025-02-11 at 00.22.04.png](/img/user/Attachments/Screenshot%202025-02-11%20at%2000.22.04.png)

*   **Concept:** This slide visually demonstrates how combining gene duplication (increasing gene copy number) and domain insertion (adding functional modules) can lead to increased protein complexity and functional diversity.

**Slide 9: Internal gene duplication cont**
 *internal* gene duplication, meaning duplication of domains or exons within a gene.
*   **Bullet Points:** Lists examples of consequences of internal gene duplication:
    *   **increase in gene size via duplication of domains (exons):**  The primary effect is an increase in the gene's size.
    *   **aka gene elongation:**  Internal duplication leads to gene elongation.
    *   **dosage repetition - ubiquitin:** Example of dosage repetition – increasing the number of copies of a domain, as in ubiquitin.
    *   **structural extension - collagen:** Example of structural extension – lengthening a protein, as in collagen.
    *   **domain divergence - immunoglobulins:** Example of domain divergence – duplicated domains can diverge in function, as seen in immunoglobulins.
*   **Diagram:** Shows a gene with three domains (A, B, C) and the effect of "Duplication of gene segment B".
    *   Domain B is duplicated in tandem, resulting in a gene with domains A, B, B, C.

![Screenshot 2025-02-11 at 00.24.36.png](/img/user/Attachments/Screenshot%202025-02-11%20at%2000.24.36.png)
**Slide 10: Internal gene duplication cont**

*   **Title:** "Internal gene duplication cont" -  Continues the discussion on internal gene duplication and its relationship to protein domains and exons.
*   **Bullet Points:** "Relationships between domains and exons may be:"  lists different possible relationships:
    *   **exact:**  One exon corresponds to one domain.
    *   **approximate:**  Exon boundaries roughly align with domain boundaries.
    *   **one exon encodes 2 or more domains:**  A single exon can encode multiple domains.
    *   **one domain encoded by 2 or more exons:** A domain can be split across multiple exons.
    *   **complete lack of correspondence:**  No clear relationship between exon and domain boundaries.
    *   **Range between the extremes:**  Emphasizes that the actual relationship can vary.
*   **Diagrams:** Illustrate two scenarios:
    *   **exact:**  Exon boundaries perfectly match domain boundaries.  Each colored box likely represents both an exon and a domain.
    *   **example of everything:** Shows a more complex and realistic scenario where exon and domain boundaries are not neatly aligned, and there's a mix of relationships listed in the bullet points.
![Screenshot 2025-02-11 at 00.24.56.png](/img/user/Attachments/Screenshot%202025-02-11%20at%2000.24.56.png)



**Slide 11: Internal gene duplication cont**

*   **Example: amplification of a simple domain - Dystrophin:**  Focuses on Dystrophin as a concrete example.
*   **Dystrophin Details (Bullet Points):**
    *   **3685 aa over 79 exons spanning 2400 kb:** Provides size information for the Dystrophin protein and gene.
    *   **inc 24 tandem repeats of 109 amino acids:** Highlights the presence of 24 internal repeats, each 109 amino acids long, formed by domain duplication.
    *   **rod-like structure separating protein-binding domains:** Describes the function of the repeat region as a structural spacer.
    *   **α-helical configuration used as spacer:**  Specifies the secondary structure of the spacer region.
*   **Diagram:**  Illustrates the Dystrophin protein structure.
    *   **Exon map (top):** Shows the locations of exons along the gene, with labels for exon numbers.
    *   **(a) Actin-binding and Membrane-binding domains:** Marks the positions of these functional domains at the N-terminus and C-terminus, respectively.
    *   **Repeat region (middle):** The central region is depicted as a series of green blocks, representing the 24 tandem repeats.
    *   **N-terminus and C-terminus labels.**

*   **Concept:** This slide provides a real-world example of internal domain duplication and its functional consequences, using the well-studied protein Dystrophin. It illustrates how domain repeats can contribute to protein structure and function (in this case, a structural spacer).![Screenshot 2025-02-11 at 00.26.06.png](/img/user/Attachments/Screenshot%202025-02-11%20at%2000.26.06.png)

**Slide 12: Exon shuffling and mosaic proteins**

*  .
*   **Bullet Points:**
    *   **if structural = functional modules then:**  The premise is that if exons often correspond to functional domains (modules).
    *   **modules (domains) can be moved around genome:** Exons (and thus domains) can be shuffled and recombined in the genome.
    *   **fulfil new functions:** Exon shuffling can lead to the creation of new protein architectures and potentially new functions.
    *   **proteins show a mosaic history:** Proteins created by exon shuffling are "mosaic" because they are composed of domains from different origins.
*   **Diagrams:** Illustrate exon shuffling between two genes.
    *   **Top Left:** Gene with domains A, B, C.
    *   **Top Right:** Gene with domains X, Y.
    *   **Bottom:**  Recombinant gene formed by shuffling, now containing domains A, B, Y.
    *   Arrows indicate the exchange of exons/domains.
*   **Copyright Information:** Includes copyright details.
*   **Concept:** This slide explains exon shuffling as a mechanism for evolutionary innovation. By recombining exons (and thus domains) from different genes, new protein structures and potentially new functions can arise. This is a key process in creating the diversity of protein architectures.
![Screenshot 2025-02-11 at 00.26.57.png](/img/user/Attachments/Screenshot%202025-02-11%20at%2000.26.57.png)
**Slide 13: Exon shuffling and mosaic proteins cont**

*   **Bullet Points:**
    *   **modular architecture of proteins:** Emphasizes that proteins are often built from modular domains.
    *   **characteristic of phylogenetically new proteins with no counterparts in bacteria:** Mosaic proteins are more common in eukaryotes and contribute to their greater complexity compared to bacteria.
    *   **provides greater evolutionary flexibility:** Exon shuffling enhances evolutionary flexibility by allowing for rapid creation of new protein combinations.
    *   **a major mechanism of evolution of new proteins since radiation of eukaryotes:**  Exon shuffling is considered a significant driver of protein evolution, especially in eukaryotes.
    *   **directed or haphazard?:**  Raises the question of whether exon shuffling is a random process or somewhat directed.
    *   **limited by relationship between exons and domains:**  Acknowledges that the process is constrained by the existing relationships between exons and domains.
*   **Copyright Information:** Includes copyright details.
*   **Concept:** This slide discusses the significance of exon shuffling as a major evolutionary force, particularly in eukaryotes. It emphasizes its role in generating complex, mosaic proteins and increasing evolutionary potential. It also acknowledges some of the open questions and limitations of this process.

**Slide 14: The incidence of internal repeats in proteins**

*   **Title:** "The incidence of internal repeats in proteins" - This slide presents data on the frequency of internal repeats in proteins across different organisms and protein lengths.
*   **Graphs:** Two graphs are shown:
    *   **Top Graph:**  "% proteins with internal repeats" vs. "Average protein sequence length".  Scatter plot showing different organisms (Archae, Eubacteria, Eukaryotes) and gene subsets.  Each point represents an organism or group, showing the average protein length and the percentage of proteins with internal repeats.
    *   **Bottom Left Graph:** "% proteins with internal repeats" vs. "Protein sequence length". Line graph showing eukaryotes, prokaryotes, and archaea. Shows how the percentage of proteins with internal repeats changes as protein length increases.
    *   **Bottom Right Graph:**  Zoomed-in version of the bottom left graph for shorter protein lengths.
*   **Axes:**  Graphs are labeled with axes titles and units.
*   **Legends:** Legends explain the symbols used for different organism groups.
*   **Citation:** Marcotte et al., 1998 is cited as the source of the data.
*   **Concept:** This slide presents empirical data supporting the importance of internal repeats in protein evolution. The graphs suggest that:
    *   Eukaryotes tend to have a higher percentage of proteins with internal repeats compared to prokaryotes and archaea.
    *   The incidence of internal repeats generally increases with protein sequence length.
    *   This data strengthens the idea that internal duplication is a significant mechanism for protein evolution, especially in eukaryotes.

**Slide 15: Supradomains: recurring domain combinations**

*   **Title:** "Supradomains: recurring domain combinations" - Introduces the concept of supradomains, which are recurring combinations of protein domains.
*   **Image (Left):** A 3D protein structure of eEF-1alpha is shown, likely to visually represent a protein with multiple domains.
*   **Diagram (Right):** Shows a series of protein complexes or proteins involved in translation (eIF-2gamma, IF-2 and eIF-5b, etc.).
    *   Each entry is represented by a horizontal bar, and different colored blocks on the bar represent different protein domains.
    *   The color key at the bottom explains what each color represents (e.g., P-loop containing nucleotide triphosphate hydrolases, Translation proteins, etc.).
*   **Color Key:**  Provides a legend for the domain colors used in the diagram.
*   **Citation:** Chothia et al., 2003 is cited as a source.
*   **Concept:** This slide illustrates that protein domains are not randomly combined. Certain domain combinations, termed "supradomains," recur in different proteins, often within related functional pathways (like translation in this example). This suggests that some domain combinations are functionally advantageous and have been selected for during evolution.
![Screenshot 2025-02-11 at 00.28.18.png](/img/user/Attachments/Screenshot%202025-02-11%20at%2000.28.18.png)
**Slide 16: Hypothesis: the limited number of observed domain topologies...**

*   **Title:** "Hypothesis: the limited number of observed domain topologies may be due to the evolution of protein domains from a limited 'vocabulary' of such supersecondary structure elements." -  Presents a hypothesis to explain why there's a limited set of protein domain folds, despite the vast sequence space.
*   **Bullet Points (Arguments supporting the hypothesis):**
    *   **Combinatorial Complexity is Forbidding:**  Evolving a whole domain from scratch in one step is extremely improbable due to the vast sequence space (20^100 possible sequences for a 100-residue domain).
    *   **Foldability is Rare:** Only a tiny fraction of these sequences would even fold into a stable structure, let alone be functional.
    *   **Supersecondary Structures are Easier:**  Forming supersecondary structure units (like beta-hairpins) requires optimizing only ~20 residues, which is much more feasible for biological systems.
    *   **Vast Difference in Complexity:** The difference in complexity between evolving a whole domain vs. a supersecondary structure is enormous, analogous to the difference between the mass of an electron and the universe.
    *   **No Known Mechanisms for De Novo Domain Evolution:**  There are no known non-biological mechanisms that could efficiently generate long polypeptide chains that fold into domains in sufficient quantities to explore sequence space effectively.
    *   **Prebiotic Synthesis of Short Peptides:** Prebiotic synthesis of short peptides is more plausible.
    *   **Evolution Started from Short Peptides:**  Evolution likely started with shorter peptide building blocks rather than long chains.
    *   **Module Assembly is More Efficient:** Assembling domains from smaller modules (supersecondary structures) is more efficient than de novo domain evolution, allowing for optimization at a higher level.
    *   **Fragments from Non-homologous Proteins:**  The finding of similar fragments in unrelated proteins points to a common origin and suggests a limited "vocabulary" of building blocks.
*   **Citation:** Söding & Lupas, 2003 is cited as the source.
*   **Concept:** This slide presents a compelling hypothesis that protein domains evolved not de novo but from a limited set of simpler, reusable building blocks (supersecondary structure elements). This "proteins from pieces" approach makes protein evolution much more efficient and explains the observed limited diversity of domain folds.

**Slide 17: Proteins from pieces**

*   **Title:** "Proteins from pieces" - This slide visually illustrates the "proteins from pieces" concept introduced in the previous slide, showing different protein folds categorized by their supersecondary structure building blocks.
*   **Categories (a-g):**  Protein folds are grouped into categories based on the supersecondary structure elements they are built from.
    *   **(a) Supersecondary structure elements:** Shows examples like ββ-hairpin, αα-hairpin, βαβ-element.
    *   **(b) Fibrous proteins:**  Examples like Left/Right-handed β-helix, Coiled coil, Collagen, β-roll.
    *   **(c) Solenoid proteins:** Examples like Stacked β-hairpin, TPR repeats, Leucine-rich repeats.
    *   **(d) Symmetrical superfolds:** Examples like β-trefoil, Jelly-roll, Immunoglobulin fold, TIM-barrel, Ferredoxin fold.
    *   **(e) Non-symmetrical superfolds:** Examples like OB-fold, UB-roll, Updown bundle, Globin-like, Doubly wound.
    *   **(f) β-propeller:** Example: 7-bladed propeller.
    *   **(g) Membrane domains:** Examples: Porin, Membrane all-α.
*   **Images:** For each category, cartoon representations of protein folds are shown, visually highlighting their structural features and building blocks.
*   **Concept:** This slide provides visual evidence for the "proteins from pieces" hypothesis by showcasing diverse protein folds and categorizing them based on their shared supersecondary structure elements. It reinforces the idea that protein complexity arises from combining and rearranging a limited set of basic structural units.

**Slide 18: Circular permutation**

*   **Title:** "Circular permutation" - Introduces the concept of circular permutation in proteins.
*   **Bullet Points (Definition and Properties):**
    *   **Definition:** Circular permutation can be visualized as arising from ligating the N and C termini of a protein and then cleaving the loop at another site to create new termini. This effectively shuffles the order of the protein sequence while preserving the overall fold.
    *   **Genetic Engineering:** Circular permutation can be achieved through genetic engineering.
    *   **Stable and Functional Conformations:** Circularly permuted proteins often fold into stable and functional conformations, suggesting the fold is robust to the order of the sequence.
    *   **Slower Folding Rates:** However, they may fold at slower rates than the original "parent" protein.
    *   **N-terminus Not Required:**  The original N-terminus is not essential for folding, indicating redundancy in folding initiation.
    *   **Multiple Folding Pathways:**  Multiple folding pathways can lead to the same protein structure, suggesting flexibility in the folding process.
    *   **Naturally Occurring:** Circular permutation is found in naturally occurring proteins, implying it is an evolutionary mechanism.
*   **Citation:** Söding & Lupas, 2003 is cited as a source.
*   **Concept:** This slide defines circular permutation and highlights its surprising properties – proteins can maintain their fold and function even when the sequence order is rearranged. This indicates a level of redundancy and robustness in protein folding and suggests that evolutionary mechanisms can rearrange protein sequences without necessarily disrupting function.

**Slide 19: CP in naturally occuring proteins**

*   **Title:** "CP in naturally occuring proteins" -  Continues the discussion of circular permutation, focusing on its occurrence and mechanisms in natural proteins.
*   **Bullet Points:**
    *   **Mechanisms:** Lists possible mechanisms for how circular permutation arises naturally:
        *   **can arise from a posttranslational modification:**  Though less common, post-translational modifications could potentially induce circular permutation.
        *   **from gene duplication:** Gene duplication followed by recombination events could lead to circular permutation.
        *   **exon shuffling:** Exon shuffling might also play a role in creating circularly permuted proteins.
    *   **Symmetry:**  Discusses the relationship between circular permutation and protein symmetry:
        *   **Symmetric Structure and Alignment:** If a protein has a symmetric structure, it will align to itself and other structurally similar proteins both with and without circular permutation.
        *   **Identifying Symmetric Structures:** This property can be used to identify symmetric protein structures.
        *   **Definition of Symmetric Protein:** A protein is considered symmetric if it is related to another protein both with and without circular permutation, and the two alignments are distinct.
    *   **N and C Termini Proximity:**  In many cases, the N and C termini are far apart in circularly permuted proteins, indicating that their proximity is not a prerequisite for circular permutation.
*   **Citation:** Söding & Lupas, 2003 is cited as the source.
*   **Concept:** This slide explores the evolutionary origins and implications of circular permutation in natural proteins. It suggests mechanisms for its emergence and highlights its connection to protein symmetry, providing a tool for identifying symmetric structures and emphasizing the flexibility of protein architecture.

**Slide 20: Symmetric circularly permuted protein pairs**

*   **Title:** "Symmetric circularly permuted protein pairs" - Provides visual examples of symmetric circularly permuted protein pairs.
*   **Images:** Shows pairs of protein structures (1dsbal & 1cuk_2, 1stma_ & 1pgs_1, 2acy_ & 1psda3, 1ihwa_ & 1sso_).
    *   Each protein in a pair is colored in two parts: red and blue.
    *   "N" and "C" labels indicate the N-terminus and C-terminus positions.
*   **Text Description:** Explains the color-coding:
    *   Each structure is made of two parts, red and blue.
    *   For each pair, similarly colored parts match structurally (red to red, blue to blue).
    *   The red part is the N-terminal part in one protein and the C-terminal part in the other.
    *   The blue part is the C-terminal part in one protein and the N-terminal part in the other.
    *   The point where the color changes is the cut position for circular permutation.
*   **Citation:** Jung & Lee, 2001 is cited as the source.
*   **Concept:** This slide provides visual, concrete examples of symmetric circular permutation. By coloring the proteins and explaining the color-coding, it clearly illustrates how the sequence order is permuted while the overall fold is maintained in these symmetric pairs.
![Screenshot 2025-02-11 at 00.32.55.png](/img/user/Attachments/Screenshot%202025-02-11%20at%2000.32.55.png)


**Slide 21: Nonsymmetric circularly permuted protein pairs**

*   **Title:** "Nonsymmetric circularly permuted protein pairs" - Provides visual examples of *nonsymmetric* circularly permuted protein pairs.
*   **Images:** Shows pairs of protein structures (1rhga_ & 1bcfa_, lexg_ & 1tul_, 1qora2 & 1rnl_2, 1pne_ & 1gtqa_).
    *   Similar to the previous slide, each protein in a pair is colored in red and blue, with "N" and "C" labels.
*   **Color-coding:**  The color-coding is the same as in the previous slide, indicating the N-terminal and C-terminal parts and the cut position for circular permutation.
*   **Citation:** Jung & Lee, 2001 is cited as the source.
*   **Concept:** This slide extends the examples of circular permutation to nonsymmetric cases. While the principle of sequence rearrangement and fold conservation is the same, these examples are not symmetric in their overall structure, demonstrating that circular permutation is not limited to symmetric proteins.

**Slide 22: Domain swapping**

*   **Title:** "Domain swapping" - Introduces the concept of domain swapping.
*   **Bullet Points (Definition and Properties):**
    *   **Definition:** Three-dimensional domain swapping is a process where two or more protein molecules exchange part of their structure to form intertwined oligomers (multimers).
    *   **Subunit Structure:** The oligomers are made of subunits that have the same structure as the original monomer, except for a "hinge loop".
    *   **Hinge Loop:** The hinge loop connects the exchanged part to the rest of the structure. In the monomer, it is folded back on itself; in the oligomer, it is extended and involved in swapping.
    *   **Swapping Units:** Proteins can swap entire domains or just individual secondary structure elements.
    *   **Primary Interface:** The exchanged part maintains the same interactions in the oligomer as in the monomer, but these interactions become *inter*-molecular (between subunits) rather than *intra*-molecular (within a subunit). These are called the "primary" interface.
    *   **Secondary Interface:** Because subunits are close in domain-swapped oligomers, a new interaction interface can form that is absent in the monomer. This is termed the "secondary" interface.
*   **Concept:** This slide defines domain swapping as a mechanism for protein oligomerization. It emphasizes the exchange of structural parts between protein molecules, the role of the hinge loop, and the distinction between primary and secondary interfaces in the resulting oligomers.
![Screenshot 2025-02-11 at 00.34.41.png](/img/user/Attachments/Screenshot%202025-02-11%20at%2000.34.41.png)
**Slide 23: Simplified representation of domain swapping**

*   **Title:** "Simplified representation of a monomer and a domain-swapped dimer, with the secondary surface highlighted in red" - Provides a simplified visual representation of domain swapping.
*   **Diagrams:** Cartoon diagrams showing:
    *   **monomers (left):** Two separate monomer units.
    *   **domain swapped dimers (right):** Two monomers that have undergone domain swapping to form a dimer. The "secondary surface" (new interface) is highlighted in red.
*   **Visual Simplicity:**  The diagrams use simple shapes and colors to illustrate the concept of domain swapping in a clear and easy-to-understand way.
*   **Concept:** This slide provides a visual aid to understand the process of domain swapping and the formation of a dimer. It highlights the new interface (secondary surface) created by domain swapping, which is important for oligomer stability and function.

**Slide 24: Schematic representation of structures of a monomer of suc1**

*   **Title:** "Schematic representation of structures of a monomer of suc1" -  Provides a more realistic structural example of domain swapping using the protein suc1.
*   **Images:** Shows two structural representations of suc1:
    *   **Monomer (left):** Structure of a suc1 monomer.
    *   **Domain-swapped dimer (right):** Structure of a suc1 domain-swapped dimer.
    *   **Red Coloring:** The "domain-swapping C-terminal strand and the hinge loop" are highlighted in red in both structures.
*   **Text Description:** "The domain-swapping C-terminal strand and the hinge loop are shown in red" explains the color-coding.
*   **Concept:** This slide provides a real structural example of domain swapping, using the suc1 protein. By highlighting the swapped region and hinge loop, it makes the domain-swapping mechanism more tangible and shows that it is not just a theoretical concept but occurs in real proteins.
![Screenshot 2025-02-11 at 00.35.13.png](/img/user/Attachments/Screenshot%202025-02-11%20at%2000.35.13.png)
**Slide 25: Schematic representation of open-ended and closed-ended domain-swapped oligomers**

*   **Title:** "Schematic representation of open-ended and closed-ended domain-swapped oligomers" - Illustrates different types of domain-swapped oligomers based on their architecture.
*   **Diagrams:** Cartoon diagrams showing:
    *   **cyclic (closed-ended) domain swapped oligomers (left):**  A triangular arrangement of subunits, forming a closed ring or cycle.
    *   **linear (open-ended) domain swapped oligomers (right):** A chain-like arrangement of subunits, forming an open-ended polymer.
*   **Labels:**  Diagrams are labeled with the type of oligomerization (cyclic/closed-ended, linear/open-ended).
*   **Concept:** This slide shows that domain swapping can lead to different oligomer architectures – closed, cyclic structures or open, linear polymers. This structural diversity can have implications for the function and properties of the resulting protein assemblies.

**Slide 26: Why protein oligomers**

*   **Title:** "Why protein oligomers" - Discusses the evolutionary advantages of protein oligomerization.
*   **Bullet Points (Advantages of Oligomers over Monomers):**
    *   **possibility of allosteric control:** Oligomerization allows for allosteric regulation, where binding at one site affects activity at another site, enabling fine-tuning of protein function.
    *   **higher local concentration of active sites:** In enzymes, oligomerization can concentrate active sites, increasing reaction rates and efficiency.
    *   **larger binding surfaces:** Oligomers can create larger binding surfaces, allowing for interaction with larger ligands or multiple binding partners.
    *   **new active sites at subunit interfaces:**  Active sites can be formed at the interfaces between subunits in an oligomer, creating novel catalytic or binding properties.
    *   **economic ways to produce large protein interaction networks and molecular machines:** Oligomerization is an economical way to build large protein complexes and molecular machines from repeating subunits, reducing the genetic coding needed.
*   **Citation:** Liu & Eisenberg, 2002 is cited as a source.
*   **Concept:** This slide explains the evolutionary rationale for protein oligomerization. It highlights the functional advantages that oligomeric proteins have over monomers, including regulatory control, increased efficiency, enhanced binding capabilities, and economy of genetic coding.

**Slide 27: Change in Oligomerisation**

*   **Title:** "Change in Oligomerisation" -  Provides an example of evolutionary change in oligomerization state within a protein superfamily.
*   **Example: Thioredoxin superfamily:** Uses the Thioredoxin superfamily as an example.
*   **Images:** Shows protein structures:
    *   **peroxidase (top right):**  Representing a peroxidase from the Thioredoxin superfamily, depicted as an oligomer or dimer.
    *   **calsequestrin (bottom left):**  Representing calsequestrin, also from the Thioredoxin superfamily, depicted as a monomer.
*   **Labels:** Labels "peroxidase" and "calsequestrin" identify the proteins.
*   **Credit:** "© Christine Orengo" indicates the source of the images.
*   **Concept:** This slide provides a concrete example of how oligomerization state can change during evolution within a protein superfamily.  Even within a family of related proteins, some members can be monomers while others are oligomers, suggesting that oligomerization state is subject to evolutionary modification and functional adaptation.

**Slide 28: Domain Enlargement (2+ fold)**

*   **Title:** "Domain Enlargement (2+ fold) : ~30% functionally diverse superfamilies" - Discusses domain enlargement and its prevalence in functionally diverse superfamilies.
*   **Statistic:** "~30% functionally diverse superfamilies" indicates that domain enlargement is a relatively common phenomenon.
*   **Examples (with fold increase):** Shows several examples of proteins with domain enlargement, with the approximate fold increase in domain size indicated:
    *   **pyruvate kinase (3.7 fold)**
    *   **methane monooxygenase hydroxylase component α chain**
    *   **pyruvate, phosphate dikinase**
    *   **ferritin-like rubrerythrin (3.5 fold)**
    *   **phosphoenolpyruvate carboxylase**
    *   **biotin carboxylase**
*   **Images:**  Shows structural representations of these proteins, likely highlighting the domain enlargement.
*   **Credit:** "© Christine Orengo" indicates the source of the images.
*   **Concept:** This slide illustrates domain enlargement as an evolutionary mechanism that contributes to protein functional diversity.  It shows that domains can significantly increase in size over evolutionary time, potentially leading to new or modified functions. The statistic suggests that domain enlargement is a significant factor in the evolution of protein superfamilies.

**Slide 29: Change in Domain Partner**

*   **Title:** "Change in Domain Partner : ~90% of functionally diverse superfamilies" - Discusses the concept of "change in domain partner" and its very high prevalence in functionally diverse superfamilies.
*   **Statistic:** "~90% of functionally diverse superfamilies" -  This very high percentage emphasizes that changes in domain partners are an extremely dominant mechanism in protein evolution.
*   **Examples:** Shows two protein examples illustrating change in domain partner:
    *   **Methionine Aminopeptidase Type 1 (1mat) monomer/protein substrates:** Example of a monomeric enzyme that acts on protein substrates.
    *   **Creatinase (1chmA) dimer/small molecule substrates:** Example of a dimeric enzyme that acts on small molecule substrates.
*   **Images:**  Shows structural representations of these proteins.
*   **Labels:** Labels indicate protein names and substrate types.
*   **Credit:** "© Christine Orengo" indicates the source of the images.
*   **Concept:** This slide highlights "change in domain partner" as a *major* driver of protein functional diversification. The examples and statistic strongly suggest that evolving new functions often involves changing the domains that a protein interacts with, leading to altered substrate specificity, regulation, or interaction partners. The high percentage (90%) underscores the dominant role of this mechanism in protein evolution.

**Slide 30: Changes in Domain Partners: 90% of functionally diverse enzyme families**

*   **Title:** "Changes in Domain Partners: 90% of functionally diverse enzyme families" - Continues to explore changes in domain partners, specifically within enzyme families.
*   **Statistic:** "90% of functionally diverse enzyme families" -  Reiterates the high prevalence of domain partner changes in enzyme evolution.
*   **Schematic Diagram:**  Shows a schematic representation of domain architectures in different enzymes.
    *   Each row represents a different enzyme: biotin carboxylase and others, eukaryotic glutathione synthetase, succinyl-CoA synthetase, carbamoyl-phosphate synthase, synapsin Ia, pyruvate, phosphate dikinase.
    *   Each enzyme is represented by a sequence of colored shapes (squares, circles, triangles, etc.), representing different protein domains.
    *   The "+" symbol with "catalytic ATP-grasp fold" likely indicates a common catalytic domain present in some of these enzymes.
*   **Color Key (Implicit):** The different shapes and colors represent different domain types, although a specific key is not provided on this slide.
*   **Credit:** "© Christine Orengo" indicates the source of the diagram.
*   **Concept:** This slide provides a more detailed, schematic view of how domain architectures vary across different enzyme families. It reinforces the message from the previous slide: changes in domain partners are a widespread and crucial mechanism for generating functional diversity within enzyme families. The diagram visually demonstrates the modular nature of proteins and how different domain combinations create functional variations.
