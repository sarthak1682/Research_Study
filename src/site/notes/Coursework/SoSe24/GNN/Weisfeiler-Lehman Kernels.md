---
{"dg-publish":true,"permalink":"/coursework/so-se24/gnn/weisfeiler-lehman-kernels/","noteIcon":""}
---

---
Algo: 
1. K-Step Color Refinement to enrich node Colors
	1. Diff. colors capture different K-Hop Neighbourhood Structures
2. Graph is repr. as a Bag of Colors (/Count number of Nodes with a given Color)
3. WL Kernel Value = Inner Product of Color Count Vectors

Complexity: 
1. Time Complexity for color refinement for each step is linear in #(edges)
2. Counting Colors takes linear times wrt #(nodes)
3. Total Time Complexity is linear in #(edges)

The 1-Weisfeiler-Lehman (1-WL) test
Useful for identifying the non-isomorphic graphs (although not a guarantee)