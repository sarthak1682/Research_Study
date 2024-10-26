---
{"dg-publish":true,"permalink":"/coursework/so-se24/qc/c6-quantum-error-correction/","noteIcon":""}
---

---

Reasons for Errors? 
	Measuring a Qubit -> Change of State
	No Cloning Theorem
	Errors: Continuous

## Classical EC
![Screenshot 2024-07-26 at 01.07.32.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2001.07.32.png)

### 3-Bit Repetition Code
Encoding
![Screenshot 2024-07-26 at 01.08.28.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2001.08.28.png)


Decoding
![Screenshot 2024-07-26 at 01.08.43.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2001.08.43.png)


Correct, for one bit flip (d-1/2)
detect, for upto 2 (d-1)
notation: n,k,d: 3,1,3 (k = no of transmitted logical bits)
n = trnasmitter physical qubits
d = distance 

p: bit flipped
![Screenshot 2024-07-26 at 01.16.13.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2001.16.13.png)

decrease the error prob from O(p) to p^2

## Noise in Quantum Systems


![Screenshot 2024-07-26 at 01.24.13.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2001.24.13.png)



## 3 Qubit Bit-Flip Repetition Code

![Screenshot 2024-07-26 at 01.56.14.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2001.56.14.png)

#### psi_2
- α|0⟩|0⟩|0⟩ = α|000⟩ (when the first qubit is |0⟩)
- β|1⟩|1⟩|1⟩ = β|111⟩ (when the first qubit is |1⟩)


#### Transformation from |ψ₂⟩ to |ψ₃⟩:
a) Start with |ψ₂⟩ = α|000⟩ + β|111⟩

b) Apply the error operator E = a · I + b · X to the first qubit: E = a · I + b · X = [a 0; 0 a] + [0 b; b 0] = [a b; b a]

c) This operation is equivalent to applying a rotation Rₓ(θ) around the X-axis, where: a = cos(θ/2) b = -i sin(θ/2)

d) Applying this to |ψ₂⟩:

|ψ₃⟩ = E|ψ₂⟩ = (a · I + b · X)(α|000⟩ + β|111⟩) = a(α|000⟩ + β|111⟩) + b(α|100⟩ + β|011⟩) = aα|000⟩ + aβ|111⟩ + bα|100⟩ + bβ|011⟩

e) Substituting a = cos(θ/2) and b = -i sin(θ/2):

|ψ₃⟩ = α cos(θ/2)|000⟩ - iα sin(θ/2)|100⟩ - iβ sin(θ/2)|011⟩ + β cos(θ/2)|111⟩


The transformation essentially introduces a superposition on the first qubit, spreading the initial |000⟩ and |111⟩ states into a combination of |000⟩, |100⟩, |011⟩, and |111⟩ states, with amplitudes determined by the rotation angle θ.


#### Add a voting Scheme


![Screenshot 2024-07-26 at 01.58.56.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2001.58.56.png)


![Screenshot 2024-07-26 at 01.59.08.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2001.59.08.png)


State of our qubit is proportional to the og qubit with a global phase of either cos(theta/2) or        -isin(theta/2) 

How to solve it? Syndrome Measurements. 


#### Syndrome Measurements

What is? 
Check the type of error by checking the parity of the individual qubit pairs with the ancilla qubits
![Screenshot 2024-07-26 at 02.02.42.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2002.02.42.png)


![Screenshot 2024-07-26 at 02.02.53.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2002.02.53.png)


Error Correction? 
![Screenshot 2024-07-26 at 02.03.07.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2002.03.07.png)

![Screenshot 2024-07-26 at 02.04.22.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2002.04.22.png)




## 3 Qubit Phase Flip Rep Code

Enclose error region with hadamard Gates

![Screenshot 2024-07-26 at 02.06.03.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2002.06.03.png)


## Shor 9 Qubit Code

Bit flip: X error prob goes down, Z goes up
Phase flip: opp.

![Screenshot 2024-07-26 at 02.38.22.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2002.38.22.png)
with this both errors : p^2
9,1,3

Transversal Gates? 
Can be applied by applying some gate on each qubit individually. 
![Screenshot 2024-10-06 at 00.48.00.png](/img/user/Attachments/Screenshot%202024-10-06%20at%2000.48.00.png)
