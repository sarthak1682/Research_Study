---
{"dg-publish":true,"permalink":"/math/","noteIcon":""}
---

---
We will show that a cpwl function with respect to $\Gamma$ can be represented by a ReLU-network of a certain size.

Strategy: Construct a basis of the space of cpwl functions on $\Gamma$.

**Lemma 4.11:** Let $\Gamma = \text{conv}(\eta_0, \dots, \eta_d)$ be a $d$-simplex. For all $y_0, \dots, y_d \in \mathbb{R}$, there exists a unique $g \in P_1^d$ such that $g(\eta_i) = y_i, \ i = 0, \dots, d$.

**Proof:** Since $\eta_1 - \eta_0, \dots, \eta_d - \eta_0$ is a basis of $\mathbb{R}^d$, there exists a unique $w \in \mathbb{R}^d$ such that

$w^T(\eta_i - \eta_0) = y_i - y_0, \ i=1,\dots,d$.

Then $g(x) := w^T x + (y_0 - w^T \eta_0)$

Satisfies $g(\eta_0) = y_0$

$g(\eta_i) = w^T \eta_i - w^T \eta_0 + y_0 = y_i - y_0 + y_0 = y_i$.

Moreover, for every $g \in P_1^d$ and $\sum_{i=0}^d \alpha_i = 1$

It holds

$g(\sum_{i=0}^d \alpha_i \eta_i) = v^T (\sum_{i=0}^d \alpha_i \eta_i) + z$ $= \sum_{i=0}^d \alpha_i (v^T \eta_i + z) = \sum_{i=0}^d \alpha_i g(\eta_i)$ 

Hence, $g$ is uniquely determined by its values on the nodes. $\square$



vᵀ(∑ αᵢηᵢ) = vᵀ(α₀η₀ + α₁η₁ + ... + α<sub>d</sub>η<sub>d</sub>)
            = vᵀ(α₀η₀) + vᵀ(α₁η₁) + ... + vᵀ(α<sub>d</sub>η<sub>d</sub>)  // Distributivity
            = α₀(vᵀη₀) + α₁(vᵀη₁) + ... + α<sub>d</sub>(vᵀη<sub>d</sub>)  // Scalar Multiplication
            = ∑ αᵢ(vᵀηᵢ)


---
Since $\Omega$ is the union of simplices $\tau \in \mathcal{T}$, every cpwl with respect to $\mathcal{T}$ is uniquely determined through its values at the nodes.

The desired basis consists of cpwl functions $\phi_\eta : \Omega \to \mathbb{R}$ with respect to $\mathcal{T}$ such that

$\phi_\eta(\nu) = \delta_{\eta \nu}$ for all $\nu \in \mathcal{V}$.

Assuming such functions $\phi_\eta, \eta \in \mathcal{T}$, exist, we can write every cpwl function $f: \Omega \to \mathbb{R}$ with $f|_{\partial \Omega} = 0$ as

$f(x) = \sum_{\eta \in \mathcal{V} \cap \Omega^\circ} f(\eta) \phi_\eta(x) \ \forall x \in \Omega$.
$\qquad$ interior of $\Omega$

For the proof of existence of the $\phi_\eta$ (and corresponding bounds on size, width, depth of corresponding ReLU networks) we need to introduce the patch $\omega(\eta)$ of the node $\eta$ as

$\omega(\eta) := \bigcup_{\tau \in \mathcal{T} : \eta \in \tau} \tau$.



---
In order to achieve explicit bounds on size, width, depth we work with certain triangulations.

**Definition 4.12:** A regular triangulation is called *locally convex* if $\omega(\eta)$ is convex for all interior nodes $\eta \in \mathcal{V} \cap \Omega^\circ$.

**Theorem 4.13:** Let $\Omega \subset \mathbb{R}^d$ be compact and $\mathcal{T}$ a locally convex regular triangulation of $\Omega$. Let $f: \Omega \to \mathbb{R}$ be cpwl with respect to $\mathcal{T}$ and $f|_{\partial \Omega} = 0$. Then there exists a ReLU neural net $\Phi: \Omega \to \mathbb{R}$ with $\Phi(x) = f(x)$ for all $x \in \Omega$ such that

$size(\Phi) \leq c_1 d^2 k_\mathcal{T} \# \mathcal{T}$

$width(\Phi) \leq 12(d+1)k_\mathcal{T} \# \mathcal{T}$

$depth(\Phi) \leq \lceil \log_2(k_\mathcal{T}) \rceil + 3$

The constant $c_1 > 0$ is absolute (does not depend on anything).

---

First step: Write a patch as intersection of finitely many half-spaces.

$aff(S) := \{ \sum_{j=1}^u \alpha_j x_j : u \in \mathbb{N}, x_j \in S, \alpha_j \in \mathbb{R}, \sum_{j=1}^u \alpha_j = 1 \}$.

For $\tau \in \mathcal{T}$ and $\eta \in \mathcal{V}(\tau)$

$H_0(\tau, \eta) := aff(V(\tau) \setminus \{\eta\})$ is the affine hyperplane passing


through $V(\tau) \setminus \{\eta\}$.

$H_+(\tau, \eta) := \{x \in \mathbb{R}^d : x \text{ is on the same side of } H_0(\tau, \eta) \text{ as } \eta\} \cup H_0(\tau, \eta)$.

**Lemma 4.14:** Let $\eta$ be an interior node. Then a patch $\omega(\eta)$ is convex if and only if

$\omega(\eta) = \bigcap_{\tau \in \mathcal{T} : \eta \in \tau} H_+(\tau, \eta)$.

**Proof:** Right hand side is finite intersection of convex sets and hence convex itself.

Now assume that $\omega(\eta)$ is convex.
"$\supset$": Suppose $x \notin \omega(\eta)$.

Then $\text{conv}(\{x, \eta\}) \text{ must pass through } \partial \omega(\eta)$.
One can show that

 $\partial \omega(\eta) = \bigcup_{\tau \in \mathcal{T} : \eta \in \tau} \text{conv}(V(\tau) \setminus \{\eta\})$

Hence, there exists $\tau \in \mathcal{T}$ with $\eta \in \tau$ such that $\text{conv}(\{x, \eta\})$ passes through $aff(V(\tau) \setminus \{\eta\}) = H_0(\tau, \eta)$.

Hence $\eta$ and $x$ lie on different sides of $H_0(\tau, \eta)$. This means that $x \notin \bigcap_{\tau \in \mathcal{T} : \eta \in \tau} H_+(\tau, \eta)$, i.e.

$\omega(\eta) \supset \bigcap_{\tau \in \mathcal{T} : \eta \in \tau} H_+(\tau, \eta)$.

"$\subset$": Let $\tau \in \mathcal{T}$ with $\eta \in \tau$ and let $x \notin H_+(\tau, \eta)$. Assume $x \in \omega(\eta)$. By convexity $\text{conv}(\{x\} \cup \tau) \subset \omega(\eta)$.

It follows that there exists a point in $\text{conv}(V(\tau) \setminus \{\eta\})$ which is contained in the interior of $\omega(\eta)$. This contradicts (*).

Hence, $x \notin \omega(\eta)$, i.e.

$\omega(\eta) \subset \bigcap_{\tau \in \mathcal{T} : \eta \in \tau} H_+(\tau, \eta)$. $\square$

---

For $\tau \in \mathcal{T}$ and $\eta \in V(\tau)$ introduce $g_{\tau, \eta} \in P_1^d$ satisfying

$g_{\tau, \eta}(\nu) = \begin{cases} 1 & \text{if } \eta = \nu \\ 0 & \text{if } \eta \neq \nu \end{cases}$ for all $\nu \in V(\tau)$

$g_{\tau, \eta}$ exists and is unique by Lemma 4.11.








----

Proof of Theorem 4.13:

For every interior node $\eta \in \mathcal{V} \cap \Omega^\circ$ we use the representation of Lemma 4.15, i.e., for all $x \in \Omega$

$\phi_\eta(x) = \max\{0, \min_{\tau \in \mathcal{T} : \eta \in \tau} g_{\tau, \eta}(x) \}$.

We can write

$\phi_\eta = \sigma \circ \Phi_{\#\{\tau \in \mathcal{T} : \eta \in \tau\}}^{\text{min}} \circ (g_{\tau, \eta})_{\tau \in \mathcal{T} : \eta \in \tau}$
$\qquad$ parallelization (with shared input)

By Lemma 4.2

$size(\phi_\eta) \leq 2 \left( size\left(\sigma \circ \Phi_{\#\{\tau \in \mathcal{T} : \eta \in \tau\}}^{\text{min}}\right) + size\left((g_{\tau, \eta})_{\tau \in \mathcal{T} : \eta \in \tau}\right) \right)$

$\leq 4 \left( size(\sigma) + size\left(\Phi_{\#\{\tau \in \mathcal{T} : \eta \in \tau\}}^{\text{min}}\right) + 2(d+1) \#\{\tau \in \mathcal{T} : \eta \in \tau\} \right)$
$\qquad$ # of coefficients of $g_{\tau, \eta} \in P_1^d$
$\qquad$ Lemma 4.16
$\leq 4 + 4 \cdot 16 \cdot \#\{\tau \in \mathcal{T} : \eta \in \tau\} + 2(d+1) \#\{\tau \in \mathcal{T} : \eta \in \tau\}$

$\leq 4 + 64 k_\mathcal{T} + 2(d+1)k_\mathcal{T}$

$= 4 + (2d + 68)k_\mathcal{T}$

$depth(\phi_\eta) = depth(\sigma) + depth\left(\Phi_{\#\{\tau \in \mathcal{T} : \eta \in \tau\}}^{\text{min}}\right) + depth\left( (g_{\tau, \eta})_{\tau \in \mathcal{T} : \eta \in \tau} \right) + 2$
$=1 \qquad \qquad \leq \lceil \log_2(k_{\mathcal{T}})\rceil \qquad = 0$

$\leq \lceil \log_2(k_\mathcal{T}) \rceil + 3$

$width(\phi_\eta) \leq 2 \max\{1, 3k_\mathcal{T}\} = 6k_\mathcal{T}$.



We can write $f(x) = \sum_{\eta \in \mathcal{V} \cap \Omega^\circ} \alpha_\eta \phi_\eta(x) = \Phi(x)$. $depth(\Phi) = \max_{\eta \in \mathcal{V} \cap \Omega^\circ} \{ depth(\phi_\eta) \}$

By Lemma 4.3

$size(\Phi) \leq 2 \sum_{\eta \in \mathcal{V} \cap \Omega^\circ} size(\phi_\eta) + \sum_{\eta \in \mathcal{V} \cap \Omega^\circ} \lceil \log_2(k_\mathcal{T}) \rceil \cdot depth(\phi_\eta)$

$\#(\mathcal{V} \setminus \Omega^\circ) \leq (d+1) \#\mathcal{T}$ (each $V(\tau)$ has $d+1$ nodes)

$size(\Phi) \leq 2(4 + (2d+68)k_\mathcal{T}) (d+1) \#\mathcal{T} + (d+1) \#\mathcal{T} \lceil \log_2(k_\mathcal{T}) \rceil$

$\leq c_1 d^2 k_\mathcal{T} \# \mathcal{T}$

$width(\Phi) \leq 2 \sum_{\eta \in \mathcal{V} \cap \Omega^\circ} width(\phi_\eta)$

$\leq 2 \cdot (d+1) \# \mathcal{T} \cdot 6 k_\mathcal{T}$

$\leq 12(d+1)k_\mathcal{T} \#\mathcal{T}$

$\leq \lceil \log_2(k_\mathcal{T}) \rceil + 3$.

---
For the approximation result we introduce the space of Hölder continuous functions of order $s \in (0, 1]$.

$\|f\|_{C^{0,s}(\Omega)} := \sup_{x \in \Omega} |f(x)| + \sup_{\substack{x, y \in \Omega \\ x \neq y}} \frac{|f(x) - f(y)|}{\|x-y\|_2^s}$

$C^{0,s}(\Omega) := \{f: \Omega \to \mathbb{R} \text{ continuous}, \|f\|_{C^{0,s}(\Omega)} < \infty \}$

Note that $C^1(\Omega) \subset C^{0,s}(\Omega)$.


---
# Smooth Functions and Taylor's Theorem

## Definitions and Setup

The notes deal with smooth functions and their Taylor expansions. Let's break down the key components:

### Definition 4.23

For $k \in \mathbb{N}_0$ (non-negative integers), $s \in [0,1]$, and $\Omega \subset \mathbb{R}^d$, we define the norm for functions in $C^{k,s}(\Omega)$ (functions with $k$ continuous derivatives and Hölder continuous $k$-th derivatives with exponent $s$) as:

$$|f|_{C^{k,s}(\Omega)} := \sup_{x \in \Omega} \max_{\alpha \in \mathbb{N}_0^d, |\alpha| \leq k} |D^{\alpha}f(x)| + \sup_{x \neq y \in \Omega} \max_{\alpha \in \mathbb{N}_0^d, |\alpha| = k} \frac{|D^{\alpha}f(x) - D^{\alpha}f(y)|}{|x-y|_2^s}$$

And $C^{k,s}(\Omega) = {f \in C^k(\Omega) : |f|_{C^{k,s}(\Omega)} < \infty}$

### Lemma 4.24 (Taylor's Formula with Remainder)

For $k \in \mathbb{N}_0$, $s \in [0,1]$, $\Omega \subset \mathbb{R}^d$, and $f \in C^{k,s}(\Omega)$, it holds for all $a, x \in \Omega$:

$$f(x) = \sum_{\alpha \in \mathbb{N}_0^d, |\alpha| \leq k} \frac{D^{\alpha}f(a)}{\alpha!}(x-a)^{\alpha} + R_k(x)$$

where $R_k(x)$ is the remainder term that satisfies the bound:

$$|R_k(x)| \leq h^{k+s} \frac{d^{k+s/2}}{k!} |f|_{C^{k,s}(\Omega)}$$

where $h = \max_{i=1,...,d}|a_i - x_i|$ is the maximum coordinate-wise distance.

## The Proof of Lemma 4.24

The proof uses the one-dimensional Taylor formula. For $g \in C^k(\mathbb{R})$, $b,t \in \mathbb{R}$:

$$g(t) = \sum_{j=0}^{k-1} \frac{g^{(j)}(b)}{j!}(t-b)^j + \frac{g^{(k)}(\xi)}{k!}(t-b)^k$$

for some $\xi$ between $b$ and $t$.

### Step 1: Apply the 1D formula to a path between points

Let $g(t) = f(a + t(x-a))$ for $t \in [0,1]$. Then:

- $g(0) = f(a)$
- $g(1) = f(x)$

Using the 1D Taylor formula:

$$f(x) = g(1) = \sum_{j=0}^k \frac{g^{(j)}(0)}{j!} + \frac{g^{(k)}(\xi) - g^{(k)}(0)}{k!}$$

for some $\xi \in [0,1]$.

### Step 2: Express the derivatives of g in terms of f

By the chain rule and multi-index notation:

$$g^{(j)}(t) = \sum_{\alpha \in \mathbb{N}_0^d, |\alpha|=j} \binom{j}{\alpha}D^{\alpha}f(a+t(x-a))(x-a)^{\alpha}$$

This gives us:

$$f(x) = \sum_{\alpha \in \mathbb{N}_0^d, |\alpha| \leq k} \frac{D^{\alpha}f(a)}{\alpha!}(x-a)^{\alpha} + \sum_{\alpha \in \mathbb{N}_0^d, |\alpha| = k} \frac{D^{\alpha}f(a+\xi(x-a))-D^{\alpha}f(a)}{\alpha!}(x-a)^{\alpha}$$
further explanation: 

Let me explain in detail how the chain rule and multi-index notation are used to express the derivatives of the path function.

We defined $g(t) = f(a + t(x-a))$ for $t \in [0,1]$, which gives us a path from point $a$ (when $t=0$) to point $x$ (when $t=1$).

### Applying the Chain Rule

When we differentiate $g$ with respect to $t$, we need to use the chain rule since $g$ is a composition. Let's start with the first derivative:

$$g'(t) = \nabla f(a + t(x-a)) \cdot (x-a)$$

This is the dot product of the gradient of $f$ evaluated at the point $a + t(x-a)$ with the direction vector $(x-a)$.

For the second derivative: $$g''(t) = (x-a)^T \cdot H_f(a + t(x-a)) \cdot (x-a)$$

Where $H_f$ is the Hessian matrix of $f$ (matrix of second partial derivatives).

### Using Multi-Index Notation

This pattern becomes increasingly complex for higher derivatives, which is where multi-index notation becomes valuable. A multi-index $\alpha = (\alpha_1, \alpha_2, ..., \alpha_d)$ is a tuple of non-negative integers where $|\alpha| = \alpha_1 + \alpha_2 + ... + \alpha_d$ represents the total order of differentiation.

For a multi-index $\alpha$, the partial derivative operator is defined as: $$D^\alpha = \frac{\partial^{|\alpha|}}{\partial x_1^{\alpha_1} \partial x_2^{\alpha_2} ... \partial x_d^{\alpha_d}}$$

Now, for the $j$-th derivative of $g$, we use the chain rule and collect terms with the same total order of differentiation:

$$g^{(j)}(t) = \sum_{\alpha \in \mathbb{N}_0^d, |\alpha|=j} \binom{j}{\alpha} D^\alpha f(a+t(x-a))(x-a)^\alpha$$

Where:

- The sum is over all multi-indices $\alpha$ with $|\alpha| = j$
- $\binom{j}{\alpha} = \frac{j!}{\alpha_1! \alpha_2! ... \alpha_d!}$ is the multinomial coefficient
- $(x-a)^\alpha = (x_1-a_1)^{\alpha_1}(x_2-a_2)^{\alpha_2}...(x_d-a_d)^{\alpha_d}$

### Example with Specific Values

For clarity, let's see an example in two dimensions ($d=2$) for $j=2$:

For $j=2$, the multi-indices with $|\alpha| = 2$ are $(2,0)$, $(1,1)$, and $(0,2)$.

Then: $$g^{(2)}(t) = \binom{2}{2,0} D^{(2,0)}f(a+t(x-a))(x_1-a_1)^2 + \binom{2}{1,1} D^{(1,1)}f(a+t(x-a))(x_1-a_1)(x_2-a_2) + \binom{2}{0,2} D^{(0,2)}f(a+t(x-a))(x_2-a_2)^2$$

This equals: $$g^{(2)}(t) = \frac{\partial^2 f}{\partial x_1^2}(a+t(x-a))(x_1-a_1)^2 + 2\frac{\partial^2 f}{\partial x_1 \partial x_2}(a+t(x-a))(x_1-a_1)(x_2-a_2) + \frac{\partial^2 f}{\partial x_2^2}(a+t(x-a))(x_2-a_2)^2$$

### Key Insight

When we evaluate $g^{(j)}(0)$, we get: $$g^{(j)}(0) = \sum_{\alpha \in \mathbb{N}_0^d, |\alpha|=j} \binom{j}{\alpha} D^\alpha f(a)(x-a)^\alpha$$

This is precisely what we need to express the terms in the Taylor expansion: $$\frac{g^{(j)}(0)}{j!} = \sum_{\alpha \in \mathbb{N}_0^d, |\alpha|=j} \frac{D^\alpha f(a)}{\alpha!}(x-a)^\alpha$$

Where we used the identity $\frac{\binom{j}{\alpha}}{j!} = \frac{1}{\alpha!}$.

This elegant relationship allows us to transform the one-dimensional Taylor expansion of $g$ into the multi-dimensional Taylor expansion of $f$, gathering terms with the same order of differentiation and expressing the coefficients in terms of the partial derivatives of $f$.
### Step 3: Bound the remainder term

The remainder term is:

$$R_k(x) = \sum_{\alpha \in \mathbb{N}_0^d, |\alpha| = k} \frac{D^{\alpha}f(a+\xi(x-a))-D^{\alpha}f(a)}{\alpha!}(x-a)^{\alpha}$$

Using the Hölder continuity of $D^{\alpha}f$ for $|\alpha| = k$:

$$|D^{\alpha}f(a+\xi(x-a))-D^{\alpha}f(a)| \leq |f|_{C^{k,s}(\Omega)} |\xi(x-a)|_2^s$$

And we can bound:

$$|R_k(x)| \leq h^k \max_{\alpha \in \mathbb{N}_0^d, |\alpha| = k} \sup_{\xi \in [0,1]} |D^{\alpha}f(a+\xi(x-a))-D^{\alpha}f(a)| \cdot \frac{1}{k!} \sum_{\alpha \in \mathbb{N}_0^d, |\alpha| = k} \binom{k}{\alpha}$$

### Step 4: Apply multinomial theorem and distance bounds

- $\sum_{\alpha \in \mathbb{N}_0^d, |\alpha| = k} \binom{k}{\alpha} = d^k$ (multinomial theorem)
- $|\xi(x-a)|_2^s \leq (\xi \cdot \sqrt{d} \cdot h)^s \leq (\sqrt{d} \cdot h)^s$

This leads to the final bound:

$$|R_k(x)| \leq h^{k+s} \frac{d^{k+s/2}}{k!} |f|_{C^{k,s}(\Omega)}$$

## Relationships Between Function Spaces

The notes also mention that for $0 \leq s \leq t \leq 1$:

$$C^k(\Omega) \supseteq C^{k,s}(\Omega) \supseteq C^{k,t}(\Omega) \supseteq C^{k+1}(\Omega)$$

This shows the hierarchy of smoothness classes, with higher regularity (more derivatives or higher Hölder exponents) resulting in more restricted function spaces.

[Claude](https://claude.ai/chat/806b142e-a792-4774-8a89-0dc27ffc0d02)

---
# Transcription of Mathematical Notes

## Image 1:

$$\leq h^{k+S} \frac{d^{k+\frac{S}{2}}}{h!} |f|_{C^{k,S}(\Omega)}$$

**Theorem 4.25:** Let $\alpha, h \in \mathbb{N}$, $S \in [0,1]$ and $\Omega = [0,1]^d$. For every $f \in C^{h,S}(\Omega)$ and all $N \geq 2$ there exists a ReLU-network $\Phi_N$ such that

$$\sup_{x \in \Omega} |f(x) - \Phi_N(x)| \leq CN^{-\frac{h+S}{\alpha}} |f|_{C^{h,S}(\Omega)}$$

and $$\text{size}(\Phi_N) \leq c_1 N \log(N)$$

and $$\text{depth}(\Phi_N) \leq c_2 \log(N),$$

for some constants $C, c_1, c_2$ depending only on $\alpha$ and $h$.

**Proof:** It suffices to show the theorem for the case $\max{\frac{\alpha^{k+S/2}}{h!}, e^{\alpha}|f|_{C^{h,S}(\Omega)}} \leq 1$ for the general case use a rescaling argument.

**Step 1:** We construct the network. Let

$$M = \lceil N^{1/\alpha} \rceil, \quad \Sigma := N^{-\frac{h+S}{\alpha}}$$

As in the proof of Theorem we consider the simplicial mesh with the nodes $V = {v/M, v \in \mathbb{N}_0^d, v \leq M}$ for all $i = 1, \ldots, d$.

We denote by $\varphi_v$ the CPWL-basis used in the proof of Thm 4.25 such that $\varphi_v(v') = \delta_{v,v'}$.

## Image 2:

We claim that $$\sum_{v \in V} \varphi_v(x) = 1 \quad \text{for all } x \in \Omega$$

Indeed, assume that $x \in T$ for a simplex $T$ of the triangulation.

For all $v \in V(T)$ we have $\varphi_v(x) = g_{T,v}(x)$ (Lemma 4.15), where $g_{T,v}(x)$ is the unique affine function satisfying

$$g_{T,v}(v') = \begin{cases} 1 & v'=v \ 0 & v' \neq v \end{cases} \quad \text{for all } v' \in V(T)$$

Since $\varphi_{v'}(x) = 0$ for all $v' \not\in V(T)$ and $x \in T$ (Lemma 4.15), it holds

$$\sum_{v \in V} \varphi_v(x) = \sum_{v \in V(T)} g_{T,v}(x)$$

Observe that $\sum_{v \in V(T)} g_{T,v}(v') = 1$ for all $v' \in V(T)$. Since $\sum_{v \in V(T)} g_{T,v}$ is the unique affine function with these values on $V(T)$ we have

$$\sum_{v \in V(T)} g_{T,v}(x) = 1 \quad \text{for all } x \in T.$$

Since $T$ was arbitrary, we have

$$\sum_{v \in V} \varphi_v(x) = 1 \quad \text{for all } x \in \Omega.$$

## Image 3:

Further, observe that

$$\text{supp}(\varphi_v) \subseteq {x \in \Omega \mid |x-v|_\infty \leq \frac{1}{M}}$$

where $|x|_\infty = \max_{i=1,...,d} |x_i|$

For $v \in V$ define $p_v \in P_h^d$ as

$$p_v(x) := \sum_{|\alpha| \leq h} \frac{D^\alpha f(v)}{\alpha!}(x-v)^\alpha$$

and its approximation

$$\hat{p}_v(x) := \sum_{|\alpha| \leq h} \frac{D^\alpha f(v)}{\alpha!} \Phi_{M,\Sigma}(x_{i_1}, v_{i_1}, ..., x_{i_h}, v_{i_h})$$

where $(i_1, ..., i_h) \in {1,...,d}^h$ is arbitrary but fixed such that $#{j|i_j=i} = \alpha_i$ for all $i = 1,...,d$.

# Explanation of Neural Network Approximation Theorem

## Overview

The mathematical notes describe Theorem 4.25, which is a fundamental result in the theory of neural network approximation. This theorem establishes bounds on how well ReLU neural networks can approximate functions from certain smoothness classes, specifically functions in Hölder spaces $C^{h,S}(\Omega)$.

## Key Concepts

### Hölder Spaces

- $C^{h,S}(\Omega)$ represents the space of functions that have continuous derivatives up to order $h$ and whose $h$-th derivatives satisfy a Hölder condition with exponent $S \in [0,1]$.
- $|f|_{C^{h,S}(\Omega)}$ is the norm of function $f$ in this space, measuring both the size of derivatives up to order $h$ and the "smoothness" of the $h$-th derivatives.

### ReLU Networks

- ReLU (Rectified Linear Unit) is an activation function defined as $\text{ReLU}(x) = \max(0, x)$.
- A ReLU network refers to a neural network that uses ReLU as its activation function.
- $\Phi_N$ represents a ReLU network with a certain complexity related to parameter $N$.

### Network Complexity Measures

- $\text{size}(\Phi_N)$ refers to the number of parameters or weights in the network.
- $\text{depth}(\Phi_N)$ refers to the number of layers in the network.

## The Theorem Explained

Theorem 4.25 states that for any function $f$ in the Hölder space $C^{h,S}(\Omega)$ on the unit cube $\Omega = [0,1]^d$, there exists a ReLU network $\Phi_N$ that approximates $f$ with the following guarantees:

1. **Approximation Error**: The supremum norm of the error is bounded by: $$\sup_{x \in \Omega} |f(x) - \Phi_N(x)| \leq CN^{-\frac{h+S}{\alpha}} |f|_{C^{h,S}(\Omega)}$$
    
    This means the error decreases as $N$ increases, with the rate depending on the smoothness ($h+S$) of the function and parameter $\alpha$.
    
2. **Network Size**: The size of the network is bounded by: $$\text{size}(\Phi_N) \leq c_1 N \log(N)$$
    
    This shows that the network's complexity grows slightly faster than linearly with $N$.
    
3. **Network Depth**: The depth of the network is bounded by: $$\text{depth}(\Phi_N) \leq c_2 \log(N)$$
    
    This indicates that the depth grows logarithmically with $N$.
    

## Proof Strategy

The proof proceeds by constructing a specific ReLU network that achieves the desired approximation:

1. **Scaling Assumption**: The proof first assumes that the function norm is bounded by 1, with a note that the general case follows by rescaling.
    
2. **Network Construction**:
    
    - Define parameters $M = \lceil N^{1/\alpha} \rceil$ and $\Sigma = N^{-\frac{h+S}{\alpha}}$.
    - Create a simplicial mesh (triangulation) of the domain with nodes at points $v/M$ for integer vectors $v$.
    - Use CPWL (Continuous Piecewise Linear) basis functions $\varphi_v$ centered at each node.
3. **Partition of Unity**: Show that the basis functions sum to 1 everywhere: $$\sum_{v \in V} \varphi_v(x) = 1 \quad \text{for all } x \in \Omega$$
    
    This is proven by:
    
    - Considering a point $x$ in simplex $T$
    - Showing that for vertices $v$ of $T$, $\varphi_v(x)$ equals an affine function $g_{T,v}(x)$
    - Proving that these affine functions sum to 1 on the simplex
4. **Local Support**: Establish that each basis function $\varphi_v$ has local support: $$\text{supp}(\varphi_v) \subseteq {x \in \Omega \mid |x-v|_\infty \leq \frac{1}{M}}$$
    
5. **Polynomial Approximation**: For each node $v$, define a polynomial $p_v$ that approximates $f$ near $v$ using the Taylor expansion: $$p_v(x) := \sum_{|\alpha| \leq h} \frac{D^\alpha f(v)}{\alpha!}(x-v)^\alpha$$
    
6. **Network Approximation**: Create a neural network approximation $\hat{p}_v$ of each polynomial $p_v$ by replacing monomial terms with network approximations.
    

The full proof would continue by combining these pieces to construct the final approximating network $\Phi_N$ and verify that it satisfies all required bounds.

## Significance

This theorem provides theoretical justification for using deep ReLU networks to approximate smooth functions. It establishes:

1. How the approximation error decreases with network complexity
2. The trade-off between network size and approximation quality
3. The benefit of depth (logarithmic growth) versus width (near-linear growth)

The result belongs to the field of approximation theory for neural networks, which provides mathematical foundations for understanding the expressive power of neural networks and their ability to approximate functions from different smoothness classes.


---
-15-                                                                                     -16-

combinations of functions of the form
x ↦ g<sub>θ</sub>(x) = C<sub>f</sub> q<sub>x</sub>(θ), θ ∈ Rᵈ.

It remains to prove that g<sub>θ</sub> ∈ conv(G<sub>C</sub>) for all θ ∈ Rᵈ. Setting z = x ⋅ (θ / ||θ||) this follows if the map

g̃<sub>θ</sub> : [-1, 1] → R
g̃<sub>θ</sub>(z) = C<sub>f</sub> (cos(2π||θ||₂z + κ(θ)) - cos(κ(θ))) / (2π||θ||₂)

can be approximated arbitrarily well by convex combinations of the functions

[-1, 1] ∋ z ↦ γ 1<sub>R+</sub>(az + b')
with a ∈ {-1, 1}, b' ∈ [-1, 1] and |γ| ≤ 2C
Note that g̃<sub>θ</sub>(0) = 0.

Define for T ∈ ℕ

g<sub>T, +</sub>(z) := Σ (|g̃<sub>θ</sub>(i/T) - g̃<sub>θ</sub>((i-1)/T)| / (2C<sub>f</sub>)) (2C<sub>f</sub> sgn(g̃<sub>θ</sub>(i/T) - g̃<sub>θ</sub>((i-1)/T)) 1<sub>R+</sub>(z - i/T))
          i=1

g<sub>T, -</sub>(z) := Σ (|g̃<sub>θ</sub>(-i/T) - g̃<sub>θ</sub>((1-i)/T)| / (2C<sub>f</sub>)) (2C<sub>f</sub> sgn(g̃<sub>θ</sub>(-i/T) - g̃<sub>θ</sub>((1-i)/T)) 1<sub>R+</sub>(-z + i/T))
         i=1

g<sub>T, +</sub>(z) + g<sub>T, -</sub>(z) = Σ (|g̃<sub>θ</sub>(i/T) - g̃<sub>θ</sub>((i-1)/T)|) 1<sub>R+</sub>(z - i/T)
                       i=1
                   +  Σ (|g̃<sub>θ</sub>(-i/T) - g̃<sub>θ</sub>((1-i)/T)|) 1<sub>R+</sub>(-z + i/T)
                       i=1
                   = Σ αᵢ,₊ 1<sub>R+</sub>(z - i/T) + Σ αᵢ,₋ 1<sub>R+</sub>(-z + i/T)
                      i=1                 i=1


max_{i,j∈{1,...,K}} sup_{x∈B^d₀_τ} |(F(x; w̃))_i - (F(x; w̃))_j - ((F(x; w))_i - (F(x; w))_j)|



d/dt [f(g(t))] =  ∂f/∂x<sub>1</sub> * dg<sub>1</sub>/dt  +  ∂f/∂x<sub>2</sub> * dg<sub>2</sub>/dt  +  ...  +  ∂f/∂x<sub>n</sub> * dg<sub>n</sub>/dt


---
You're absolutely right to question that! There's a subtle but important distinction that needs to be clarified in the last equation, and it's *not* that both lambdas are the same. They are still λ<sub>1</sub> and λ<sub>2</sub>, but the update is applied *separately* to each component of the `w` vector. Let's break it down:

**The Setup:**

*   We have a 2D quadratic function:  `f(w) = 1/2 w<sup>T</sup>Dw`, where `w = (w<sub>1</sub>, w<sub>2</sub>)` is a 2-dimensional vector, and `D = (λ<sub>1</sub> 0; 0 λ<sub>2</sub>)` is a diagonal matrix with eigenvalues λ<sub>1</sub> and λ<sub>2</sub>.  We assume λ<sub>1</sub> ≥ λ<sub>2</sub> > 0.
*   Gradient Descent update: `w<sub>k+1</sub> = w<sub>k</sub> - h∇f(w<sub>k</sub>) = w<sub>k</sub> - hDw<sub>k</sub>`, where `h` is the learning rate.

**The Matrix Multiplication:**

The key is to understand what happens when we perform the matrix multiplication `w<sub>k</sub> - hDw<sub>k</sub>`:

1.  **`Dw<sub>k</sub>`:**
    ```
    (λ<sub>1</sub>  0) (w<sub>1,k</sub>)   =  (λ<sub>1</sub>w<sub>1,k</sub>)
    (0  λ<sub>2</sub>) (w<sub>2,k</sub>)       (λ<sub>2</sub>w<sub>2,k</sub>)
    ```
    This multiplies each component of `w<sub>k</sub>` by its corresponding eigenvalue.
    (λ<sub>1</sub>  0) (w<sub>1,k</sub>)   =  (λ<sub>1</sub>w<sub>1,k</sub>)
    (0  λ<sub>2</sub>) (w<sub>2,k</sub>)       (λ<sub>2</sub>w<sub>2,k</sub>)
    
2.  **`w<sub>k</sub> - hDw<sub>k</sub>`:**
    ```
    (w<sub>1,k</sub>)  -  h(λ<sub>1</sub>w<sub>1,k</sub>)   =  (w<sub>1,k</sub> - hλ<sub>1</sub>w<sub>1,k</sub>)  =  ((1 - hλ<sub>1</sub>)w<sub>1,k</sub>)
    (w<sub>2,k</sub>)     (λ<sub>2</sub>w<sub>2,k</sub>)       (w<sub>2,k</sub> - hλ<sub>2</sub>w<sub>2,k</sub>)      ((1 - hλ<sub>2</sub>)w<sub>2,k</sub>)
    ```
    This subtracts `h` times the result of `Dw<sub>k</sub>` from `w<sub>k</sub>`.  Notice how the update for `w<sub>1,k</sub>` *only* involves λ<sub>1</sub>, and the update for `w<sub>2,k</sub>` *only* involves λ<sub>2</sub>.
    (w<sub>1,k</sub>)  -  h(λ<sub>1</sub>w<sub>1,k</sub>)   =  (w<sub>1,k</sub> - hλ<sub>1</sub>w<sub>1,k</sub>)  =  ((1 - hλ<sub>1</sub>)w<sub>1,k</sub>)
    (w<sub>2,k</sub>)     (λ<sub>2</sub>w<sub>2,k</sub>)       (w<sub>2,k</sub> - hλ<sub>2</sub>w<sub>2,k</sub>)      ((1 - hλ<sub>2</sub>)w<sub>2,k</sub>)

3.  **Factoring:**
    ```
    ((1 - hλ<sub>1</sub>)w<sub>1,k</sub>)  =  (1 - hλ<sub>1</sub>  0) (w<sub>1,k</sub>)
    ((1 - hλ<sub>2</sub>)w<sub>2,k</sub>)      (0  1 - hλ<sub>2</sub>) (w<sub>2,k</sub>)
    ```
    This is just rewriting the result in matrix form. This makes it clear that the update can be represented as a matrix multiplication:
    `w<sub>k+1</sub> = (1 - hλ<sub>1</sub>  0; 0  1 - hλ<sub>2</sub>)w<sub>k</sub>`
    ((1 - hλ<sub>1</sub>)w<sub>1,k</sub>)  =  (1 - hλ<sub>1</sub>  0) (w<sub>1,k</sub>)
    ((1 - hλ<sub>2</sub>)w<sub>2,k</sub>)      (0  1 - hλ<sub>2</sub>) (w<sub>2,k</sub>)
**The Last Equation (Corrected Interpretation):**

The last equation in the original image is:

```

```
w<sub>k+1</sub> = (1 - λ<sub>1</sub>h)<sup>k+1</sup>  0; 0  (1 - λ<sub>2</sub>h)<sup>k+1</sup>)w<sub>0</sub>


This equation is expressing the result of applying the gradient descent update *repeatedly* (k+1 times), starting from the initial point `w<sub>0</sub>`.  It's *not* saying that the eigenvalues are the same. Here's the correct way to think about it:

*   **Component-wise Updates:**  Because `D` is diagonal, the updates for `w<sub>1</sub>` and `w<sub>2</sub>` are *independent*.  Each component is scaled by its own factor at each iteration:
    *   `w<sub>1,k+1</sub> = (1 - hλ<sub>1</sub>)w<sub>1,k</sub>`
    *   `w<sub>2,k+1</sub> = (1 - hλ<sub>2</sub>)w<sub>2,k</sub>`

*   **Repeated Application:** After k+1 iterations:
    *   `w<sub>1,k+1</sub> = (1 - hλ<sub>1</sub>)<sup>k+1</sup>w<sub>1,0</sub>`  (The initial `w<sub>1,0</sub>` is multiplied by `(1 - hλ<sub>1</sub>)` a total of k+1 times).
    *   `w<sub>2,k+1</sub> = (1 - hλ<sub>2</sub>)<sup>k+1</sup>w<sub>2,0</sub>`  (The initial `w<sub>2,0</sub>` is multiplied by `(1 - hλ<sub>2</sub>)` a total of k+1 times).

*   **Matrix Form:**  We can write this compactly in matrix form:
    ```
    (w<sub>1,k+1</sub>)  =  ((1 - hλ<sub>1</sub>)<sup>k+1</sup>  0) (w<sub>1,0</sub>)
    (w<sub>2,k+1</sub>)      (0  (1 - hλ<sub>2</sub>)<sup>k+1</sup>) (w<sub>2,0</sub>)
    ```
    Which is the same as:
     `w<sub>k+1</sub> = (1 - λ<sub>1</sub>h)<sup>k+1</sup>  0; 0  (1 - λ<sub>2</sub>h)<sup>k+1</sup>)w<sub>0</sub>`

**Key Point:** The diagonal matrix `(1 - λ<sub>1</sub>h)<sup>k+1</sup>  0; 0  (1 - λ<sub>2</sub>h)<sup>k+1</sup>)` represents the *cumulative effect* of the repeated updates.  The eigenvalues λ<sub>1</sub> and λ<sub>2</sub> control the convergence rate along each dimension *independently*.  If λ<sub>1</sub> > λ<sub>2</sub>, the convergence will be slower along the direction corresponding to λ<sub>1</sub> (the direction of the first eigenvector). The fact that they are diagonalized means we can analyze the convergence separately.

In short: The equation is correct, the eigenvalues are not the same. It describes how a diagonal matrix transforms a vector.


---
*   **argmin<sub>h≤1/λ<sub>1</sub></sub> max{|1 - hλ<sub>1</sub>|, |1 - hλ<sub>2</sub>|} = argmin<sub>h≤1/λ<sub>1</sub></sub>(1 - hλ<sub>2</sub>) = 1/λ<sub>1</sub>**
    * We pick the largest possible value in the range `h≤1/λ<sub>1</sub>` to minimize `1 - hλ<sub>2</sub>`. The largest h that satisfies this condition is 1/λ<sub>1</sub>.
    *   **max{|1 - hλ<sub>1</sub>|, |1 - hλ<sub>2</sub>|} = 1 - λ<sub>2</sub>/λ<sub>1</sub> = (λ<sub>1</sub> - λ<sub>2</sub>)/λ<sub>1</sub>**


-16-                                                                       -17-

GD converges if and only if
|1 - λ<sub>1</sub>h| < 1 and |1 - λ<sub>2</sub>h| < 1

Optimal step size
h\* = argmin<sub>h>0</sub> max{|1 - hλ<sub>1</sub>|, |1 - hλ<sub>2</sub>|}

If h ≤ 1/λ<sub>1</sub> ≤ 1/λ<sub>2</sub> then

argmin<sub>h≤1/λ<sub>1</sub></sub> max{|1 - hλ<sub>1</sub>|, |1 - hλ<sub>2</sub>|}

argmin<sub>h≤1/λ<sub>1</sub></sub> max{1 - hλ<sub>2</sub>, 1 - hλ<sub>1</sub>}
= argmin<sub>h≤1/λ<sub>1</sub></sub> 1 - hλ<sub>2</sub> = 1/λ<sub>1</sub> and
max{|1 - hλ<sub>1</sub>|, |1 - hλ<sub>2</sub>|} = 1 - λ<sub>2</sub>/λ<sub>1</sub>
= (λ<sub>1</sub> - λ<sub>2</sub>)/λ<sub>1</sub>

If 1/λ<sub>1</sub> ≤ h ≤ 1/λ<sub>2</sub> then

argmin<sub>1/λ<sub>1</sub>≤h≤1/λ<sub>2</sub></sub> max{hλ<sub>1</sub> - 1, 1 - hλ<sub>2</sub>}

                                                                        hλ<sub>1</sub> - 1 ≥ 1 - hλ<sub>2</sub> <=> h ≥ 2/(λ<sub>1</sub> + λ<sub>2</sub>)

                                                                        For 2/(λ<sub>1</sub> + λ<sub>2</sub>) ≤ h ≤ 1/λ<sub>2</sub>
                                                                        max{hλ<sub>1</sub> - 1, 1 - hλ<sub>2</sub>}
                                                                        = hλ<sub>1</sub> - 1 and minimum for these
                                                                        h is taken for h = 2/(λ<sub>1</sub> + λ<sub>2</sub>) giving
                                                                        max{|1-hλ<sub>1</sub>|, |1-hλ<sub>2</sub>|} = λ<sub>1</sub>(2/(λ<sub>1</sub>+λ<sub>2</sub>)) - 1 = (λ<sub>1</sub>-λ<sub>2</sub>)/(λ<sub>1</sub>+λ<sub>2</sub>)

                                                                        For 1/λ<sub>1</sub> ≤ h ≤ 2/(λ<sub>1</sub> + λ<sub>2</sub>)
                                                                         max{hλ<sub>1</sub> - 1, 1 - hλ<sub>2</sub>}
                                                                         = 1 - hλ<sub>2</sub> and minimum is taken
                                                                         for h=2/(λ<sub>1</sub> + λ<sub>2</sub>) giving
                                                                        max{|1 - hλ<sub>1</sub>|, |1 - hλ<sub>2</sub>|} = 1 - 2λ<sub>2</sub>/(λ<sub>1</sub> + λ<sub>2</sub>) = (λ<sub>1</sub>-λ<sub>2</sub>)/(λ<sub>1</sub> + λ<sub>2</sub>)

If h ≥ 1/λ<sub>2</sub> we have

max{|1 - hλ<sub>1</sub>|, |1 - hλ<sub>2</sub>|}
= max{hλ<sub>1</sub> - 1, hλ<sub>2</sub> - 1}


