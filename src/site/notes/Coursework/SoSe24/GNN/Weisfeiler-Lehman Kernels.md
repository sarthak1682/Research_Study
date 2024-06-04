---
{"dg-publish":true,"permalink":"/coursework/so-se24/gnn/weisfeiler-lehman-kernels/","noteIcon":""}
---

---
[The Weisfeiler-Lehman Isomorphism Test | David Bieber](https://davidbieber.com/post/2019-05-10-weisfeiler-lehman-isomorphism-test/)
[Stanford CS224W: ML with Graphs | 2021 | Lecture 2.3 - Traditional Feature-based Methods: Graph - YouTube](https://www.youtube.com/watch?v=buzsHTa4Hgs&t=1056s) (from Color Refinement to WL Kernel)

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

" Since both Graph 1 and Graph 2 have this same canonical form, we cannot rule out the possibility that they are isomorphic" since some non-isomorphic graphs also have the same canonical form![Screenshot 2024-05-29 at 12.15.14.png](/img/user/Attachments/Screenshot%202024-05-29%20at%2012.15.14.png)
(they _are_ in fact isomorphic, but the algorithm doesn’t allow us to conclude this definitively.)