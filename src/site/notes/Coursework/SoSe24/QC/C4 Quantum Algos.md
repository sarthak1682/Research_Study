---
{"dg-publish":true,"permalink":"/coursework/so-se24/qc/c4-quantum-algos/","noteIcon":""}
---

.---
## Deutsch Algo

Solves? 
	Given: binary $f: {0,1} \to {0,1}$ (Oracle)
	Decide: f is constant or f is balanced

vs Classical?
	need 2 calls


Circuit?
![Screenshot 2024-07-24 at 16.13.26.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2016.13.26.png)
	$U_f:\ket{x,y} \to \ket{x, y \oplus f(x)}$   (implementation of $f$ as a unitary op)


States? 
#TODO 


How to read? 
	if $\ket{0}$ is measured on the upper qubit -> f is constant, otherwise it is balanced



## Hadamard on a Quantum Register


$H_{n}\ket{x}  =  \frac{1}{\sqrt{2^{n}}} \sum\limits_{z=0}^{2^{n-1}}(-1)^{x \cdot z}\ket{z}$         


Example
	![Screenshot 2024-07-24 at 16.25.16.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2016.25.16.png)



## Deutsch-Jozsa Algo

Solves? 
	Given: binary $f: {0,1}^n \to {0,1}$ (Oracle)
	Decide: f is constant or f is balanced

Classical? 
	In the balanced Case, 2^n-1 + 1 function calls are needed in the worst case. 

Circuit? 
![Screenshot 2024-07-24 at 16.27.50.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2016.27.50.png)

Interpreting the result:
- If all n qubits are measured as |0>, the function is constant.
- If any of the n qubits are measured as |1>, the function is balanced.

States? 
	

## Grover's Algo

Solves? 
	search for an Element in an unsorted database

Classical? 
	O(N), on avg. N/2 Attempts

Oracle? 
	![Screenshot 2024-07-24 at 16.29.34.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2016.29.34.png)

	![Screenshot 2024-07-24 at 16.29.48.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2016.29.48.png)


States? 
#TODO 


### Amplitude Amplification

what? 
	Increase the probability of measuring the corr. State

How? 
	Reflecting an amplitude around the mean value: a -> 2m -a

Number of it? 
	Max # of useful iter when searching for k solutions: $\lfloor {\frac{\pi}{4}}{\sqrt{\frac{N}{k}}} \rfloor$

Complexity? 
	O(root N)


Circuit? 

![Screenshot 2024-07-24 at 16.37.43.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2016.37.43.png)

D_n = -H_n* R_n * H_n
![Screenshot 2024-07-24 at 16.39.03.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2016.39.03.png)

where, R_2 is
![Screenshot 2024-07-24 at 16.37.56.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2016.37.56.png)


### Max-Cut with Grover

Max-Cut? 
	find a partition, max # of edges

Complexity? 
	NP-Complete, NP Hard if you want accuracy to be more than 94.10%


Circuit? 
	Node? 
		![Screenshot 2024-07-24 at 16.50.21.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2016.50.21.png)
	Edges? 
		![Screenshot 2024-07-24 at 16.50.50.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2016.50.50.png)
	Entire Circuit together? 
		![Screenshot 2024-07-24 at 16.51.25.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2016.51.25.png)

Counters in the Circuit? 
	Add the # of edges for a specific bipartition

Run Time  
vs 2^n in classical
![Screenshot 2024-07-24 at 16.55.03.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2016.55.03.png)
k; the number of results


Complexity
	![Screenshot 2024-07-24 at 16.54.48.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2016.54.48.png)



## VQAs

Motivation? 
	Algos presented above are tough on today's hardware: 
		oracle complex
		several repetition

Steps? 
	1. Define a cost-function
	2. circuit Ansatz
	3. Running a classical optimization procedure




### QAOA

### Cost-F

Cost Function? (QUBO)
	1. variables have to be binary
	2. fn includes linear and quadratic terms
	3. no other constraints on the var 
C(x) = sum over edges (x_i + x_j - 2x_ix_j) 

Cost Hamiltonian? 
x are eigenvectors, C(x): eigenvalues
![Screenshot 2024-07-24 at 17.40.43.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2017.40.43.png)


![Screenshot 2024-07-24 at 17.41.33.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2017.41.33.png)
![Screenshot 2024-07-24 at 17.41.46.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2017.41.46.png)
![Screenshot 2024-07-24 at 17.41.41.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2017.41.41.png)

![Screenshot 2024-07-24 at 17.42.46.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2017.42.46.png)


### Circuit-Ansatz

Cost Hamiltonian!

Mixer Hamiltonian? 
	Diffusion analogue from Grover
	![Screenshot 2024-07-24 at 17.44.53.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2017.44.53.png)


Variational Params? 
![Screenshot 2024-07-24 at 17.45.31.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2017.45.31.png)


![Screenshot 2024-07-24 at 17.45.40.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2017.45.40.png)

![Screenshot 2024-07-24 at 17.47.15.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2017.47.15.png)


![Screenshot 2024-07-24 at 17.47.23.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2017.47.23.png)

![Screenshot 2024-07-24 at 17.50.31.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2017.50.31.png)

![Screenshot 2024-07-24 at 17.50.23.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2017.50.23.png)

![Screenshot 2024-07-24 at 17.50.43.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2017.50.43.png)

![Screenshot 2024-07-24 at 17.50.55.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2017.50.55.png)


## QFT

[[Coursework/SoSe24/dl4science/Discrete, Fast Fourier Transform (D, FFT)\|Discrete, Fast Fourier Transform (D, FFT)]]

![Screenshot 2024-07-24 at 22.22.56.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2022.22.56.png)

 $QFT_{N}|k\rangle = \frac{1}{\sqrt{N}} \sum_{j=0}^{N-1} e^{2\pi i \frac{kj}{N}} |j\rangle$ : fourier coeff multiplied by basis states

![Screenshot 2024-07-24 at 22.23.56.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2022.23.56.png)

similarity: initial state 0 into an equally weighted superposition, amplitudes are different, while abs. values are the still the same.
![Screenshot 2024-07-24 at 22.26.22.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2022.26.22.png)
R_k rotates the phase by 2pi/k around the Z axis. 


![Screenshot 2024-07-24 at 22.25.52.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2022.25.52.png)

Initial state: |x2x1x0⟩

1. After H on x2: 1/√2 (|0⟩ + |1⟩) ⊗ |x1x0⟩
2. After controlled-R4 (control: x1, target: x2): 1/√2 (|0⟩|x1⟩ + e^(iπx1/4)|1⟩|x1⟩) ⊗ |x0⟩
3. After controlled-R8 (control: x0, target: x2): 1/√2 (|0⟩|x1x0⟩ + e^(iπ(x1/4 + x0/8))|1⟩|x1x0⟩)
4. After H on x1: 1/2 (|0⟩ + e^(iπ(x1/4 + x0/8))|1⟩) ⊗ (|0⟩ + |1⟩) ⊗ |x0⟩
5. After controlled-R4 (control: x0, target: x1): 1/2 (|0⟩ + e^(iπ(x1/4 + x0/8))|1⟩) ⊗ (|0⟩ + e^(iπx0/4)|1⟩) ⊗ |x0⟩
6. After H on x0: 1/2√2 (|0⟩ + e^(iπ(x1/4 + x0/8))|1⟩) ⊗ (|0⟩ + e^(iπx0/4)|1⟩) ⊗ (|0⟩ + |1⟩)
7. After SWAP between x2 and x0: 1/2√2 (|0⟩ + |1⟩) ⊗ (|0⟩ + e^(iπx0/4)|1⟩) ⊗ (|0⟩ + e^(iπ(x1/4 + x0/8))|1⟩)

Final state (|y0y1y2⟩): 1/2√2 (|0⟩ + |1⟩) ⊗ (|0⟩ + e^(iπx0/4)|1⟩) ⊗ (|0⟩ + e^(iπ(x1/4 + x0/8))|1⟩)

### Finding the Period using QFT

Input Range
	{0,1...,M-1} 
Period 
	r

3 Conditions:
1. f is bijective within a period
2. r is a div of M
3. M >> r^2


Input Reg
	x: size $ceil{log(M)}$ 

Output Reg
	y: large enuff to represent f(x)


![Screenshot 2024-07-24 at 22.37.58.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2022.37.58.png)

x is in superposition over all possible inputs, entangled with y
![Screenshot 2024-07-24 at 22.40.14.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2022.40.14.png)

measure y
	get value: f(a)
entanglement ensures that only those input in x that have an amp != 0 are pre-images of f(a)

![Screenshot 2024-07-24 at 22.43.01.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2022.43.01.png)


 ![Screenshot 2024-07-24 at 22.43.09.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2022.43.09.png)

The QFT essentially redistributes the amplitudes of the input state into peaks in the frequency domain. In this case, it transforms the evenly spaced values [a₀ + j·r] into a state where the amplitudes are concentrated around multiples of M/r.

![Screenshot 2024-07-24 at 22.44.14.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2022.44.14.png)

![Screenshot 2024-07-24 at 22.45.10.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2022.45.10.png)





## Shor

One Way function? 
	f that can be calculated eff. in only one dir
	e.g: Prime Factorization


How to generate an RSA Key-Pair? 
	1. p,q are prime (3,5)
	2. RSA Modulus: N = pq (15), Euler's totient Function $\phi(N)$ = 8
	3. unrelated number pk, pk < $\phi(N)$  (pk = 7)
	4. Multiplicative Inv. sk of pk, wrt phi, sk = 7
	5. pk, N is the public key: (7,15), sk: 7 secret key

Euler's Theorem
	if a and N are coprime (gcd = 1), then $a^{\phi(N)} \equiv 1 mod N (a,N \in \mathbb{N})$ 

Relevance? 
	$a^{pk \times sk} \equiv a mod N$, this relation can be used for encryption
	$c = m^{(pk)}mod N$, m being the message
	$c^{(sk)} mod N = m$ 

Calculating the 2nd Key? 
Given: pk, N, c 
1. get r of c^x mod 91
2. get sk by sk*pk = 1 mod r

Where is the algo? 

setting up
there exists an r such that, a^r -1 = 0 mod N gcd (a, N) = 1, (euler's theorem) 
z = a^r - 1
z = (a^(r/2) + 1)* (a^(r/2) -1)
	r even
	(a^(r/2) + 1) is not a multiple of N

find gcd((a^(r/2) - 1), N) = v
	v is from 2 to N: v is a non-trivial div of N -> v = q or p
	v = 1 -> (a^(r/2) - 1) and N not related, (a^(r/2) - 1) is only a divisor of k (z = kN)
	v = N, (a^(r/2) - 1) is a multiple of N, (a^(r/2) + 1) is a div of k 


Complexity:
Shor (log(n)^4) approx. n^3
Quantum Part: log(n)^3 (modular exp)
QFT: log(n)^2 gates
classical part: log(n) multiplications





Sieve: O(e^(n* sqrt3))



Flowchart
![Screenshot 2024-07-24 at 23.09.13.png](/img/user/Attachments/Screenshot%202024-07-24%20at%2023.09.13.png)