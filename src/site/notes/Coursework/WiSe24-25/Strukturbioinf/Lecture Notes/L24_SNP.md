---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l24-snp/","noteIcon":""}
---

---
[[L24_SBioInf_MM.canvas|L24_SBioInf_MM]]

**Slide 2: DNA Sequence Variations**

*   **Title:** DNA Sequence Variations
*   **Main Point:** Explains that there are different kinds of variations in DNA sequences.
*   **Key Variations:**
    *   **SNPs (Single Nucleotide Polymorphisms):** The most common type, where a single nucleotide base (A, T, C, or G) is changed. The example shows a 'T' changed to a 'C'.  This is the primary focus of the presentation.
    *   **STRs (Simple Tandem Repeat Polymorphisms):**  Repetitive sequences of DNA (like "CT" repeated multiple times).  The number of repeats varies between individuals.
    *   **Indels (Insertions/Deletions):**  Sections of DNA are either added (inserted) or removed (deleted). The example shows a deletion.
*   **Significance:** These variations are the basis of genetic differences between individuals.
![Screenshot 2025-02-06 at 02.28.25.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2002.28.25.png)



**Slide 5: Single Nucleotide Polymorphism**

*   **Key Concepts:**
    *   **Single Nucleotide Change:** One base in the DNA sequence is replaced by another.
    *   **Example:** AAGGTTA becomes ATGGTTA (A is replaced by T).
    *   **Coding vs. Non-coding SNPs:**
        *   Most SNPs are outside of coding regions (the parts of genes that directly code for proteins).
        *   SNPs *within* coding regions are particularly important because they can change the protein's amino acid sequence and potentially its function.

**Slide 6: Single nucleotide polymorphisms (SNPs)**

*   **Key Concepts:**
    *    SNPs are the most common genetic variation in humans.
    *    Density of SNPs is about 1 in every 100-300 bases.
    *    SNPs may occur in coding regions, introns, regulatory regions, or intergenic regions.

**Slide 7: SNPs and disease**

*   **Title:** SNPs and disease
*   **Main Concepts:**
     *   Functional variation- if SNP is located in coding region it can change amino acid sequence of a protein.
     *    Regulatory variation- if SNP is in a noncoding region it can still affect the gene expression.
     *   Association- SNPS can be used to perform study of whole genome.

**Slide 8: Table 1: Glossary of terms; Table 2: SNP functional classes**

*   **Title:** Glossary of terms & SNP Functional classes
*   **Key Concepts:**
    *   **Allele:**  A specific version of a gene or genetic marker.
    *   **Coding Region:** The part of a gene that codes for a protein.
    *   **Haplotype:**  A set of DNA variations (like SNPs) that tend to be inherited together.
    *   **Missense Mutation:** A change in DNA that causes a *different* amino acid to be incorporated into a protein.
    *   **Nonsense Mutation:**  A change in DNA that introduces a premature *stop* codon, leading to a shortened, often non-functional protein.
    *   **Rare Variant:** A genetic variant found in less than 1% of the population.
    *   **SNP (Single Nucleotide Polymorphism):**  A single base change, usually defined as occurring in >1% of the population.
    *   **cSNP:**  Coding SNP (in a protein-coding region).
    *   **rSNP:** Regulatory SNP (in a regulatory region).
    *   **sSNP:** Synonymous SNP (in a coding region, but *doesn't* change the amino acid).
    *   **nsSNP:** Non-synonymous SNP (in a coding region, and *does* change the amino acid).
    *   **iSNP:** Intronic SNP (in an intron, a non-coding part of a gene).


**Slide 10: Discovery methods**

*   **Main point:** Main method for discovering SNPs is to compare DNA.

**Slide 11: The SNP Consortium**
    *   Used algorithms like Polybayes and NQS to detect SNPs.




**Slide 20: A Decision Tree for SNP Analysis**

*   **Title:** A Decision Tree for SNP Analysis
*   **Main Point:** Presents a flowchart outlining a systematic approach to analyzing the potential impact of a SNP.  This is a *very important* slide, as it summarizes a key strategy.
*   **Key Steps:**
    1.  **Initial Classification:** Determine the SNP's location:
        *   Is it in a coding region (exonic)?
        *   Is it in a promoter region (controls gene expression)?
        *   Is it in an intron (non-coding part of a gene)?
        *   Is it in a 3' UTR (untranslated region, important for regulation)?
        *   Is it near a miRNA binding site (microRNAs regulate gene expression)?
    2.  **If Exonic (in a coding region):**
        *   Is it in an Open Reading Frame (ORF) - the part that actually codes for protein?
        *   Is it synonymous (doesn't change the amino acid) or non-synonymous (changes the amino acid)?
    3.  **If Non-synonymous:**
        *   **Identify AA environment:** Is the amino acid in a transmembrane (TM) region, intracellular (IC) region, or extracellular (EC) region?
        *   **Substitution Score:**  Use a scoring system (like those discussed later) to assess the likely impact of the amino acid change.  Positive scores are generally preferred (less likely to be damaging), negative scores are unpreferred (more likely to be damaging), and 0 is neutral.
        *   **Functional Characterisation:**  Perform experiments to directly test the effect of the SNP.
        *   **Structure Prediction:** Use computational methods to predict how the amino acid change might affect the protein's 3D structure.
    4.  **Other Considerations:**
        *   **Regulatory ESE/ESS?**  Exonic/Intronic Splicing Enhancers/Silencers - these are sequences that influence how genes are spliced (processed).
        *   **Transcription Factor Binding?** Does the SNP affect the binding of proteins that control gene expression?
        *   **Orthologous Mutations:**  Look at similar genes in other species.  Has this amino acid been changed in other species, and what was the effect?
        *   **Known Protein Feature Disruption?** Does the SNP disrupt a known functional domain or important site in the protein?
        *   **Conserved in Alignment?**  Is the amino acid highly conserved (unchanging) across different species?  High conservation suggests importance.

**Slide 21: Mutations and disease**
*    States that the structure of protein can determine the function.
*   **Key points:**
     *    Most mutations affect structure and protein function.
     *   If mutation is inherited before the age of reproduction, and if it doesn't lead to death, that mutation is important.
     * From a structural perspective, the most interesting mutations alter biological function with a single-residue change (missense mutation)
	-  Such mutations are analogous to non-synonymous single nucleotide polymorphisms(SNPs), although the affect of SNPs on phenotype is not usually well established.

**Slide 22: Nonsynonymous single nucleotide polymorphisms**

*   **Main point:** non-synonymous can cause drastic changes.
* Most alterations are deleterious and so are eventually eliminated through purifying selection
- However, beneficial mutations can sweep through the population and become fixed, thus contributing to species differentiation

**Slide 23: Importance of nonsynonymous substitutions in humans**

*   **Title:** Importance of nonsynonymous substitutions in humans
*   **Main point:** Nonsynonymous has an affect on genes, including disease (half of genetic changes known to cause diseases)

**Slide 24: Problem: prediction of substitution effect
*    There are so many different options on the market, and it is expensive and difficult to determine the best solution.
*   **Key points:**
     *  The goal is to have the computational method predict whether the amino acid substitution affects the protein function.

**Slide 25: Possible approaches**

*   **Main points:**
     *    Prediction can be based on the sequence homology.
     *   Structure can be used for prediction.




**Slide 28: Equations**

*    Relative Entropy- compares amino acid to mutation.
*    Grantham Score- difference between human amino acid and homolog.
*    Relative Mutation Probability.![Screenshot 2025-02-06 at 02.39.33.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2002.39.33.png)

**Slide 29: Relative mutation probabilities**

*   **Main Point:** Shows graphs of relative mutation probabilities as a function of mutation site conservation and solvent accessibility.
*   **Key Observations:**
    *   **Graph (a) - Conservation vs. Probability:**
        *   As conservation *increases* (moving to the right on the x-axis), the probability of a *disease-causing* mutation *increases*.  This makes intuitive sense: highly conserved positions are often crucial for function.
        *   As conservation increases, the probability of a *benign* (non-disease-causing) non-synonymous SNP *decreases*.
        *   Synonymous SNPs (which don't change the amino acid) are mostly neutral, so their probability is relatively constant.
    *   **Graph (b) - Solvent Accessibility vs. Probability:**
        *   As solvent accessibility *increases* (moving to the right, meaning the amino acid is more exposed on the protein's surface), the probability of a *benign* non-synonymous SNP *increases*.  Surface residues are often less critical for the protein's core structure.
        *   As solvent accessibility increases, the probability of a *disease-causing* mutation *decreases*.  Buried residues are often important for maintaining the protein's fold.
![Screenshot 2025-02-06 at 02.40.43.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2002.40.43.png)







**Slide 34: Comments**

*   **Main point:**
      *   Average gene has four SNPs.
      *   Arginine is the most commonly mutated in both disease-associated mutations and non-synonymous SNPs
      *    Glycine is second most common due to its small size.





**Slide 37: Porphyria cutanea tarda (PCT; OMIM 176100)**
![Screenshot 2025-02-06 at 02.44.00.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2002.44.00.png)

**Slide 38: Disruption of protein–protein interactions**
Von Hippel-Lindau syndrome (VHL) is an inherited condition causing predisposition to cancer. It's often due to a mutation in the VHL gene, which normally produces a protein that degrades HIF. A common mutation, Tyr98His, disrupts VHL's binding to HIF, preventing HIF degradation. This leads to the expression of growth factors and blood vessel proliferation, contributing to cancer developme

**Slide 39: Disruption of a hydrogen-bonding network**
The VHL protein complex (with elongin B and C) degrades HIF. Arginine 167 in VHL is essential for structural stability through hydrogen bonds. The Arg167Gln mutation, found in many VHL families, allows complex formation but reduces its stability, making it less effective at HIF degradation. This mutation abolishes key hydrogen bonds.

**Slide 40: Interference with DNA binding**
Inherited mutations in the p53 tumor suppressor gene are rare but significant. p53 protein has three domains, and inherited mutations mainly occur in the DNA-binding domain. A hotspot mutation, like arginine 273 to histidine, disrupts DNA binding, contributing to conditions like Li-Fraumeni syndrome

**Slide 41: Breaking disulfide covalent bonds**
Von Willebrand factor (VWF) is a large protein crucial for platelet adhesion at injury sites. Type IIA von Willebrand disease arises from alterations in the VWF gene, leading to low platelet count and loss of VWF multimers. Within VWF, the A1 domain regulates platelet binding. A rare mutation, Cys509Arg, disrupts a disulfide bond in the A1 domain, causing it to become inactive. This results in uncontrolled platelet binding, platelet aggregation, and their removal from the blood.

**Slide 42: Mutation of catalytic residues**

Factor IX is crucial for blood clotting. Many mutations in Factor IX are linked to haemophilia B, an X-linked bleeding disorder. Factor IXa activates Factor X in the coagulation cascade. Its catalytic domain is a serine protease with a serine-histidine-aspartic acid catalytic triad. A mutation replacing the catalytic serine with arginine eliminates enzyme activity, causing severe haemophilia

**Slide 43: Mutation of metal-binding residues**

Cu,Zn superoxide dismutase (SOD1) protects cells by converting harmful superoxide radicals. It uses copper and zinc ions in its active site. SOD1 mutations are linked to familial ALS (Lou Gehrig's disease), causing motor neuron degeneration. Two mutations, His46Arg and His48Gln, disrupt copper binding and greatly reduce SOD1 activity. The His46Arg mutation, even with one functional gene copy, results in slower disease onset compared to other ALS-associated mutations.

**Slide 44: Disrupting quaternary structure**
The Ala4Val mutation in SOD1 is the most frequent and aggressive mutation linked to familial ALS (FALS). It's located at the SOD1 homodimer interface, away from the active site. This mutation causes a small structural change due to the larger valine residue, reducing the stability of the SOD1 homodimer. It's proposed that this instability leads to the formation of toxic protein aggregates, damaging motor neurons



**Slide 46: Flowchart for amino acid substitution (AAS) prediction**

*   **Key Steps:**
    1.  **Input:**  Protein sequence and the amino acid substitution.
    2.  **Three Main Approaches:**
        *   **Structure:**  If a 3D structure is available, use it to assess the substitution's impact (solvent accessibility, interactions with other residues, etc.).
        *   **Sequence:** Use sequence databases and multiple sequence alignments to assess conservation (how often the original amino acid is found at that position in related proteins).
        *   **Annotation:** Use databases (like SWISS-PROT) and prediction tools to gather information about the protein (e.g., is it a transmembrane protein?  Are there known functional domains?).
    3.  **Apply Scoring Rules:** Combine the information from the structure, sequence, and annotation to generate a prediction.
    4.  **Output:**  A prediction of whether the substitution is likely to be damaging or neutral.

**Slide 47: Method and Web site**


*   **Key Methods:**
    *   **SIFT (Sorting Intolerant From Tolerant):** Based primarily on sequence homology (conservation).
    *   **PolyPhen (Polymorphism Phenotyping):** Uses both sequence conservation and structural information.
    *   **SNPs3D:** Uses both structure-based and sequence-based Support Vector Machines (SVMs - a type of machine learning algorithm).
    *   **PANTHER PSEC:** Based on sequence homology using Hidden Markov Models (HMMs).
    *   **PMUT:** Uses neural networks.
    *   **TopoSNP:** Considers the location of the substitution within the protein's structure (buried, surface, pocket) and conservation.
*   **Performance Metrics:**
    *   **FN error (False Negative):**  The method incorrectly predicts a damaging mutation as neutral.
    *   **FP error (False Positive):** The method incorrectly predicts a neutral mutation as damaging.
    *   **dbSNP:** Percentage of SNPs in the dbSNP database predicted to be damaging.
    *   **Coverage:** The percentage of input sequences for which the method can make a prediction.

**Slide 48: Polyphen: Structural consequences of the respective non-synonymous mutations in proteins**

*   **Main points:**
    *   Known disease mutation.
    *    Large number of non-synonymous are mapped onto protein structures.



**Slide 50: Properties of disease-causing mutations**

*   **Key Findings:**
    *   Disease-causing mutations often occur at sites with *low* solvent accessibility (i.e., buried within the protein).
    *   They often affect intrinsic structural features, like beta-strands.
    *   They are often located at functionally important sites (active sites, sites involved in disulfide bonds, evolutionarily conserved sites, beta strands, <5% Solvent Accessibility).

**Slide 51: Many non-synonymous SNPs have a phenotypic effect**

*   **Main point:** Shows the fraction of polymorphic sites in important regions 45%

**Slide 52: Impact of amino acid variants**

*   **Title:** Impact of amino acid variants
*    **Main points:**
     *    Impacts folding.
     *   Interaction sites.
     * Solubility
     * Stability


**Slide 53: Sequence variant that disrupts a critical disulphide bond**
This image describes a **sequence variant that disrupts a critical disulfide bond** in the HLA-H protein.

Specifically, the normal protein has a disulfide bond between **Cysteine (Cys) at position 203 and Cysteine at position 260**. The **allelic variant replaces Cys 260 with Tyrosine (Tyr 260)**, thus breaking the disulfide bond.
![Screenshot 2025-02-06 at 03.01.06.png](/img/user/Attachments/Screenshot%202025-02-06%20at%2003.01.06.png)

This variant is linked to **hereditary hemochromatosis**

Slide 54: 
checking if a substitution:

- **Occurs in an active or binding site.**
- **Alters interactions with ligands in the protein structure.**
- **Changes hydrophobicity or charge in a buried site.**
- **Destroys a disulfide bond.**
- **Affects protein solubility.**
- **Inserts proline in an alpha helix.**
- **Is incompatible with the evolutionary substitution profile at that site.**


**Slide 55: Benchmark**

**"Deleterious data set" (Likely to affect protein phenotype):**

- **Purpose:** Represents **true positive examples** - mutations that _are_ harmful.

**"Divergence data set" (Substitutions without negative effect):**

- **Purpose:** Represents **false positive examples** - mutations that are predicted harmful but are likely benign.

**Slide 57: A complicated case...**

*   **Main Point:** Presents an example where simple sequence analysis or structural analysis alone is *not* sufficient to predict the impact of a mutation. This highlights the complexity of genotype-phenotype relationships.
*   **Key Takeaway:**  In some cases, you need to consider multiple lines of evidence (sequence, structure, function, evolutionary context) to understand the impact of a mutation.



**Slide 60: SIFT: sort intolerant from tolerant substitutions**

*   **Main Point:** Introduces the SIFT method, which is another widely used tool for predicting the impact of amino acid substitutions.
*   **Key Concepts:**
    *   SIFT is based primarily on *sequence homology* (conservation).
    *   It uses multiple sequence alignments to identify positions that are highly conserved across different species.
    *   Substitutions at highly conserved positions are more likely to be deleterious.


**Slide 62: Application**
- **SIFT uses sequence homology, not protein structure:** This allows SIFT to analyze **more non-synonymous SNPs**(single nucleotide polymorphisms that change the amino acid sequence) compared to methods relying solely on protein structure information.
- **SIFT is automated and quick:** This makes it useful for **predicting deleterious missense variants**, helping to prioritize candidates for disease association studies and further experimental investigation.
- **SIFT can be applied to large-scale reverse genetic projects:** It can be used in studies where mutations are randomly introduced, genes are identified, and resulting phenotypes are analyzed. This helps to understand the functional consequences of genetic changes on a broader scale.


**Slide 64: Prediction depends on the diversity of the sequences used in the alignment.**

*   **Key Observation:**  If the alignment contains only very closely related sequences, SIFT will tend to overpredict the number of deleterious substitutions.  A more diverse alignment is needed for accurate predictions.

