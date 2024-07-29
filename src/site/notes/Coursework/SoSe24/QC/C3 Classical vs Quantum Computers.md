---
{"dg-publish":true,"permalink":"/coursework/so-se24/qc/c3-classical-vs-quantum-computers/","noteIcon":""}
---

---


# Important Complexity Classes




![Screenshot 2024-07-22 at 21.28.58.png](/img/user/Attachments/Screenshot%202024-07-22%20at%2021.28.58.png)


## P, NP and PSPACE

P
	efficiently solvable by classical Computers 

NP
	efficiently verified =
	solved non-deterministically in polynomial time

NP-Complete
	1. Problem is in NP
	2. Every other problem in NP can be reduced to this problem in polynomial time

NP-Hard
	1. Every other problem in NP can be reduced to this problem in polynomial time
	2. Problem does NOT need to be in NP
	= not efficiently verifiable

PSPACE
	Class of Problems which take polynomial Memory

P $\subseteq$ NP $\subseteq$ PSPACE


## BPP (Bounded Error Probabilistic Polynomial Time)

there has to be an Algo solving the problem in polynomial time with a bounded error probability. 


# Quantum Complexity


have to establish a link between circuit and runtime complexity


## Circuit Complexity 

Size of a Circuit
	# of its elementary Gates (at most 2 input bits)

Quantum Runtime of a computational Problem
	A computational problem can be solved in p runtime on a QC $\equiv$ it can be computed by a uniform quantum circuit of polynomial size

Uniform Circuit
	This refers to a family of circuits where there's a single, efficient procedure (like a program) that can describe how to build a circuit for any input size. Imagine a machine that takes the input size and spits out the exact circuit needed for that size. This procedure itself shouldn't be too complex, ideally running in polynomial time (explained below).
    
Polynomial Size
	This means the number of gates in the circuit grows proportionally to the size of the input, not exploding exponentially. As the input gets bigger, the circuit needs to be more complex, but not unreasonably so. Imagine the number of gates increasing steadily, not jumping dramatically with each additional input bit.





## BQP
![Screenshot 2024-07-22 at 21.50.26.png](/img/user/Attachments/Screenshot%202024-07-22%20at%2021.50.26.png)
BQP? 
	Analogous to BPP

Conditions?
	Correct solution 0 or 1 computed with a prob greater than a half
	Algo can be computed using uniform qc of polynomial size


## Reversible Computations

Toffoli Gates: universal for boolean Logic
	![Screenshot 2024-07-22 at 21.48.34.png](/img/user/Attachments/Screenshot%202024-07-22%20at%2021.48.34.png)


BQP $\subseteq$ PSPACE
BPP $\subset$ BQP (Shor's Algo)

# Quantum Oracles and Interference

![Screenshot 2024-07-22 at 21.50.47.png](/img/user/Attachments/Screenshot%202024-07-22%20at%2021.50.47.png)