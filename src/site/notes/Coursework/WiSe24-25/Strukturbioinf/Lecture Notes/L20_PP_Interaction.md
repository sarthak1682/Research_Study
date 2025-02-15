---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l20-pp-interaction/","noteIcon":""}
---

---
[[L20_SbioInf_MM.canvas|L20_SbioInf_MM]]


**Slide 2: Plan of the Lecture**

*   **Bullet Points:**
    *   **Protein interactions in the cell:**  This suggests the lecture will start by discussing the biological context and importance of protein interactions within cells.
    *   **Experimental methods:** The lecture will cover techniques used to study protein interactions.
    *   **Databases:**  It will discuss resources that compile and store protein interaction data.
    *   **Protein interactions in 3D:**  This topic likely focuses on the structural aspects and analysis of protein interactions at the atomic level.
    *   **Protein interaction networks:** The presentation will explore how protein interactions form complex networks and what we can learn from them.
    *   **Modules:**  This suggests a discussion of functional modules within protein interaction networks.
    *   **Evolutionary conservation of protein interactions:** The lecture will touch upon how protein interactions are maintained across evolution.
    *   **Prediction of protein interactions:**  Finally, the presentation will cover computational approaches to predict protein interactions.
*   **Overall Purpose:** This slide provides a roadmap for the audience, outlining the structure and key topics of the lecture. It helps them anticipate the flow of information.

**Slide 3: What are protein interactions?**
*   **Bullet Points:**
    *   **Importance:** "Important in processes such as protein-complex formation, signal transduction and transport" 
    *   **Examples:** 
        *   **enzyme-inhibitor complex:**  An example of a protein-protein interaction involved in regulation.
        *   **antibody-antigen complex:**  Illustrates interactions in the immune system.
        *   **receptor-ligand interactions:**  Examples of signalling at the cell surface.
        *   **multiprotein complexes such as ribosomes or RNA polymerases:**  Shows large, stable assemblies of proteins working together.


**Slide 4: Protein interactions are crucial in many aspects of biological function**

**1. Genetic Pathways:**

- **Explanation:** Genes code for proteins. When genes interact (genetically), it often means the proteins they code for physically interact. This interaction can lead to a change in the activity or function of one or both proteins, influencing a biological pathway.

**2. Pathway Scaffolding:**

- **Explanation:** Scaffolding proteins provide a platform for multiple proteins in a pathway to interact efficiently. By holding the proteins in close proximity, they increase the likelihood of interactions and enhance the speed and specificity of signal transduction.

**3. Enzymatic Reactions:**

- **Visual:** Two proteins, X and Y, are shown interacting. An additional molecule, P, is involved in the interaction, likely as a substrate or product. An arrow indicates a change or transformation.
- **Explanation:** Many enzymes are proteins that interact with their substrates (also often proteins) to catalyse specific reactions. The interaction stabilizes the enzyme-substrate complex, allowing the reaction to proceed efficiently.

**4. Molecular Machines:**

- **Explanation:** Many biological processes rely on large molecular machines composed of multiple interacting proteins. These machines perform complex tasks like DNA replication, protein synthesis, and cellular movement. Their function depends on the specific and coordinated interactions between the component proteins.

**Slide 5: The types of protein interactions**


*   **Binary protein protein interactions:**  Interactions between just two proteins. This is the simplest form.
*   **Multi-protein complexes:** Interactions involving more than two proteins, forming assemblies or complexes.




**Slide 7: Methods to detect protein interactions**



**Slide 8: High-throughput methods for detecting protein interactions**

*   **Bullet Points:**
    *   **Yeast two hybrid essay
    *   **Mass spectrometry of purified complexes:** Used for identifying components of protein complexes
    *   **Correlated mRNA expression (synexpression):** An indirect method based on gene expression patterns to infer functional relationships and potential interactions.
    *   **Genetic interactions (synthetic lethality):**  Another indirect method, using genetic data to infer functional relationships and potential physical interactions.
    *   **In silico predictions through genome analysis:** Computational approaches to predict interactions from genomic data.


**Slide 9: The yeast two-hybrid system for detecting protein-protein interactions**

![[ Screenshot 2025-02-09 at 00.30.16.png\| Screenshot 2025-02-09 at 00.30.16.png]] 

 Key components labeled:
    *   **Köder (Bait):**  German word for 'bait', indicating the bait protein.
    *   **Beute (Prey):** German word for 'prey', indicating the prey protein.
    *   **target protein:**  The protein being used as bait.
    *   **binding partner:** The protein being used as prey.
    *   **DNA-binding domain (BAIT):** Part of the bait fusion protein that binds to DNA.
    *   **transcriptional activation domain (PREY):** Part of the prey fusion protein that activates transcription.
    *   **yeast cell:** The cellular environment for the assay.
    *   **RECOMBINANT GENES ENCODING BAIT AND PREY INTRODUCED INTO YEAST CELL:**  Describes the genetic engineering step.
    *   **CAPTURED PREY:**  Represents the interaction between bait and prey proteins.
    *   **transcriptional activator binding site:** DNA sequence where the transcription factor binds.
    *   **TRANSCRIPTION OF REPORTER GENE:**  Indicates gene expression as a readout of interaction.
    *   **reporter protein:** The protein product of the reporter gene, detectable in the assay.
    * A recombinant gene is a gene that has been artificially constructed by combining DNA from different sources.
*   **Bullet Points:**
    *   **Pairs of proteins to be tested... ('hybrids') in yeast:** Explains the fundamental concept of fusion proteins ('hybrids') in the Y2H system.
    *   **One protein is fused to a DNA-binding domain, the other to a transcriptional activator domain:** Describes the key components of the fusion proteins.
    *   **Any interaction between them is detected by the formation of a functional transcription factor:** Explains how protein interaction leads to a measurable output (reporter gene expression).


**Slide 10: Measuring protein interactions by two-hybrid analysis**

note nothing
*   **Diagram:**  Shows a more detailed workflow of a large-scale Y2H experiment:
    *   **Bait and Prey circles:** Representing the sets of bait and prey proteins.
    *   **ORF1 - ORF6000:** Indicates that the experiment is designed to test all possible pairwise combinations of Open Reading Frames (ORFs) from a genome (e.g., yeast).
    *   **DNA binding domain and Activation domain labels:**  Highlighting the fusion protein components.
    *   **Basic transcription apparatus and Reporter gene:**  Showing the transcriptional machinery and the readout.
*   **Text below Diagram:**  Describes the experimental procedure:
    *   **Each of the ~6000 open reading frames (ORFs)...Saccharomyces cerevisiae genome (ORF1-ORF6000)...:** Explains the scale of the experiment, testing interactions of all yeast ORFs.
    *   **...polymerase chain reaction (PCR)-amplified and cloned as a DNA-binding domain fusion (bait) in a MATa strain, and as an activation domain fusion (prey) in a MATα strain.:** Describes the cloning and yeast strains used.
    *   **These two sets of clones were mated with each other in all possible combinations.:**  Explains the combinatorial nature of the experiment.
    *   **The diploid cells formed were selected for the activation of the reporter genes...:** Describes the selection process for positive interactions.
    *   **...tag sequencing of a pair of bait and prey plasmids cohabiting in each positive clone enabled the interaction to be decoded.:** Explains how interactions are identified using tag sequencing.


**Slide 11: Yeast two-hybrid strategies.**
![Screenshot 2025-02-05 at 21.27.55.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2021.27.55.png)

**Slide 12: Yeast two-hybrid assay**
An assay is a procedure used to analyze the composition or quantity of a substance.

*   **Benefits (Bullet Points):**
    *   **in vivo technique:**  Y2H is performed in living cells, which is a benefit compared to purely *in vitro* methods.
    *   **transient and unstable interactions can be detected:** Y2H can detect interactions that are not very strong or stable, which might be missed by other methods requiring strong binding for purification.
*   **Drawbacks (Bullet Points):**
    *   **only two proteins are tested at a time (no cooperative binding):**  Y2H is typically a pairwise assay, it doesn't easily capture interactions in larger complexes or cooperative binding.
    *   **takes place in the nucleus, so many proteins are not in their native compartment:**  Y2H forces proteins to be expressed and interact in the yeast nucleus, which might not be their natural cellular location, potentially leading to false positives or negatives.
    *   **predicts possible interactions, but is unrelated to the physiological setting:** Y2H detects potential interactions, but these may not be biologically relevant in the actual cellular context or under physiological conditions.


**Slide 13: Mass spectrometry of purified complexes**

*   **Bullet Points:**
    *   **Individual proteins are tagged and used as 'hooks' to biochemically purify whole protein complexes:** Explains the basic principle of affinity purification, using tagged proteins as "bait" to pull down interacting partners and complexes.
    *   **These are then separated and their components identified by mass spectrometry:** Describes the downstream analysis step, using MS to identify the proteins in the purified complex.

**Slide 14: Figure 1 | General overview of an affinity purification and mass spectrometry experiment.**

*   **Diagram (a-e):** A step-by-step visual representation of the affinity purification-MS workflow:
    *   **(a):**  Shows a protein of interest (blue, tagged) in a complex with binding partners (orange, green) and contaminants (red).
    *   **(b):**  Indicates an optional SDS-PAGE separation step to further purify the complex.
    *   **(c):**  Depicts proteolysis (digestion with trypsin) of the proteins into peptides.This breaks down proteins into smaller peptide fragments
    *   **(d):**  Shows a mass spectrum (m/z peaks) representing the peptides.
    *   **(e):**  Illustrates database searching and analysis of MS data to identify proteins.
![Screenshot 2025-02-05 at 21.34.02.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2021.34.02.png)




**Slide 15: Figure 2 | Main routes of protein-complex purification.**



- **(a) Immunochemical Purification:** This method isolates the _endogenous_ (naturally occurring) protein complex using an antibody specific to one of its components.
- **(b) One-Step Affinity Purification:** This method involves expressing a tagged version of a protein within the cell. The tag allows the protein, and thus the complex it's part of, to be easily captured using an affinity column.   
    
- **(c) Two-Step Affinity Purification:** This is similar to one-step, but uses two different tags separated by a cleavable linker. This allows for a very high level of purification, but may disrupt weaker interactions within the complex.   
    
Elution: the process of extracting or separating one material from another by washing with a solvent.

**Detailed Breakdown**

Let's go through each method in detail:

**(a) Immunochemical Purification**

1. **Endogenous Complex:** The starting point is the cell's natural protein complex, represented by the various colored shapes bound together.
2. **Purification with Antibody:** An antibody specific to one of the proteins in the complex (the red "Y" shape) is introduced. This antibody binds to its target protein.
3. **(1) Washing:** Unbound components are washed away, leaving the antibody-complex bound.
4. **(2) Elution:** The complex is released from the antibody, often by changing the pH or salt concentration.
5. **Purified Protein Complex:** The result is the isolated, naturally occurring protein complex.

**(b) One-Step Affinity Purification**

6. **Protein Sequence Fused to Tag:** The gene encoding one of the proteins in the complex is modified to include a tag sequence (represented by the blue rectangle). This is often done using recombinant DNA technology.
7. **(a) Homologous Recombination / (b) Transient Transfection / (c) Retroviral Gene Transfer:** These are methods to introduce the tagged gene into cells, allowing them to produce the tagged protein.
8. **Expression of Tagged Protein:** The cell expresses the protein with the attached tag.
9. **Assembly of Complex Containing Tagged Protein:** The tagged protein assembles into the protein complex.
10. **Purification Using Affinity Column Against Tag:** The cell extract is passed through a column containing a substance that specifically binds to the tag (represented by the blue rectangle fitting into the column).   
    
11. **(1) Washing:** Unbound components are washed away.
12. **(2) Elution:** The tagged complex is released from the column, usually by introducing a high concentration of the molecule that resembles the tag, or by changing the buffer conditions.
13. **Purified Protein Complex:** The protein complex, now containing the single tag, is isolated.

Homologs are genes/proteins that share a common evolutionary ancestor. Think of them as "relatives" in different organisms. There are two main types:

Orthologs are homologous genes found in different species that evolved from a common ancestor through speciation. They typically perform similar functions. For example, the insulin gene in humans and mice are orthologs - they both regulate blood sugar and evolved from the insulin gene in their common ancestor.

Paralogs (the other main type of homologs) arise through gene duplication within the same species and often develop new functions. For example, the genes for hemoglobin and myoglobin are paralogs - they both bind oxygen but serve different roles.

**(c) Two-Step Affinity Purification**

14. **Protein Sequence Fused to Tandem Tag:** The gene is modified to include two tags (blue and red rectangles) separated by a cleavable linker (green zig-zag).
15. **(a) Homologous Recombination / (b) Transient Transfection / (c) Retroviral Gene Transfer:** Methods to introduce the doubly-tagged gene into cells.
16. **Expression of Tagged Protein Containing Two Tags Spaced by a Cleavable Linker:** The cell produces the protein with both tags and the linker.
17. **Assembly of Complex Containing Tagged Protein:** The tagged protein incorporates into the complex.
18. **First Purification Step Using Affinity Column Against Tag:** The cell extract is passed through a column specific for the first tag (blue).
19. **(1) Washing:** Unbound components are washed away.
20. **(2) Elution by Cleavage:** The linker between the two tags is cleaved (e.g., using a specific protease), releasing the complex from the first column.
21. **Second Purification Step Using Affinity Column Against Tag:** The released complex is passed through a second column, this time specific for the second tag (red).
22. **(1) Washing:** Unbound components are washed away.
23. **(2) Elution:** The highly purified complex is eluted from the second column.
24. **Purified Protein Complex:** The final result is a very pure protein complex, potentially with fewer contaminants than the one-step method.


**Slide 16: Matrix and spoke models**
![Screenshot 2025-02-05 at 22.31.27.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2022.31.27.png)


**Slide 17: Figure 4 | Illustration of the types of protein networks that can be elucidated with different experimental approaches.**


![Screenshot 2025-02-05 at 22.32.39.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2022.32.39.png)

A pulldown assay works by using an immobilized "bait" protein to capture and isolate "prey" proteins that interact with it from a complex mixture

**Slide 18: Defining complexes by purification enrichment (PE) and socio-affinity scores**
![Screenshot 2025-02-05 at 22.33.58.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2022.33.58.png) 

Spoke MAtrix and -ve Evidence 


**Slide 19: Figure 1 | Synopsis of the genome-wide screen for complexes and data analysis.**
nah

**Slide 20: Mass spectrometry of purified complexes**


*   **Benefits (Bullet Points):**
    *   **several members of a complex can be tagged, giving an internal check for consistency:**  Tagging multiple proteins can improve data reliability and provide cross-validation.
    *   **detects real complexes in physiological settings:** MS of purified complexes aims to capture native protein complexes from cells, reflecting physiologically relevant interactions.
*   **Drawbacks (Bullet Points):**
    *   **might miss some complexes that are not present under the given conditions:** Complex formation and stability can be condition-dependent, so not all complexes might be captured in a single experiment.
    *   **tagging may disturb complex formation:**  Adding tags to proteins can potentially interfere with their natural interactions or complex assembly.
    *   **loosely associated components may be washed off during purification:**  Weak or transient interactions might be lost during purification steps, leading to an incomplete picture of the complex.


**Slide 21: Correlated mRNA expression (synexpression)**

*   **Method (Bullet Points):**
    *   **mRNA levels are systematically measured under a variety of different cellular conditions
    *   **genes are grouped if they show a similar transcriptional response to these conditions
    *   **these groups are enriched in genes encoding physically interacting proteins:** 
*   **Benefits (Bullet Points):**
    *   **in vivo technique, albeit an indirect one:** Synexpression analysis uses *in vivo* data (mRNA levels from cells), but it's an indirect inference of protein interaction.
    *   **much broader coverage of cellular conditions than other methods:** Gene expression can be measured under a wide range of conditions, providing a broader context than some direct interaction assays.
*   **Drawbacks (Bullet Points):**
    *   **powerful method for discriminating cell states or disease outcomes, but is a relatively inaccurate predictor of direct physical interaction:** Synexpression is good for functional relationships but less precise for predicting direct physical interactions. Correlation doesn't equal causation or direct physical contact.
    *   **very sensitive to parameter choices and clustering methods during analysis:** 


**Slide 22: Genetic interactions (synthetic lethality)**

*   **Title:** "Genetic interactions (synthetic lethality)" - Introduces another indirect high-throughput method: Synthetic Lethality analysis.
*   **Method (Bullet Points):**
    *   **two nonessential genes that cause lethality when mutated at the same time form a synthetic lethal interaction:** Defines synthetic lethality: mutations in two genes individually are not lethal, but combined mutations are.
    *   **such genes are often functionally associated and their encoded proteins may also interact physically:** Explains the inference: synthetic lethal interactions suggest functional association and potential physical interaction between the encoded proteins.
*   **Benefits (Bullet Points):**
    *   **in vivo technique, albeit an indirect one:** Synthetic lethality is studied in living organisms, but it's an indirect inference of protein interaction.
    *   **amenable to unbiased genome-wide screens:** Genetic screens for synthetic lethality can be conducted on a genome-wide scale, making it a high-throughput approach.


**Slide 23: Protein interaction versus genetic interaction**

*   **Diagram (Right) - Genetic interaction:** Shows three rows of gene representations (boxes):
    *   **Row 1:** Gene 1 (blue box) knocked out (crossed out), Gene 2 (yellow box) functional -> happy face (cell survives).
    *   **Row 2:** Gene 1 (blue box) functional, Gene 2 (yellow box) knocked out (crossed out) -> happy face (cell survives).
    *   **Row 3:** Gene 1 (blue box) knocked out (crossed out), Gene 2 (yellow box) knocked out (crossed out) -> sad face (cell dies, synthetic lethality).
* 

**Slide 24: Negative interaction data (non-interacting proteins)**

*   **Pairs of proteins whose cellular localization is different:**
	*   **unlikely to participate in a biologically relevant interaction:**  Proteins in different cellular compartments are less likely to physically interact in a biologically meaningful way. This can be used to define negative examples.
*   **Pairs of proteins randlmly selected from the set of all proteins pairs that are not known to interact:** Randomly chosen pairs from proteins not known to interact can also serve as negative examples.


a bunch of useless stuff 




**Slide 34: Three ways in which two proteins can bind to each other**
![Screenshot 2025-02-05 at 22.43.50.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2022.43.50.png)




**Slide 35: Types of protein-protein interactions**

**1. Homo- and Hetero-oligomeric Complexes:**

- **Oligomeric:** This term refers to a complex made up of multiple protein subunits (called protomers). Think of it like building a structure with identical or different Lego bricks.![Screenshot 2025-02-05 at 22.48.15.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2022.48.15.png)
	- Hemoglobin is a heterotetramer (/diprotomer)
- **Homo-oligomeric:** This means the complex is formed by _identical_ protein chains. Imagine a structure built entirely of the same type of Lego brick. For example, a protein made up of four identical subunits is a homotetramer (tetra- means four).
- **Hetero-oligomeric:** This means the complex is formed by _different_ protein chains. Think of a Lego structure built with various types of bricks. For example, hemoglobin, which carries oxygen in your blood, is a heterotetramer, made of two alpha-globin chains and two beta-globin chains.

**2. Non-obligate and Obligate Complexes:**

- **Obligate:** In an obligate PPI, the individual protein chains (protomers) _cannot_ exist as stable, functional units on their own within a living organism (in vivo). They _must_ be bound to their partner(s) to be functional. Think of two puzzle pieces that only make sense when connected. Neither piece is functional on its own.
- **Non-obligate:** In a non-obligate PPI, the individual protein chains _can_ exist as stable, functional units on their own. They interact with other proteins under certain conditions, but they are not _required_ to be bound to function. Imagine two friends who sometimes hang out, but each has their own separate life and activities. Many hetero-oligomeric structures involve non-obligate interactions. The different protein chains can function independently but come together for a specific purpose.

**3. Transient and Permanent Complexes:**

- **Transient:** These interactions are temporary. The proteins bind for a specific purpose, and then they dissociate (separate). Think of a handshake – you connect briefly and then let go. These interactions are often involved in signaling pathways, where proteins need to interact briefly to transmit a signal and then separate to reset the system.
- **Permanent:** These interactions are long-lasting and stable. The proteins are essentially always bound together. Think of the foundation of a building – it's a permanent structure. These interactions are often found in structural proteins or in complexes that perform essential, ongoing functions.

- Physicochemical and geometrical properties of the interfaces of **Weak Homodimers:** Explores properties like:
    
    - Accessible Surface Area
    - Dissociation Constant
    - Interface Gap Volume
    - Porosity

- **Interface Parameter Summary:** Lists key parameters for different dimer types:
    
    - Homodimers (various affinities)
    - Transient Homodimers
    - Transient Heterodimers
    - Non-obligate Heterodimers **Measured parameters include:**
        - Contact Area
        - Planarity
        - Polar Residue Percentage
        - GAP Index (Geometrically Accessible Packing) (lower the better)

**Slide 40: Examples of different complex types (diagrammatic)**
![Screenshot 2025-02-05 at 22.53.12.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2022.53.12.png)

**Slide 41: Control of protein oligomerization**
![Screenshot 2025-02-05 at 23.00.19.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.00.19.png)
- If genes for different subunits are **co-expressed** (produced at the same time), they have a 
- **Compartmentalisation** (proteins being confined within organelles or specific regions) can increase local concentration and promote oligomerization.


**Slide 42: Relation between different types of protein-protein interactions, their binding affinity and the localization of their protomers**

- **Binding Affinity (ΔG):** Represented on the vertical axis. Moving upwards means **stronger binding affinity** (more negative ΔG, more stable interaction). Moving downwards means **weaker binding affinity**.
    
- **Localization of Protomers (Subunits):** Represented on the horizontal axis. Moving from left to right reflects the **localization** of the protein subunits (protomers). "Co-expressed" means the proteins are produced in the same place and likely at the same time. "Different places" means they are produced in different cellular locations or at different times.
![Screenshot 2025-02-05 at 23.04.50.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.04.50.png)


Non-Obl-TT PPI - These are important for dynamic cellular processes like signaling, where interactions need to be switched on and off quickly.
Non-obligate weak transient PPIs- Important for very dynamic and reversible interactions that might be sensitive to subtle changes in cellular conditions.



**Slide 43: Contact area and polarity of the interfaces of various nonobligate and obligate complexes**
![Screenshot 2025-02-05 at 23.08.32.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.08.32.png)


**obligate protein complexes tend to have larger contact areas and less polar (more hydrophobic) interfaces**compared to non-obligate complexes. This suggests stronger, more stable interactions for obligate complexes. Weak transient interactions (like those in the ellipse) have smaller contact areas and more polar interfaces. Larger contact area and lower polarity interface are linked to less structural change upon complex formation, whereas smaller and polar interface imply structural rearrangements are more likely upon complexation.


**Slide 44: Protein-protein recognition sites may form one or several patches on the protein surface**

blah

**Slide 45: Recognition patches in protease-inhibitor complexes**
a **patch** refers to a **localized and contiguous region on the surface of a protein that is involved in interaction with another protein.**.
![Screenshot 2025-02-05 at 23.10.33.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.10.33.png)







**Slide 53: Clustering coefficient**
yk this one 2Ev/k(k-1)


**Slide 54: Assortativity**
![Screenshot 2025-02-05 at 23.12.19.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.12.19.png)




**Slide 55: Shortest path**
blah

**Slide 56: Betweenness**
yk this

**Slide 57: Random network**
![Screenshot 2025-02-05 at 23.13.40.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.13.40.png)

*   **Bullet Points:**  Characteristics of random networks:
    *   **The node degrees follow a Poisson distribution...approximately the same number of links.** - 
    *   **The clustering coefficient (C) is independent of a node's degree (k)...horizontal line if plotted as a function of k.** - Describes clustering coefficient behavior.
    *   **In this network, the values for the shortest paths...small-world network.**


**Slide 58: Scale-free network**
![Screenshot 2025-02-05 at 23.14.17.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.14.17.png)


**Slide 59: Scale free networks (growth)**
![Screenshot 2025-02-05 at 23.14.34.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.14.34.png)


**Slide 60: Hierarchical network**
![Screenshot 2025-02-05 at 23.15.32.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.15.32.png)


**Slide 61: Centrality and letality in protein networks**
essential proteins and their impact on organism's survival (lethality)


**Slide 62: Hubs are essential**
![Screenshot 2025-02-05 at 23.17.20.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.17.20.png)




**Slide 63: Bottlenecks tend to be essential**
![Screenshot 2025-02-05 at 23.17.53.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.17.53.png)


**Slide 64: A Biological Example of a Nonhub–Bottleneck in the Interaction Network**

Cak1p is a cyclin-dependent kinase-activating kinase involved in two key signaling-transduction pathways: cell cycle and sporulation.

**Cyclin-Dependent Kinase (CDK):**

- **Kinases** are enzymes that add phosphate groups to other proteins. This process is called **phosphorylation**, and it often acts like a switch, changing the protein's activity (turning it on or off, or changing how it interacts with other molecules).
- **Cyclin-Dependent** means these kinases _require_ proteins called **cyclins** to be active. CDKs are not active on their own; they need to bind to a cyclin partner.

Transduction: process of converting the initial signal into a cellular response.
The **cell cycle** is the ordered series of events that a cell goes through to duplicate its contents and divide into two daughter cells.
**Sporulation** is a process of forming **spores**. Spores are often dormant, resistant cells that can survive harsh conditions. It's a form of reproduction or survival strategy in certain organisms, like bacteria, fungi, algae, and some plants.



**Slide 65: Functional modules in interaction networks**


**Slide 66: Functional group interaction map**


**Slide 67: Network-based prediction of protein function**


**Slide 68: Figure 2 | Disease modules.**
![Screenshot 2025-02-05 at 23.24.53.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.24.53.png)

**Slide 69: Figure 2 A disease module. (a) Dispersed disease modules, (b) Overlapping disease modules.**
![Screenshot 2025-02-05 at 23.25.45.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.25.45.png)




**Slide 70: Protein interaction networks from different cellular status**


**Slide 71: Large-scale interaction data and the distribution of interactions according to functional categories**


**Slide 72: Counting interactions**


**Slide 73: Quantitative comparison of interaction data sets**

**Slide 74: Network alignment**

1. **Protein interaction data:** Information about how proteins interact with each other within each species.
2. **Orthology information (protein sequence similarity):** Information about which proteins from different species are evolutionarily related and have similar sequences.

**The process:**

- **Identifies "matched proteins":** It finds proteins across different species that have similar sequences. These are likely to be orthologs (proteins with a common ancestor).
- **Looks for "conserved interactions":** It examines the interactions between these matched proteins in each species. If an interaction is present in multiple species between similar proteins, it's considered "conserved".
- ==**Creates an "aligned network":** In this network:==
    - ==**Nodes** represent groups of sequence-similar proteins (one from each species).==
    - ==**Links** represent conserved interactions between these protein groups.==

In network alignment, a **protein group** is a set of proteins, where **each protein comes from a _different_ species**, and all proteins within the group are considered to be **sequence-similar**.

**Slide 75: Computational prediction of protein-protein interactions: two main areas**
main goals of computational PPI prediction:
    *   **Determining whether two proteins are likely to interact:**  
    *   **Understanding of the mechanism of protein-protein interactions and the identification of residues in proteins which are involved in those interactions.** - 

**Slide 76: Predicting protein interactions in 3D**
 main tasks in 3D-based PPI prediction:
    *   **Determine whether two protein with known structure interact:**  Predicting interaction given structures.
    *   **Predict the structure of the complex given two monomers:** Protein-protein docking.
    *   **Find protein interaction sites on protein's surface:** Interface prediction.



**Slide 78: Interface prediction**

*   **Residues type and properties, e.g.:**
	*   **interface propensity:**  Amino acid preferences at interfaces.
	*   **hydrophobicity:**  Hydrophobic nature of interfaces.
*   **Evolutionary conservation:** Conservation of interface residues across evolution.
*   **Information contained in the atomic coordinates of the structure:**
	*   **surface accessibility:**  Exposed surface area of interface residues.
	*   **tertiary structure (spatial neighbors):**  Proximity of residues in 3D space.
	*   **secondary structure:** Secondary structure elements at interfaces.
	*   **crystallographic B-factors:** Flexibility or mobility of residues.
	*   **properties that describe the chemical composition and the shape of the protein surface:** Overall surface properties.

##### 

**Slide 81: Conservation of gene order among U.urealyticum, M.pneumoniae, and M.genitalium**

Conservation of gene order" refers to the idea that **the arrangement of genes along a chromosome is maintained across different species over evolutionary time.**

**Slide 82: Conservation of gene order: a fingerprint of proteins that physically interact**


**Slide 83: Figure 1 (Phylogenetic tree and triplet comparisons) and Figure 2 (Trp operon structure)**


**Slide 84: Methods for predicting protein interaction partners from genomic and sequence information**


*   **Diagrams (a-e):**  Illustrates four genomic/sequence-based methods:
    *   **(a) Phylogenetic profiles:**  Presence/absence pattern of genes across genomes.
    *   **(b) Conservation of gene neighborhood:**  Conserved gene order.
    *   **(c) Gene fusion:**  Fusion of two genes into a single gene in some organisms.
    *   **(d) Similarity of phylogenetic trees:**  Comparing phylogenetic tree topologies for different protein families.
    *   **(e) Correlated mutations:**  Analysis of correlated mutations in protein sequences.


**Slide 85: Conservation of gene order (chromosomal neighborhood)**
![Screenshot 2025-02-05 at 23.47.33.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.47.33.png)



**Slide 86: Phylogenetic profiling**

*
![Screenshot 2025-02-05 at 23.48.04.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.48.04.png)


**Slide 87: Similarity of expression profiles**
![Screenshot 2025-02-05 at 23.48.39.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.48.39.png)


**Slide 94: Extraction of knowledge on protein-protein interaction by association rule discovery**

![Screenshot 2025-02-05 at 23.49.12.png](/img/user/Attachments/Screenshot%202025-02-05%20at%2023.49.12.png)

