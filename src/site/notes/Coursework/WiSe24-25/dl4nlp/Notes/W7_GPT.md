---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/w7-gpt/","noteIcon":""}
---

---


> [!PDF|] [[dl4nlp-slides-complete.pdf#page=438&selection=2,0,27,44|dl4nlp-slides-complete, p.438]]
> Transformer decoder as backbone of the architecture 12-layer-decoder with masked self-attention mechanism 
> Hidden dimension H = 768, A = 12 Attention heads 
> BPE vocabulary w/ 40k merges 
> Learned positional embeddings (as opposed to fixed, sinusoidal ones in the original Transformer)

GPT-1

![Attachments/dl4nlp-slides-complete 31.jpg](/img/user/Attachments/dl4nlp-slides-complete%2031.jpg)

[[dl4nlp-slides-complete.pdf#page=438&rect=31,48,319,145|dl4nlp-slides-complete, p.438]]


Objectives: 
![Screenshot 2025-01-05 at 04.38.36.png](/img/user/Attachments/Screenshot%202025-01-05%20at%2004.38.36.png)
next-token pred

Fine-tuning
Sequence-level pred
![Screenshot 2025-01-05 at 04.39.18.png](/img/user/Attachments/Screenshot%202025-01-05%20at%2004.39.18.png)

Combine: 
![Screenshot 2025-02-17 at 16.37.31.png](/img/user/Attachments/Screenshot%202025-02-17%20at%2016.37.31.png)



---
## GPT-2

decoder pre-trained on AR LM 
Context: 1024
Byte-Level BPE for tokenization




---
## GPT-3

![Attachments/dl4nlp-slides-complete 27.jpg](/img/user/Attachments/dl4nlp-slides-complete%2027.jpg)

[[dl4nlp-slides-complete.pdf#page=458&rect=46,60,341,212|dl4nlp-slides-complete, p.458]]

GPT vs BERT


ICL :
Outer Loop = Pre-training

Inner Loop
> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=460&annotation=8363R|dl4nlp-slides-complete, p.460]]
> t uses these abilities to rapidly adapt to a desired task (= in-context learning) Just a single forward pass w/o any gradient updates



![Screenshot 2025-01-05 at 04.26.42.png](/img/user/Attachments/Screenshot%202025-01-05%20at%2004.26.42.png)