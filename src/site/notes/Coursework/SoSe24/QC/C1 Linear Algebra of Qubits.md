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

If one measures a qubit and the result turns out to be 0 qubit, then the only thing that can be said with certainty is $\alpha$ =! 0 must have been true. 


### Measurement in Bases other than the Computational Basis

Choosing X-Axis as the computational Basis
$$ \ket{+} = \frac{1}{\sqrt{2}} (|0\rangle + |1\rangle);
\ket{-} = \frac{1}{\sqrt{2}} (|0\rangle - |1\rangle)
$$


Choosing Y-Axis as the computational Basis
$$ 

 \ket{i} = \frac{1}{\sqrt{2}} (|0\rangle + i|1\rangle);
\ket{-i} = \frac{1}{\sqrt{2}} (|0\rangle - i|1\rangle)
$$



Each bases are normalized eigenvectors of the corresponding Pauli Matrices with eigenvalue +1 and -1.


Conversion 

$$ 
\alpha\ket{0} + \beta\ket{1}
= \hat{\alpha}\ket{+} + \hat{\beta}\ket{-} 
= \tilde{\alpha}\ket{i}+  \tilde{\beta}\ket{-i}

$$

where, 
$$ 
\hat{\alpha} = \frac{1}{sqrt(2)}(\alpha + \beta)
$$$$
\hat{\beta} = \frac{1}{sqrt(2)}(\alpha - \beta)

$$
and where, 
$$
\tilde{\alpha}
=  \frac{1}{sqrt(2)}(\alpha - i\beta)



$$
$$
\tilde{\beta} =  \frac{1}{sqrt(2)}(\alpha + i\beta)
$$



### Observables

Physical Entities are repr. by linear operators in the hilbert space

[[Coursework/SoSe24/QC/Hilbert Space\|Hilbert Space]]

Observable: any physical quantity that one can measure out of a particle (position, momentum etc.)

linear operator: map on a vector space that preserves structure (on that space)
Addition is still addition, scalar mult is still the same
![Screenshot 2024-06-06 at 14.38.55.png](/img/user/Attachments/Screenshot%202024-06-06%20at%2014.38.55.png)

Linear Op. = Abstract Map, Matrix is the repr. of that in a particular basis


given an observable, how can one get all the possible values that one can measure?  find the eigenvalues
to find out which particular eigenstate corresponds to that particular value, find the eigenvector
eignv. = def. states, eignval. = def. values
[[Coursework/SoSe24/QC/Hermitian Operators\|Hermitian Operators]]


## Density Matrix
Can be used to repr. mixed state, prob. distr. over pure quantum state

$$ 
\rho = \sum\limits_{i}p_{i}\ket{\psi_i}\bra{\psi_i}

$$
40% of 0 and 60 of 1 would look like
$$ \rho = \frac{2}{5}\ket{0}\bra{0}
+  \frac{3}{5}\ket{1}\bra{1}
= \begin{pmatrix}   \frac{2}{5} & 0\\ 0 & \frac{3}{5}  \\  \end{pmatrix}
$$

### Exp. Value


$$ E = tr(O\rho)$$
## No Cloning Theorem 

