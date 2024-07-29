---
{"dg-publish":true,"permalink":"/coursework/so-se24/qc/c2-applying-entanglement/","noteIcon":""}
---

---


## Quantum Teleportation

Goal: transmitting qubits from one point to another without losing superposition and phase info? 


Alice wants to send the following qubit to Bob$$ \ket{\psi} = \alpha\ket{0} + \beta\ket{1}$$ 
what to use: 3 Qubits and 2 classical Bits
2 entangled qubits, one with alice and other with bob, a msg qubit psi. 

step1: create entanglement (H then CNOT)

results: state_1 = tensorproduct(psi, two qubit state)


step2: alice applies CNOT to both her qubits, msg qbit = control, the other= target
step3: hadamard on msg qubit (8 part sum now)
step4: alice measures and then transports info through the classical channel
step5: ways for bob to read the info

![IMG_51F01784358B-1.jpeg](/img/user/Attachments/IMG_51F01784358B-1.jpeg)


Circuit![Screenshot 2024-06-06 at 15.37.48.png](/img/user/Attachments/Screenshot%202024-06-06%20at%2015.37.48.png)





## Superdense Coding


Goal: transmitting classical info with a quantum channel (inv. teleportation)
req: 2 classical bits and a single qubit

step1: create entanglement (Hadamard then CNOT)


step2:  if b_0 = 1 then X gate, if b_1 = 1 then Z Gate 

step3: reverse entaglement (CNOT then Hadamard) by Bob

How Bob Ought to read it off: 
![Screenshot 2024-06-06 at 15.45.38.png](/img/user/Attachments/Screenshot%202024-06-06%20at%2015.45.38.png)


![Screenshot 2024-06-06 at 15.44.21.png](/img/user/Attachments/Screenshot%202024-06-06%20at%2015.44.21.png)



## Ent Swapping



![Screenshot 2024-06-06 at 15.52.23.png](/img/user/Attachments/Screenshot%202024-06-06%20at%2015.52.23.png)


![Screenshot 2024-06-06 at 15.49.28.png](/img/user/Attachments/Screenshot%202024-06-06%20at%2015.49.28.png)

Calculations


![Screenshot 2024-07-26 at 21.41.20.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2021.41.20.png)


![IMG_2C9D10381FAB-1.jpeg](/img/user/Attachments/IMG_2C9D10381FAB-1.jpeg)


![IMG_E2E855856161-1.jpeg](/img/user/Attachments/IMG_E2E855856161-1.jpeg)



## Bell's Ineq.  

An intuitive Explanation: 
what you would expect vs what you get: 

![Screenshot 2024-06-06 at 16.21.37.png](/img/user/Attachments/Screenshot%202024-06-06%20at%2016.21.37.png)

1. Introduction: The CHSH inequality is a generalization of Bell's test. It uses four measurement bases selected independently of each other, unlike Bell's original setup.
2. Experimental Setup:

- There's a source emitting particle pairs.
- Two detectors (A and A' on one side, B and B' on the other) measure these particles.

3. Measurement Results:

- Each measurement yields a result of either {0, 1} or an eigenvalue of +1 or -1.
- In the classical case, variables A, A', B, B' can randomly assume values of +1 or -1.

4. Classical Equation: The image presents a classical equation (2.10): A(B + B') + A'(B - B') = A·B + A·B' + A'·B - A'·B' = ±2
5. Expected Value: The expected value S of this equation depends on the random distribution of the four variables and must satisfy the CHSH inequality (2.11): S = |E(AB) + E(AB') + E(A'B) - E(A'B')| ≤ 2
6. Quantum Case:

- In quantum mechanics, there are states that can violate this inequality.
- Alice and Bob share a quantum state |ψ⟩.
- The expected value for any observable AB is given by equation (2.12): ⟨ψ| A ⊗ B |ψ⟩

7. Quantum Inequality: For quantum states, the CHSH inequality takes the form (2.13): S = |⟨ψ| A ⊗ B |ψ⟩ + ⟨ψ| A ⊗ B' |ψ⟩ + ⟨ψ| A' ⊗ B |ψ⟩ - ⟨ψ| A' ⊗ B' |ψ⟩| ≤ 2√2
8. Violation of CHSH Inequality:
![Screenshot 2024-07-21 at 18.03.11.png](/img/user/Attachments/Screenshot%202024-07-21%20at%2018.03.11.png)

Why is A = Z an Observable? 
Definition:
	•	An observable in quantum mechanics is a Hermitian operator. Hermitian operators have real eigenvalues and their eigenvectors form a complete basis. These properties make them suitable for representing measurable physical quantities.
	2.	Pauli Matrices:
	•	The Pauli matrices are a set of three 2x2 Hermitian and unitary matrices. They are defined as follows:
$$
Z = \begin{pmatrix}
1 & 0 \\
0 & -1
\end{pmatrix}, \quad
X = \begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix}, \quad
Y = \begin{pmatrix}
0 & -i \\
i & 0
\end{pmatrix} $$
	Each of these matrices is Hermitian ( Z^\dagger = Z ,  X^\dagger = X , and  Y^\dagger = Y ), ensuring their eigenvalues are real.
	3.	Eigenvalues and Measurement:
	•	The eigenvalues of  Z  are \pm 1. When you measure the observable  Z , the possible outcomes are its eigenvalues, i.e., \pm 1.
	•	For a qubit in state  |\psi\rangle , the measurement of  Z  will project  |\psi\rangle  onto one of its eigenstates (which are  |0\rangle  and  |1\rangle  in this case) with corresponding eigenvalues \pm 1.
## No-Communication Theorem

