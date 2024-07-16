---
{"dg-publish":true,"permalink":"/coursework/so-se24/gen-ai/practice-12345-important-code/","noteIcon":""}
---

---

### Utils

```
Convert the crop to grayscale
gray_crop = np.dot(crop[..., :3], [0.2989, 0.5870, 0.1140])

Insert the grayscale patch into the original image
capybara_copy[y:y+256, x:x+256] = np.dstack((gray_crop, gray_crop, gray_crop))

Add a channel dimension
grayscale_image = grayscale_image[:, :, np.newaxis]

Normalize image (the grayscale image that we produced before) to [0, 1] range
image = grayscale_image.astype(np.float32) / 255.0

Remove the channel dimension
gaussian_kernel = np.squeeze(gaussian_kernel, axis=-1)

Swap the Axes to (C, H, W)
tensor_image_swapped = tensor_image.permute(2, 0, 1)

random NumPy array of shape (5,5,1)
x = np.random.rand(5, 5, 1)

Set the weights of the convolutional layer
conv.weight.data = tensor_w


plt.scatter(xtest[:, 0], xtest[:, 1], c=ytest, cmap='viridis', s=10, edgecolors='k')


# Create a grid of points

xx, yy = np.meshgrid(np.arange(x1_min, x1_max, h),

np.arange(x2_min, x2_max, h))

grid = np.c_[xx.ravel(), yy.ravel()]
plt.scatter(grid[:, 0], grid[:, 1], s=1)

```

### P1
#### Conv_Operation

``` 
def conv2d(x, kernel):
	
	"""
	
	Performs a 2D convolution operation with a single kernel.
	
	  
	
	Args:
	
	x (array): the input array of shape (H, W, 1).
	
	kernel (array): the kernel that is convolved over the input.
	
	  
	
	Returns:
	
	out (array): the output array.
	
	"""

	# Get the dimensions of the input and kernel
	
	H, W, _ = x.shape
	
	kH, kW = kernel.shape
	
	  
	
	# Calculate the output dimensions
	
	oH = H - kH + 1
	
	oW = W - kW + 1
	
	  
	
	# Initialize the output array with zeros
	
	out = np.zeros((oH, oW))
	
	  
	
	# Perform the convolution operation, assuming a stride of 1, and no padding
	
	for i in range(oH):
	
		for j in range(oW):
	
			out[i, j] = np.sum(x[i:i+kH, j:j+kW, 0] * kernel)
	
	  
	
	return out



```


#### Gaussian Filter
```
def gaussian_filter(size, mean=0, var=1):

	"""
	
	Returns an isotropic Gaussian filter with.
	
	Args:
	
	size (int): the size of the kernel.
	
	mean (float/int): the mean of the Gaussian.
	
	var (float/int): the variance of the Gaussian.
	
	  
	
	Returns:
	
	f (array): the Gaussian filter of shape (size, size, 1).
	
	"""

	# Create a grid of (x, y) coordinates
	
	x, y = np.meshgrid(np.linspace(-size // 2 + 1, size // 2, size),
	
	np.linspace(-size // 2 + 1, size // 2, size))
	
	  
	
	# Compute the Gaussian filter
	
	f = np.exp(-((x - mean)**2 + (y - mean)**2) / (2 * var)) / (2 * np.pi * var)
	
	  
	
	# Normalize the filter to ensure the sum is 1
	
	f /= np.sum(f)
	
	  
	
	# Reshape the filter to (size, size, 1)
	
	f = f.reshape(size, size, 1)
	
	  
	
	return f

```

##### Laplacian Kernel 

```
Define the Laplacian kernel(s)

laplacian_kernel = np.array([[0, 1, 0], [1, -4, 1], [0, 1, 0]])

laplacian_kernel_1 = np.array([[1, 1, 1], [1, -8, 1], [1, 1, 1]])

laplacian_kernel_2 = np.array([[0.25, 0.5, 0.25], [0.5, -3, 0.5], [0.25, 0.5, 0.25]])

```




#### Theory
Q1: How does it (the laplacian filter) detect the edges?

Q2: What mathematical operation Laplacian filter corresponds to?

  

The (sum of) **second-order partial derivatives** effectively measures how the intensity of the image varies in the vicinity of each pixel, which in turn, helps with **edge-detection** (i.e. whenever there is a zero crossing, an edge gets detected!)




#####  Problems with handcrafted filters
| Problem | Description | How does Deep Learning help? 
|----------|----------|----------|
| Sensitivity to noise | Potential for spurious edges | Robustness (using a lot of data) |
| Limited Repr. | Can't capture high level features | Use CNNs |


### P2

##### KNNs
```
#kneighbours function: This function returns the k nearest neighbours of a given point

def kneighbours(k, point, xtrain):

	distances = []
	
	for i in range(len(xtrain)):
	
	distance = np.linalg.norm(point-xtrain[i]) # One can also implement a custom distance function
	
	distances.append((i, distance))
	
	  
	
	distances.sort(key=lambda x: x[1]) # Sort by distance
	
	return (distances[1:k+1]) # Because the nearest neighbour is the point itself



Library Uses:
knn = KNeighborsClassifier(n_neighbors=k)
knn.fit(xtrain, ytrain)
predicted_label = knn.predict(xt)


```


##### Linear Regression
```
def fit(xtrain, ytrain):

	ones = np.ones((xtrain.shape[0], 1)) # bias
	
	xtrain = np.concatenate([ones, xtrain], axis=1)
	
	  
	
	w_ = (np.linalg.inv(xtrain.T @ xtrain)) @ (xtrain.T @ ytrain)
	
	b_ = w_[0] # Extract bias term from first element
	
	w_ = w_[1:] # Remove bias term from weights

	return w_, b_

  

def predict(xtest, w, b):

	return np.sign(xtest @ w + b)

```


```
def softmax(z):

	exp_z = np.exp(z - np.max(z, axis=1, keepdims=True))
	
	return exp_z / np.sum(exp_z, axis=1, keepdims=True)

  

def cross_entropy_loss(y_pred, y_true):

	return -np.sum(y_true * np.log(y_pred + 1e-9)) / y_true.shape[0]

  

def accuracy(y_pred, y_true):

	y_pred_cls = np.argmax(y_pred, axis=1)
	
	acc = np.mean(y_pred_cls == y_true)
	
	return acc




```
![Screenshot 2024-07-10 at 20.16.14.png](/img/user/Attachments/Screenshot%202024-07-10%20at%2020.16.14.png)


 Gradient for weights
 $$\text{dw} = \frac{1}{m} \mathbf{x}^\top \text{dz} $$

The gradient of biases  \text{db}  is computed by averaging the error (difference between predicted and true outputs) across all samples in the batch

$$  \text{db} = \frac{1}{m} \sum_{i=1}^{m} \text{dz}_{i} $$






### P3

#### Linear Layer
```

class Linear:

	def __init__(self, in_channels, out_channels):
	
		self.in_channels = in_channels
		
		self.out_channels = out_channels
		
		self.weight = torch.randn(in_channels, out_channels) #start with random weights
		
		self.bias = torch.zeros(out_channels) #start with zero bias
		
		self.last_input = None
		
		self.grad_weight = None
		
		self.grad_bias = None
	
	def forward(self, x, remember=False):
	
		if remember:
		
			self.last_input = x
		
		# Linear transformation and adding bias
		
		newx = torch.matmul(x, self.weight) + self.bias
		
		return newx
	
	def backward(self, gradient):
	
		self.grad_weight = torch.matmul(self.last_input.T, gradient) # multiply input with gradient, which is given
		
		self.grad_bias = torch.sum(gradient, axis=0) # sum over all elements
		
		# Calculate the new gradient
		
		newgrad = torch.matmul(gradient, self.weight.T)
		
		return newgrad
	
	def update(self, learning_rate):
	
		self.weight -= learning_rate * self.grad_weight
		
		self.bias -= learning_rate * self.grad_bias

```


#### ReLU

```

class ReLU:

	def __init__(self):

		self.last_input = None

	def forward(self, x, remember=False):

		if remember:
		
			self.last_input = x
		
		# Apply ReLU activation (take the max of 0 and input)
		
		newx = torch.nn.functional.relu(x)
		
		return newx

	def backward(self, gradient):

		# ReLU derivative: 1 for positive values, 0 for negative values
		
		newgrad = torch.where(self.last_input > 0, gradient, torch.zeros_like(gradient)) #create a tensor with the same shape as gradient

  

		return newgrad

	def update(self, learning_rate):

		#we don't have any parameters here

		pass

```



#### SoftMax
```
class Softmax:

	def __init__(self, dim=-1):
	
		self.last_output = None
		
		self.dim = dim
		
	def forward(self, x, remember=False):
		
		x = torch.exp(x-torch.amax(x)) #numerical stable version -> normalize by max(x)
		
		x = x/(torch.sum(x, dim=self.dim, keepdim=True)+1e-12)
		
		if remember:
		
			self.last_output = x
		
		return x
	
	def backward(self, gradient):
	
		jacobian = -self.last_output[:,:,None]*self.last_output[:,None,:] #BxLxL # computes -S(x)ᵢS(x)ⱼ for all i,j pairs.
	
	  
	
	#correct diagonal entries
	
		jacobian += torch.eye(self.last_output.size(-1)).unsqueeze(0)*self.last_output.unsqueeze(-1).repeat(1,1,self.last_output.size(-1))
		 #dds S(x)ᵢ to the diagonal elements, effectively computing S(x)ᵢδᵢⱼ.
		
		return torch.einsum("bj,bji->bi", gradient, jacobian)
	
	def update(self, learning_rate):
	
		#we don't have any parameters here
	
		pass


```


#### CE Loss
```
class CrossEntropyLoss:

	def __init__(self, dim=-1):
	
		self.last_input = None
		
		self.last_ground_truth = None
		
		self.dim = dim
		
	def forward(self, p, y):
	
		#convert y to one hot
		
		one_hot = torch.eye(p.size(-1))[y]
		
		self.last_input = p
		
		self.last_ground_truth = one_hot
		
		losses = -torch.sum(one_hot*torch.log(p), dim=-1)
		
		total_loss = torch.mean(losses)
		
		return total_loss
	
	def backward(self):
	
		return torch.where(self.last_ground_truth==1,-1.0/self.last_input, 0.0)


```

#### MLP
```
class MLP:

	def __init__(self, in_channels=2, hidden_channels=[], out_channels=2):
	
		self.in_channels = in_channels
		
		self.layers = []
		
		if len(hidden_channels)==0:
		
			self.layers.append(Linear(in_channels, out_channels))
		
		else:
		
			self.layers.append(Linear(in_channels, hidden_channels[0]))
		
			self.layers.append(ReLU())
		
		for i in range(len(hidden_channels)-1):
		
			self.layers.append(Linear(hidden_channels[i], hidden_channels[i+1]))
			
			self.layers.append(ReLU())
			
			self.layers.append(Linear(hidden_channels[-1], out_channels))
			
			self.layers.append(Softmax(dim=-1))
			
		self.criterion = CrossEntropyLoss(dim=-1)
	
	def forward(self, x, remember=False):
	
		for layer in self.layers:
		
		x = layer.forward(x, remember=remember)
		
		return x
	
	def backward(self): #calculate gradients
	
		grad = self.criterion.backward()
		
		for layer in reversed(self.layers):
		
		grad = layer.backward(grad)
		
		def update(self, learning_rate): #update each layer via gradient descent
		
		for layer in self.layers:
		
		layer.update(learning_rate)
	
	def training_step(self, x, y, learning_rate):
	
		probabilities = self.forward(x, remember=True) #store inputs for backward pass!
		
		loss = self.criterion.forward(probabilities, y)
		
		self.backward() #calculate gradients
		
		self.update(learning_rate) #update using gradient descent
		
		return loss
	
	

```
### P4\
```
class Net(nn.Module):

def __init__(self):

############ your code here ############

  

	super(Net, self).__init__() # there will be attribute error otherwise, inherit from nn.Module
	
	#input_shape = (32, 32, 3) # 32x32x3
	
	self.conv1 = nn.Conv2d(in_channels= 3, out_channels= 6, kernel_size= 5, stride= 1, padding= 0)
	
	self.relu1 = nn.ReLU()
	
	self.pool1 = nn.MaxPool2d(kernel_size= 2, stride= 2)
	
	  
	
	self.conv2 = nn.Conv2d(in_channels= 6, out_channels= 16, kernel_size= 5, stride= 1, padding= 0)
	
	self.relu2 = nn.ReLU()
	
	self.pool2 = nn.MaxPool2d(kernel_size= 2, stride= 2)
	
	  
	
	self.fc1 = nn.Linear(in_features= 16*5*5, out_features= 120) # gotta flatten here
	
	self.relu3 = nn.ReLU()
	
	  
	
	self.fc2 = nn.Linear(in_features= 120, out_features= 84)
	
	self.relu4 = nn.ReLU()
	
	  
	
	self.fc3 = nn.Linear(in_features= 84, out_features= 10)

  
  

############ end of your code############

def forward(self, x):

############ your code here ############

  

	x = self.pool1(self.relu1(self.conv1(x)))
	
	x = self.pool2(self.relu2(self.conv2(x)))
	
	  
	
	x = x.reshape(-1, 16*5*5) # effects of flattening in init
	
	  
	
	x = self.relu3(self.fc1(x))
	
	x = self.relu4(self.fc2(x))
	
	x = self.fc3(x)
	
	  
	
	############ end of your code############
	
	return x



```


### P5

```
def deep_dream(md, image_array, layer_numbers, num_optim_steps=20, learning_rate=0.1, weight_decay=1e-5, tv_weight=0.001):

	# Process image and return variable
	
	processed_image = preprocess_image(image_array, False)
	
	processed_image = torch.tensor(processed_image, device=device).float()
	
	processed_image.requires_grad = True
	
	# print the processed image
	
	#plt.imshow(processed_image.detach().cpu().numpy().transpose(1, 2, 0))
	
	#plt.show()
	
	optimizer = Adam([processed_image], lr=learning_rate, weight_decay=weight_decay)
	
	  
	  
	
	for i in range(1, num_optim_steps):
	
		optimizer.zero_grad()
		
		x = processed_image
		
		l = []
		
		for index, layer in enumerate(md):
		
		x = layer(x)
		
		if index in layer_numbers:
		
		l.append(x)
		
		#print(len(activations_l2))
		
		#print(activations_l2[0].shape)
		
		l = sum([torch.mean(torch.norm(act, 2)) for act in l])
		
		l = l + total_variation_loss(processed_image, tv_weight)
		
		#loss = sum([torch.mean(torch.norm(act, 2)) for act in activations_l2])
		
		#loss = loss + total_variation_loss(processed_image, tv_weight)
		
		  
		
		l.backward()
		
		optimizer.step()
		
		# Log the total loss value
		
		#print(f'Step {i}, Total Loss: {loss_activation_total.item()}')
		
		optimized_image = recreate_image(processed_image)
	
	  
	
	return optimized_image


```



