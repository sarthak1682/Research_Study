---
{"dg-publish":true,"permalink":"/coursework/so-se24/gen-ai/practice-67890-important-code/","noteIcon":""}
---

---

#### P6
```
class Autoencoder(nn.Module):

  

	def __init__(self, input_shape=(28, 28)):
	
		super(Autoencoder, self).__init__()
		
		self.encoder = nn.Sequential(
		
			#nn.Flatten(), # Flatten the input tensor
			
			  
			
			# Linear with 128 neurons and then ReLU
			
			nn.Linear(784, 128),
			
			nn.ReLU(True),
			
			  
			
			# Linear with 64 neurons and then ReLU
			
			nn.Linear(128, 64),
			
			nn.ReLU(True),
			
			  
			
			# Linear with 32 neurons and then ReLU
			
			nn.Linear(64, 32),
			
			nn.ReLU(True),
			
			  
			
			# Linear with 16 neurons and then ReLU
			
			nn.Linear(32, 16),
			
			nn.ReLU(True),
			
			  
			
			# Linear with 8 neurons and then ReLU
			
			nn.Linear(16, 8),
			
			nn.ReLU(True),
		
		  
		
		)
	
		self.decoder = nn.Sequential(
		
			# Linear with 8 neurons and then ReLU
			
			nn.Linear(8, 8),
			
			nn.ReLU(True),
			
			  
			
			# Linear with 32 neurons and then ReLU
			
			nn.Linear(8, 32),
			
			nn.ReLU(True),
			
			  
			
			# Linear with 64 neurons and then ReLU
			
			nn.Linear(32, 64),
			
			nn.ReLU(True),
			
			  
			
			# Linear with 128 neurons and then ReLU
			
			nn.Linear(64, 128),
			
			nn.ReLU(True),
			
			  
			
			# Linear with 784 neurons and then Tanh
			
			nn.Linear(128, 784),
			
			nn.Tanh()
		
	  
	  
	  
	
	)
	
	  

	def forward(self, x):
	
		x = self.encoder(x)
		
		x = self.decoder(x)
		
		  
		
		return x



```



```
  

class Conv_Autoencoder(nn.Module):

	def __init__(self):
	
		super(Conv_Autoencoder,self).__init__()
		
		self.encoder = nn.Sequential(
		
			nn.Conv2d(1,4,kernel_size=5),
			
			nn.ReLU(True),
			
			  
			
			nn.Conv2d(4,8,kernel_size=5),
			
			nn.ReLU(True),
			
			nn.Flatten(),
			
			  
			
			nn.Linear(8 * 20 * 20, 10),
			
			  
			
			nn.Softmax(dim=1)
			
		)
		
		self.decoder = nn.Sequential(
		
			nn.Linear(10, 400),
			
			nn.ReLU(True),
			
			nn.Linear(400, 4000),
			
			nn.ReLU(True),
			
			nn.Unflatten(1, (10, 20, 20)),
			
			nn.ConvTranspose2d(10, 10, kernel_size=5),
			
			nn.ReLU(True),
			
			nn.ConvTranspose2d(10, 1, kernel_size=5),
			
			nn.Tanh()
		
		)
	
	def forward(self, x):
	
		x = x.view(-1, 1, 28, 28)
		
		x = self.encoder(x)
		
		x = self.decoder(x)
		
		x = x.view(-1, 28*28)
		
		return x
	

```



### P7 

```
class VAE(nn.Module):

  

	def __init__(self, num_channels=1, num_classes=10, latent_dim=2, embed_dim=16):
	
	super(VAE, self).__init__()
	
	self.latent_dim = latent_dim
	
	self.embedding = nn.Embedding(num_embeddings=num_classes, embedding_dim=embed_dim)
	
	  
	
	self.encoder = nn.ModuleList([
	
	nn.Conv2d(in_channels=num_channels, out_channels=8, kernel_size=3, stride=2, padding=1),
	
	nn.Conv2d(in_channels=8, out_channels=16, kernel_size=3, stride=2, padding=1),
	
	nn.Conv2d(in_channels=16, out_channels=32, kernel_size=3, stride=2, padding=1),
	
	])
	
	  
	
	self.decoder = nn.ModuleList([
	
	nn.Conv2d(in_channels=32, out_channels=16, kernel_size=3, padding=1),
	
	nn.Conv2d(in_channels=16, out_channels=8, kernel_size=3),
	
	nn.Conv2d(in_channels=8, out_channels=num_channels, kernel_size=3, padding=1),
	
	])
	
	self.fc_latent = nn.Linear(in_features=latent_dim + embed_dim, out_features=512)
	
	  
	
	self.fc_mean = nn.Linear(in_features=512 + embed_dim, out_features=latent_dim)
	
	self.fc_var = nn.Linear(in_features=512 + embed_dim, out_features=latent_dim)
	
	self.leaky_relu = nn.LeakyReLU()
	
	self.sigmoid = nn.Sigmoid()
	
	  
	
	def forward(self, x, y):
	
	"""
	
	Args:
	
	x (tensor): Image(s) of shape [B, C, H, W].
	
	y (tensor): Class label(s) of shape [B,].
	
	  
	
	Returns:
	
	x_recon (tensor): Reconstructed image(s) of shape [B, C, H, W].
	
	mean (tensor): Mean of shape [B, latent_dim].
	
	log_var (tensor): Log variance of shape [B, latent_dim].
	
	"""
	
	mean, log_var = self.encode(x, y)
	
	# Reparameterization Trick
	
	eps = torch.randn(log_var.shape, device=log_var.device)
	
	z = mean + torch.exp(log_var * 0.5) * eps
	
	x_recon = self.decode(z, y)
	
	return x_recon, mean, log_var
	
	  
	
	def encode(self, x, y):
	
	"""
	
	Args:
	
	x (tensor): Image(s) of shape [B, C, H, W].
	
	y (tensor): Class label(s) of shape [B,].
	
	  
	
	Returns:
	
	mean (tensor): Mean of shape [B, latent_dim].
	
	log_var (tensor): Log variance of shape [B, latent_dim].
	
	"""
	
	for layer in self.encoder:
	
	x = layer(x)
	
	x = self.leaky_relu(x)
	
	x = torch.reshape(x, (x.shape[0], -1))
	
	class_embed = self.embedding(y)
	
	# Concat class information
	
	mean = self.fc_mean(torch.cat((x, class_embed), dim=1))
	
	log_var = self.fc_var(torch.cat((x, class_embed), dim=1))
	
	return mean, log_var
	
	  
	
	def decode(self, z, y):
	
	"""
	
	Args:
	
	z (tensor): Latent variable(s) of shape [B, latent_dim].
	
	y (tensor): Class label(s) of shape [B,].
	
	  
	
	Returns:
	
	x (tensor): Reconstructed image(s) of shape [B, C, H, W].
	
	"""
	
	class_embed = self.embedding(y)
	
	# Concat class information
	
	x = self.fc_latent(torch.cat((z, class_embed), dim=1))
	
	x = torch.reshape(x, (-1, 32, 4, 4))
	
	for layer in self.decoder:
	
	x = nn.functional.interpolate(x, scale_factor=2, mode='bilinear', align_corners=True)
	
	x = self.leaky_relu(x)
	
	x = layer(x)
	
	x = self.sigmoid(x)
	
	return x
	
	  
	
	def sample(self, y, device):
	
	"""
	
	Args:
	
	y (int): Class label.
	
	device (torch.device): Which device to use (cuda or cpu).
	
	  
	
	Returns:
	
	(tensor): Image of shape [1, C, H, W].
	
	"""
	
	z = torch.randn((1, self.latent_dim), device=device)
	
	return self.decode(z, torch.tensor([y], device=device))
	
	  
	
	def sample_latent(self, x, y):
	
	"""
	
	Args:
	
	x (tensor): Image(s) of shape [B, C, H, W].
	
	y (tensor): Class label(s) of shape [B,].
	
	  
	
	Returns:
	
	z (tensor): Latent variable(s) of shape [B, latent_dim].
	
	"""
	
	mean, log_var = self.encode(x, y)
	
	# Reparameterization Trick
	
	eps = torch.randn(log_var.shape, device=log_var.device)
	
	z = mean + torch.exp(log_var * 0.5) * eps
	
	return z
	
	
	



```



VAE Loss

```
  

def vae_loss(x, x_recon, mean, log_var, alpha, beta):

	# Reconstruction loss
	
	recon_loss = nn.functional.binary_cross_entropy(x_recon, x, reduction='sum')
	
	# KL divergence loss
	
	kl_loss = -0.5 * torch.sum(1 + log_var - mean.pow(2) - log_var.exp())
	
	return alpha*recon_loss + beta*kl_loss



```


### P8

```
# Define the Generator nd rthe Discriminator

class Generator(nn.Module):

	def __init__(self, num_classes, nz, ngf):
	
		super(Generator, self).__init__()
		
		self.num_classes = num_classes
		
		self.nz = nz
		
		self.ngf = ngf
		
		self.label_emb = nn.Embedding(num_classes, nz)
		
		  
		
		self.main = nn.Sequential(
		
		nn.ConvTranspose2d(nz + num_classes, ngf * 4, 4, 1, 0, bias=False),
		
		nn.BatchNorm2d(ngf * 4),
		
		nn.ReLU(True),
		
		nn.ConvTranspose2d(ngf * 4, ngf * 2, 4, 2, 1, bias=False),
		
		nn.BatchNorm2d(ngf * 2),
		
		nn.ReLU(True),
		
		nn.ConvTranspose2d(ngf * 2, ngf, 4, 2, 1, bias=False),
		
		nn.BatchNorm2d(ngf),
		
		nn.ReLU(True),
		
		nn.ConvTranspose2d(ngf, 1, 4, 2, 1, bias=False),
		
		nn.Tanh()
		
		  
		
		)

  

"""Generator transforms a 228-dimensional vector (noise + class embedding) into a 32x32 single-channel image through a series of transposed convolutions that progressively increase spatial dimensions while decreasing the number of channels.
"""

  

def forward(self, noise, labels):

	batch_size = noise.size(0)
	
	label_embedding = self.label_emb(labels).view(batch_size, self.nz, 1, 1)
	
	input = torch.cat((noise, label_embedding), dim=1)
	
	return self.main(input)





```


```

class Discriminator(nn.Module):

	def __init__(self, num_classes, image_size, ndf):
	
		super(Discriminator, self).__init__()
		
		self.num_classes = num_classes
		
		self.image_size = image_size
		
		self.ndf = ndf
		
		self.label_emb = nn.Embedding(num_classes, num_classes)
		
		self.main = nn.Sequential(
		
		nn.Conv2d(1 + num_classes, ndf, 4, 2, 1, bias=False),
		
		nn.LeakyReLU(0.2, inplace=True),
		
		nn.Conv2d(ndf, ndf * 2, 4, 2, 1, bias=False),
		
		nn.BatchNorm2d(ndf * 2),
		
		nn.LeakyReLU(0.2, inplace=True),
		
		nn.Conv2d(ndf * 2, ndf * 4, 4, 2, 1, bias=False),
		
		nn.BatchNorm2d(ndf * 4),
		
		nn.LeakyReLU(0.2, inplace=True),
		
		nn.Conv2d(ndf * 4, 1, 4, 1, 0, bias=False),
		
		nn.Sigmoid()
	
	)

  

def forward(self, image, labels):

	batch_size = image.size(0)
	
	label_embedding = self.label_emb(labels)
	
	label_embedding = label_embedding.view(batch_size, self.num_classes, 1, 1)
	
	label_embedding = label_embedding.repeat(1, 1, self.image_size, self.image_size)
	
	input = torch.cat((image, label_embedding), dim=1)
	
	return self.main(input).view(-1, 1)


```



### P9

RNNs
```
class VanillaRNN(nn.Module):
	
	def __init__(self, seq_length, input_dim, num_hidden, num_classes, batch_size, device="cpu"):
	
		super(VanillaRNN, self).__init__()
		
		self.seq_length = seq_length
		
		self.input_dim = input_dim
		
		self.num_hidden = num_hidden
		
		self.num_classes = num_classes
		
		self.batch_size = batch_size
		
		self.device = device
		
		self.W_ih = nn.Parameter(torch.randn(num_hidden, input_dim, device=device))
		
		self.W_hh = nn.Parameter(torch.randn(num_hidden, num_hidden, device=device))
		
		self.b_h = nn.Parameter(torch.zeros(num_hidden, device=device))
		
		self.W_ho = nn.Parameter(torch.randn(num_classes, num_hidden, device=device))
		
		self.b_o = nn.Parameter(torch.zeros(num_classes, device=device))
		
	  
	
	def forward(self, x):
	
		# x: (batch_size, seq_length, input_dim)
		
		batch_size = x.size(0)
		
		# Initialize hidden state
		
		h_t = torch.zeros(batch_size, self.num_hidden, device=self.device)
		
		outputs = []
		
		  
		
		for t in range(self.seq_length):
		
		x_t = x[:, t, :] # Get input at time step t: (batch_size, input_dim)
		
		h_t = torch.tanh(x_t @ self.W_ih.T + h_t @ self.W_hh.T + self.b_h)
		
		# Compute output
		
		y_t = h_t @ self.W_ho.T + self.b_o
		
		outputs.append(y_t)
		
		return torch.stack(outputs, dim=1) # (batch_size, seq_length, num_classes)
		


```



```
class LSTM(nn.Module):

	def __init__(self, seq_length, input_dim, num_hidden, num_classes, batch_size, device="cpu"):
	
		super(LSTM, self).__init__()
		
		self.seq_length = seq_length
		
		self.input_dim = input_dim
		
		self.num_hidden = num_hidden
		
		self.num_classes = num_classes
		
		self.batch_size = batch_size
		
		self.device = device
		
		  
		
		# Initialize weights and biases
		
		self.Wgx = nn.Parameter(torch.randn(num_hidden, input_dim).to(device))
		
		self.Wgh = nn.Parameter(torch.randn(num_hidden, num_hidden).to(device))
		
		self.bg = nn.Parameter(torch.zeros(num_hidden).to(device))
		
		  
		
		self.Wix = nn.Parameter(torch.randn(num_hidden, input_dim).to(device))
		
		self.Wih = nn.Parameter(torch.randn(num_hidden, num_hidden).to(device))
		
		self.bi = nn.Parameter(torch.zeros(num_hidden).to(device))
		
		  
		
		self.Wfx = nn.Parameter(torch.randn(num_hidden, input_dim).to(device))
		
		self.Wfh = nn.Parameter(torch.randn(num_hidden, num_hidden).to(device))
		
		self.bf = nn.Parameter(torch.zeros(num_hidden).to(device))
		
		  
		
		self.Wox = nn.Parameter(torch.randn(num_hidden, input_dim).to(device))
		
		self.Woh = nn.Parameter(torch.randn(num_hidden, num_hidden).to(device))
		
		self.bo = nn.Parameter(torch.zeros(num_hidden).to(device))
		
		  
		
		self.Wph = nn.Parameter(torch.randn(num_classes, num_hidden).to(device))
		
		self.bp = nn.Parameter(torch.zeros(num_classes).to(device))
		
	  

	def forward(self, x):
	
		# x shape: (batch_size, seq_length, input_dim)
		
		h = torch.zeros(self.batch_size, self.num_hidden).to(self.device)
		
		c = torch.zeros(self.batch_size, self.num_hidden).to(self.device)
		
		outputs = []
		
		  
		
		for t in range(self.seq_length):
		
		xt = x[:, t, :]
		
		  
		
		# Eq. 4
		
		g = torch.tanh(torch.mm(xt, self.Wgx.t()) + torch.mm(h, self.Wgh.t()) + self.bg) # potential LTM
		
		  
		
		# Eq. 5
		
		i = torch.sigmoid(torch.mm(xt, self.Wix.t()) + torch.mm(h, self.Wih.t()) + self.bi) # potential LTM to remember
		
		  
		
		# Eq. 6
		
		f = torch.sigmoid(torch.mm(xt, self.Wfx.t()) + torch.mm(h, self.Wfh.t()) + self.bf) # %LTM to remember
		
		  
		
		# Eq. 7
		
		o = torch.sigmoid(torch.mm(xt, self.Wox.t()) + torch.mm(h, self.Woh.t()) + self.bo) # % short-term memory to remember
		
		# Eq. 8
		
		c = g * i + c * f # new long-term memory
		
		  
		
		# Eq. 9
		
		h = torch.tanh(c) * o
		
		  
		
		# Eq. 10
		
		p = torch.mm(h, self.Wph.t()) + self.bp
		
		  
		
		outputs.append(p)
		
		  
		
		# Stack outputs for all time steps
		
		return torch.stack(outputs, dim=1)
		
	

```




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


