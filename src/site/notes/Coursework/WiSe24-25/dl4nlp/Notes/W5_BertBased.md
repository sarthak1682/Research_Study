---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/w5-bert-based/","noteIcon":""}
---

---
###  Roberta: Robustly Optimized BERT Approach


> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=336&annotation=8342R|dl4nlp-slides-complete, p.336]]
> Change of the MASK ing strategy 
> 	 BERT masks the sequences once before pre-training !
> 	 RoBERTa uses dynamic MASK ing ! 
> 	RoBERTa sees the same sequence MASK ed differently 
> 	RoBERTa does not use the additional NSP objective during pre-training
>   Authors claim that BERT is seriously "undertrained"
> 	   160 GB pre-training corpus instead of 13 GB 
> 	   Pre-training is performed with larger batch sizes (8k) 
>   Training on full-length sequences only (512 tokens)


> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=338&annotation=8345R|dl4nlp-slides-complete, p.338]]
> Dynamic Masking (RoBERTa): Duplicate the training corpus ten times Apply MASK ing procedure to each duplicate of the pre-training corpus Train for 40 epochs

![Attachments/dl4nlp-slides-complete 47.jpg](/img/user/Attachments/dl4nlp-slides-complete%2047.jpg)

[[dl4nlp-slides-complete.pdf#page=339&rect=20,20,349,270|dl4nlp-slides-complete, p.339]]


---
### ALBERT: A lite BERT

The key change is **disentangling the size of the word embedding layer (E) from the size of the hidden layer (H)**.
> [!PDF|] [[dl4nlp-slides-complete.pdf#page=345&selection=16,11,22,1|dl4nlp-slides-complete, p.345]]
> Transformer/BERT: E = H

done to save memory and compute resources

If E≠HE=H, you need a projection from the embedding dimension EE to the dimension used by each head (often H/AH/A if there are AA attention heads)

- Potentially _shrink_ the embedding layer dimension to reduce parameter usage or speed up the model.
- Keep or _expand_ the hidden dimension to maintain (or increase) the model’s ability to encode complex patterns. (Most of the model’s representational power is in the deeper transformer layers—so you may want to _allocate more capacity_ there (i.e., keep HH large))
- Experiment with different EE-to-HH ratios to find the sweet spot between memory, speed, and model performance.
#### cross-layer parameter sharing
 Sharing parameters, especially FFN parameters, drastically reduces the model size.

Sharing parameters hurts performance compared to the baseline (no sharing). This effect is more pronounced:

- For models with larger embedding sizes (E).
- When sharing FFN parameters compared to attention parameters.
	Why? 
	The key intuition is that parameter sharing creates a bottleneck in the model's representational capacity, forcing different layers to use the same transformation when they would benefit from learning specialized functions. This limitation becomes more severe as model size increases since larger models have more potential for layer-specific specialization

Another change is n-gram masking instead of single tokens



Alber also has SOP (Sentence Order Pred.)

---
### Model Distillation


types of targets 
“hard” targets (typical one-hot labels)
“soft” targets (continuous probability distributions)
	Logits + L2Loss
	Softmax Scores
	Temp in Softmax

Temp:
	A higher temperature smooths the probability distribution produced by the teacher, making it "softer." This softened distribution provides more information for the student to learn from than just the hard predictions (highest probability class). During inference (actual use of the student model), the temperature is set back to 1 to get standard softmax probabilities. z_i/z_j are raw logits
	![Attachments/dl4nlp-slides-complete 18.jpg](/img/user/Attachments/dl4nlp-slides-complete%2018.jpg)

[[dl4nlp-slides-complete.pdf#page=362&rect=117,169,254,211|dl4nlp-slides-complete, p.362]]

> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=363&annotation=8348R|dl4nlp-slides-complete, p.363]]
> Advantage of the soft targets: ! No need to know the true labels of the training instances ! More fine-grained information about the teacher’s behaviour 
> When true labels are known: Weighted average of two different objective functions possible ! 
> 	On soft targets (Be close to the teacher ) 
> 	 on hard targets (be close to the “ground truth“ 


Distillbert (1/2 Layers, No Segment Embedding req. for NSP)

![Attachments/dl4nlp-slides-complete 19.jpg](/img/user/Attachments/dl4nlp-slides-complete%2019.jpg)

[[dl4nlp-slides-complete.pdf#page=365&rect=22,109,333,244|dl4nlp-slides-complete, p.365]]

subseq. papers show that removing MLM loss has little impact. 


Pruning:
- **Common pruning procedure in NLP:**  
    A popular way to decide which parts to prune is to measure how sensitive the model’s loss is to each parameter or neuron.
    
    Importance Score (IS)(Θ)  =  Ex,y ⁣∣∂L(x)∂Θ∣Importance Score (IS)(Θ)=Ex,y​​∂Θ∂L(x)​​
    - Here, ΘΘ could represent a particular neuron, weight, or module.
    - A large absolute gradient implies that changing that parameter has a big impact on the loss, so it is considered more “important.”
    - Conversely, a small gradient suggests the parameter is less critical.
- **Common choices for what to prune:**
    
    - **Attention heads** (removing entire heads in the Transformer’s multi-head attention).
    - **Intermediate neurons in feed-forward layers** (removing entire neurons in the MLP part of a Transformer block).


![Attachments/dl4nlp-slides-complete 20.jpg](/img/user/Attachments/dl4nlp-slides-complete%2020.jpg)

[[dl4nlp-slides-complete.pdf#page=370&rect=110,110,296,150|dl4nlp-slides-complete, p.370]]
Sensitivity of the loss wrt the values of the neurons

SSL Pruning:
![Attachments/dl4nlp-slides-complete 21.jpg](/img/user/Attachments/dl4nlp-slides-complete%2021.jpg)

[[dl4nlp-slides-complete.pdf#page=371&rect=95,147,296,173|dl4nlp-slides-complete, p.371]]


![Screenshot 2025-02-17 at 15.21.07.png](/img/user/Attachments/Screenshot%202025-02-17%20at%2015.21.07.png)
