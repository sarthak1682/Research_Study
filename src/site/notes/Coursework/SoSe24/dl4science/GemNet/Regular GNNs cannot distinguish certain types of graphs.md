---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/regular-gn-ns-cannot-distinguish-certain-types-of-graphs/","noteIcon":""}
---

---
[Weights & Biases](https://wandb.ai/syllogismos/machine-learning-with-graphs/reports/18-Limitations-of-Graph-Neural-Networks--VmlldzozODUxMzQ)
[Stanford CS224W: ML with Graphs | 2021 | Lecture 9.2 - Designing the Most Powerful GNNs - YouTube](https://www.youtube.com/watch?v=B5y47gWt3co&list=PLoROMvodv4rOP-ImU-O1rYRg2RFxomvFp&index=22)

---

Q- What are regulars GNNs? 
By "regular GNNs," we typically mean **basic [[Coursework/SoSe24/dl4science/GemNet/message passing over the network\|message passing over the network]] GNNs** that update node representations through aggregating information from their neighbors. These include popular models like Graph Convolutional Networks (GCNs), GraphSAGE, and Graph Attention Networks (GATs). They rely on local neighborhood aggregation and are limited in distinguishing non-isomorphic graphs that the Weisfeiler-Lehman test cannot differentiate.
[[Coursework/SoSe24/dl4science/GemNet/GCN\|GCN]], [[GraphSAGE\|GraphSAGE]], [[GAT (Graph Attention Net)\|GAT (Graph Attention Net)]]


GCNs and GraphSAGE can't differentiate between the two
![Screenshot 2024-06-03 at 15.22.59.png](/img/user/Attachments/Screenshot%202024-06-03%20at%2015.22.59.png)


What we have to do is:  make sure that our aggregation mechanism through the computational graph is injective (aggr. = function over a multiset, has to be injective)

GCN: Uses mean pooling at the msg passing step, doesn't diff between the aggregation of {a,b} and {a,a,b,b} for example


Solution? GINs (read the wandb article)

