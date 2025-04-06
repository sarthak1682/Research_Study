---
{"dg-publish":true,"permalink":"/coursework/so-se24/gen-ai/ch-3-netw-vis-and-understanding/","noteIcon":""}
---

---
#### Visualizing what models have learned

##### Vis. Filters

![Screenshot 2024-07-13 at 15.00.00.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2015.00.00.png)






##### Vis. Final Layer Feat.


![Screenshot 2024-07-13 at 15.00.27.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2015.00.27.png)
Last Layer: 
1. Run the net on many Images, get the feat. Vectors
2. Test Image -> Show Nearest Neighbours

Last Layer: Dim Reduction
	From 4096 to 2 through PCA/t-SNE


#### Understanding Input Pixels

##### Id. imp. Pixels


Maximally Activating Patches
1. Pick a Layer (conv5: 128x13x13), a channel (result of a filter)" 17/128
2. Pass many Images, record Values of a channel
3. Extract the regions (patches) from the input images that maximally activate the chosen filter in the specified layer and channel.


Saliency via Occlusion
	Mask part of the Image before feeding it to the CNN
	Change in Prob
##### Saliency via BackProp

What's going on? 
	Compute Gradient: $\frac{dS_c}{dI_{i,j}}$ (class score wrt pixel i, j) ( how much a small change in each pixel will affect the class score.)
	Take the abs value of the Grad.
	Take the Max over RGB Channels

![Screenshot 2024-07-13 at 15.27.42.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2015.27.42.png)

Uncovering Biases
![Screenshot 2024-07-13 at 15.27.57.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2015.27.57.png)

##### Guided BackProp to Generate Images

What's it about? 
	modify the backward pass to filter out negative gradients, which can result in clearer and more interpretable visualizations of what features the network has learned to identify

How to do it? 
	• If the gradient coming from the deeper layer is positive, and the activation from the forward pass is positive, the gradient is allowed to pass through.
	• If either the gradient or the activation is negative, the gradient is set to zero.


![Screenshot 2024-07-13 at 15.37.51.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2015.37.51.png)



##### Gradient Ascent for Vis. Feat. 

What is about?
	Generate a synthetic Image that maximally activates a neuron. 
	 understand what patterns in the input image cause certain neurons to activate strongly.

How to do it? 
	1.	Choose a Layer and Neuron: Select a layer and a specific neuron within that layer whose activation you want to maximize. Neurons deeper in the network capture more complex and abstract features.
	2.	Define a Loss Function: Define a loss function that reflects the objective of maximizing the activation of the chosen neuron. A common choice is to maximize the mean activation of the neuron in the chosen layer. The loss function ( L ) typically looks like:

	$L = \text{mean}(f_i)$ 

where  f_i  is the activation of the neuron of interest in the chosen layer.
	3.	Gradient Calculation: Compute the gradient of the loss function with respect to the input image pixels. This gradient indicates how the input image should be modified to increase the activation of the chosen neuron.
	4.	Update the Input Image: Update the input image pixels in the direction that maximizes the loss function (i.e., increase the activation of the neuron). This update is done iteratively using:

$x_{\text{new}} = x_{\text{old}} + \alpha \cdot \text{sign}(\nabla_x L)$

Here,  $x_{\text{new}}$  and  $x_{\text{old}}$  are the new and current versions of the input image,  $\alpha$  is a small step size to control the magnitude of changes, and  $\nabla_x L$  is the gradient of the loss function with respect to the input image pixels.
	5.	Iteration: Repeat the process for several iterations or until the activation of the chosen neuron reaches a desired level or stabilizes.



#### Upconv. and Generator Netw.

Upsampling? 
	the process of increasing the spatial dimensions (resolution) of an image or a feature map

Transp_Conv?
	or  (Fractionally Strided Convolution): applies a learned filter to upsample the feature map. It can learn to upsample while simultaneously learning to denoise or deblur, making it useful in tasks like image super-resolution.

Upconv.?
combines convolutional and upsampling layers to learn to upsample feature maps

###### U-Net
![Screenshot 2024-07-13 at 16.40.24.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2016.40.24.png)

1.  Contracting Path (Encoder) : normal stuff
2. Bottleneck: Repr. in its most abstract form
3. Decoder: 
	1. **Upconvolution (Transpose Convolution)**: The expanding path begins with upconvolutional layers, also known as transpose convolutions or deconvolutions. These layers upsample the feature maps back to the original input image resolution.
	2. **Concatenation and Convolution**: At each step of the decoder, the upsampled feature maps from the previous layer are concatenated with the corresponding feature maps from the contracting path (encoder). This allows the network to recover spatial information lost during the contracting path.
	3.  **Convolutional Blocks**: After concatenation, several convolutional layers are applied to process the combined feature maps. Each convolutional layer is followed by ReLU activation.
	4. Final Layer:: The final layer of the network is a 1x1 convolutional layer that produces the segmentation mask.


What's a Mask? 
	a **mask** refers to an image where each pixel value indicates the class or category of the corresponding pixel in the input image



#### Adv. Attacks

How to? 
	Start from an arbitrary image, pick an arb. class, modify the img to max the class, repeat until the net is fooled
#### Style Transfer

##### Feat. Inv.

Goal? 
	Find a new img that: 
	- Matches a given CNN feature vector
	- Looks "natural" (achieved through image prior regularization)

How to? 
	- Start with a given CNN feature vector (Φ0) for an image.
	- Use optimization techniques to find an image (x) that minimizes the objective function.
	- The resulting image (x*) should have features closely matching the given vector and appear natural due to the regularization.



##### Deep Dream

The Enhancement Step
	The algorithm takes layer activations (of a chosen layer ofc) and amplifies them
How? 
	- Let's denote our input image as I and the activation of a particular layer in the network as A(I).
	- We want to modify I to maximize A(I). This is done through gradient ascent.
	- The gradient of A with respect to I, ∇I A(I), tells us how to change I to increase A.
	- The update step can be expressed as: I' = I + η * ∇I A(I) Where:
		- I' is the updated image
		- η (eta) is the learning rate or step size

![Screenshot 2024-07-13 at 17.05.46.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2017.05.46.png)

##### Texture Synthesis

Q? 
	Given a sample patch of some texture, generate a bigger image of the same texture


![Screenshot 2024-07-13 at 17.06.36.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2017.06.36.png)


kNNs?
- Input: An example texture image is provided as input.
- Patch extraction: The algorithm divides the input texture into small overlapping patches.
- Synthesis process:
    - Start with a small "seed" region in the output image.
    - Gradually grow the output texture by filling in one pixel or patch at a time.
    - For each new pixel or patch to be synthesized: a. Look at its neighboring pixels that have already been filled. b. Find the most similar neighborhood in the input texture using a nearest neighbor search. c. Copy the corresponding pixel or patch from the input to the output.


Neural Text. Syn. w Gram-Matrix? 
	a) Feature Extraction:
	- Pass the example texture through a pre-trained CNN (often VGG).
	- Extract feature maps from various layers of the network.
	b) Gram Matrix Computation:
	- For each layer's feature maps, compute the Gram matrix: G[i,j] = Σ_k F[i,k] * F[j,k] where F is the feature map, i and j are feature channels, and k iterates over spatial positions.
	c) Texture Generation:
	- Start with a random noise image.
	- Pass this image through the same CNN.
	- Compute Gram matrices for the generated image's feature maps.
	- Define a loss function as the mean squared error between the Gram matrices of the example texture and the generated image.
	- Use gradient descent to update the generated image, minimizing this loss
	![Screenshot 2024-07-13 at 17.14.52.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2017.14.52.png)


##### Neural Style Transfer

![Screenshot 2024-07-13 at 17.24.58.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2017.24.58.png)

- Input Images:
    - Style Image: The "Starry Night" painting by Van Gogh, which provides the artistic style.
    - Content Image: A photograph of a town with buildings near water, which provides the content.
    - Output Image: Starts as random noise and will be gradually optimized.
- Neural Network: The diagram shows a series of layers (represented by colored rectangles), likely from a pre-trained convolutional neural network like VGG.
- Feature Extraction:
    - The style image (ys), content image (yc), and the output image (ŷ) are all passed through this network.
    - Different layers of the network capture different levels of features:
        - Lower layers (left side) capture more basic features.
        - Higher layers (right side) capture more complex, content-specific features.
- Loss Computation: The diagram shows two types of losses being computed:
    - Style Loss: Computed at multiple layers (φ.relu1_2, φ.relu2_2, φ.relu3_3, φ.relu4_3), comparing the style features of the output image to the style image.
    - Content Loss: Computed at a higher layer (φ.relu3_3), comparing the content features of the output image to the content image
- Problems:
	- Requires many backward/forward passes through VGG, very slow!
	- Solution: another NN for style transfer
	- Fast Style Transfer: (instance norm instead of batch norm for better results)

		![Screenshot 2024-07-13 at 17.26.56.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2017.26.56.png)




One Net, Many Styles
	Use conditional instance normalization: learn separate scale and shift params for each style

Before: 
![Screenshot 2024-07-13 at 17.33.30.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2017.33.30.png)

- Input:
    - Content: An image of a flower field 
    - Style set: Multiple artistic images representing various styles
- Network Architecture:
    - An encoder-decoder structure
    - The encoder compresses the content image
    - The decoder generates the stylized output
- Loss Functions:
    - RGB Loss: Compares the output to the content image in color space
    - Perceptual Loss: Uses a pre-trained ImageNet model (fixed, not dependent on style) to compare features of the content and stylized images, helps maintain the content structure but not optimized for style transfer. 
- Adversarial Component:
    - A discriminator (D) is used, introducing an adversarial loss
    - This helps in generating more convincing stylizations
- Output:
    - A stylized version of the content image, maintaining the overall structure but adopting artistic characteristics


After:
![Screenshot 2024-07-13 at 17.34.09.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2017.34.09.png)


![Screenshot 2024-07-13 at 17.35.06.png](/img/user/Attachments/Screenshot%202024-07-13%20at%2017.35.06.png)

SAC Loss:
The loss measures how different the encoded content is after going through the stylization process (G) and being re-encoded (E), compared to the original encoded content.
- A lower loss means the stylized image retains more of the original content structure.
- Unlike the fixed perceptual loss, this new loss is style-dependent.
- The content representation E(content) adapts based on the target style.
- This allows for better preservation of content while being more flexible to different styles.

Transformed Image Loss:
    - Replaces the simple RGB loss from the first image.
    - Uses a transformation T() on both the original and stylized images.
    - This likely allows for more sophisticated comparisons between the content and stylized images.