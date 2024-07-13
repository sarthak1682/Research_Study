---
{"dg-publish":true,"permalink":"/coursework/so-se24/gen-ai/practice-1-important-code/","noteIcon":""}
---

---
P1:

#### Utils

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


P2:

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


