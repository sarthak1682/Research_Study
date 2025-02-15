---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/bleu/","noteIcon":""}
---

---
The BLEU score is calculated as follows:

1. Precision (for each n-gram) is calculated as the ratio of the number of n-grams in the candidate translation that match the reference translations to the total number of n-grams in the candidate translation.
2. The BLEU score is then computed as BP * exp(Σ Wn * log(Pn)), where BP is the brevity penalty (to penalize overly short translations), Wn are the weights for each n-gram precision score Pn, and the summation is over the different n-gram lengths.

To provide an example:

Suppose we have a candidate translation and two reference translations:

Candidate: "The quick brown fox jumps over the lazy dog." Reference 1: "The fast brown fox leaps across the sluggish canine." Reference 2: "The speedy orange vulpine bounds over the indolent hound."

For the 1-gram precision, the candidate has 9 words, and 7 of them match the references, so the 1-gram precision would be 5/9

For the 2-gram precision, the candidate has 8 2-grams, and 5 of them match the references, so the 2-gram precision would be 2/8 = 0.25.

The BLEU score would then be calculated using these precision values, the brevity penalty, and the weights for each n-gram.