---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/cm-ij-calc/","noteIcon":""}
---

---
### **Step-by-Step Explanation of the Formula**

CMij=rij=1N∑klWkl(sikl−⟨si⟩)(sjkl−⟨sj⟩)σiσjCMij​=rij​=N1​kl∑​Wkl​σi​σj​(sikl​−⟨si​⟩)(sjkl​−⟨sj​⟩)​

![Screenshot 2025-02-08 at 18.22.52.png](/img/user/Attachments/Screenshot%202025-02-08%20at%2018.22.52.png)
where:

- NN = number of sequences in the MSA.
- k,lk,l = indices of sequence pairs.
- siklsikl​ = similarity score between residues at position ii in sequences kk and ll.
- ⟨si⟩⟨si​⟩ = average similarity score for position ii.
- σiσi​ = standard deviation of similarity scores for position ii.
- WklWkl​ = weight to downweight similar sequences.

---

### **Example Calculation**

#### **Step 1: Consider an MSA**

Assume we have the following aligned sequences:

less

CopyEdit

`Seq 1: A T G C Seq 2: A C G C Seq 3: G T A C Seq 4: A T G G`

We want to compute CM12CM12​, the correlated mutation score between positions **1 and 2**.

#### **Step 2: Define a Similarity Matrix**

Let’s assume we use a simple similarity scoring system:

|Residue Pair|Score|
|---|---|
|Same|1|
|Different|0|

We compute the pairwise similarity at positions 1 and 2:

|Sequence Pair|Position 1 Similarity|Position 2 Similarity|
|---|---|---|
|(Seq1, Seq2)|1|0|
|(Seq1, Seq3)|0|1|
|(Seq1, Seq4)|1|1|
|(Seq2, Seq3)|0|0|
|(Seq2, Seq4)|1|0|
|(Seq3, Seq4)|0|1|

#### **Step 3: Compute Mean Similarity**

⟨s1⟩=1+0+1+0+1+06=36=0.5⟨s1​⟩=61+0+1+0+1+0​=63​=0.5⟨s2⟩=0+1+1+0+0+16=36=0.5⟨s2​⟩=60+1+1+0+0+1​=63​=0.5

#### **Step 4: Compute Standard Deviations**

σ1=(1−0.5)2+(0−0.5)2+(1−0.5)2+(0−0.5)2+(1−0.5)2+(0−0.5)26σ1​=6(1−0.5)2+(0−0.5)2+(1−0.5)2+(0−0.5)2+(1−0.5)2+(0−0.5)2​​=0.25+0.25+0.25+0.25+0.25+0.256=1.56=0.5=60.25+0.25+0.25+0.25+0.25+0.25​​=61.5​​=0.5σ2=0.5(by the same calculation as σ1)σ2​=0.5(by the same calculation as σ1​)

#### **Step 5: Compute Pearson Correlation (CM1212​)**

CM12=1N∑klWkl(sikl−⟨si⟩)(sjkl−⟨sj⟩)σiσjCM12​=N1​kl∑​Wkl​σi​σj​(sikl​−⟨si​⟩)(sjkl​−⟨sj​⟩)​=16∑(s1−0.5)(s2−0.5)0.5×0.5=61​∑0.5×0.5(s1​−0.5)(s2​−0.5)​=16[(1−0.5)(0−0.5)0.25+(0−0.5)(1−0.5)0.25+...]=61​[0.25(1−0.5)(0−0.5)​+0.25(0−0.5)(1−0.5)​+...]

After computing the sum, if CM1212​ is **positive**, it means these positions **co-evolve** (mutations are correlated). If it's **negative**, mutations at one position tend to **avoid** mutations at the other.