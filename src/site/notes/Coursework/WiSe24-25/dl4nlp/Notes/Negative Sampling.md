---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/negative-sampling/","noteIcon":""}
---

---
The key idea of negative sampling is to reformulate the word2vec training from a massive multiclass prediction problem (predicting probability distribution over entire vocabulary) into a simpler binary classification task.

Here's how it works:

1. For each word pair that appears in the corpus ("positive samples"), like ("cat", "dog") that actually occur near each other:
    - We attempt to maximize P(pos|w("cat"), v("dog"))
    - This probability is modeled as σ(w·v) where σ is the sigmoid function
2. Then we randomly sample words that don't appear together ("negative samples"):
    - For example, maybe ("cat", "democracy") which likely don't appear together
    - We maximize P(neg|w("cat"), v("democracy")) = 1 - P(pos|w("cat"), v("democracy"))
    - This pushes apart vectors for unrelated words

The likelihood function (L) in the second slide combines both:

- First product term: maximize probability of positive samples (real word pairs)
- Second product term: maximize probability of negative samples (random word pairs)


![Attachments/dl4nlp-slides-complete 6.jpg](/img/user/Attachments/dl4nlp-slides-complete%206.jpg)

[[dl4nlp-slides-complete.pdf#page=68&rect=6,65,361,191&color=important|dl4nlp-slides-complete, p.68]]

![Attachments/dl4nlp-slides-complete 7.jpg](/img/user/Attachments/dl4nlp-slides-complete%207.jpg)

[[dl4nlp-slides-complete.pdf#page=69&rect=6,26,358,271&color=important|dl4nlp-slides-complete, p.69]]



1. Components in Word2Vec with negative sampling:
- x(i): A word pair, which could be either:
    - Real pair from corpus (like "cat" and "dog" appearing together)
    - Randomly created pair (like "cat" and "democracy")
- y(i): Binary label:
    - y=1 for real pairs from corpus (positive samples)
    - y=0 for random pairs (negative samples)
- θ: Model parameters (the word vectors w and context vectors v)
- P(1|·): Probability of being a real pair = σ(w·v)
- P(0|·): Probability of being a random pair = 1 - σ(w·v)

2. Practical Implementation Details:
- Creating negative samples:
    - Common approach: Take a real bigram like "new york"
    - Replace second word with random word: "new potato"
    - Do this 1x to 20x more than positive samples
    - Generate these per batch during training

3. Computational Efficiency (from last question):
- For vocabulary size |V| = 1,000,000
- Using M = 20 negative samples
- Need only M + 1 ≈ log₂|V| dot products
    - That's about 20 calculations vs 1,000,000 in naive softmax!