---
{"dg-publish":true,"permalink":"/coursework/so-se24/qc/c1-linear-algebra-of-qubits/","noteIcon":""}
---

---
## Qubits
$$ state\_vector:  \ket{\psi} = \begin{pmatrix}\alpha \\ \beta \end{pmatrix} = \alpha* \begin{pmatrix} 1 \\ 0 \end{pmatrix} + \beta* \begin{pmatrix} 0 \\ 1 \end{pmatrix}
= \alpha*\ket{0} + \beta*\ket{1}; (\alpha, \beta \in \mathbb{C}); | \alpha |^{2}+ | \beta |^{2}= 1
$$
$$ \bra{\psi} = 
\begin{pmatrix} \alpha^* & \beta^* \end{pmatrix}

$$
## Graphical Repr. of Qubits

The Bloch Sphere
![IMG_804C37DB24B2-1.jpeg| center | 400](/img/user/Attachments/IMG_804C37DB24B2-1.jpeg)


$$ state\_{vector:} \ket{\psi} = cos(\frac{\theta}{2})\ket{0} + sin\frac{\theta}{2}e^{i*\phi}\ket{1};  (\theta \in [0,\pi], \phi \in [0,2\pi]) $$
	theta is the angle between the vector and positive z axis,
	phi is the angle made by the component on the x-y plane with the x axis


## Quantum Gates

A State Transition is a unitary Matrix, which 

preserves Lengths
$$ (||U * v|| = ||v||) $$

preserves Angles:
$$<Uv | Uw> = <v | w>$$
Product of Matrix with its Conjugate Transpose is Identity
$$
U * U^{†} = I () 
$$

$$ unitary\_matrix: U = \begin{bmatrix}
a & b \\
c & d
\end{bmatrix} 
= \sum_i\limits\ket{\phi_i'}\bra{\phi_{i}}
  $$

### Pauli Gates + Hadamard Gate


Also, XX = YY = ZZ = I 

![JPEG image-44A5-9E95-93-0.jpeg](/img/user/Attachments/JPEG%20image-44A5-9E95-93-0.jpeg)





### Arbitrary Rotation Gates

$$ R_A(\theta)
= e^\frac{-Ai\theta}{2}
= cos(\frac{\theta}{2})I - isin\frac{\theta}{2}A 
; (A = X,Y,Z)
$$





## Multi-Qubit Systems

### Quantum Registers

The combination of two qubits into a register R is the tensor product of the state vectors, proving the following is indeed easy. 

$$ R = \ket{a} ⊗ \ket{b} = \ket{a}\ket{b}
= \begin{pmatrix}
\alpha_0 \\
\beta_0
\end{pmatrix}
⊗
 \begin{pmatrix}
\alpha_1 \\
\beta_1
\end{pmatrix}

= 
\alpha_0\alpha_1\ket{0}\ket{0}+
\alpha_0\beta_1\ket{0}\ket{1}+
\alpha_1\beta_0\ket{1}\ket{0}+
\alpha_1\beta_1\ket{1}\ket{1}

$$

### Controlled Multi-Qubit Gates

![JPEG image-4B5F-A52A-18-0.jpeg|center| 300](/img/user/Attachments/JPEG%20image-4B5F-A52A-18-0.jpeg)

The matrix of a controlled Gate U on a state |x_1x_0> with x_1  as the control qubit and x_o as the target qubit is defined as 
$$ CU_{Matrix}
= \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\  0 & 0 & U_{11} & U_{12} \\0 & 0 & U_{21} & U_{22}
\end{bmatrix} (U = Unitary Matrix)

$$

$$ CU_{braket} = \ket{0}\bra{0} ⊗ I + \ket{1}\bra{1} ⊗ U = Control⊗Target + Control⊗Target  $$


### SWAP Gate

![IMG_7D4A43147801-1.jpeg| center| 400](/img/user/Attachments/IMG_7D4A43147801-1.jpeg)


$$ SWAP = 

\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 \\  0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1
\end{bmatrix}


$$


## Simple Quantum Algos

### Entanglement Circuit

![IMG_3AB89F183277-1.jpeg| center | 400](/img/user/Attachments/IMG_3AB89F183277-1.jpeg)

They are known as the four _maximally entangled two-qubit Bell states_ and form a maximally entangled basis, known as the Bell basis, of the four-dimensional hilbert space for 2-qubits
$$ 
\ket{a_1a_0}= \ket{00} \implies \ket{\beta_{00}} 
= |Φ^+\rangle = \frac{1}{\sqrt{2}} (|00\rangle + |11\rangle) 
= CNOT(H ⊗ I) \ket{00}

$$
$$
\ket{a_1a_0}= \ket{10} \implies \ket{\beta_{10}} 
= |Φ^-\rangle = \frac{1}{\sqrt{2}} (|00\rangle - |11\rangle) 
$$
$$\ket{a_1a_0}= \ket{01} \implies \ket{\beta_{01}} 
= |\psi^+\rangle = \frac{1}{\sqrt{2}} (|01\rangle + |10\rangle) 
$$
$$
\ket{a_1a_0}= \ket{11} \implies \ket{\beta_{11}} 
= |\psi^-\rangle = \frac{1}{\sqrt{2}} (|01\rangle - |10\rangle) 
$$

the positive amplitude states are EPR Pairs

## Measuring Qubits

