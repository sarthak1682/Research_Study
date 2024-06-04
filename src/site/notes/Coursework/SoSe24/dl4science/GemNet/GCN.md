---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/gcn/","noteIcon":""}
---

---
[Graph Convolutional Networks (GCNs) made simple - YouTube](https://www.youtube.com/watch?v=2KRAOZIULzw)


---
1 Layer GCN
![Screenshot 2024-06-03 at 15.10.13.png](/img/user/Attachments/Screenshot%202024-06-03%20at%2015.10.13.png)

Step 1: Get the average of its neighbours
Step 2: Pass the Avg vector through a dense NN Layer (Matrix Mul + NonLinear Activation)


2 layer GCN: it's same as any other NN except for the preprocessing step at the beginning of each layer. 
![Screenshot 2024-06-03 at 15.13.08.png](/img/user/Attachments/Screenshot%202024-06-03%20at%2015.13.08.png)





OG Kipf and Welling Paper


Adjacency Matrix  with self-connections: D_tilda = degree matrix, d_i, d_j: neighbourhood size of the two nodes being connected
![Screenshot 2024-06-03 at 15.18.31.png](/img/user/Attachments/Screenshot%202024-06-03%20at%2015.18.31.png)
![Screenshot 2024-06-03 at 15.16.44.png](/img/user/Attachments/Screenshot%202024-06-03%20at%2015.16.44.png)
Represents the normalized adjc. matrix



![Screenshot 2024-06-03 at 15.17.39.png](/img/user/Attachments/Screenshot%202024-06-03%20at%2015.17.39.png)
is the adjacency matrix with self-loops added


GCN-Eq
![Screenshot 2024-06-03 at 15.20.46.png](/img/user/Attachments/Screenshot%202024-06-03%20at%2015.20.46.png)

mean pooling is applied at the msg passing stage 