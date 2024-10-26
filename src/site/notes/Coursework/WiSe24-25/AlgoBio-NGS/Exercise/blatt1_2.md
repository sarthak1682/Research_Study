---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/algo-bio-ngs/exercise/blatt1-2/","noteIcon":""}
---

---
Name: Sarthak Parikh

Proof that Tripartite Graph Decision Problem is NP-Complete. (a 2-Step Proof)

Step1: Prove that it's in NP
Verifying the solution consists only of checking the edges, can be done in polynomial time

Step2: Reduce the 3-Coloring Problem (Already NP-Complete) to the tripartite graph problem
If G can be 3-colored, it can be partitioned into three independent sets, thus making it a tripartite graph (and vice versa)
Therefore, if an algorithm solves the tripartite graph problem, it can be used to solve the 3-coloring problem. 

Hence proved. 