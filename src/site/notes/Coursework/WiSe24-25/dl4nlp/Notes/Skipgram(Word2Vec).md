---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/skipgram-word2-vec/","noteIcon":""}
---

---

> [!PDF|] [[dl4nlp-slides-complete.pdf#page=75&selection=2,6,3,24|dl4nlp-slides-complete, p.75]]
> Learn many bigram language models at the same time.


1. Core Concept: Skip-gram is a technique to learn word embeddings (vector representations of words) by predicting surrounding context words given a target word.
2. Training Objective:

- Given a target word, the model tries to predict neighboring words within a fixed window size
- For example, if we have the sentence "The quick brown fox jumps" and the target word is "brown":
    - It tries to predict: "quick", "fox" (if window size = 1)
    - It tries to predict: "The", "quick", "fox", "jumps" (if window size = 2)

3. How it Works:

- Uses a sliding window approach over text
- For each target word (w[t]):
    - Predicts words before it: p(w[t-1]|w[t])
    - Predicts words after it: p(w[t+1]|w[t])
    - Can extend to larger windows (w[t-2], w[t+2], etc.)
    - Window size 'c' determines how many words before and after to predict

4. Training Process:

- Objective is to maximize the probability of correctly predicting context words
- Uses negative log-likelihood for the whole corpus of size N
- Employs negative sampling as an approximation technique to make training more efficient
    - For each positive example, samples M negative examples
    - This helps avoid having to compute probabilities over the entire vocabulary

![Attachments/dl4nlp-slides-complete 8.jpg](/img/user/Attachments/dl4nlp-slides-complete%208.jpg)

[[dl4nlp-slides-complete.pdf#page=76&rect=17,22,359,251&color=important|dl4nlp-slides-complete, p.76]]
5. Key Benefits:

- All models share word vectors and parameters
- Can learn multiple language models simultaneously
- Efficient for learning high-quality word vectors
- Captures semantic relationships between words