---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/ml/evidence/","noteIcon":""}
---

---
> [!PDF|255, 208, 0] [[W678_10.pdf#page=62&annotation=1080R|W678_10, p.62]]
> Evidence

1. First Equation: P(S = s) = ∑_h P(S = s|H = h)P(H = h)
- This is the law of total probability

2. Generative AI Application:

- P(H = h) is a simple distribution (like a normal distribution or uniform distribution)
- P(S = s|H = h) is modeled by a neural network (DNN)
- Together they produce P(S = s), which can be a complex distribution

3. Special Deterministic Case:

- When s = f(h), meaning s is determined exactly by h through function f
- P(S = s|H = h) becomes a delta function δ(s - f(h))
- This means the probability is 1 when s equals f(h), and 0 otherwise
- The equation simplifies to summing P(H = h) over all h values where f(h) = s

4. Invertible Case:

- If f(h) can be inverted (meaning you can go backwards from s to h uniquely)
- The inverse function g(s) gives you h = g(s)
- Then P(S = s) = P(H = g(s))
- g(s) is called the encoder (goes from output to hidden state)
- f(h) is called the decoder or generator (goes from hidden state to output)