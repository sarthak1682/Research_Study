---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/fast-text/","noteIcon":""}
---

---
> [!PDF|187, 97, 229] [[dl4nlp-slides-complete.pdf#page=79&annotation=8302R|dl4nlp-slides-complete, p.79]]
> Accomplishments: Words can be repesented as dense, low-dimensional vectors X 
> Easy to capture similarity between words X
>  Additive Compositionality of word vectors X 
> 
> Open issues: Even if we train Word2Vec on a very large corpus, we will still encounter unknown words at test time 
> What about rare words? 
> 	Orthography can often help us: ~w ( remuneration) should be similar to ~w ( remunerate) (same stem) ~w ( iteration) , ~w ( consideration) . . . (same suffix ⇡ same POS)






Core Innovation - Subword Information:
The key innovation of FastText is how it handles words - instead of treating each word as an atomic unit, it breaks words into character n-grams. 
For example, the word "example" would be broken down into:

- Character trigrams (n=3): <ex, exa, xam, amp, mpl, ple, le>
- In practice, they use variable length n-grams (typically 2 ≤ n ≤ 4)
- This helps with:
    - Rare words
    - Unknown words
    - Understanding morphological relationships (like prefixes and suffixes)

![Attachments/dl4nlp-slides-complete 10.jpg](/img/user/Attachments/dl4nlp-slides-complete%2010.jpg)

[[dl4nlp-slides-complete.pdf#page=81&rect=9,31,349,248&color=important|dl4nlp-slides-complete, p.81]]



Mathematical Framework: For known words, the vector is calculated as:
- A combination of the word's own vector and the sum of its n-gram vectors
- This is represented in the mathematical formula shown in slide 2
For unknown words:
- The model can still generate a meaningful vector by combining the vectors of its constituent n-grams
- This is one of FastText's major advantages over traditional word embedding models
- ![dl4nlp-slides-complete 9.jpg](/img/user/Attachments/dl4nlp-slides-complete%209.jpg)


Training Process:

1. ngrams typically contain character sequences of 3-6 characters
2. The skipgram objective is modified to incorporate the new subword-based approach
3. During backpropagation, the gradient is distributed to both the word vector and its associated n-gram vectors


Backprop in FastText: 
During backpropagation in FastText, there's a unique aspect to how gradients are handled. The key point is that the gradient is distributed to both:

1. The main word vector (w̄)
2. All the constituent n-gram vectors (ḡ) that make up that word

This means:

1. Primary Update:

- When an error is calculated for a word, the gradient doesn't just update a single word vector like in traditional word2vec
- Instead, the gradient affects multiple vectors simultaneously

2. Distributed Learning:

- The gradient is split between:
    - The full word representation
    - Each of its n-gram subcomponents
- This means if you have the word "example", updates would affect:
    - The vector for "example" itself
    - The vectors for all its n-grams (<ex, exa, xam, etc.)

3. Shared Learning Benefits:

- This distributed update has a powerful effect:
    - Common n-grams between words allow for shared learning
    - For example, if "walking" and "talked" both have errors, the shared morpheme patterns (like common endings) get updated together
    - This helps the model learn morphological patterns

4. Advantage Over Traditional Methods:

- In traditional word embeddings, each word learns independently
- In FastText, the n-gram sharing means:
    - Learning for one word can improve representations of related words
    - Even rare words benefit from updates to common n-grams
    - New words can get meaningful vectors if their n-grams were seen during training

The formula shown in the slides (with the partial derivative ∂L/∂w̄) indicates that during backpropagation:

- The loss gradient is propagated back through the network
- It affects both the word vector and all associated n-gram vectors
- This creates a more robust learning process where morphological patterns are captured in the embedding space