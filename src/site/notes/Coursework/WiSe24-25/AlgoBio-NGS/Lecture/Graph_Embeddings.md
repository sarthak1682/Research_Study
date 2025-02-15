---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/algo-bio-ngs/lecture/graph-embeddings/","noteIcon":""}
---

---


## L1: 

![Attachments/Graph_Embedding.jpg](/img/user/Attachments/Graph_Embedding.jpg)

[[Graph_Embedding.pdf#page=6&rect=62,275,567,358|Graph_Embedding, p.6]]


### Line


First order proximity for undir. edge (i,j)
p1(vi, vj) = 1 / (1 + exp(-uTᵢ * uj))
	u is a low-d repr. of v

![Attachments/Graph_Embedding 1.jpg](/img/user/Attachments/Graph_Embedding%201.jpg)

[[Graph_Embedding.pdf#page=10&rect=205,323,630,417|Graph_Embedding, p.10]]
KL-Div

Second-Order proximity
![Attachments/Graph_Embedding 2.jpg](/img/user/Attachments/Graph_Embedding%202.jpg)

[[Graph_Embedding.pdf#page=11&rect=196,384,807,494|Graph_Embedding, p.11]]

-  **the Notation:**
    
    - **vᵢ:** Represents a node in the graph.
        
    - **uᵢ ∈ Rᵈ:** Represents the d-dimensional embedding vector for node vᵢ when vᵢ is treated as a regular node. This vector is learned.
        
    - **uᵢ' ∈ Rᵈ:** Represents the d-dimensional embedding vector for node vᵢ when vᵢ is treated as context. This vector is learned as well. It's a separate embedding that captures the "influence" of vᵢ on other nodes.

> [!PDF|255, 208, 0] [[Graph_Embedding.pdf#page=13&annotation=531R|Graph_Embedding, p.13]]
> Combining first-order and second-order proximities: 1. Train LINE model preserving the first-order proximity 2. Train LINE model preserving the second-order proximity separately 3. Concatenate the embeddings trained by the two methods for each vertex


---
### Random Walk: 

![Screenshot 2025-01-27 at 22.55.33.png](/img/user/Attachments/Screenshot%202025-01-27%20at%2022.55.33.png)


---
### Word2Vec

> [!PDF|255, 208, 0] [[Graph_Embedding.pdf#page=15&annotation=534R|Graph_Embedding, p.15]]
> Aim: analyze similarity of words, semantic relationships


---
### Vector Offset

![Attachments/Graph_Embedding 3.jpg](/img/user/Attachments/Graph_Embedding%203.jpg)

[[Graph_Embedding.pdf#page=16&rect=140,294,744,490|Graph_Embedding, p.16]]

----
## L2

### Word2Vec/SkipGram


### Deepwalk
![Attachments/Graph_Embedding 4.jpg](/img/user/Attachments/Graph_Embedding%204.jpg)

[[Graph_Embedding.pdf#page=19&rect=16,65,807,426|Graph_Embedding, p.19]]


- **Algorithm 1 DEEPWALK:** 
    
- **Input:** Graph, window size (w), embedding size (d), walks per vertex (γ), walk length (t)
    
- **Output:** A matrix of vertex representations.
    
- **Steps:**
    
    1. Initialize random embeddings for each node.
        
    2. Build a binary tree from all the nodes.
        
    3. Repeat for gamma number of times:
        
    4. Shuffle the node list (to generate a random ordering).
        
    5. Iterate through every node in the graph:
        
        - Generate a random walk of given length (t), starting from current node.
            
        - Use skipgram to learn the embedding.


- **Algorithm 2 SkipGram:** 
    
    - **Inputs:** Embedding matrix, random walks and window size.
        
    - **Steps:**
        
        1. Iterate through all nodes in random walk.
            
        2. Consider nodes within a given window size (from j-w to j+w).
            
        3. Compute negative log probability.
            
        4. Update embeddings based on calculated gradients.



### Node2Vec

Biased random walk method
Node context sampled by considering both local and global structure information from original graph
DFS + BFS

![Attachments/Graph_Embedding 5.jpg](/img/user/Attachments/Graph_Embedding%205.jpg)

[[Graph_Embedding.pdf#page=23&rect=55,70,822,497|Graph_Embedding, p.23]]

- **Parameter p (return parameter):**
    
    - p controls the tendency to return to the previous node,
        
        - a higher p value leads to a tendency of not going back to the previous node.
            
- **Parameter q (in-out parameter):**
    
    - q controls the tendency to explore nodes far from the previous node (BFS like) vs the nodes closer to the previous node (DFS like).
        
        - Higher q values lead to wider exploration, while lower q values lead to local exploration.
            
- **Specific Scenarios:**
    
    - p > max(q, 1) (Slide 8) : Less likely to sample visited nodes (moderate exploration).
        
    - p < min(q, 1) (Slide 9) : leads to backtracking to the previous node (local sampling)
        
    - q > 1 (Slide 10) : approximates BFS behavior (micro view of node neighborhoods).
        
    - q < 1 (Slide 11): approximates DFS behavior (macro view).
        
    - q = p (Slide 12): becomes equivalent to DeepWalk.


![Attachments/Graph_Embedding 6.jpg](/img/user/Attachments/Graph_Embedding%206.jpg)

[[Graph_Embedding.pdf#page=30&rect=37,38,823,490|Graph_Embedding, p.30]]


![Attachments/Graph_Embedding 7.jpg](/img/user/Attachments/Graph_Embedding%207.jpg)

[[Graph_Embedding.pdf#page=31&rect=71,293,690,487|Graph_Embedding, p.31]] (Simplified)


![Attachments/Graph_Embedding 8.jpg](/img/user/Attachments/Graph_Embedding%208.jpg)

[[Graph_Embedding.pdf#page=29&rect=141,236,756,346|Graph_Embedding, p.29]]

- **Algorithm 1:** LearnFeatures procedure
    
    - **Input:** graph, embedding dimension, walks per node, walk length, context size, parameters p and q
        
        - Preprocessing: Biased walk probabilities are calculated
            
        - Initialize empty walk set.
            
        - Create random walk starting from each node.
            
        - Update embedding using stochastic gradient descent.
            
- **Algorithm 2:** node2vecWalk procedure
    
    - **Input:** biased graph, starting node and length of walk.
        
        - Create list of random walks of given length
            
        - Traverse from a node in random walk, and add that node to the walk.

---

### Struc2Vec


- **Limitations of Previous Approaches:** Deepwalk and node2vec don't consider distant nodes (> random walk l) which are structurally similar.

**Contexts:**
- Sequences of structurally similar nodes are the context of the node.
- These sequences are generated via weighted random walks on a multilayer graph.


![Attachments/Graph_Embedding 9.jpg](/img/user/Attachments/Graph_Embedding%209.jpg)

[[Graph_Embedding.pdf#page=35&rect=34,59,756,564|Graph_Embedding, p.35]]


> [!PDF|255, 208, 0] [[Graph_Embedding.pdf#page=36&annotation=537R|Graph_Embedding, p.36]]
> 𝑠(𝑅( 𝑢 ) and 𝑠(𝑅( 𝑣 ) can have different sizes

(use DTW for that)
![Attachments/Graph_Embedding 10.jpg](/img/user/Attachments/Graph_Embedding%2010.jpg)

[[Graph_Embedding.pdf#page=37&rect=42,47,789,490|Graph_Embedding, p.37]]


---

## L3

M = multilayer graph
- **Layer k = 0, ..., k* = weighted, undirected complete graph:** This explains the structure of individual layers within M.
    
    - There are k layers, starting from layer 0 up to layer k.
        
    - Each layer is a weighted graph, meaning its edges have associated numerical values.
        
    - Each layer is undirected, meaning edges don't have a direction (relation between two nodes is reciprocal).
        
    - Each layer is a complete graph, meaning every node is connected to every other node in that layer. This is a very dense representation.

**Edge weight:**

- wk(u, v) = e^(-fk(u,v)), k = 0, ..., k*
**The higher fk(u, v) the lower wk(u, v)**

- wk(u, v) ≤ 1: Edge weights will never be more than 1.
    
- wk(u, v) = 1 <=> fk(u, v) = 0

### Inter-Layer 

edges that go between layers (and not just within). These edges will be directed.

**Edge weights:**

- w(uk, uk+1) = log(Γk(u) + e), k = 0,..., k*-1
- w(uk, uk-1) = 1, k = 1,..., k*

**Γk(u) = number of edges incident to u with weight > average edge weight of complete graph in layer k:** This crucial definition helps to encode similarity within the layer.

- It is the number of edges from node u to other nodes in layer k that have an edge weight higher than the average edge weight of all edges in the layer k.
    
- It basically measures how many "strong" connections a node has with other nodes in its layer
> By moving up one layer, number of similar nodes can only decrease


### Generating Context

**probability of stepping from u to v in layer k:**

- Pk(u, v) = e^(-fk(u,v)) / Zk(u)
- Zk(u) = ∑ e^(-fk(u,v)) (sum over all v!=u). This calculates the sum of the edge weights of all edges incident to a given node u (other than itself) so that the probability Pk(u, v) is normalized


**Example:** In a walk, if e^(-fk(u,v)) is 0.8 to node 'a' and 0.2 to node 'b' and Zk(u) is 1, then the random walker will move to 'a' with 80% probability and to 'b' with 20% probability.


-  probabilities of moving up and down in layers.
    
- Pk(uk, uk+1) = w(uk, uk+1) / (w(uk, uk+1) + w(uk, uk-1))
Pk(uk, uk-1) = 1 - Pk(uk, uk+1)



---
### GCN

![Attachments/Graph_Embedding 11.jpg](/img/user/Attachments/Graph_Embedding%2011.jpg)

[[Graph_Embedding.pdf#page=55&rect=9,1,701,515|Graph_Embedding, p.55]]

![Attachments/Graph_Embedding 12.jpg](/img/user/Attachments/Graph_Embedding%2012.jpg)

[[Graph_Embedding.pdf#page=56&rect=19,179,693,458|Graph_Embedding, p.56]]

> [!PDF|255, 208, 0] [[Graph_Embedding.pdf#page=58&annotation=543R|Graph_Embedding, p.58]]
> When GNNs’ architectures go deep, the models’ performance will get degraded
= Suspended Animation Problem


---

## L4 (Applications)


---

## L5 Transformers 

[[Coursework/SoSe24/GenAI/Ch 6 ARMs\|Ch 6 ARMs]]

