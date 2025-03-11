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