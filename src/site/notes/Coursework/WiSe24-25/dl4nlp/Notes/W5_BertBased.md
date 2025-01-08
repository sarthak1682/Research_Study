---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/w5-bert-based/","noteIcon":""}
---

---
###  Roberta: Robustly Optimized BERT Approach


> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=336&annotation=8342R|dl4nlp-slides-complete, p.336]]
> Change of the MASK ing strategy ! BERT masks the sequences once before pre-training !
>  RoBERTa uses dynamic MASK ing ! RoBERTa sees the same sequence MASK ed differently RoBERTa does not use the additional NSP objective during pre-training
>   Authors claim that BERT is seriously "undertrained" 160 GB pre-training corpus instead of 13 GB Pre-training is performed with larger batch sizes (8k) Training on full-length sequences only (512 tokens)


> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=338&annotation=8345R|dl4nlp-slides-complete, p.338]]
> Dynamic Masking (RoBERTa): Duplicate the training corpus ten times Apply MASK ing procedure to each duplicate of the pre-training corpus Train for 40 epochs


---
### ALBERT: A lite BERT

The key change is **disentangling the size of the word embedding layer (E) from the size of the hidden layer (H)**.
	done to save memory and compute resources

#### cross-layer parameter sharing
 Sharing parameters, especially FFN parameters, drastically reduces the model size.

Sharing parameters hurts performance compared to the baseline (no sharing). This effect is more pronounced:

- For models with larger embedding sizes (E).
- When sharing FFN parameters compared to attention parameters.


---
### Model Distillation

Temp:
	A higher temperature smooths the probability distribution produced by the teacher, making it "softer." This softened distribution provides more information for the student to learn from than just the hard predictions (highest probability class). During inference (actual use of the student model), the temperature is set back to 1 to get standard softmax probabilities.![Attachments/dl4nlp-slides-complete 18.jpg](/img/user/Attachments/dl4nlp-slides-complete%2018.jpg)

[[dl4nlp-slides-complete.pdf#page=362&rect=117,169,254,211|dl4nlp-slides-complete, p.362]]

> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=363&annotation=8348R|dl4nlp-slides-complete, p.363]]
> Advantage of the soft targets: ! No need to know the true labels of the training instances ! More fine-grained information about the teacher’s behaviour 
> When true labels are known: Weighted average of two different objective functions possible ! 
> 	On soft targets (Be close to the teacher ) 
> 	 on hard targets (be close to the “ground truth“ 

![Attachments/dl4nlp-slides-complete 19.jpg](/img/user/Attachments/dl4nlp-slides-complete%2019.jpg)

[[dl4nlp-slides-complete.pdf#page=365&rect=22,109,333,244|dl4nlp-slides-complete, p.365]]


Pruning:

![Attachments/dl4nlp-slides-complete 20.jpg](/img/user/Attachments/dl4nlp-slides-complete%2020.jpg)

[[dl4nlp-slides-complete.pdf#page=370&rect=110,110,296,150|dl4nlp-slides-complete, p.370]]
Sensitivity of the loss wrt the values of the neurons

SSL Pruning:
![Attachments/dl4nlp-slides-complete 21.jpg](/img/user/Attachments/dl4nlp-slides-complete%2021.jpg)

[[dl4nlp-slides-complete.pdf#page=371&rect=95,147,296,173|dl4nlp-slides-complete, p.371]]



