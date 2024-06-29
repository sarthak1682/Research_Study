---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/tensors/","noteIcon":""}
---

---
def.
A tensor is a mathematical object that describes linear relations between vectors, scalars, and other tensors. It generalizes concepts like scalars (0th order tensors), vectors (1st order tensors), and matrices (2nd order tensors) to higher dimensions.


tensor fields
def. 
A tensor field is a mathematical entity that assigns a tensor to every point in a space. It's essentially a function that maps each point in a space to a tensor.

Ex.
0th order tensor (scalar):
    - Temperature at a point
1st order tensor (vector):
- Velocity of a moving object
Higher order tensors:
- Riemann curvature tensor (4th order) in general relativity


context in ML with examples
Input data tensors:

- Images: A color image can be represented as a 3rd order tensor
    - Dimensions: (height, width, color_channels)    - Example: A 224x224 RGB image would be a tensor of shape (224, 224, 3)