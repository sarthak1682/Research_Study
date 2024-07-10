---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/the-main-update/","noteIcon":""}
---

---
![Screenshot 2024-07-01 at 15.17.35.png](/img/user/Attachments/Screenshot%202024-07-01%20at%2015.17.35.png)

- For each atom 'a' in the molecule:
    - It starts with a self-interaction term (θH(lo) amo). (theta is a learned scalar)
    - It then considers all neighboring atoms 'b'.
- For each neighbor:
    - It applies a filter function F  to the relative position (xb - xa). (it's a rotationally eq. filter)
    - This filter combines a learnable radial part with spherical harmonics.
	    - with a (learned) radial part R, which is any polynomial of degree ≤ D, and the real spherical harmonics Ylm with degree l and order m.
	    - The spherical harmonics are the basis for the Fourier transformation of functions on the sphere, analogously to sine waves for functions on R
- The filter output is then combined with the input representation of the neighboring atom (H (li) bmi).
- These combinations are summed over all degrees and orders of the filter and input representations.
- The Clebsch-Gordan coefficients ensure that this summation results in a valid SO(3) representation for the output.They arise from decomposing the tensor product of two input SO(3) representations (the filter and input representations) into a sum of output representations

Universality of Polynomial Regression
The universality of polynomial regression refers to its capability to approximate any continuous function to arbitrary precision within a given interval, given a sufficiently high degree of polynomial.

**For any continuous function ff defined on a closed interval [a,b][a,b] of the real numbers RR and for any ϵ>0ϵ>0, there exists a polynomial P(x)P(x) such that** ∣f(x)−P(x)∣<ϵfor all x∈[a,b].∣f(x)−P(x)∣<ϵfor all x∈[a,b].

In simpler terms, given any continuous function ff and any small positive number ϵϵ, we can find a polynomial P(x)P(x)that approximates f(x)f(x) arbitrarily closely (within ϵϵ) on the interval [a,b][a,b].

