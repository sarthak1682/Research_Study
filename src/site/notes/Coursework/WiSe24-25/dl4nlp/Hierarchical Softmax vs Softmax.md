---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/hierarchical-softmax-vs-softmax/","noteIcon":""}
---

---
**. The Problem with Traditional Softmax:**

- **Computational Cost:** Traditional softmax **calculates probabilities for all words in the vocabulary**, which becomes very expensive with large vocabularies.
- **Normalization:** It involves summing up the exponents of scores for all words, which can be numerically unstable.

**2. How Hierarchical Softmax Works:**

- **Tree Structure:** The vocabulary is organized into a hierarchical tree, often a binary tree. Each leaf node represents a word.   
    
- **Probability Calculation:** Instead of computing the probability directly, the model traverses the tree from the root to the leaf node corresponding to the target word. At each internal node, the model makes a binary decision about which branch to follow, based on the learned probabilities associated with each branch. The final probability of the word is the product of the probabilities of the branches taken along the path.   
    
- **Efficiency:** This approach significantly reduces the number of computations needed, as the model only needs to evaluate probabilities along a specific path in the tree, rather than for all words in the vocabulary.   
    

**3. Benefits of Hierarchical Softmax:**

- **Computational Efficiency:** It significantly reduces the computational cost, especially for large vocabularies.   
from 
> [!PDF|187, 97, 229] [[dl4nlp-slides-complete.pdf#page=68&annotation=8299R|dl4nlp-slides-complete, p.68]]
> O(| V |) to O( log2 | V |)

- **Improved Training Speed:** This leads to faster training of NLP models.   
    
- **Reduced Memory Usage:** It requires less memory compared to traditional softmax.!


![Screenshot 2024-10-26 at 17.48.57.png](/img/user/Attachments/Screenshot%202024-10-26%20at%2017.48.57.png)