---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l14-ssp/","noteIcon":""}
---

---
[Site Unreachable](https://aistudio.google.com/prompts/14wtW__r72YV3oyhTEdsOlQ1avQAQaEAv)


---




**Slide 8: Secondary Structure Elements**

This slide lists the standard secondary structure elements defined by the DSSP algorithm ): alpha-helix (H), 3-10 helix (G), pi-helix (I), beta-sheet (E), isolated beta-bridge (B), turn (T), coil (C), and bend (S). Simplification: H = HGI, E = EB, C = CTS

**Slide 9: Propensities and Windows**

This slide introduces the concepts of amino acid propensities (the likelihood of an amino acid to be in a particular secondary structure) and sliding windows.  



**Slide 12: Using Propensities in Prediction Schemes**
![Screenshot 2025-01-08 at 07.41.27.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2007.41.27.png)



**Slide 13: Chou-Fasman Method**

This slide describes the Chou-Fasman method, which uses a table of conformational parameters (propensities) derived from circular dichroism (CD) spectroscopy data. The table provides the likelihood of each amino acid being in a helix, sheet, or turn. The method is based on the frequency of residues in known 3D structures and uses a set of rules to govern the prediction.  It is designed for soluble, globular proteins.

![Screenshot 2025-01-08 at 07.47.40.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2007.47.40.png)

![Screenshot 2025-01-08 at 07.48.01.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2007.48.01.png)


**Slide 20: Chou-Fasman Summary**

This slide summarizes the Chou-Fasman method, highlighting its limitations: potential ambiguity in predictions, ad hoc rules, and limited accuracy (~50-60%).

**Slide 21: GOR Method**

This slide introduces the GOR method, which builds upon the Chou-Fasman method but uses information from neighboring residues. It uses a sliding window of 17 residues and separate matrices for each secondary structure element. The GOR III method has an accuracy of ~64%.

**Slide 22: GOR Scoring Matrix**

This slide illustrates the concept of the GOR scoring matrix. Each row in the matrix represents a different secondary structure type (A, B, etc.).  The columns represent positions within the sliding window relative to the central residue (0). The values in the matrix represent the log-odds scores for each amino acid at each position in the window, contributing to the prediction of the central residue's secondary structure.
![Screenshot 2025-01-08 at 07.51.03.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2007.51.03.png)





**Slide 28: Nearest Neighbor Method**

This slide describes a nearest-neighbor method for secondary structure prediction. It involves building a table of sequence windows from known structures and finding the best alignments of a given window in a test sequence. The prediction for the central residue is based on the frequency of observed secondary structures in the aligned windows.

**Slide 29: Comparing Sequence Segments**

This slide presents a formula for calculating the distance between two sequence segments, considering the probabilities of secondary structure states given the amino acid sequence within a window.  This distance metric is used in nearest-neighbor methods.

**Slide 30: Nearest Neighbor Approach**

This slide provides a more detailed explanation of the nearest-neighbor approach for secondary structure prediction, including how the propensities are calculated based on the closest 25 neighbors within a window of 13 residues. 




**Slide 45-47: Prediction from Multiple Sequences**

These slides explain the benefits of using multiple sequence alignments for secondary structure prediction, improving accuracy by 6-7%.  They highlight the dependence on alignment quality and how multiple sequences can improve prediction confidence.

**Slide 48: Neural Networks with Multiple Alignments**

This slide illustrates the combination of profile information from multiple sequence alignments with a neural network for secondary structure prediction.

**Slide 49-50: PSI-PRED**

These slides describe the PSI-PRED method, which uses PSI-BLAST to generate a position-specific scoring matrix (PSSM) and feeds it into a neural network for improved secondary structure prediction.
![Screenshot 2025-01-08 at 07.59.53.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2007.59.53.png)

**Slide 51: Test Sequences**

This slide discusses the criteria for selecting test sequences to evaluate prediction accuracy: known structures, diversity of protein families (<25% pairwise similarity), large dataset, and the jack-knife approach (a resampling technique).

**Slide 52-53: Evaluation Metrics**

These slides introduce evaluation metrics for secondary structure prediction:
* **Q-index (Q3):** Percentage of correctly predicted residues for all three states (helix, strand, coil).![Screenshot 2025-01-08 at 08.03.29.png](/img/user/Attachments/Screenshot%202025-01-08%20at%2008.03.29.png)
* **Correlation coefficient (Ca):** Measures the agreement between predicted and observed secondary structure.

**Slide 54-57: Segment-Based Quality Measure (Sov)**


SOV (Segment Overlap Measure) is a metric used to evaluate the accuracy of secondary structure predictions, particularly in the context of comparing predicted segments to observed segments in a protein.

**Why SOV is needed:**

* **Segments, not residues:** Secondary structure is fundamentally about segments (helices, strands, coils), not individual residues. A prediction that correctly identifies a helix but is off by one or two residues at the ends shouldn't be penalized as heavily as a completely wrong prediction.
* **Natural variation:**  Even in homologous proteins, the exact boundaries of secondary structure elements can vary slightly. SOV accounts for this natural variation.
* **Ambiguity in definition:** Different methods might define secondary structure boundaries slightly differently. SOV is more robust to these variations.

**How SOV is calculated:**

The SOV formula is:

```
SOV = 100 * (1 / ΣᵢN(i)) * Σᵢ Σₛ₍ᵢ₎ Σ minov(s₁, s₂) + δ(s₁, s₂) * len(s₁) / maxov(s₁, s₂) 
```

Let's break down the variables:

* **`i`:**  Represents the secondary structure state (helix, strand, or coil).
* **`N(i)`:**  The total number of residues in state `i` across both the observed and predicted structures.  `ΣᵢN(i)` sums this over all three states.
* **`S(i)`:**  The set of all observed segments in state `i`.
* **`s₁`:** An observed segment in state `i`.
* **`s₂`:** A predicted segment in state `i`.
* **`len(s₁)`:** The length (number of residues) of the observed segment `s₁`.
* **`minov(s₁, s₂)`:** The number of residues in the *minimum overlap* between `s₁` and `s₂`.  This is the number of residues that are correctly predicted to be in state `i` *and* are in the correct location.
* **`maxov(s₁, s₂)`:** The number of residues in the *maximum overlap* between `s₁` and `s₂`. This is the total number of residues covered by either `s₁` or `s₂`, representing the extent of the segment.
* **`δ(s₁, s₂)`:** A length difference weight that down-weights the contribution of segments whose ends are displaced, but less so than if simply `minov()` were used. It's designed to be more forgiving of small boundary shifts. It's calculated as follows:

```
δ(s₁, s₂) = min {
                   [maxov(s₁, s₂) - minov(s₁, s₂)] / minov(s₁, s₂),
                   int(0.5 * len(s₁)),
                   int(0.5 * len(s₂))
                }
```

* The first term in the `min{}` is a scaled measure of the displacement.
* The second and third terms consider half the lengths of the observed and predicted segments, respectively, preventing excessive penalties when one segment is much shorter than the other. `int()` indicates rounding down to the nearest integer.


**In essence:**  SOV rewards predictions that have a high degree of overlap between observed and predicted segments, both in terms of the number of residues (`minov`) and the position of the segments. The `δ` factor provides a nuanced way to handle differences in segment boundaries. The normalization by `len(s₁)` and `maxov(s₁, s₂)` ensures that the metric is comparable across different proteins and segments of varying lengths.

**Example:**

Imagine an observed helix (H) segment of length 10.  A prediction correctly identifies a helix but is shifted by two residues at one end.

* `len(s₁)` = 10
* `minov(s₁, s₂)` = 8
* `maxov(s₁, s₂)` = 10
* `δ(s₁, s₂)` would likely be quite small.


