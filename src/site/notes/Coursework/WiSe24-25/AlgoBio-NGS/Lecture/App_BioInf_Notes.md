---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/algo-bio-ngs/lecture/app-bio-inf-notes/","noteIcon":""}
---

---

## De Bruijn Graph

- **Superstring Problem:** Find the shortest string (superstring) that contains all given substrings.
    
- **k-mers:** These substrings are of length k and are called k-mers.
    
- **Example:** If the alphabet is {0,1} and k=3, all possible 3-mers are 000, 001, 010, 011, 100, 101, 110, and 111. (Circular Superstring: 00011101)

 Eulerian paths:  which traverse each edge in a graph exactly once
 Hamiltonian Paths: every node exactly once. 

for k = 5§ 
- Each node represents a (k-1)-length string = 4-bit string in this case
- A directed edge exists from node x to node y if and only if:
    - The last (k-2) = 3 bits of x match the first (k-2) = 3 bits of y
    - Together they form a valid k-length string


![Screenshot 2025-01-27 at 18.50.27.png](/img/user/Attachments/Screenshot%202025-01-27%20at%2018.50.27.png)

In deg = Out deg
> [!PDF|255, 208, 0] [[App_BioInf.pdf#page=23&annotation=406R|App_BioInf, p.23]]
> A directed graph has an Eulerian cycle ⇔ Every vertex has equal in-degree and out-degree, and all of its vertices with nonzero degree belong to a single strongly connected component, can be found in O(E)


![Attachments/App_BioInf.jpg](/img/user/Attachments/App_BioInf.jpg)

[[App_BioInf.pdf#page=26&rect=40,35,790,497|App_BioInf, p.26]]


Genomes with multiple linear chromosomes require finding Eulerian paths (which have distinct start and end points) instead of Eulerian cycles


### Velvet

> [!PDF|255, 208, 0] [[App_BioInf.pdf#page=30&annotation=409R|App_BioInf, p.30]]
> Algorithms for de novo short read assembly using de Bruijn graphs• Steps: 1. Construction of de Bruijn graph-like structure 2. Simplification 3. Error removal a. Removing tips b. Removing bubbles with the Tour Bus algorithm c. Removing erroneous connections

![Screenshot 2025-01-27 at 21.06.35.png](/img/user/Attachments/Screenshot%202025-01-27%20at%2021.06.35.png)

For example, if you have the sequence AGTC, its reverse complement is GACT.


Simplification

> [!PDF|255, 208, 0] [[App_BioInf.pdf#page=34&annotation=412R|App_BioInf, p.34]]
> Node A has only one outgoing arc that points to another node B that has only one ingoing arc
![Attachments/App_BioInf 1.jpg](/img/user/Attachments/App_BioInf%201.jpg)


[[App_BioInf.pdf#page=34&rect=162,69,719,350|App_BioInf, p.34]]


Error Removal - Tip Removal 
> [!PDF|255, 208, 0] [[App_BioInf.pdf#page=36&annotation=415R|App_BioInf, p.36]]
>  two criteria: length and minority count 



![Attachments/App_BioInf 2.jpg](/img/user/Attachments/App_BioInf%202.jpg)

[[App_BioInf.pdf#page=35&rect=212,32,723,310|App_BioInf, p.35]]

Tour Bus: 
![Screenshot 2025-01-27 at 21.13.49.png](/img/user/Attachments/Screenshot%202025-01-27%20at%2021.13.49.png)

Removing erroneous connection with coverage cutoff

---
### Super Reads
Super-reads are longer sequences constructed by extending shorter DNA reads using k-mer analysis. Here's how they work:

1. The Process:

- Start with a k-mer count lookup table that tracks how often each k-mer (short DNA sequence) appears
- Look at the k-mer at the end of a read
- Check what bases could come next (there are four possibilities: A, T, C, or G)
- If only one of these possible next k-mers actually occurs in the data, it's a "unique following k-mer"
- Add that unique base to extend the read
- Continue this process until you can no longer uniquely extend the sequence
- Perform this extension on both the 3' and 5' ends of the read

2. Key Properties:

- Each original read is contained within a super-read (no information is lost)
- Multiple original reads often combine into the same super-read
- This significantly **reduces the dataset size** while preserving information
- They can be efficiently computed using a de Bruijn graph

3. Real-world Example Results:

- For bacterial genome assembly: 2,050,868 paired-end reads were reduced to 5,168 super-reads
- For mouse genome assembly: 50 million reads were reduced to 297,279 super-reads

---

Partial Order: reflexivity, transitivity and anti symmetry

Compatibility: if the overlap contains the same implied introns

![Screenshot 2025-01-27 at 21.24.59.png](/img/user/Attachments/Screenshot%202025-01-27%20at%2021.24.59.png)

Hasse Diagram: 
(u,v) belong to G if u R v and no w s.t u R w R v

![Attachments/App_BioInf 3.jpg](/img/user/Attachments/App_BioInf%203.jpg)

[[App_BioInf.pdf#page=53&rect=373,81,612,269|App_BioInf, p.53]]

- **Chain:** A chain is a totally ordered subset of the partial order. This means that for any two elements x,y within the chain, we know either x<=y or y<=x.
    
- **Anti-chain:** An anti-chain is a set of elements that are pairwise incomparable. For any two elements x,y in the anti-chain, we know that x </= y and y </= x

![Attachments/App_BioInf 4.jpg](/img/user/Attachments/App_BioInf%204.jpg)

[[App_BioInf.pdf#page=54&rect=327,44,792,279|App_BioInf, p.54]]


- **Dilworth's Theorem:**
    
    - Let 'P' be a finite partially ordered set.
        
    - The maximum number of elements in any anti-chain of 'P' is equal to the minimum number of chains in any partition of 'P' into chains.


- **König's Theorem:**
    
    - In a bipartite graph (where the nodes can be divided into two disjoint sets and edges only connect nodes from different sets), the number of edges in a maximum matching is equal to the number of nodes in a minimum vertex cover.

	Max Matching: Matching = set of edges without common vertices![Attachments/App_BioInf 5.jpg](/img/user/Attachments/App_BioInf%205.jpg)

[[App_BioInf.pdf#page=56&rect=66,49,736,448|App_BioInf, p.56]]

![Attachments/App_BioInf 6.jpg](/img/user/Attachments/App_BioInf%206.jpg)

[[App_BioInf.pdf#page=57&rect=55,44,705,492|App_BioInf, p.57]]

---

### StringTie

a method for transcript assembly from RNA-seq data using graph-based algorithms.


1. **Mapping reads to a reference genome.**
    
2. **Constructing a splice graph:** This represents the possible exonic regions and their connections (introns) based on aligned reads.
    
3. **Building a flow network:** The splice graph is translated into a flow network, which enables analysis of path flows.
    
4. **Finding the heaviest path:** A maximum flow algorithm, modified to accommodate edge multipliers and node biases, is used to find the most supported transcript path in the graph.
    
5. **Estimating transcript abundance:** The maximum flow problem is used to estimate transcript abundances.
    
6. **Iterate**: Repeat this process to identify all transcripts present in a dataset

![Screenshot 2025-01-27 at 21.37.24.png](/img/user/Attachments/Screenshot%202025-01-27%20at%2021.37.24.png)


![Screenshot 2025-01-27 at 21.45.51.png](/img/user/Attachments/Screenshot%202025-01-27%20at%2021.45.51.png)

![Screenshot 2025-01-27 at 21.46.01.png](/img/user/Attachments/Screenshot%202025-01-27%20at%2021.46.01.png)


