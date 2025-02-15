---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/rp-es/","noteIcon":""}
---

---

The Problem:

1. Traditional absolute positional encodings (PE) have a limitation: they assign the same embeddings to words in similar positions across different segments. For example, the first word in each segment would get the same positional encoding. **They certainly need it to work with Segment Recurrence.** 

- There's no way to capture the positional difference between x_r,j (token j in segment r) and x_r+1,j (token j in segment r+1).

The Solution:

The solution introduces relative positional encodings that consider the relative distances between tokens rather than their absolute positions.

Mathematical Breakdown:

- Absolute Attention (A^abs):
    
    A^abs_i,j = E_i W_q W_k E_j   (a)
    
              + E_i W_q W_k U_j    (b)
    
              + U_i W_q W_k E_j    (c)
    
              + U_i W_q W_k U_j    (d)
    
    Where:

- E_i, E_j are token embeddings

- U_i, U_j are absolute positional encodings

- W_q, W_k are query and key weight matrices

- Relative Attention (A^rel):
    
    A^rel_i,j = E_i W_q W_k,E E_j     (a)
    
              + E_i W_q W_k,R R_i-j    (b)
    
              + u W_k,E E_j            (c)
    
              + v W_k,R R_i-j          (d)
    
    Where:

- R_i-j represents relative position encoding between positions i and j

- W_k,E and W_k,R are separate weight matrices for content and positional information

- u and v are learnable vectors replacing the position-dependent queries

Key Improvements:

- Replace Absolute with Relative PEs:

- Instead of U_j in terms (b) and (d), use R_i-j

- R_i-j captures the relative distance between positions i and j

- Usually implemented as a combination of fixed and sinusoidal encodings

- Simplified Query Vectors:

- Replace U_i^T W_q with single trainable vectors u and v

- This reduces complexity and number of parameters

- Makes the model more efficient

- Separate Weight Matrices:

- Use W_k,E for content (token embeddings)

- Use W_k,R for positional information

- This separation allows the model to learn different transformations for content and position

Practical Example:

Consider the sentence: "The cat sat on the mat"

With absolute positioning:

- "The" (position 1) and "the" (position 5) would get similar encodings

- No direct way to encode that they are 4 positions apart

With relative positioning:

- The relationship between "cat" and "sat" (distance of 1)

- The relationship between "The" and "mat" (distance of 5)

- These relationships are directly encoded in R_i-j