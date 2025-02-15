---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/omes/","noteIcon":""}
---

---

 Opera [ChatGPT](https://chatgpt.com/c/67a3bf57-ee8c-800e-abaf-545d32e8cf26)

## Overview

The **OMES score** is a statistical measure used to detect co-evolutionary relationships between residues in a multiple sequence alignment (MSA). It compares the observed co-occurrence of residue pairs in two alignment columns with the expected co-occurrence, assuming independence.

### Key Points:

- It is based on a **chi-square nonparametric test**.
- Higher OMES scores indicate **stronger deviation** from expected co-occurrence, suggesting potential co-evolution.
- The expected frequency assumes that the distributions in two columns are independent.

## Mathematical Formulation

### Expected Co-occurrence:

Nex=NxiNyjNvalidN_{ex} = \frac{N_{xi} N_{yj}}{N_{valid}}Nex​=Nvalid​Nxi​Nyj​​

where:

- NxiN_{xi}Nxi​ = occurrences of residue xxx in column iii.
- NyjN_{yj}Nyj​ = occurrences of residue yyy in column jjj.
- NvalidN_{valid}Nvalid​ = number of sequences without gaps in columns iii and jjj.

### OMES Score Calculation:

rij=∑lL(Nobs−Nex)2Nvalidr_{ij} = \sum_{l}^{L} \frac{(N_{obs} - N_{ex})^2}{N_{valid}}rij​=l∑L​Nvalid​(Nobs​−Nex​)2​

where:

- NobsN_{obs}Nobs​ = observed co-occurrence of residue pair (x,y)(x, y)(x,y).
- LLL = number of distinct residue pairs in columns iii and jjj.

---

## Example Calculation

### Given Data:

Let's assume we have an MSA with **4 sequences** and we are analyzing columns **i and j**.

| Sequence | Column i | Column j |
| -------- | -------- | -------- |
| Seq 1    | A        | R        |
| Seq 2    | A        | K        |
| Seq 3    | G        | R        |
| Seq 4    | A        | R        |

#### Step 1: Count Observed Co-occurrences

- Nobs(A,R)=2N_{obs} (A,R) = 2Nobs​(A,R)=2 (A appears with R twice)
- Nobs(A,K)=1N_{obs} (A,K) = 1Nobs​(A,K)=1 (A appears with K once)
- Nobs(G,R)=1N_{obs} (G,R) = 1Nobs​(G,R)=1 (G appears with R once)

#### Step 2: Compute Expected Co-occurrences

1. Compute single residue frequencies:
    
    - Nxi(A)=3N_{xi} (A) = 3Nxi​(A)=3, Nxi(G)=1N_{xi} (G) = 1Nxi​(G)=1
    - Nyj(R)=3N_{yj} (R) = 3Nyj​(R)=3, Nyj(K)=1N_{yj} (K) = 1Nyj​(K)=1
    - Nvalid=4N_{valid} = 4Nvalid​=4
2. Compute NexN_{ex}Nex​:
    
    - Nex(A,R)=3×34=2.25N_{ex} (A, R) = \frac{3 \times 3}{4} = 2.25Nex​(A,R)=43×3​=2.25
    - Nex(A,K)=3×14=0.75N_{ex} (A, K) = \frac{3 \times 1}{4} = 0.75Nex​(A,K)=43×1​=0.75
    - Nex(G,R)=1×34=0.75N_{ex} (G, R) = \frac{1 \times 3}{4} = 0.75Nex​(G,R)=41×3​=0.75

#### Step 3: Compute OMES Score

rij=∑(Nobs−Nex)2Nvalidr_{ij} = \sum \frac{(N_{obs} - N_{ex})^2}{N_{valid}}rij​=∑Nvalid​(Nobs​−Nex​)2​ =(2−2.25)24+(1−0.75)24+(1−0.75)24= \frac{(2 - 2.25)^2}{4} + \frac{(1 - 0.75)^2}{4} + \frac{(1 - 0.75)^2}{4}=4(2−2.25)2​+4(1−0.75)2​+4(1−0.75)2​ =0.06254+0.06254+0.06254= \frac{0.0625}{4} + \frac{0.0625}{4} + \frac{0.0625}{4}=40.0625​+40.0625​+40.0625​ =0.046875= 0.046875=0.046875

---

## Interpretation

- If rijr_{ij}rij​ is **high**, it suggests that the two residues **co-evolve** or have **functional constraints**.
- If rijr_{ij}rij​ is **low**, the co-occurrence might be **random**.
- Comparing OMES scores across residue pairs helps identify important **functional interactions** in proteins.


---
