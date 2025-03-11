---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/w-last/","noteIcon":""}
---

---
## Fine Tuning


"old-style” single-task fine-tuning supervised training of the pre-trained model on a task-specific training set of size k (where k is not small, e.g., k = 100)

issues: > [!PDF|] [[W9101112.pdf#page=16&selection=4,1,17,50|W9101112, p.16]]
> Sequential transfer learning instead of true multi-task learning 
> Generalization of the model only w.r.t. to one task / data distribution
>  Requires quite a bit of annotated data (e.g., k = 100)
>   Single-task models have poor few-shot capabilities


few-shot prompting (e.g 5 examples, then analogize)

issues: > [!PDF|] [[W9101112.pdf#page=17&selection=3,0,4,27|W9101112, p.17]]
> Classification: Assumption: Model has learned about the task during (unsupervised) pre-training
> Text Gen: 


multi-task finetuning
	Finetuning + Prompting
	tasks in the classical NLP Sense




instruction tuning (can be seen as a form of fine-tuning)
	includes open-ended gen and alignment
	HHH (Helpful, Harmless and Honest)

continued pre-training is also called finetuning sometimes

---
## COT-P


improves on arithmetic + commonsense![Screenshot 2025-02-16 at 14.26.20.png](/img/user/Attachments/Screenshot%202025-02-16%20at%2014.26.20.png)


What could go wrong? 
1. Hallucinated reasoning steps where the model invents plausible-sounding but incorrect logical connections, leading to wrong conclusions despite appearing methodical.
2. Computational overhead since forcing the model to show all work takes more tokens/time than direct answers, which may be unnecessary for simpler tasks.
3. Path dependence where early reasoning mistakes propagate through the chain, amplifying errors rather than catching them.
4. Over-explanation on trivial tasks where step-by-step reasoning adds unnecessary complexity and potential failure points.
5. False confidence from detailed reasoning that looks thorough but may still be fundamentally flawed - the appearance of careful thought doesn't guarantee accuracy.


helpful for problems with generator-verifier gap (Sudoko, Programming)

---
## RLHF

Why? 
- Alignment
- Harm 
- Hallucination
- Dialog/Follow Instructions/Be helpful in a dialog/Sycophancy is a problem

> [!PDF|] [[W9101112.pdf#page=102&selection=0,32,10,37|W9101112, p.102]]
>  Three steps from GPT3 to InstructGPT
1. Finetuning on human-written dialogs
2. Create a reward model that measures quality of dialogs – not directly based on dialogs, but on preferences which dialogs are better/worse. 
3. Use reward model for further training
![Screenshot 2025-02-16 at 14.33.46.png](/img/user/Attachments/Screenshot%202025-02-16%20at%2014.33.46.png)

Step 1: SFT

Step2: RM
![Screenshot 2025-02-16 at 14.36.01.png](/img/user/Attachments/Screenshot%202025-02-16%20at%2014.36.01.png)
- The loss is minimized when the model assigns higher scores to preferred responses
- The sigmoid ensures smooth gradients for training
- The log makes the model particularly averse to confident wrong predictions
- The scaling factor ensures the loss is comparable across different numbers of comparisons


1. Training Signal Clarity

- When all comparisons (x1 < x2 < x3) are in one batch, the signal is clear: "don't move"
- When split across batches, you get potentially confusing signals as each batch only sees part of the ordering


Step3: PPO
![Screenshot 2025-02-16 at 14.37.04.png](/img/user/Attachments/Screenshot%202025-02-16%20at%2014.37.04.png)

Note that PPO is better than SFT on all detailed measures, but not on hallucinations!

Attack Suffix
![Screenshot 2025-02-16 at 14.45.05.png](/img/user/Attachments/Screenshot%202025-02-16%20at%2014.45.05.png)

Word Rep. Attacks
![Screenshot 2025-02-16 at 14.45.24.png](/img/user/Attachments/Screenshot%202025-02-16%20at%2014.45.24.png)


Hallucination Formal Def
![Screenshot 2025-02-16 at 14.45.50.png](/img/user/Attachments/Screenshot%202025-02-16%20at%2014.45.50.png)


---
## Scaling Laws
(about pre-training)
Imp
![Attachments/W9101112.jpg](/img/user/Attachments/W9101112.jpg)

[[W9101112.pdf#page=187&rect=13,22,340,206|W9101112, p.187]]


### 1. **“Convergence is inefficient”**

- **Context**: In large-scale training, you often have a fixed compute budget CC. However, you can vary:
    
    - NN: the amount of data you use,
    - DD: the size (or number of parameters) of the model.
- **Key idea**: When CC (compute) is fixed, it’s more effective to train **larger models** but stop training **before they fully converge**. This strategy—often called _early stopping_—tends to yield better performance than using a smaller model and training it to convergence.
    
- **Claim**: As models grow in size, they generally:
    
    1. Perform better overall (given the same compute).
    2. Are more sample-efficient (they learn more from each token/instance)


### 2. **Optimal batch size**

- **Claim**: There is an “optimal batch size” for training large models, determined by the _gradient noise scale_ (a measure of how noisy the gradient is across different examples).
    
- **Why does this matter?**
    
    - If the batch size is too small, training can be unstable or slow to converge.
    - If the batch size is too large, you waste compute by over-smoothing the gradient (and might also generalize worse).
    - There’s a sweet spot where the model trains efficiently and effectively.
- **Practical takeaway**: Research  suggests that for very large language models, the optimal batch size is around **1–2 million tokens** per update at today’s scale

![Screenshot 2025-02-16 at 14.51.39.png](/img/user/Attachments/Screenshot%202025-02-16%20at%2014.51.39.png)
Chinchilla has 1/4x params and 4x tokens for training than Gopher

Nowadays there has been a shift towards joint opt. of training and testing 


$P(word_i|word_j) = \frac{\exp(\mathbf{w}^{(i)} \cdot \mathbf{v}^{(j)})}{\sum_{k=1}^{|V|} \exp(\mathbf{w}^{(k)} \cdot \mathbf{v}^{(j)})}$
