---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/algo-bio-ngs/exercise/blatt1-1/","noteIcon":""}
---

---
Name: Sarthak Parikh

Proof by Induction

for n=1, the number of edges is of course zero, ie No Edges!

Induction Hypothesis:
Assume that for a tree of k nodes, there are k-1 edges. 

Induction Step: 
Prove that for a tree with k+1 nodes, there should be k edges. 

Since, every Tree has at least one leaf node, we can remove it, thus making the tree consisting of only k nodes, which, by the induction hypothesis above, has k-1 edges. 
Now we can place the leaf node back, thereby adding only one edge, constructing a tree of k edges. 

Hence, proved. 
