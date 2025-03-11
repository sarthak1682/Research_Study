---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dl4nlp/notes/important-code/","noteIcon":""}
---

---


```
class BiLSTM(nn.Module):

def __init__(self, vocab_size, embedding_dim, rnn_size, hidden_size, dropout):

super().__init__()

  

# embedding layer

self.embedding = nn.Embedding(vocab_size, embedding_dim)

  

# dropout layer

self.dropout = nn.Dropout(dropout)

  

# Bidirectional LSTM layer

self.lstm = nn.LSTM(

input_size=embedding_dim,

hidden_size=rnn_size,

bidirectional=True,

batch_first=True

)

  

# linear layer for dimensionality reduction

self.linear1 = nn.Linear(rnn_size * 2, hidden_size)

self.relu = nn.ReLU()

  

# a second linear layer for classification output

self.linear2 = nn.Linear(hidden_size, 2)

  
  
  

def forward(self, seq, lengths): #describe the flow of information

  

embedded = self.dropout(self.embedding(seq))

  

# packing for LSTM

packed_embedded = nn.utils.rnn.pack_padded_sequence(embedded, lengths, batch_first=True, enforce_sorted=False)

  

#pass it thru

packed_output, (hidden, cell) = self.lstm(packed_embedded)

  

# unpack to get the padded sequences

output, _ = nn.utils.rnn.pad_packed_sequence(packed_output, batch_first=True)

  

#mean pooling

pooled_output = torch.mean(output, dim=1)

  

# first linear + relu

hidden_output = self.relu(self.linear1(pooled_output))

  

# apply dropout

hidden_output = self.dropout(hidden_output)

  

# final linear layer

logits = self.linear2(hidden_output)

  

return logits




```


1. **Embedding** → Convert input tokens to dense vectors.
2. **Packing** → Ignore padding for efficient LSTM computation.
3. **LSTM Processing** → Extract sequential representations.
4. **Unpacking** → Convert packed output back to padded format.
5. **Mean Pooling** → Aggregate information across time steps.
6. **Feedforward Layers** → Apply a fully connected network with dropout and non-linearity.
7. **Output Logits** → Final predictions.


---


```
class MultiHeadAttention(nn.Module):

def __init__(self, emb_dim, num_heads):

super().__init__()

#storing the parameters

self.emb_dim = emb_dim #size of the feature vectors used to represent each word or token in the input sequence.

self.num_heads = num_heads

self.head_dim = emb_dim // num_heads

  
  

#assert condition, error message

assert self.head_dim * num_heads == emb_dim, "Embedding dimension must be divisible by number of heads"

#linear layers as specified

self.q_linear = nn.Linear(emb_dim, num_heads * self.head_dim)

self.k_linear = nn.Linear(emb_dim, num_heads * self.head_dim)

self.v_linear = nn.Linear(emb_dim, num_heads * self.head_dim)

#output layer

self.out_linear = nn.Linear(num_heads * self.head_dim, emb_dim)

def forward(self, query, key, value, mask=None):

batch_size = query.size(0)

q_seq_len = query.size(1)

k_seq_len = key.size(1)

v_seq_len = value.size(1)

#linear projections

Q = self.q_linear(query) # (batch_size, q_seq_len, num_heads * head_dim)

K = self.k_linear(key) # ""

V = self.v_linear(value) # ""

#reshape Q, K, V to separate num_heads dimension

#modfied shape: (batch_size, num_heads, seq_len, head_dim)

Q = Q.view(batch_size, q_seq_len, self.num_heads, self.head_dim).transpose(1, 2)

K = K.view(batch_size, k_seq_len, self.num_heads, self.head_dim).transpose(1, 2)

V = V.view(batch_size, v_seq_len, self.num_heads, self.head_dim).transpose(1, 2)

#computing SDPA

key_out = torch.matmul(Q, K.transpose(-2, -1)) # (batch_size, num_heads, q_seq_len, k_seq_len)

#scale by sqrt(d_k)

key_out = key_out / torch.sqrt(torch.tensor(self.head_dim, dtype=torch.float32))

#Mask...

if mask is not None:

key_out = key_out.masked_fill(mask == 0, -1e20)

#softmax

attention = F.softmax(key_out, dim=-1)

#apply attention to V

out = torch.matmul(attention, V) # (batch_size, num_heads, q_seq_len, head_dim)

#eshape + concat

out = out.transpose(1, 2).contiguous() # (batch_size, q_seq_len, num_heads, head_dim)

out = out.view(batch_size, q_seq_len, self.num_heads * self.head_dim) # (batch_size, q_seq_len, emb_dim)

#final linear layer

out = self.out_linear(out)

return out







```