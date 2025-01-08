---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/ddp/","noteIcon":""}
---

---
**3. Double Dynamic Programming (DDP):**

DDP attempts to address the interdependence issue in structural alignment.  It uses two levels of dynamic programming:

1. **Low-level DP:**  For each pair of residues (a_i, b_j) from proteins A and B, perform a dynamic programming alignment of the local structural environment around a_i and b_j. This gives a score reflecting the likelihood that this residue pair belongs to an optimal alignment.  The local environment could be defined by distances to neighboring residues or other structural features.

2. **High-level DP:**  Construct a high-level scoring matrix where each entry (i, j) contains the score obtained from the low-level DP for the residue pair (a_i, b_j). This matrix captures the structural similarity around each potential residue pair.

3. **Final alignment:** Perform a standard dynamic programming alignment using the high-level scoring matrix. This final step effectively incorporates structural information from the local environments into the global alignment.

DDP is more computationally intensive than iterative methods, but it can sometimes produce better alignments, especially for distantly related proteins.![Screenshot 2025-01-07 at 08.31.50.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2008.31.50.png)

If two alignment paths cross the same matrix position, the scores of those positions are summed
One part of the alignment (black) is found in both comparisons (corroborative evidence of similarity)

A second dynamic programming alignment is performed through this matrix