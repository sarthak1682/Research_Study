---
{"dg-publish":true,"permalink":"/coursework/so-se24/phil-ml/a2-el-norelli-et-al/","noteIcon":""}
---

---
Links: 
[Artificial Scientific Discovery - Antonio Norelli final PhD exam - YouTube](https://www.youtube.com/watch?v=0uD51aHiYlA&t=614s)
[[2201.10222] Explanatory Learning: Beyond Empiricism in Neural Networks](https://arxiv.org/abs/2201.10222)
[Explanatory Learning: Beyond Empiricism in Neural Networks | OpenReview](https://openreview.net/forum?id=46lmrnVBHBL)


---
# Video

Modelling the problem faced by a scientist. 

hardcoding a lang. interpreter is seen to be a limitation => learned interpreter

lang is learned from explanations and observations 

"a true artificial scientist can only emerge when the machine can autonomously interpret symbols"

---
# Paper

try to model an artificial scientist: which for them is "make correct pred for a new phenomenon given some observations with explanations and observations of other phenomena" 

validate it on odeen (game engine) to produce explanations, they propose CRN (Critical Rationalist Networks), whose working hypothesis is not the parameters but propositions that can either be accepted or rejected.
The biggest contribution is the learned symbol interpreter, without which, as they claim, a true artificial scientist can never emerge. 




Glimpses of Popper?



Explainability vs Representativity:


---
# Review 

"The machine Conjecture Generator (CG) estimates the link between observations (data) and explanations (sentences), while the machine Interpreter (I) estimates the correctness of an explanation (sentence) given the observations (data)."

"Another way of looking at the fundamental difference between the rationalist and empiricist models presented in the paper is given by the nature of the hypothesis space: in CRNs the hypothesis space is the set of all strings , while in the empiricist models the hypothesis space is the n-dimensional vector space , with n equal to the number of parameters of the neural networks implementing Emp-C or Emp-L."


---
# Questions:

Modelling the problem faced by a scientist: well posed? how are conjectures generated though? 

"a true artificial scientist can only emerge when the machine can autonomously interpret symbols": claim made with an example of Shannon and this citation "Learning transferable visual models from natural language supervision" : make sense? 

What makes Explanations, well, Explanations?: Deutsch: Hard to Vary, did you see that here? or according to Popper, theories have to "stick their neck out". 

The Apparatus to explain a new Phenomenon is learned from examples, right? 

D_o (observation set) is assumed to be "representative" of P_o: does it hold in practice? 

Stochastic CG: what do you think about it? 