---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/w2-dl4nlp/","noteIcon":""}
---

----


## ELMO

[ChatGPT](https://chatgpt.com/c/6729e997-4b18-800b-a91b-f5204f652c3c)
![Attachments/dl4nlp-slides-complete 34.jpg](/img/user/Attachments/dl4nlp-slides-complete%2034.jpg)

[[dl4nlp-slides-complete.pdf#page=131&rect=19,14,330,243|dl4nlp-slides-complete, p.131]]

This slide provides an overview of ELMo (Embeddings from Language Models) embeddings, a method for obtaining context-sensitive representations of tokens based on a two-layer bidirectional LSTM (BiLSTM) architecture.

### Key Components

1. **Character-based Token Representations:**
   - ELMo embeddings start with a character-level representation for each token. This initial representation is context-independent and helps capture the morphological features of each word.

2. **Two-layer BiLSTM Architecture:**
   - The main architecture for ELMo embeddings is a two-layer BiLSTM. This architecture enables ELMo to capture context-sensitive information by passing each token's representation through both forward and backward LSTMs.

3. **Context-dependent Representations:**
   - In each layer, two context-dependent representations are generated for each token:
     - \(\overrightarrow{h_{k,j}^{LM}}\): Forward LSTM representation for the \(k\)-th token in the \(j\)-th layer.
     - \(\overleftarrow{h_{k,j}^{LM}}\): Backward LSTM representation for the \(k\)-th token in the \(j\)-th layer.
   - Since there are two layers, each token has a total of four context-dependent representations (two per layer).

4. **Five Representations per Token:**
   - Along with the initial character-based representation \(\tilde{x}_k^{LM}\), each token has five different representations in total:
     - One character-based representation.
     - Four context-dependent representations from the two layers of BiLSTM (two in each layer).

   - These five representations provide a rich, context-sensitive embedding for each token, combining character-level information with multi-layer contextual information from forward and backward LSTMs.

### Graphical Representation (Slides 6 and 7)

The graphical representation shows the structure of the two-layer BiLSTM:
   - **Character-based Embedding:** The character-based token representations are at the bottom, providing the base embeddings for each token.
   - **Forward and Backward LSTM Passes:** Each token is processed through both a forward and backward LSTM in each layer, with arrows indicating the flow of information in each direction.
   - **Two Layers:** The tokens pass through Layer 1, then Layer 2, with each layer generating a new set of forward and backward representations.

Overall, ELMo embeddings capture rich, context-sensitive information for each token, combining character-based and multi-layered context-dependent information.

---

Bi-Dir. RNNs
![Attachments/dl4nlp-slides-complete 33.jpg](/img/user/Attachments/dl4nlp-slides-complete%2033.jpg)

[[dl4nlp-slides-complete.pdf#page=111&rect=26,95,344,160|dl4nlp-slides-complete, p.111]]


![Attachments/dl4nlp-slides-complete 42.jpg](/img/user/Attachments/dl4nlp-slides-complete%2042.jpg)

[[dl4nlp-slides-complete.pdf#page=276&rect=25,188,293,228|dl4nlp-slides-complete, p.276]]
## Tokenization

A **morpheme** is the smallest unit of meaning in a language.

- **Free morphemes**: These can stand alone as words, such as "cat," "run," or "happy." Each one has meaning by itself.
    
- **Bound morphemes**: These cannot stand alone and need to attach to other morphemes. For example:
    
    - **Prefixes**: "un-" in "undo" or "re-" in "rewrite."
    - **Suffixes**: "-s" in "cats" (indicating plural) or "-ed" in "walked" (indicating past tense).

### BPE
a compression and subword tokenization technique

![Attachments/dl4nlp-slides-complete 35.jpg](/img/user/Attachments/dl4nlp-slides-complete%2035.jpg)

[[dl4nlp-slides-complete.pdf#page=152&rect=6,22,346,271|dl4nlp-slides-complete, p.152]]

