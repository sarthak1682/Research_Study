---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/w6-post-bert-arch/","noteIcon":""}
---

---


### ELECTRA

> [!PDF|] [[dl4nlp-slides-complete.pdf#page=379&selection=9,0,15,1|dl4nlp-slides-complete, p.379]]
> (Small) generator model G + (large) Discriminator model D


> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=379&annotation=8354R|dl4nlp-slides-complete, p.379]]
> Generator task: Masked language modeling Discriminator task: Replaced token detection  Predict for each token, whether it is "original" or produced by G

![Attachments/dl4nlp-slides-complete 22.jpg](/img/user/Attachments/dl4nlp-slides-complete%2022.jpg)

[[dl4nlp-slides-complete.pdf#page=380&rect=12,120,348,237|dl4nlp-slides-complete, p.380]]

G and D are transformer encoders, jointly trained


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



![Screenshot 2025-02-17 at 15.43.57.png](/img/user/Attachments/Screenshot%202025-02-17%20at%2015.43.57.png)
Components:

- θ: model parameters we're trying to optimize
- z~Z[T]: sampling permutations z from all possible permutations Z[T]
- x[z[t]]: token at position z[t] in permuted order
- x[z<t]: all tokens that come before z[t] in the permuted order
![Screenshot 2025-02-17 at 15.44.12.png](/img/user/Attachments/Screenshot%202025-02-17%20at%2015.44.12.png)

take a look at the ones before this as well

![Screenshot 2025-01-05 at 03.10.42.png](/img/user/Attachments/Screenshot%202025-01-05%20at%2003.10.42.png)
- The content stream (`h`) builds rich representations by seeing all tokens
- The query stream (`g`) makes predictions while maintaining the autoregressive property
- Both use the same word embeddings (`w`) but process them differently



Model Input: 

Sample Gen: 2 sentences concat

Relative Segment + Relative Positional Encoding vs BERT (both Abs.)
[[RPE\|RPE]]

![dl4nlp-slides-complete 48.jpg](/img/user/Attachments/dl4nlp-slides-complete%2048.jpg)



[[dl4nlp-slides-complete.pdf#page=397&rect=16,28,353,249|dl4nlp-slides-complete, p.397]]
XLNet only predicts the last tokens in a factorization order

Segment Recurrence Mech [[Coursework/WiSe24-25/dl4nlp/Notes/Segment_Rec\|Segment_Rec]]

No Independence Assumption


----
## Tasks as text-to-text Problem

Problems with BERT: 
1) diff model for each task (no true multitask learning)
2) pretraining + finetuning (fine tuning is kinda untypical for humans, task description is typical)
3) needs a lot of examples (we only need a few) 
4) overfitting

---

## T5 (text-to-text transfer transformer)

Input: 

> [!PDF|] [[dl4nlp-slides-complete.pdf#page=423&selection=3,0,7,37|dl4nlp-slides-complete, p.423]]
> SentencePiece framework w/ WordPiece tokens Add task-specific (text) prefix to the original input Choice of the prefix: Hyperparameter!!

Output: 
text, if not in possible alternatives, pred = wrong


Task Prefix vs Prompting: Model fine-tuned on samples with prefix vs zero-shot

![Screenshot 2025-02-17 at 16.30.43.png](/img/user/Attachments/Screenshot%202025-02-17%20at%2016.30.43.png)


token spans: ![Screenshot 2025-02-17 at 16.31.02.png](/img/user/Attachments/Screenshot%202025-02-17%20at%2016.31.02.png)


- **Adapter layers:** Adding small, task-specific layers to the model.
    
- **Gradual Unfreezing (cf. ULMFIT):** A technique where you gradually unfreeze layers of the model during fine-tuning.

 **Multi-task learning strategies:**  
*  **Examples-proportional mixing:** Mixing data from multiple tasks proportionally to the number of examples in each task.  
*  **Temperature-scaled mixing:** Adjust the mixing using temperature.



