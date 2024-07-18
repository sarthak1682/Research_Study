---
{"dg-publish":true,"permalink":"/coursework/so-se24/gen-ai/ch-6-ar-ms/","noteIcon":""}
---

---


#### Self-Attention

###### QKV
Example with a Sentence

Let’s take a sentence: “The cat sat on the mat.”

	1.	Formulating the Query:
Suppose we are focusing on the word “sat.” This word acts as our query.
	2.	Matching the Query with Keys:
We compare “sat” (query) with the keys (attributes) of all the other words (“The,” “cat,” “on,” “the,” “mat”) to determine their relevance.
	3.	Retrieving Values:
Based on the relevance scores (how well the keys match the query), we combine the values (actual information) of all words to understand the context of “sat.”

Simplified Mathematical Explanation
	1.	Query, Key, Value Vectors:
Each word in a sentence is represented as a vector (a list of numbers). For the word “sat,” we have:
	•	Query vector  Q_{sat} 
	•	Key vectors  K_{the}, K_{cat}, K_{sat}, K_{on}, K_{the}, K_{mat} 
	•	Value vectors  V_{the}, V_{cat}, V_{sat}, V_{on}, V_{the}, V_{mat} 
	2.	Attention Scores:
We calculate attention scores by taking the dot product of the query vector  Q_{sat}  with each key vector:
	•	Score with “The”:  Q_{sat} \cdot K_{the} 
	•	Score with “cat”:  Q_{sat} \cdot K_{cat} 
	•	And so on…
	3.	Softmax and Weighted Sum:
These scores are passed through a softmax function to convert them into probabilities (weights), which are then used to compute a weighted sum of the value vectors. This gives us the final attention output for “sat.”


##### Attention Mechanism with Dimensions

Given the sentence "The cat sat on the mat", let's use the embedding dimension $d_{model}$ for simplicity. The sentence has 6 words, so the input matrix $X$  is $6 \times 4$ 

###### Step-by-Step Explanation
**Input Embedding Matrix $X$**
   The input sentence "The cat sat on the mat" is converted into an embedding matrix $X$:
   $$
   X = \begin{bmatrix}
   x_1 \\
   x_2 \\
   x_3 \\
   x_4 \\
   x_5 \\
   x_6
   \end{bmatrix} \text{ where each } x_i \in \mathbb{R}^4
   $$
   For simplicity, assume:
   
   $$
   X = \begin{bmatrix}
   0.1 & 0.2 & 0.3 & 0.4 \\
   0.2 & 0.3 & 0.4 & 0.5 \\
   0.3 & 0.4 & 0.5 & 0.6 \\
   0.4 & 0.5 & 0.6 & 0.7 \\
   0.5 & 0.6 & 0.7 & 0.8 \\
   0.6 & 0.7 & 0.8 & 0.9
   \end{bmatrix}
   $$
   
   
1. **Weight Matrices $W_Q, W_K, W_V$**
   These are learnable parameters in the attention mechanism. Each matrix has dimensions $4 \times 4$:
   $$
   W_Q = \begin{bmatrix}
   0.1 & 0.2 & 0.3 & 0.4 \\
   0.2 & 0.3 & 0.4 & 0.5 \\
   0.3 & 0.4 & 0.5 & 0.6 \\
   0.4 & 0.5 & 0.6 & 0.7
   \end{bmatrix}, 
   W_K = \begin{bmatrix}
   0.5 & 0.6 & 0.7 & 0.8 \\
   0.6 & 0.7 & 0.8 & 0.9 \\
   0.7 & 0.8 & 0.9 & 1.0 \\
   0.8 & 0.9 & 1.0 & 1.1
   \end{bmatrix}, 
   W_V = \begin{bmatrix}
   0.9 & 1.0 & 1.1 & 1.2 \\
   1.0 & 1.1 & 1.2 & 1.3 \\
   1.1 & 1.2 & 1.3 & 1.4 \\
   1.2 & 1.3 & 1.4 & 1.5
   \end{bmatrix}
   $$
3. **Compute Queries $Q$, Keys $K$, and Values $V$**
   $$
   Q = X W_Q, \quad K = X W_K, \quad V = X W_V
   $$
   Given $X$ is $6 \times 4$ and $W_Q, W_K, W_V$ are $4 \times 4$:
   $$
   Q = \begin{bmatrix}
   0.3 & 0.4 & 0.5 & 0.6 \\
   0.4 & 0.5 & 0.6 & 0.7 \\
   0.5 & 0.6 & 0.7 & 0.8 \\
   0.6 & 0.7 & 0.8 & 0.9 \\
   0.7 & 0.8 & 0.9 & 1.0 \\
   0.8 & 0.9 & 1.0 & 1.1
   \end{bmatrix}, 
   K = \begin{bmatrix}
   0.7 & 0.8 & 0.9 & 1.0 \\
   0.8 & 0.9 & 1.0 & 1.1 \\
   0.9 & 1.0 & 1.1 & 1.2 \\
   1.0 & 1.1 & 1.2 & 1.3 \\
   1.1 & 1.2 & 1.3 & 1.4 \\
   1.2 & 1.3 & 1.4 & 1.5
   \end{bmatrix}, 
   V = \begin{bmatrix}
   1.0 & 1.1 & 1.2 & 1.3 \\
   1.1 & 1.2 & 1.3 & 1.4 \\
   1.2 & 1.3 & 1.4 & 1.5 \\
   1.3 & 1.4 & 1.5 & 1.6 \\
   1.4 & 1.5 & 1.6 & 1.7 \\
   1.5 & 1.6 & 1.7 & 1.8
   \end{bmatrix}
   $$
4. **Compute Attention Scores**
   $$
   \text{Attention Scores} = Q K^T
   $$
   If $Q$ and $K$ are both $6 \times 4$, then $Q K^T$ results in a $6 \times 6$ matrix:
   $$
   Q K^T = \begin{bmatrix}
   1.54 & 1.78 & 2.02 & 2.26 & 2.50 & 2.74 \\
   1.78 & 2.06 & 2.34 & 2.62 & 2.90 & 3.18 \\
   2.02 & 2.34 & 2.66 & 2.98 & 3.30 & 3.62 \\
   2.26 & 2.62 & 2.98 & 3.34 & 3.70 & 4.06 \\
   2.50 & 2.90 & 3.30 & 3.70 & 4.10 & 4.50 \\
   2.74 & 3.18 & 3.62 & 4.06 & 4.50 & 4.94
   \end{bmatrix}
   $$
5. **Apply Softmax to Get Attention Weights**
$$\text{Attention Weights} = \text{softmax}(Q K^T)$$
6. **Compute the Attention Output**
   Multiply the attention weights by the value matrix $V$:
   $$
   \text{Attention Output} = \text{Attention Weights} \cdot V
   $$
   Assuming the attention weights matrix is $6 \times 6$ and $V$ is $6 \times 4$, the attention output will be $6 \times 4$:
   $$
   \text{Attention Output} = \begin{bmatrix}
   1.48 & 1.62 & 1.76 & 1.90 \\
   1.68 & 1.84 & 2.00 & 2.16 \\
   1.88 & 2.06 & 2.24 & 2.42 \\
   2.08 & 2.28 & 2.48 & 2.68 \\
   2.28 & 2.50 & 2.72 & 2.94 \\
   2.48 & 2.72 & 2.96 & 3.20
   \end{bmatrix}
   $$
###### Summary of Dimensions
- **Input Embedding Matrix $X$**: $6 \times 4$
- **Weight Matrices $W_Q, W_K, W_V$**: $4 \times 4$
- **Query, Key, Value Matrices $Q, K, V$**: $6 \times 4$
- **Attention Scores**: $6 \times 6$
- **Attention Weights**: $6 \times 6$
- **Attention Output**: $6 \times 4$


#### Multi-Headed Attention

##### What is Multi-Headed Attention?

Multi-headed attention is an extension of the attention mechanism where multiple attention "heads" are used simultaneously. Each head independently computes attention, allowing the model to focus on different parts of the input. The outputs from each head are then concatenated and transformed to produce the final result.

##### Process of Multi-Headed Attention

Let's use the same example sentence: "The cat sat on the mat," with embedding dimension $d_{model} = 8$, and we'll have 2 heads for simplicity.

###### 1. **Input Representation**

Assume the embedded input matrix $X$ for our sentence is:

$$
X = \begin{bmatrix}
x_1 \\
x_2 \\
x_3 \\
x_4 \\
x_5 \\
x_6
\end{bmatrix}
$$

where each $x_i$ is an 8-dimensional vector.

###### 2. **Linear Projections for Each Head**

For multi-headed attention, we project the input $X$ into multiple sets of Query (Q), Key (K), and Value (V) matrices. Each head has its own set of weight matrices.

Assume we have two heads, so we'll have separate weight matrices for each head.

**Head 1:**
$$
W_Q^{(1)}, W_K^{(1)}, W_V^{(1)} \text{ of size } 8 \times 4
$$

**Head 2:**
$$
W_Q^{(2)}, W_K^{(2)}, W_V^{(2)} \text{ of size } 8 \times 4
$$

###### 3. **Computing Queries, Keys, and Values for Each Head**

For each head, we compute the Q, K, and V matrices:

$$
Q^{(1)} = X W_Q^{(1)}, \quad K^{(1)} = X W_K^{(1)}, \quad V^{(1)} = X W_V^{(1)}
$$
$$
Q^{(2)} = X W_Q^{(2)}, \quad K^{(2)} = X W_K^{(2)}, \quad V^{(2)} = X W_V^{(2)}
$$

Assuming $X$ is $6 \times 8$ and $W_Q^{(1)}, W_K^{(1)}, W_V^{(1)}, W_Q^{(2)}, W_K^{(2)}, W_V^{(2)}$ are $8 \times 4$, the resulting Q, K, V matrices for each head will be $6 \times 4$.

###### 4. **Calculating Attention for Each Head**

For each head, we calculate the attention scores, apply softmax, and compute the weighted sum of values.

**Head 1:**
$$
\text{Attention Scores}^{(1)} = Q^{(1)} K^{(1)T}, \quad \text{Attention Weights}^{(1)} = \text{softmax}(\text{Attention Scores}^{(1)})
$$
$$
\text{Attention Output}^{(1)} = \text{Attention Weights}^{(1)} \cdot V^{(1)}
$$

**Head 2:**
$$
\text{Attention Scores}^{(2)} = Q^{(2)} K^{(2)T}, \quad \text{Attention Weights}^{(2)} = \text{softmax}(\text{Attention Scores}^{(2)})
$$
$$
\text{Attention Output}^{(2)} = \text{Attention Weights}^{(2)} \cdot V^{(2)}
$$

###### 5. **Concatenating the Outputs**

The outputs from each head are concatenated:

$$
\text{Concat Output} = \begin{bmatrix}
\text{Attention Output}^{(1)} \\
\text{Attention Output}^{(2)}
\end{bmatrix}
$$

If each head's output is $6 \times 4$, the concatenated output will be $6 \times 8$.

###### 6. **Final Linear Transformation**

The concatenated output is then transformed by a final linear layer to produce the final multi-head attention output. This final layer has a weight matrix $W_O$ of size $8 \times 8$:

$$
\text{Final Output} = \text{Concat Output} \cdot W_O
$$

##### Summary

1. **Input Representation (X)**: $6 \times 8$
2. **Linear Projections (Q, K, V for each head)**:
   - Head 1: $Q^{(1)}, K^{(1)}, V^{(1)}$ - each $6 \times 4$
   - Head 2: $Q^{(2)}, K^{(2)}, V^{(2)}$ - each $6 \times 4$
3. **Attention Calculation for Each Head**:
   - Head 1: Output $6 \times 4$
   - Head 2: Output $6 \times 4$
4. **Concatenation**: $6 \times 8$
5. **Final Linear Transformation**: $6 \times 8$

##### Key Points

- **Multiple Heads**: Each head independently computes attention, allowing the model to capture different relationships and dependencies.
- **Dimensionality Reduction**: Each head uses smaller dimensions (e.g., 4 instead of 8), ensuring the combined output maintains the original dimension size.
- **Learnable Parameters**: Each head has its own learnable weight matrices ($W_Q, W_K, W_V$), and there is a final weight matrix ($W_O$) for the linear transformation of concatenated outputs.

Multi-headed attention allows the model to simultaneously focus on different parts of the sequence, enhancing its ability to understand complex relationships within the data.



#### Positional Encoding
- Let $d$ be the dimension of the model (i.e., the embedding dimension)
- Let $pos$ be the position of a token in the sequence (starting from 0)
- Let $i$ be the dimension index (from 0 to $d-1$)

The positional encoding $PE$ for a given position $pos$ and dimension $i$ is defined as follows:

$PE_{(pos,2i)} = \sin\left(\frac{pos}{10000^{2i/d}}\right)$

$PE_{(pos,2i+1)} = \cos\left(\frac{pos}{10000^{2i/d}}\right)$

Where:

- $PE_{(pos,2i)}$ is used for even indices
- $PE_{(pos,2i+1)}$ is used for odd indices

This formula creates a unique encoding for each position, with the following properties:

1. It's deterministic and doesn't require training.
2. It can handle sequences of arbitrary length.
3. The encodings for different positions are linearly independent.

To use this encoding:

1. Calculate the positional encoding vector $PE_{pos}$ for each position in your sequence.
2. Add this vector to the corresponding token embedding $E_{pos}$: $X_{pos} = E_{pos} + PE_{pos}$

Where $X_{pos}$ is the final input to the transformer for the token at position $pos$.


Ex. : 
"The cat sat"
d_model  = 4 (typically $d_k = d_v = d_{model} / h$, where $h$ is the number of attention heads.)
Embeddings for "cat": E_1= [0.5, 0.2, -0.3, 0.1]
Positional Encoding for X_1: PE_1 [0.8415, 0.5403, 0.0001, 1.0000]

 X_1 = E_1 + PE_1 






#### ViT


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/coursework/so-se24/gen-ai/practice-67890-important-code/#p10" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



### P10

#### Multi-Headed Self-Attention
```

class SelfAttention2d(nn.Module):

def __init__(

self,

embed_dim: int = 256,

head_dim: int = 32,

value_dim: int = 32,

num_heads: int = 8,

):

  

super().__init__() # Initialize the nn.Module

  

self.embed_dim = embed_dim

self.head_dim = head_dim

self.value_dim = value_dim

self.num_heads = num_heads

  

# single head linear layers

self.q = nn.Linear(embed_dim, head_dim * num_heads, bias = False)

self.k = nn.Linear(embed_dim, head_dim * num_heads, bias = False)

self.v = nn.Linear(embed_dim, value_dim * num_heads, bias = False)

self.out = nn.Linear(value_dim * num_heads, embed_dim, bias = False)

  
  

def forward(self, x: torch.Tensor) -> torch.Tensor:

B, D, H, W = x.shape

print(f'x.shape: {x.shape}')

  

#reshape inputs

x = x.view(B, D, H * W).transpose(1, 2)

print(f'x.shape: {x.shape}')

  
  

#apply linear projections

q = self.q(x)

k = self.k(x)

v = self.v(x)

  

print(f'q.shape: {q.shape}')

print(f'k.shape: {k.shape}')

print(f'v.shape: {v.shape}')

  

# Reshape q, k, v for multi-head attention

q = rearrange(q, 'b n (h d) -> b h n d', h=self.num_heads) # (B, num_heads, H*W, head_dim)

k = rearrange(k, 'b n (h d) -> b h n d', h=self.num_heads) # (B, num_heads, H*W, head_dim)

v = rearrange(v, 'b n (h d) -> b h n d', h=self.num_heads) # (B, num_heads, H*W, value_dim)

  

print(f'q.shape: {q.shape}')

print(f'k.shape: {k.shape}')

print(f'v.shape: {v.shape}')

  
  
  

#compute attention scores

scores = torch.einsum('b h i d, b h j d -> b h i j', q, k)

  

print(f'head_dim: {self.head_dim}')

  

scores = scores / math.sqrt(self.head_dim)

  

print(f'scores.shape: {scores.shape}')

  

#apply softmax

attention = F.softmax(scores, dim = -1)

  

print(f'attention.shape: {attention.shape}')

  

#compute attention output

attn_out = torch.einsum('b h i j, b h j d -> b h i d', attention, v)

print(f'attn_out.shape: {attn_out.shape}')

  

attn_out = rearrange(attn_out, 'b h n d -> b n (h d)')

print(f'attn_out.shape: {attn_out.shape}')

  
  
  

#attn_out = attn_out.transpose(1, 2).view(B, D, H, W)

  

#print(attn_out[0][0][0])

#print(f'attn_out.shape: {attn_out.shape}')

#print(attn_out[0][0][0])

  
  

out = self.out(attn_out)

print(f'out.shape: {out.shape}')

  
  

out = out.transpose(1, 2).view(B, D, H, W)

print(f'out.shape: {out.shape}')

  

print(out[1][0][0])

  
  

return out


```



#### ViT
```

class ResidualModule(nn.Module):

def __init__(

self,

inner_module: nn.Module

):

super().__init__()

self.inner_module = inner_module

  

def forward(self, x: torch.Tensor) -> torch.Tensor:

return x + self.inner_module(x)

  

class FeedForwardBlock(nn.Module):

def __init__(self, hidden_size: int, mlp_size: int, p_dropout: float):

super().__init__()

self.linear1 = nn.Linear(hidden_size, mlp_size)

self.dropout1 = nn.Dropout(p_dropout)

self.linear2 = nn.Linear(mlp_size, hidden_size)

self.dropout2 = nn.Dropout(p_dropout)

self.activation = nn.GELU()

  

def forward(self, x: torch.Tensor) -> torch.Tensor:

x = self.linear1(x)

x = self.dropout1(x)

x = self.activation(x)

x = self.linear2(x)

x = self.dropout2(x)

return x

  

class SelfAttentionTransformerBlock(nn.Module):

def __init__(self, hidden_size: int, mlp_size: int, n_heads: int, p_dropout: float):

super().__init__()

self.norm1 = nn.LayerNorm(hidden_size)

self.attention = nn.MultiheadAttention(hidden_size, n_heads, dropout=p_dropout, batch_first=True)

self.norm2 = nn.LayerNorm(hidden_size)

self.ffn = FeedForwardBlock(hidden_size, mlp_size, p_dropout)

  

def forward(self, x: torch.Tensor) -> torch.Tensor:

residual = x

x = self.norm1(x)

x, _ = self.attention(x, x, x)

x = residual + x

residual = x

x = self.norm2(x)

x = self.ffn(x)

x = residual + x

return x

  

  

class VisionTransformer(nn.Module):

def __init__(

self,

in_channels: int = 3,

patch_size: int = 4,

image_size: int = 32,

layers: int = 6,

hidden_size: int = 256,

mlp_size: int = 512,

n_heads: int = 8,

num_classes: int = 10,

p_dropout: float = 0.2,

):

super().__init__()

  

self.patch_size = patch_size

self.hidden_size = hidden_size

num_patches = (image_size // patch_size) ** 2

patch_dim = in_channels * patch_size * patch_size

self.patch_embed = nn.Linear(patch_dim, hidden_size)

self.cls_token = nn.Parameter(torch.randn(1, 1, hidden_size))

self.pos_embed = nn.Parameter(torch.randn(1, num_patches + 1, hidden_size))

self.dropout = nn.Dropout(p_dropout)

self.transformer_blocks = nn.Sequential(*[

SelfAttentionTransformerBlock(hidden_size, mlp_size, n_heads, p_dropout)

for _ in range(layers)

])

self.norm = nn.LayerNorm(hidden_size)

self.head = nn.Linear(hidden_size, num_classes)

  
  

def patchify(self, x: torch.Tensor) -> torch.Tensor:

"""Takes an image tensor of shape (B, C, H, W) and transforms it to a sequence of patches (B, L, D), with a learnable linear projection after flattening,

and a standard additive positional encoding applied. Note that the activations in (Vision) Transformer implementations are

typically passed around in channels-_last_ layout, different from typical PyTorch norms.

  

Args:

x (torch.Tensor): Input tensor of shape (B, C, H, W)

  

Returns:

torch.Tensor: Embedded patch sequence tensor with positional encodings applied and shape (B, L, D)

"""

B, C, H, W = x.shape

x = x.reshape(B, C, H // self.patch_size, self.patch_size, W // self.patch_size, self.patch_size)

x = x.permute(0, 2, 4, 1, 3, 5).contiguous()

x = x.view(B, -1, C * self.patch_size * self.patch_size)

x = self.patch_embed(x)

cls_tokens = self.cls_token.expand(B, -1, -1)

x = torch.cat((cls_tokens, x), dim=1)

x = x + self.pos_embed

x = self.dropout(x)

return x

def forward(self, x: torch.Tensor) -> torch.Tensor:

"""Takes an image tensor of shape (B, C, H, W), applies patching, a standard ViT and then an output projection of the CLS token

to finally create a class logit prediction of shape (B, N_cls)

  

Args:

x (torch.Tensor): Input tensor of shape (B, C, H, W)

  

Returns:

torch.Tensor: Output logits of shape (B, N_cls)

"""

x = self.patchify(x)

x = self.transformer_blocks(x)

x = self.norm(x)

x = x[:, 0] # Use only the CLS token

x = self.head(x)

return x

```




</div></div>



#### VQGAN

![Screenshot 2024-07-14 at 16.04.28.png](/img/user/Attachments/Screenshot%202024-07-14%20at%2016.04.28.png)
Steps
1.	Encoding:
	•	The input image is encoded into feature maps by the CNN encoder  E .
	2.	Quantization:
	•	The continuous feature maps are quantized using a vector quantizer that maps them to the nearest vectors in the codebook, resulting in discrete latent codes  \mathbf{z_q} .
		e.g. token "1" might represent a patch of fur, "42" a dog's eye, "94" part of the background, etc.
	3.	Decoding:
	•	The discrete latent codes are decoded back into an image by the CNN decoder  G .
	4.	Discrimination:
	•	The generated image is then evaluated by the patch-wise discriminator  D , which determines if the patches of the image look realistic.
	5.	Loss Computation:
	•	The LPIPS loss ensures that the generated image is perceptually similar to the original image.
	•	The adversarial loss drives the generator to produce images that can fool the discriminator, enhancing the realism of the generated images.


#### Taming Transformers

VQGAN + Transformers
![Screenshot 2024-07-14 at 16.10.37.png](/img/user/Attachments/Screenshot%202024-07-14%20at%2016.10.37.png)

What does the transformer do here? 
- Token Sequence:
    - These tokens are arranged in a 2D grid, then flattened into a sequence
    - Sequence example: [1, 42, 94, 1, 60, 1, 22, 3, 1, ...] (representing: fur, eye, ear, fur, nose, fur, grass, sky, fur, ...)
- Transformer Input:
    - Each token is converted to an embedding vector
    - Positional encoding is added to maintain spatial information
- Transformer Processing:
    - Self-attention mechanisms allow the model to relate different parts of the image
    - For example, it might learn that eyes (token 42) often appear in pairs, or that fur (token 1) is usually surrounding facial features
- Autoregressive Prediction:
    - The Transformer predicts the next token in the sequence
    - For instance, after seeing [fur, eye, ear], it might predict a high probability for another fur token or a nose token
- Transformer Output:
    - For each position, the Transformer outputs a probability distribution over all possible tokens
    - Example output for the next token: 70% chance of fur (token 1) 20% chance of nose (token 60) 5% chance of eye (token 42) 5% distributed among other tokens
- Token Selection:
    - Based on these probabilities, a token is selected (either the most probable or - - sampled)
    - This process continues until the entire sequence is generated or completed
- Image Reconstruction:
    - The generated sequence of tokens is sent back to the VQGAN decoder
    - The decoder maps each token back to image features: Token 1 → Patch of fur texture Token 42 → Dog's eye Token 94 → Ear shape
    - These features are combined to reconstruct the full image
- Final Output:
    - A coherent dog image is produced, with the global structure (arrangement of eyes, ears, nose) guided by the Transformer, and local details (fur texture, eye shape) handled by the VQGAN