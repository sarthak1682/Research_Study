---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/w1-dl4nlp/","noteIcon":""}
---

---

Can you embed a sentence, mapping a cluster of thought possible? 

One-hot vs Dense Embeddings? 
	- of One-hot
		- High D
		- Not possible to measure similarity

![Attachments/dl4nlp-slides-complete 32.jpg](/img/user/Attachments/dl4nlp-slides-complete%2032.jpg)

[[dl4nlp-slides-complete.pdf#page=20&rect=78,64,297,246|dl4nlp-slides-complete, p.20]]

Induction vs Transduction:

Induction:- This is the process of making generalizations from specific observations. For example, if you observe sev> [!PDF|] [[dl4nlp-slides-complete.pdf#page=36&selection=44,25,44,27|dl4nlp-slides-complete, p.36]]
> DT
eral instances of a phenomenon, you might infer a general rule. In machine learning, this involves creating a model based on a set of training data and using it to make predictions about unseen data.
    
    Example: After seeing many apples falling from trees, you might generalize that "all apples fall down due to gravity."
    
Transduction: Instead of inferring a general rule, transduction focuses on making predictions directly from specific cases without forming a general rule. It’s often seen as a more direct way to infer from given data points to new ones. In machine learning, this can be associated with algorithms like k-nearest neighbors, where the model directly relates known cases to make predictions about new cases, without inferring an explicit underlying rule.
    
    Example: Given that you've seen an apple fall in a similar situation, you predict another apple will fall under the same conditions without assuming a general rule for all apples.



Transfer Learning: Pre-training + Fine-tuning
> [!PDF|187,97,229] [[dl4nlp-slides-complete.pdf#page=21&annotation=8285R|dl4nlp-slides-complete, p.21]]
> Pre-training: Using unlabeled corpora in conjunction with self-supervised objectives is commonly referred to as Pre-Training the model

> [!PDF|187,97,229] [[dl4nlp-slides-complete.pdf#page=22&annotation=8288R|dl4nlp-slides-complete, p.22]]
> The second phase of transfer learning, i.e. adapting the pre-trained model to a labeled data set for a specific downstream task is referred to as Fine-Tuning

 Prompting Differences
![Attachments/dl4nlp-slides-complete.jpg](/img/user/Attachments/dl4nlp-slides-complete.jpg)


unigram vs bigram

- **Unigram:** Each individual word is a unit. (e.g., "the", "quick", "brown", "fox")
- **Bigram:** Each two-word sequence is a unit. (e.g., "the quick", "quick brown", "brown fox")


NLP Tasks
Seq Tagging
![Screenshot 2024-10-26 at 17.36.15.png](/img/user/Attachments/Screenshot%202024-10-26%20at%2017.36.15.png)

Structure Prediction
![Screenshot 2024-10-26 at 17.36.46.png](/img/user/Attachments/Screenshot%202024-10-26%20at%2017.36.46.png)


Semantics
![Screenshot 2024-10-26 at 17.37.05.png](/img/user/Attachments/Screenshot%202024-10-26%20at%2017.37.05.png)



### Neural Prob LM

Next token Prediction: 
![Attachments/dl4nlp-slides-complete 1.jpg](/img/user/Attachments/dl4nlp-slides-complete%201.jpg)

[[dl4nlp-slides-complete.pdf#page=53&rect=26,62,352,220&color=important|dl4nlp-slides-complete, p.53]]


Problems with Markov: 

Curse of Dim, Sparsity (
> [!PDF|] [[dl4nlp-slides-complete.pdf#page=55&selection=40,7,63,5|dl4nlp-slides-complete, p.55]]
> considering |V | = 1.000.000 & bi-grams as context Unlikely to observe all of them bi-gram combinations (a) ever (b) often
)


Using a neural network induces non-linearity and overcomes the shortcomings of traditional models (e.g Markov Models)
(a)  Linear increase in  # parameters with increasing context size
(b)  Better generalization
Input:  Context of  (n  −  1)  words  [w(t−n+1):(t−1)] 
In between: 
Look-up table  [~w(wt−n+1);  ..;  ~w(wt−2);  ~w(wt−1)] 
Non-linearity  e.g. tanh, ReLU 
Output: Probability distribution over the next word  P(wt  |w(t−n+1):(t−1))

![Screenshot 2024-10-16 at 11.41.45.png](/img/user/Attachments/Screenshot%202024-10-16%20at%2011.41.45.png)


Problems? 
Vanilla Softmax: Expensive, 
Solution: Hierarchical Softmax/Sampling
Down below


> [!PDF|187, 97, 229] [[dl4nlp-slides-complete.pdf#page=58&annotation=8291R|dl4nlp-slides-complete, p.58]]
> Still relying on the markov assumption

Wat? Not really but the context window still has to be specified manually. 

### Word Embeddings

words that similar roles wrt task get similar embeddings
![Attachments/dl4nlp-slides-complete 2.jpg](/img/user/Attachments/dl4nlp-slides-complete%202.jpg)

[[dl4nlp-slides-complete.pdf#page=63&rect=17,135,244,168&color=important|dl4nlp-slides-complete, p.63]]
Why don't we prune out the words that are quite similar and make a minimal Vocab? (Intuition is making something approximating a natural Programming Language?)

Word2Vec Model Architecture: 
[Claude](https://claude.ai/chat/474d19d6-e467-4c9c-a706-50576b4b5e2c)
![Attachments/dl4nlp-slides-complete 3.jpg](/img/user/Attachments/dl4nlp-slides-complete%203.jpg)

[[dl4nlp-slides-complete.pdf#page=65&rect=18,108,341,226|dl4nlp-slides-complete, p.65]]
f can be softmax

Problems with Softmax? 
	Needs to compute dot products with the whole vocabulary in the denominator for every single prediction

[[Coursework/WiSe24-25/dl4nlp/Notes/Hierarchical Softmax vs Softmax\|Hierarchical Softmax vs Softmax]]

[[Coursework/WiSe24-25/dl4nlp/Notes/Negative Sampling\|Negative Sampling]]

[[Coursework/WiSe24-25/dl4nlp/Notes/Skipgram(Word2Vec)\|Skipgram(Word2Vec)]]


[[Coursework/WiSe24-25/dl4nlp/Notes/CBOW\|CBOW]]

[[Coursework/WiSe24-25/dl4nlp/Notes/FastText\|FastText]]


$$\mathcal{L} = \sum_{t=1}^{T} \sum_{-c \leq j \leq c, j \neq 0} \left[ \log \sigma(v_{w_t}^T \cdot v_{w_{t+j}}) + \sum_{k=1}^{T} \mathbb{E}_{w_k \sim P_n(w)} \left[ \log \sigma(-v_{w_t}^T \cdot v_{w_k}) \right] \right]$$

