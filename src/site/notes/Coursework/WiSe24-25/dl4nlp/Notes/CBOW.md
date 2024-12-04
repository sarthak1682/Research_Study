---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/cbow/","noteIcon":""}
---

---
1. Task Structure:

- Training objective: Given a context (surrounding words), predict the center word
- It's called "continuous" because it uses continuous vector representations of words
- It's a "bag" of words because the order of context words doesn't matter

2. Using the example from the image with window size = 2:

- Sentence: "The quick brown fox jumps over the lazy dog"
- When trying to predict "brown":
    - Input context: ["the", "quick", "fox", "jumps"]
    - Target word: "brown"
- When trying to predict "fox":
    - Input context: ["quick", "brown", "jumps", "over"]
    - Target word: "fox"

3. How it differs from Skip-gram:

- Skip-gram predicts context words from the center word
- CBOW predicts the center word from context words
- CBOW tends to be faster and has better representations for more frequent words

4. The neural network architecture :

- Input layer: Context words are encoded as one-hot vectors
- Hidden layer: Creates a compressed representation
- Output layer: Produces probability distribution over vocabulary
- The model learns to maximize the probability of the correct center word given its context

5. Key advantages:

- Learns high-quality word vectors
- Can capture semantic relationships between words
- More efficient than Skip-gram for large datasets
- Better at handling frequent words