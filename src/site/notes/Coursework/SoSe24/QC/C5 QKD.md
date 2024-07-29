---
{"dg-publish":true,"permalink":"/coursework/so-se24/qc/c5-qkd/","noteIcon":""}
---

---
## BB84 Protocol


![Screenshot 2024-07-26 at 00.52.31.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2000.52.31.png)


## E91 Protocol

measure on 3 bases
don't share a quantum channel like BB84, just receive a bell pair from a common source (e.g psi_plus = 01 + 10)


### Basic Steps of E91

1. A source generates pairs of entangled particles and sends one particle from each pair to Alice and the other to Bob.
2. Alice and Bob independently and randomly choose measurement bases for each particle they receive.
3. After measurements, Alice and Bob publicly announce their measurement bases (but not the results).
4. They keep the results from measurements where they happened to choose compatible bases, discarding the rest.
5. A subset of the kept results is used to check for eavesdropping by testing Bell's inequality.
6. If no eavesdropping is detected, the remaining results form the shared secret key.

Measurement Bases
![Screenshot 2024-07-26 at 00.58.48.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2000.58.48.png)

### Attack Detection via CHSH

if ineq is NOT violated, Eve detected. 
![Screenshot 2024-07-26 at 00.59.42.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2000.59.42.png)![Screenshot 2024-07-26 at 00.59.55.png](/img/user/Attachments/Screenshot%202024-07-26%20at%2000.59.55.png)


Both require an authenticated classical channel

