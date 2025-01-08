---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/w6-post-bert/","noteIcon":""}
---

---


### ELECTRA

> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=379&annotation=8354R|dl4nlp-slides-complete, p.379]]
> Generator task: Masked language modeling Discriminator task: Replaced token detection

![Attachments/dl4nlp-slides-complete 22.jpg](/img/user/Attachments/dl4nlp-slides-complete%2022.jpg)

[[dl4nlp-slides-complete.pdf#page=380&rect=12,120,348,237|dl4nlp-slides-complete, p.380]]
> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=379&annotation=8357R|dl4nlp-slides-complete, p.379]]
> Predict for each token, whether it is "original" or produced by G


![Attachments/dl4nlp-slides-complete 23.jpg](/img/user/Attachments/dl4nlp-slides-complete%2023.jpg)

[[dl4nlp-slides-complete.pdf#page=382&rect=15,71,349,207|dl4nlp-slides-complete, p.382]]

Gen Loss: Standard MLM Loss
Disc. Loss: BCE 

smaller Gen: 1/4 to half the size of D are preferable

---
## AR vs AE

AR: only uni-dir
![Attachments/dl4nlp-slides-complete 24.jpg](/img/user/Attachments/dl4nlp-slides-complete%2024.jpg)

[[dl4nlp-slides-complete.pdf#page=386&rect=131,170,266,207|dl4nlp-slides-complete, p.386]]

![Attachments/dl4nlp-slides-complete 26.jpg](/img/user/Attachments/dl4nlp-slides-complete%2026.jpg)

[[dl4nlp-slides-complete.pdf#page=386&rect=52,71,320,114|dl4nlp-slides-complete, p.386]]

AE: reconstruct masked tokens x_bar form corrupted seq (x_hat)

AE assumes independence between corrupted tokens


---
### PLM + XLNet

AR + birdir. 
two streams of attention: Content-Stream + Query-S

The key idea is that this dual-stream approach allows XLNet to:

1. Build rich representations (through content stream)
2. Make honest predictions (through query stream)
3. Learn bidirectional context without using artificial [MASK] tokens

take a look at the ones before this as well

![Screenshot 2025-01-05 at 03.10.42.png](/img/user/Attachments/Screenshot%202025-01-05%20at%2003.10.42.png)

Model Input: 

Sample Gen: 2 sentences concat

Relative Segment + Relative Positional Encoding vs BERT (both Abs.)
[[RPE\|RPE]]


XLNet only predicts the last tokens in a factorization order

Segment Recurrence Mech [[Coursework/WiSe24-25/dl4nlp/Notes/Segment_Rec\|Segment_Rec]]

No Independence Assumption


----
### 



---

### T5 

