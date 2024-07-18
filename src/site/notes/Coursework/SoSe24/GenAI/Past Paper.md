---
{"dg-publish":true,"permalink":"/coursework/so-se24/gen-ai/past-paper/","noteIcon":""}
---

---
BatchNorm: Conv vs FC? 
1. Dimensionality:
    - FC networks: BatchNorm is 1D (across features)
    - Conv networks: BatchNorm is 2D or 3D (across channels, preserving spatial dimensions)
2. Parameter Sharing:
    - FC networks: Each neuron has its own scaling and shifting parameters
    - Conv networks: Parameters are shared across spatial dimensions for each channel
3. Spatial Information:
    - FC networks: No spatial information to preserve
    - Conv networks: Preserves spatial information within each channel
4. Computational Efficiency:
    - Conv networks: More efficient as it reduces the number of parameters and computations compared to normalizing each spatial location independently

This difference in application allows BatchNorm to be effective in both types of networks while respecting the structural properties of convolutional layers, particularly the importance of spatial information in feature maps.


```
# Shape: [batch_size, num_features]
x = torch.randn(32, 100)
bn = nn.BatchNorm1d(100)
output = bn(x)


# Shape: [batch_size, channels, height, width]
x = torch.randn(32, 64, 28, 28)
bn = nn.BatchNorm2d(64)
output = bn(x)

```


[Claude](https://claude.ai/chat/c9050761-edae-459b-9823-7d959e239ce1)
[ChatGPT](https://chatgpt.com/share/cb0bd7dc-2314-498d-b279-5472d2e5349d)
