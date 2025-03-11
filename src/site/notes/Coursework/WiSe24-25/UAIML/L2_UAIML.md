---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/uaiml/l2-uaiml/","noteIcon":""}
---

---


**Slide 3: Knowledge Representation**


*   **Different Levels of Detail:**
    *   **Atomic:** Simplest form. States are just names, no internal structure.
    *   **Factored:** States are described by variables and their values (like in propositional logic or Bayesian networks). This is common in machine learning.
    *   **Structured:** Most complex. States have internal structure, showing relationships between parts (like in first-order logic).
![Attachments/UAIML-slides-complete-2 21.jpg](/img/user/Attachments/UAIML-slides-complete-2%2021.jpg)

[[UAIML-slides-complete-2.pdf#page=15&rect=5,17,449,106|UAIML-slides-complete-2, p.15]]


**Slide 4: Knowledge Representation (Example)**

*   **Illustrates the 3 Representation Types:**
    *   **Atomic:** List all possible paths (path1, path2, ...). Inefficient and doesn't generalize.
    *   **Factored:** Use variables (xij) to indicate moves between grid cells. Requires assumptions about how moves are made.
    *   **Structured:** Use logical predicates like `Start(i)`, `Move(i,j)`. More expressive and captures relationships.






**Slide 8: Representing Uncertainty (Probabilistic Approach)**

*   **Probability Distributions:** The most common way to represent uncertainty is with probability distributions over possible states.
*   **Factored Case:**  For factored representations, this means specifying a probability distribution (mass or density function) on the Cartesian product of the domains of (random) variables X1, . . . , XN .
![Attachments/UAIML-slides-complete-2.jpg](/img/user/Attachments/UAIML-slides-complete-2.jpg)

[[UAIML-slides-complete-2.pdf#page=19&rect=134,21,314,153|UAIML-slides-complete-2, p.19]]

**Slide 9: Probabilistic Knowledge Representation**
*   **Random Variables:**  `X = {X1, ..., XN}` is a set of random variables.
*   **Joint Probability:** `P` is a joint probability measure over the combined space of all variable values (`Vx`).
*   **Probability Mass Function:** `p: Vx -> [0, 1]` defines the probability of each specific combination of variable values (assuming discrete variables).
*   **Key Aspects of Probabilistic Modeling:**
    *   **Knowledge Acquisition:** How to get the probabilities (the hardest part!).
    *   **Complexity:** How much memory/computation is needed.
    *   **Efficiency:** Can we answer questions (queries) quickly?


**Slide 10: Notation**

![Attachments/UAIML-slides-complete-2 1.jpg](/img/user/Attachments/UAIML-slides-complete-2%201.jpg)

[[UAIML-slides-complete-2.pdf#page=21&rect=6,41,449,230|UAIML-slides-complete-2, p.21]]



**Slide 11: Probabilistic Queries**

*   **Types of Questions:** Defines different kinds of questions (queries) one might ask about a probabilistic model.
*   **Query Types:**
    *   **EVI (Complete Evidence):** What's the probability of a specific, fully defined state (`X = x`)?
    *   **MAR (Marginal):** What's the probability of an event (a subset of possible states)?
    *   **CON (Conditional):** What's the probability of an event `A = a` *given* that we know another event `B = b`?  (`P(A = a | B = b)`)
    *   **MAP (Maximum a Posteriori):**  ![Attachments/UAIML-slides-complete-2 2.jpg](/img/user/Attachments/UAIML-slides-complete-2%202.jpg)

[[UAIML-slides-complete-2.pdf#page=22&rect=108,29,387,70|UAIML-slides-complete-2, p.22]]

![Attachments/UAIML-slides-complete-2 3.jpg](/img/user/Attachments/UAIML-slides-complete-2%203.jpg)

[[UAIML-slides-complete-2.pdf#page=23&rect=7,31,385,253|UAIML-slides-complete-2, p.23]]


**Slide 13: Inference through Marginalization**

*   **Marginalization:** A fundamental operation for answering queries.  It involves summing (or integrating) over variables we're *not* interested in.
*   **Formulas:**
    *   `P(b)`: Marginal probability of `B = b`.  Sum over all values of `A` and `C`.
    *   `P(a | b)`: Conditional probability of `A = a` given `B = b`.  Calculated using the marginals.
![Attachments/UAIML-slides-complete-2 4.jpg](/img/user/Attachments/UAIML-slides-complete-2%204.jpg)

[[UAIML-slides-complete-2.pdf#page=24&rect=105,75,400,162|UAIML-slides-complete-2, p.24]]

**Slide 14: Inference through Marginalization (Example)**

*   **Detailed Example:** Shows a table with a joint distribution over four variables (X1 to X4).
*   **Calculates a Conditional Probability:**  Demonstrates how to calculate `P(X3 = 1 | X2 = 0, X4 = 1)` using marginalization.  It involves summing the joint probabilities for relevant combinations.



**Slide 15: Independence**

*   **Simplification:** Independence between variables makes probabilistic modeling much easier.
*   **Full Independence:** If all variables are independent, the joint distribution is simply the product of the individual marginal distributions: `p(X1, ..., XN) = P(X1) * ... * P(XN)`.
*   **Reduced Complexity:**  This drastically reduces the number of probabilities needed to define the model.
*   **Marginals and MAP:**  Calculating marginals and finding the most likely state (MAP) become much simpler with independence.
*   **Reality:**  Full independence is rare; real-world distributions are usually somewhere between full independence and full dependence.





**Slide 17: Bayesian Networks**

*   **Directed Acyclic Graph (DAG):**  A Bayesian Network uses a DAG to represent dependencies between variables. G = (X , E)
*   **Nodes and Edges:** Nodes are variables; edges represent direct probabilistic dependencies.
*   **Key Terms:**
    *   `pa(Xi)`: Parent nodes of Xi (variables that directly influence Xi).
    *   `de(Xi)`: Descendant nodes of Xi (variables that Xi directly or indirectly influences).
    *   `nd(Xi)`: Non-descendant nodes of Xi.
![Attachments/UAIML-slides-complete-2 5.jpg](/img/user/Attachments/UAIML-slides-complete-2%205.jpg)

[[UAIML-slides-complete-2.pdf#page=28&rect=107,13,344,174|UAIML-slides-complete-2, p.28]]



**Slide 18: Bayesian Networks (Conditional Independence)**

*   **Definition:** Defines what it means for a DAG and a probability distribution to form a Bayesian Network. BN = (X,E,P)
*   **Key Property:**  Each variable (Xi) is conditionally independent of its non-descendants given its parents: `Xi ⊥⊥P nd(Xi) | pa(Xi)`.
*   **Conditional Independence:**  `P(A, B | C) = P(A | C) * P(B | C)`.  Knowing `C` makes `A` and `B` independent. (A is cond. ind. of B given C)




**Slide 20: Example: Galton Board**

*   **Galton Board:**  A physical device demonstrating the central limit theorem.  Balls fall through a series of pegs, ending up in bins at the bottom.
*   **Probabilistic Model:**  The path of a ball can be modeled as a sequence of random variables (X1, X2, X3, X4), each representing a choice at a peg.
*   **DAG Structure:**  The Galton board naturally forms a Bayesian Network.


**Slide 21: Example: Naïve Bayes**

*   **Naïve Bayes Classifier:** A simple but often effective probabilistic classifier.
*   **Key Assumption:**  Features (X1, X2, ..., Xm) are conditionally independent given the class variable (Y).
*   **DAG:**  Shows the characteristic structure of a Naïve Bayes model:  Y is the parent of all the feature variables.
![Attachments/UAIML-slides-complete-2 6.jpg](/img/user/Attachments/UAIML-slides-complete-2%206.jpg)

[[UAIML-slides-complete-2.pdf#page=32&rect=97,54,375,194|UAIML-slides-complete-2, p.32]]

**Slide 22: Bayesian Networks (Joint Distribution)**

*   **Key Result:**  Shows how to calculate the joint distribution `P(X)` in a Bayesian Network.
*   **Chain Rule:**  The joint distribution is the product of the conditional probabilities of each variable given its parents: `P(X) = Π P(Xi | pa(Xi))`.
*   **Specification:** To define a Bayesian Network, you need to specify the conditional probability distribution `P(Xi | Bi)` for each variable Xi, given each possible combination of values of its parents (Bi).
*   **Probability Tables:**  For discrete variables, these conditional probabilities are often represented in tables.


**Slide 23: Bayesian Networks (Example - Continued)**

*   **Applies the Chain Rule:**  Shows the chain rule factorization for the Galton board example (from Slide 20).  `P(X1, X2, X3, X4) = P(X1) * P(X2 | X1) * P(X3 | X1, X2) * P(X4 | X2)`.  Notice how X4 only depends on X2 (its parent).
*   **Efficiency:**  Highlights the reduction in the number of probabilities needed compared to a fully connected model.


**Slide 24: Construction of Bayesian Networks**

*   **Variable Ordering:**  Start by choosing an order for the variables.
*   **Minimal Parent Sets:**  For each variable, find the smallest set of preceding variables that make it conditionally independent of the rest.  These become its parents.
*   **Formula:** `P(Xσ(i) | pa(Xσ(i))) = P(Xσ(i) | Xσ(1), ..., Xσ(i-1))`.


**Slide 25: Construction of Bayesian Networks (Continued)**

*   **Order Matters:**  A bad variable ordering can lead to a more complex network than necessary.
*   **Causal Direction:**  Choosing a causal order (causes before effects) often leads to simpler and more interpretable networks.
*   **Galton Board Example:**  Shows two different orderings for the Galton board variables, one causal and one not.  The non-causal ordering results in a more complex dependency structure.
![Attachments/UAIML-slides-complete-2 7.jpg](/img/user/Attachments/UAIML-slides-complete-2%207.jpg)

[[UAIML-slides-complete-2.pdf#page=36&rect=17,36,408,175|UAIML-slides-complete-2, p.36]]

**Slide 26: Bayesian Networks: Further Topics**

*   **Open Questions:**  Lists important topics related to Bayesian Networks that will be covered later (or in the appendix).
    *   **D-Separation:** How to determine conditional independence just from the graph structure.
    *   **Inference Algorithms:** Efficient methods for calculating probabilities in Bayesian Networks.
    *   **Learning BNs:** How to learn the structure and parameters of a Bayesian Network from data.





**Slide 28: Probabilistic Circuits**
 probabilistic circuits (PCs) as another way to represent probability distributions.
*   **DAG Representation:** PCs are also represented as DAGs.
*   **Computational Graph:**  A PC is viewed as a computation graph with an operational semantics (meaning we know how to compute with it).
*   **Tractability:**  For certain types of PCs, inference (answering queries) can be done efficiently.
*   **Building Blocks:**  PCs are built from:
    *   Input distributions (leaves of the DAG).
    *   Sum nodes (representing mixtures).
    *   Product nodes (representing factorizations).


**Slide 29: Probabilistic Circuits (Base Case)**

*   **Single Node:** The simplest PC is a single node representing a probability distribution.

![Attachments/UAIML-slides-complete-2 8.jpg](/img/user/Attachments/UAIML-slides-complete-2%208.jpg)

[[UAIML-slides-complete-2.pdf#page=40&rect=89,141,306,233|UAIML-slides-complete-2, p.40]]
*   **Black Boxes:**  Input distributions are treated as "black boxes" that can answer certain queries.
*   **Tractable Operations:**  Input distributions are assumed to support:
    *   **EVI:** Evaluating the probability density/mass at a given point.
    *   **MAR:**  Returning 1 if normalized (or the normalization constant otherwise).
    *   **MAP:** Returning the mode (most likely value).
*   **Scope:**  `sc(N)` defines the set of variables the distribution `N` depends on.

![Attachments/UAIML-slides-complete-2 9.jpg](/img/user/Attachments/UAIML-slides-complete-2%209.jpg)

[[UAIML-slides-complete-2.pdf#page=41&rect=16,20,357,234|UAIML-slides-complete-2, p.41]]

**Slide 30: Probabilistic Circuits (Product Nodes)**

*   **Factorization:** Product nodes represent the product of independent distributions.
*   **Example:**  `p(X1, X2, X3) = p1(X1) * p2(X2) * p3(X3)`.  X1, X2, and X3 are independent.


**Slide 31: Probabilistic Circuits (Feedforward Evaluation)**

![Attachments/UAIML-slides-complete-2 10.jpg](/img/user/Attachments/UAIML-slides-complete-2%2010.jpg)

[[UAIML-slides-complete-2.pdf#page=42&rect=149,79,330,223|UAIML-slides-complete-2, p.42]]



**Slide 32: Probabilistic Circuits (Sum Nodes)**

*   **Mixture Distributions:** Sum nodes represent weighted sums of distributions (mixtures).
*   **Example:**  `p(X) = α1 * p1(X1) + α2 * p2(X2) + α3 * p3(X3)`. The αi are weights that sum to 1.


![Attachments/UAIML-slides-complete-2 11.jpg](/img/user/Attachments/UAIML-slides-complete-2%2011.jpg)

[[UAIML-slides-complete-2.pdf#page=43&rect=17,23,391,232|UAIML-slides-complete-2, p.43]]
**Slide 33: Probabilistic Circuits (Mixture Example)**

*   **Visual Example:** Shows a mixture of three Gaussian distributions. The red line is the resulting mixture distribution.
![Attachments/UAIML-slides-complete-2 12.jpg](/img/user/Attachments/UAIML-slides-complete-2%2012.jpg)

[[UAIML-slides-complete-2.pdf#page=44&rect=48,58,405,222|UAIML-slides-complete-2, p.44]]

**Slide 34: Probabilistic Circuits (Deep Circuits)**

*   **Combining Nodes:** By stacking sum and product nodes, you can create more complex (and "deep") circuits.
*   **Increased Expressivity:** Deeper circuits can represent more complex probability distributions.
![Attachments/UAIML-slides-complete-2 13.jpg](/img/user/Attachments/UAIML-slides-complete-2%2013.jpg)

[[UAIML-slides-complete-2.pdf#page=45&rect=155,28,302,193|UAIML-slides-complete-2, p.45]]

**Slide 35: Probabilistic Circuits (Arithmetic Expression)**

*   **Equivalence:**  Shows that a PC can be interpreted as an arithmetic expression over probability distributions.![Attachments/UAIML-slides-complete-2 14.jpg](/img/user/Attachments/UAIML-slides-complete-2%2014.jpg)

[[UAIML-slides-complete-2.pdf#page=46&rect=15,9,400,233|UAIML-slides-complete-2, p.46]]  

**Slide 36: Probabilistic Circuits (EVI Evaluation)**

*   **Forward Pass:** Shows how to evaluate a PC for a complete evidence query (EVI) using a forward pass.
*   **Values Propagate:**  Values from the input nodes are propagated up through the network, multiplying at product nodes and summing at sum nodes.
![Attachments/UAIML-slides-complete-2 15.jpg](/img/user/Attachments/UAIML-slides-complete-2%2015.jpg)

[[UAIML-slides-complete-2.pdf#page=47&rect=13,23,370,227|UAIML-slides-complete-2, p.47]]

**Slide 37: Probabilistic Circuits (Comparison to Graphical Models)**

*   **Recursive Semantics:** Complex PCs have a recursive definition based on their structure.
*   **Key Differences:**  Compares PCs to traditional probabilistic graphical models (like Bayesian Networks):
    *   **Nodes:**  Graphical models: variables; PCs: computational units.
    *   **Edges:** Graphical models: dependencies; PCs: order of operations.
    *   **Inference:** Graphical models: conditioning, elimination, message passing; PCs: forward/backward passes.
*   **Tractability:**  PCs require structural constraints (to be defined) to ensure efficient inference.

**Slide 38: Probabilistic Circuits (Tractability Constraints)**

*   **Decomposability:**  A product node is decomposable if its children depend on *disjoint* sets of variables (meaning they are independent).
*   **Smoothness (Completeness):**  A sum node is smooth if its children depend on the *same* set of variables.
*   **MAR Tractability:**  Marginalization (computing sums/integrals) is tractable (efficient) if the PC is decomposable and smooth.  The complexity is linear in the size of the circuit.


**Slide 39: Probabilistic Circuits (MAR - Continued)**

*   **Pushing Down Integrals:**  Shows how decomposability and smoothness allow integrals (and sums) to be "pushed down" to the children of sum and product nodes.
* ![Attachments/UAIML-slides-complete-2 16.jpg](/img/user/Attachments/UAIML-slides-complete-2%2016.jpg)

[[UAIML-slides-complete-2.pdf#page=50&rect=13,146,362,228|UAIML-slides-complete-2, p.50]]
    *   **Sum Node:**  The integral of a weighted sum is the weighted sum of the integrals.
    *   **Product Node:**  The integral of a product of independent functions is the product of the integrals.![Attachments/UAIML-slides-complete-2 17.jpg](/img/user/Attachments/UAIML-slides-complete-2%2017.jpg)

[[UAIML-slides-complete-2.pdf#page=50&rect=13,43,393,145|UAIML-slides-complete-2, p.50]]


**Slide 40: Probabilistic Circuits (MAR Example)**

*   **Example Calculation:**  Explains how to compute a marginal probability `p(x2, x4)` in the example circuit.
*   **Normalization:**  Leaf nodes corresponding to variables being marginalized out (X1 and X3) output their normalization constants (which are 1 if the distributions are normalized).
*   **Evidence:** Leaf nodes for variables with evidence (X2 and X4) output their respective values.
*   **Forward Pass:**  The final marginal probability is obtained by a forward pass through the circuit.


**Slide 41: Probabilistic Circuits (MAR Example - Visual)**

*   **Visualizes the MAR Calculation:**  Shows the example circuit with the values propagated during the marginalization calculation.


**Slide 42: Probabilistic Circuits (CON Queries)**

*   **Conditional Queries:**  CON queries (`p(a | b)`) can also be answered efficiently.
*   **Two Passes:**
    1.  Compute `p(a, b)` (a joint probability) using a forward pass.
    2.  Compute `p(b)` (a marginal probability) using another forward pass.
    3.  Divide `p(a, b)` by `p(b)` to get the conditional probability.
*   **Linear Complexity:** The overall complexity remains linear in the circuit size.


**Slide 43: Probabilistic Circuits (MAP Queries)**

*   **MAP Intractability:**  MAP queries (finding the most likely assignment) are generally *intractable* for latent variable models (models with hidden variables).
*   **Sum Node Difficulty:**  Shows why `argmax` and summation don't commute in general. This is the core reason for the intractability.  You can't simply maximize each term in a sum independently.
![Attachments/UAIML-slides-complete-2 18.jpg](/img/user/Attachments/UAIML-slides-complete-2%2018.jpg)

[[UAIML-slides-complete-2.pdf#page=54&rect=17,20,359,230|UAIML-slides-complete-2, p.54]]

**Slide 44: Probabilistic Circuits (MAP - Determinism)**

*   **Determinism (Selectivity):** A sum node is deterministic if, for any given input, *only one* of its children has a non-zero output.  This means the distributions represented by the children have disjoint supports.
*   **MAP Tractability:**  MAP becomes tractable if the PC is deterministic and decomposable.
*   **Sum Equals Max:**  Under determinism, the sum over children is equivalent to taking the maximum (because only one child contributes).
![Attachments/UAIML-slides-complete-2 19.jpg](/img/user/Attachments/UAIML-slides-complete-2%2019.jpg)

[[UAIML-slides-complete-2.pdf#page=55&rect=14,38,328,141|UAIML-slides-complete-2, p.55]]

**Slide 45: Probabilistic Circuits (MAP - Decomposability)**

*   **Product Node Simplification:**  Decomposability allows the maximization over a product node to be split into independent maximizations over its children.
*   **Bottom-Up and Top-Down:**  MAP inference in a deterministic and decomposable PC requires a bottom-up pass (to compute values) and a top-down pass (to find the maximizing assignments).
*   **Linear Complexity:** The overall complexity remains linear.
![Attachments/UAIML-slides-complete-2 20.jpg](/img/user/Attachments/UAIML-slides-complete-2%2020.jpg)

[[UAIML-slides-complete-2.pdf#page=56&rect=18,18,414,230|UAIML-slides-complete-2, p.56]]



