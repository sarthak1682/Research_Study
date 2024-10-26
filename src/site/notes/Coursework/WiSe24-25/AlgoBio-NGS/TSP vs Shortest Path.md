---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/algo-bio-ngs/tsp-vs-shortest-path/","noteIcon":""}
---

---
Q-The only difference I could think of for the question is that in [the Travelling Salesman Problem (TSP)](http://en.wikipedia.org/wiki/Travelling_salesman_problem) I need to find a minimum permutation of all the vertices in the graph and in Shortest Paths problem there is no need to consider all the vertices we can search the states space for minimum path length routes can anyone suggest more differences.


A- the TSP is to find a path that contains a permutation of **_every node in the graph_**, while in the shortest path problem, any given shortest path may, and often does, contain a **proper** subset of the nodes in the graph.

Other differences include:

- The TSP solution requires its answer to be a cycle.
- The TSP solution will necessarily repeat a node in its path, while a shortest path will not (unless one is looking for shortest path from a node to itself).
- TSP is an NP-complete problem and shortest path is known polynomial-time.

If you are looking for a precise statement of the difference I would say you just need to replace your idea of the "permuation" with the more technical and precise term "simple cycle visiting every node in the graph", or better, "Hamilton cycle":

> The TSP requires one to find the **simple cycle** covering every node in the graph with the smallest weight (alternatively, the Hamilton cycle with the least weight). The Shortest Path problem requires one to find the path between two given nodes with the smallest weight. Shortest paths need not be Hamiltonian, nor do they need to be cycles.