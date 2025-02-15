---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/segment-rec/","noteIcon":""}
---

---
T-XL: Core Objective:

- It's designed for autoregressive language modeling - predicting the next token in a sequence
- The main challenge it addresses is handling very long sequences effectively

Key Problems with Vanilla Transformers:

1. Limited Context:

- They have to split text into shorter segments
- Each segment is processed independently
- This leads to lost context between segments
- Can't capture relationships across segment boundaries

2. Resource Constraints:

- Can't have infinite memory or computing power
- Need to work within practical hardware limitations

Transformer-XL's Solutions:

1. Segment-level Recurrence:

- Caches and reuses hidden states from previous segments
- Information can flow across segment boundaries
- Creates connections between distant parts of the text

2. Improved Context Handling:

- Contextual information flows smoothly between segments
- Better at understanding long-term dependencies
- More natural processing of text structure



---
Segment Recurrence is a technique used in sequence processing where data is processed in consecutive segments of fixed length L. Here's a detailed explanation:

- Segments Definition:

- sr = [xr,1, ..., xr,L] is one segment of length L

- sr+1 = [xr+1,1, ..., xr+1,L] is the next consecutive segment

- For example, if we have a sequence [1,2,3,4,5,6,7,8] and L=4:

- First segment s₁ = [1,2,3,4]

- Second segment s₂ = [5,6,7,8]

- Hidden States:

- h^n_r represents the hidden states at layer n for segment r

- These are typically matrices/tensors of size L×d where d is the hidden dimension

- Processing Steps for segment sr+1:
    
    h̃^n_r+1 = Concat[SG(h^n-1_r), h^n-1_r+1]
    

This step:

- Takes the previous segment's hidden states (h^n-1_r)

- Applies stop-gradient (SG) to prevent backpropagation

- Concatenates it with current segment's hidden states (h^n-1_r+1)

Then three parallel computations occur:

q^n_r+1 = h̃^n_r+1 W^T_q    (Query computation)

k^n_r+1 = h̃^n_r+1 W^T_k    (Key computation)

v^n_r+1 = h̃^n_r+1 W^T_v    (Value computation)

Finally:

h^n_r+1 = Trafo(q^n_r+1, k^n_r+1, v^n_r+1)

where Trafo is typically a transformer layer operation.

Practical Example:

Let's say we're processing text: "The cat sat on the mat in the sun"

With L=4 words per segment:

Segment 1 (sr): ["The", "cat", "sat", "on"]

Segment 2 (sr+1): ["the", "mat", "in", "the"]

When processing Segment 2:

- The model uses information from Segment 1 (through the concatenation step)

1. But prevents gradients from flowing back to Segment 1 (through stop-gradient)

- This allows the model to maintain context while being computationally efficient