---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/w8-decoding/","noteIcon":""}
---

---
> [!PDF|255, 208, 0] [[Decoding_W8.pdf#page=4&annotation=432R|Decoding_W8, p.4]]
> A decoding strategy determines how to choose the next token from that distribution, that token is then added to the context


Stopping Criteria for text gen
EOS, max_l, max_t


Decoding Strategies
> [!PDF|255, 208, 0] [[Decoding_W8.pdf#page=8&annotation=435R|Decoding_W8, p.8]]
> Deterministic: 
>  Greedy search 
> Beam search
>  Contrastive search Su et al., 2022
>   Contrastive decoding Li et al., 2023
>    Stochastic : 
>    Sampling (with temperature) 
>    Top-k sampling Fan et al., 2018
>     ucleus top-p sampling Holtzman et al., 2019 
>     Typical sampling 


### Greedy Search

> [!PDF|255, 208, 0] [[Decoding_W8.pdf#page=10&annotation=438R|Decoding_W8, p.10]]
> Core idea: Greedy search selects the word with the highest probability at each timestep, iteratively building the output sequence Exploration of search space: It explores a single path through the output space, favoring the most probable word at each step without considering future consequences Candidate Sequence: Only keeps track of the most likely sequence at each step, discarding other possibilities Decision Making: It makes local decisions based solely on the highest probability at the current step without considering potential longer-term outcome


Drawbacks 
![Attachments/Decoding_W8.jpg](/img/user/Attachments/Decoding_W8.jpg)

[[Decoding_W8.pdf#page=13&rect=15,79,355,246|Decoding_W8, p.13]]

interesting drawback

other drawbacks: 

Subopt Global Solns
Lack of diversity
Incoherence
Repetitiveness
Overemphasis on Common Phrases


### Beam Search

> [!PDF|255, 208, 0] [[Decoding_W8.pdf#page=15&annotation=441R|Decoding_W8, p.15]]
> Core idea: Beam search extends the exploration to multiple possible sequences instead of just the most probable one 
> Exploration of search space: It explores multiple paths (or "beams") simultaneously, maintaining a set of promising candidate sequences 
> Candidate Sequence: Keeps a fixed number of most probable sequences (determined by the beam width parameter k) at each step 
> Decision Making: At each step, it considers multiple candidate sequences and selects the most probable ones based on their cumulative probabilities up to that point


> [!PDF|] [[Decoding_W8.pdf#page=17&selection=2,0,7,25|Decoding_W8, p.17]]
> At each timestep beam search chooses the k tokens with the highest joint probability

![Attachments/Decoding_W8 1.jpg](/img/user/Attachments/Decoding_W8%201.jpg)

[[Decoding_W8.pdf#page=16&rect=13,25,339,226|Decoding_W8, p.16]]

Beam Search can "degenerate", become repetitive

### Stochastic Decoding


#### Sampling w Temp

Sampling selects the next token randomly based on its probability. Temperature controls randomness:

- **temp → ∞:** Output distribution approaches uniform (maximum randomness).
    
- **temp → 0:** Output distribution becomes a point mass (equivalent to greedy search).

![Attachments/Decoding_W8 2.jpg](/img/user/Attachments/Decoding_W8%202.jpg)

[[Decoding_W8.pdf#page=22&rect=118,109,236,188|Decoding_W8, p.22]]


![Attachments/Decoding_W8 3.jpg](/img/user/Attachments/Decoding_W8%203.jpg)

[[Decoding_W8.pdf#page=24&rect=26,67,336,202|Decoding_W8, p.24]]
Top-K Sampling (fix k)


Top-P (Nucleus Sampling)

> [!PDF|255, 208, 0] [[Decoding_W8.pdf#page=26&annotation=444R|Decoding_W8, p.26]]
> Top-p sampling chooses from the smallest possible set of tokens whose cumulative probability exceeds the probability threshold p. 

![Attachments/Decoding_W8 16.jpg](/img/user/Attachments/Decoding_W8%2016.jpg)

[[Decoding_W8.pdf#page=26&rect=19,43,346,188|Decoding_W8, p.26]]



#### Contrastive Search

tries to find a balance between coherence and diversity

> [!PDF|255, 208, 0] [[Decoding_W8.pdf#page=28&annotation=452R|Decoding_W8, p.28]]
> When generating output, contrastive search jointly considers: The probability predicted by the language model to maintain the **semantic coherence** between the generated text and the prompt. The similarity with respect to the previous context to **avoid degeneration**


![Attachments/Decoding_W8 4.jpg](/img/user/Attachments/Decoding_W8%204.jpg)

[[Decoding_W8.pdf#page=28&rect=14,201,356,238|Decoding_W8, p.28]]

Gen of greedy search it seems
![Screenshot 2025-01-05 at 05.17.14.png](/img/user/Attachments/Screenshot%202025-01-05%20at%2005.17.14.png)



---
### Eval Metrics


#### BLEU (Bilingual Evaluation Understudy)

[[Coursework/WiSe24-25/dl4nlp/Notes/BLEU\|BLEU]]

![Attachments/Decoding_W8 8.jpg](/img/user/Attachments/Decoding_W8%208.jpg)

[[Decoding_W8.pdf#page=46&rect=99,43,309,79|Decoding_W8, p.46]]


![Attachments/Decoding_W8 10.jpg](/img/user/Attachments/Decoding_W8%2010.jpg)

[[Decoding_W8.pdf#page=45&rect=13,18,358,154|Decoding_W8, p.45]]
![Attachments/Decoding_W8 9.jpg](/img/user/Attachments/Decoding_W8%209.jpg)

[[Decoding_W8.pdf#page=46&rect=103,141,261,198|Decoding_W8, p.46]]

r = ref corpus l c = candidate corpus l

#### ROUGE(Recall-Oriented Understudy for Gisting Evaluation)


used for summaries ![Attachments/Decoding_W8 11.jpg](/img/user/Attachments/Decoding_W8%2011.jpg)

[[Decoding_W8.pdf#page=48&rect=10,68,297,219|Decoding_W8, p.48]]

---

### Diversity

![Attachments/Decoding_W8 12.jpg](/img/user/Attachments/Decoding_W8%2012.jpg)

[[Decoding_W8.pdf#page=50&rect=82,73,325,118|Decoding_W8, p.50]]

A higher rep_n indicates more repetition


![[Decoding_W8.pdf#page=51&rect=117,72,298,120|Decoding_W8, p.51]]

![Attachments/Decoding_W8 14.jpg](/img/user/Attachments/Decoding_W8%2014.jpg)

[[Decoding_W8.pdf#page=51&rect=140,155,272,198|Decoding_W8, p.51]]


generated text is: "the cat sat on the mat on the mat."

- **2-grams:** the cat, cat sat, sat on, on the, the mat, mat on, on the, the mat. (8 total, 6 unique)  rep_2 = 100 * (1 - 6/8) = 25
    
- **3-grams:** the cat sat, cat sat on, sat on the, on the mat, the mat on, mat on the, on the mat. (7 total, 6 unique) rep_3 = 100 * (1 - 6/7) ≈ 14.3
    
- **4-grams:** ... (and so on)

---

---
![Attachments/Decoding_W8 15.jpg](/img/user/Attachments/Decoding_W8%2015.jpg)

[[Decoding_W8.pdf#page=52&rect=52,125,315,156|Decoding_W8, p.52]]

Coherence

---
#### MAUVE



> [!PDF|255, 208, 0] [[Decoding_W8.pdf#page=54&annotation=461R|Decoding_W8, p.54]]
> Type I error: Q places high mass on text which is unlikely under P Type II error: Q cannot generate text which is plausible under P


> [!PDF|255, 208, 0] [[Decoding_W8.pdf#page=55&annotation=464R|Decoding_W8, p.55]]
> KL(Q|P)  penalizes  Q  if there is a text  x  that leads to a high Q(x)  but a low  P(x), which is the Type I error Similarly the Type II error is defined by  KL(P|Q)


The support of a probability distribution is the set of all possible values where the probability is non-zero.
	if one distribution has zero probability where the other has non-zero probability, standard measures like Kullback-Leibler (KL) divergence can become infinite, making comparison meaningless.

softly measuring two errors with a mixture distr. 
R<sub>λ</sub> = λP + (1 - λ)Q,   where λ ∈ (0, 1)

This creates a new distribution R<sub>λ</sub> that is a weighted average of the target distribution P and the model distribution Q. The parameter λ controls the mixing proportion:

- **λ close to 1:** R<sub>λ</sub> is more similar to P.
    
- **λ close to 0:** R<sub>λ</sub> is more similar to Q.

1. **Divergence Curve and MAUVE Score:**By varying λ from 0 to 1, MAUVE generates a divergence curve. The area under this curve represents the final MAUVE score. This score summarizes the trade-off between Type I and Type II errors across different mixing proportions.

