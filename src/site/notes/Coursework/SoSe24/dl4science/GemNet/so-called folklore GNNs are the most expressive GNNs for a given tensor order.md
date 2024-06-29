---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/so-called-folklore-gn-ns-are-the-most-expressive-gn-ns-for-a-given-tensor-order/","noteIcon":""}
---

---
### Folklore GNNs

Folklore GNNs, or higher-order GNNs, generalize the basic GNN model by using higher-order tensors instead of just node features or edge features. This allows them to capture more complex interactions within the graph.

### Tensor Order

The order of a tensor refers to the number of dimensions or indices required to describe it. For example:

- A scalar is a 0th-order tensor.
- A vector is a 1st-order tensor.
- A matrix is a 2nd-order tensor.
- Higher-order tensors have more than two dimensions.

In the context of GNNs:

- 1st-order GNNs use node features.
- 2nd-order GNNs use both node and edge features.
- Higher-order GNNs use tensors of order greater than 2, capturing interactions among larger subsets of nodes.

Maron et al. proved that for any fixed tensor order, there is a folklore GNN that can simulate any other GNN of the same or lower order.