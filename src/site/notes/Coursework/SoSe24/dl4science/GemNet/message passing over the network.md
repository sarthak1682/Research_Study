---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/message-passing-over-the-network/","noteIcon":""}
---

---
[Creating Message Passing Networks — pytorch\_geometric documentation](https://pytorch-geometric.readthedocs.io/en/latest/tutorial/create_gnn.html)

---
nodes exchanging information with their neighbors to update their own representations

![Screenshot 2024-06-03 at 15.03.51.png](/img/user/Attachments/Screenshot%202024-06-03%20at%2015.03.51.png)

this is easy enough:
1) Take a node i
2) Its own feature vector and the fv of its neightbours go through an NN Layer
3) aggregate that with its own feature vector, call it agg
4) let agg go through the same NN layer, output is the update feature vector for the node i

