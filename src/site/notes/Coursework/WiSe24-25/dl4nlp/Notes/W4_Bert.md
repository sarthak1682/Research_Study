---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/w4-bert/","noteIcon":""}
---

---
Masked LMs vs ARLMs: surrounding -> masked vs previous -> next word prediction

Adv for MLMs: learning contextualized repr. 
ARLMs better than MLMs for generating texts

SSL Objectives:
	Skip-gram [[Coursework/WiSe24-25/dl4nlp/Notes/Skipgram(Word2Vec)\|Skipgram(Word2Vec)]]
	Language Modelling
	MLM objective
	PLM: Permutation Lang Modelling
	Replaced token detection obj (needs two models)

![Attachments/dl4nlp-slides-complete 11.jpg](/img/user/Attachments/dl4nlp-slides-complete%2011.jpg)

[[dl4nlp-slides-complete.pdf#page=252&rect=21,75,294,229|dl4nlp-slides-complete, p.252]]

![Attachments/dl4nlp-slides-complete 12.jpg](/img/user/Attachments/dl4nlp-slides-complete%2012.jpg)

[[dl4nlp-slides-complete.pdf#page=255&rect=24,67,322,220|dl4nlp-slides-complete, p.255]]

good example of Avg_precision@k

MAP: (Mean Avg Precision)

![Screenshot 2025-01-04 at 02.51.14.png](/img/user/Attachments/Screenshot%202025-01-04%20at%2002.51.14.png)


MRR (mean reciprocal rank) 
![Attachments/dl4nlp-slides-complete 13.jpg](/img/user/Attachments/dl4nlp-slides-complete%2013.jpg)

[[dl4nlp-slides-complete.pdf#page=257&rect=64,97,299,181|dl4nlp-slides-complete, p.257]]

Ex: 

In Mean Reciprocal Rank (MRR), "rank" refers to the position of the first relevant item in a ranked list of results returned by a system, typically a search engine or information retrieval system. MRR focuses specifically on where the first correct answer appears, not the overall quality of the entire ranked list.

- **Example:** Imagine you search for "tallest mountain in the world." A search engine returns the following results:
    
    1. Mount Kilimanjaro
        
    2. Mount Everest
        
    3. K2
        
    4. Kangchenjunga
        
    
    The correct answer, Mount Everest, is at position 2. Therefore, the rank for this query is 2. The reciprocal rank is 1/2 = 0.5. MRR is then calculated by averaging these reciprocal ranks across multiple queries.


Perplexity: > [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=259&annotation=8324R|dl4nlp-slides-complete, p.259]]
> Measure of uncertainty of a probabilistic model


![Attachments/dl4nlp-slides-complete 14.jpg](/img/user/Attachments/dl4nlp-slides-complete%2014.jpg)

[[dl4nlp-slides-complete.pdf#page=260&rect=92,34,284,86|dl4nlp-slides-complete, p.260]]

lower bound, upper bound: 1 (every token predicted correctly vs |v| (random guess)

See how a fixed context size is a problem for this: 
	truncated context
	inconsistent eval
	not TRULY AR, is it? 
Sliding window tries to solve it but it's still expensive. 

> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=263&annotation=8327R|dl4nlp-slides-complete, p.263]]
> Question: Is a language model with lower perplexity always a “better“ model? 
> Some (Dis)Advantages of perplexity: Pro: Straight-forward applicable 
> Pro: Does not depend on “external“ labels 
> Con: Not clear what value can be considered “good“
>  Con: Corpus-/language-specific measure


> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=267&annotation=8330R|dl4nlp-slides-complete, p.267]]
> BERTScore

advantages of BertScore and BLEURT, particularly their ability to capture contextual similarities and correlate better with human judgments.


----
### Architecture:


![Screenshot 2025-01-04 at 03.17.59.png](/img/user/Attachments/Screenshot%202025-01-04%20at%2003.17.59.png)

![Attachments/dl4nlp-slides-complete 15.jpg](/img/user/Attachments/dl4nlp-slides-complete%2015.jpg)

[[dl4nlp-slides-complete.pdf#page=283&rect=19,119,333,272|dl4nlp-slides-complete, p.283]]




BERT
> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=277&annotation=8333R|dl4nlp-slides-complete, p.277]]
> Bidirectional Encoder Representations from Transformers


SSL: MLM + Next-Sentence-Prediction
Encoder: Backbone

> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=290&annotation=8336R|dl4nlp-slides-complete, p.290]]
> Modified pre-training task: Predict 15% of the tokens of which only 80% have been replaced by [MASK] 80% of the selected tokens are actually [MASK] ed 10% of the selected tokens: The model has to “understand“ that the word needs to be replaced 10% of the selected tokens: The model has to “understand“ that the word needs to be kept

---
![Attachments/dl4nlp-slides-complete 16.jpg](/img/user/Attachments/dl4nlp-slides-complete%2016.jpg)

[[dl4nlp-slides-complete.pdf#page=292&rect=20,63,356,244|dl4nlp-slides-complete, p.292]]



> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=294&annotation=8339R|dl4nlp-slides-complete, p.294]]
> LossBERT = LossMLM + Loss NSP


![Attachments/dl4nlp-slides-complete 17.jpg](/img/user/Attachments/dl4nlp-slides-complete%2017.jpg)

pretraining: [[dl4nlp-slides-complete.pdf#page=295&rect=8,65,332,224|dl4nlp-slides-complete, p.295]]


---
Taxonomy of TL: 

Hospital A: model for detecting pneumonia
Hospital B: smaller, unlabeled dataset of X-ray images (target domain), which uses different X-ray equipment and imaging protocols 

(Domain Adaptation)


Cross-Lingual: clear

Multi-Task: (on chest X Rays)

 pneumonia detection, tuberculosis detection, and lung cancer detection.

Seq TL: detect a rarer lung disease 
(source task: pneumonia detection
target task: rarer lung disease, labeled data available)

first train a model on the large pneumonia dataset. Then, we use the pre-trained layers of this model as a starting point for training a new model on the rarer lung disease dataset. We fine-tune the pre-trained layers and add new layers specific to the target task.

---
Post-bert




> [!PDF|255, 208, 0] [[dl4nlp-slides-complete.pdf#page=329&annotation=8318R|dl4nlp-slides-complete, p.329]]
> The research of  Jain and Wallace, 2019  suggests that there is no direct connection between attention weights and other measures for explainability

whoa!

