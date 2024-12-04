---
{"dg-publish":true,"permalink":"/zotero-storage/499-bensz/cs-1-induction-heads/","noteIcon":""}
---

---
#### Function and Mechanism

Induction heads operate using a 'prefix matching' attention pattern. This pattern allows them to scan previous tokens and identify if any of them match the current token. Instead of merely relying on pre-learned statistical tendencies of token sequences, induction heads dynamically focus on prior tokens that bear similarity to the current one, leveraging learned representations. When a token is sufficiently similar to a prior token, the induction head attends to the subsequent token in the sequence. Consequently, it increases the probability of predicting that the current sequence will continue similarly to the matched prior sequence.

**Example:** If the input contains the sequence "...the cat sat on the mat. The cat...", the induction head identifies the second "cat" token as matching the first one. It then attends to the token "sat" from the first sequence, increasing the likelihood of "sat" being predicted again. This capability enables Transformer models to replicate sequences and generalize patterns.



