---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/graph-cast-lam-et-al-deepmind/","noteIcon":""}
---

---
[GraphCast: Learning skillful medium-range global weather forecasting - YouTube](https://www.youtube.com/watch?v=lZlm1YSdQ9E)

---
### Summary to be submitted

GraphCast uses GNN with an encoder-process-decode configuration, where the processor uses 16 GNN layers to perform message passing and encoder and decoder convert to and from multi-mesh and long/lat grid representation.  It makes medium range weather predictions for up to 10 days, does so at a high resolution 0.25 degrees and an order of magnitude faster than the supercomputers, with a single TPU. It outperforms HRES on 90% of test variables, and is even better when forecasting is limited to the troposphere. All of this is done with a ca. 37 Million Param Model (little more than half the original AlexNet). 

The most interesting detail has to be the loss term, whereby long-term errors are penalised heavily since they can accumulate as predictions are being rolled out autoregressively. It is also designed in a way to care more about levels closer to the surface, which gets reflected back on later in the results. The author makes a point by claiming that one can manipulate the reward mechanism in way where GraphCast is better at predicting levels that are far away, if one so wishes, which is quite noteworthy. 

One other thing worth learning about was the training phase itself. They aggressively threw out hypotheses/Models which did not predict the weather well for the first 6hrs.  

Although severe weather applications performed well without doing anything special, I am skeptical of it performing well on out of sample events. 

As the authors reflected themselves at the end of the paper, I would want to see uncertainty quantification injected into it. 

---

Questions: 
Do you have an intuition of how much was data and how much the algo? Can you at all decouple the two? Do you know of better models using (basically) same data? 
Why 1979 as the starting point? 


---
### Concepts to learn

[[autoregression\|autoregression]]
[[message passing\|message passing]]
[[inverse residual variance\|inverse residual variance]]
