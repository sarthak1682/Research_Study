---
{"dg-publish":true,"permalink":"/coursework/so-se24/qc/c2-applying-entanglement/","noteIcon":""}
---

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


step2:  if b_0 = 1 then not gate, if b_1 = 1 then Z Gate 

step3: reverse entaglement (CNOT then Hadamard) by Bob

How Bob Ought to read it off: 
![Screenshot 2024-06-06 at 15.45.38.png](/img/user/Attachments/Screenshot%202024-06-06%20at%2015.45.38.png)


![Screenshot 2024-06-06 at 15.44.21.png](/img/user/Attachments/Screenshot%202024-06-06%20at%2015.44.21.png)



## Ent Swapping



![Screenshot 2024-06-06 at 15.52.23.png](/img/user/Attachments/Screenshot%202024-06-06%20at%2015.52.23.png)



![Screenshot 2024-06-06 at 15.49.28.png](/img/user/Attachments/Screenshot%202024-06-06%20at%2015.49.28.png)

Calculations

![IMG_2C9D10381FAB-1.jpeg](/img/user/Attachments/IMG_2C9D10381FAB-1.jpeg)


![IMG_E2E855856161-1.jpeg](/img/user/Attachments/IMG_E2E855856161-1.jpeg)



## Bell's Ineq. and No-Communication Theorem

An intuitive Explanation: 
what you would expect vs what you get: 

![Screenshot 2024-06-06 at 16.21.37.png](/img/user/Attachments/Screenshot%202024-06-06%20at%2016.21.37.png)




