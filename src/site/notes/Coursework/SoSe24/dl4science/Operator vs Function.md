---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/operator-vs-function/","noteIcon":""}
---

---
[quantum mechanics - What is the difference between a functional and an operator? - Physics Stack Exchange](https://physics.stackexchange.com/questions/284450/what-is-the-difference-between-a-functional-and-an-operator)

---
Answer 1:
Loosely, an operator (acting on a function space) **takes functions to functions** (e.g., 𝑓(𝑥) to −𝑖𝑓′(𝑥)). On the other hand, a functional takes **functions to numbers** (think about a certain integral, or the derivative evaluated at a certain point).

Answer 2:
**Operators** act between vector spaces, they **take a vector (in the mathematical sense) as input and give a vector as the output**. Of course, those two vector spaces don't have to be the same, in general. Momentum operator 𝑝̂ acts on a function, which is a vector in the mathematical sense, and outputs another function.

**Functionals** are also operators. Again, they **take an element from a vector space as input _but_ they give a scalar as the output**. By scalar, I mean **an element of the underlying field** (in the mathematical sense) of the original vector space. In other words, the field of coefficients of linear combinations in the vector space. 𝑝̂ is not a functional because it doesn't give a number, it gives a function. Physicists often use sloppy language and call functionals _functions of functions_. It's because, in practice, they usually are, they take a function and output a number. A simple example would be the Hamiltonian, it takes 𝑞(𝑡) and 𝑝(𝑡) as inputs and outputs a number.

Answer 3:
Diff. operator is not a functional. 