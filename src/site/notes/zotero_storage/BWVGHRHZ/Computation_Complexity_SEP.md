---
{"dg-publish":true,"permalink":"/zotero-storage/bwvghrhz/computation-complexity-sep/","noteIcon":""}
---

---

[[zotero_storage/BWVGHRHZ/Rec_enum\|Rec_enum]]


Interesting QnA on Chomkst Hierarchy:
[Chomsky Hierarchy](https://devopedia.org/chomsky-hierarchy#VideoLectures-2014)

> [!PDF|255, 208, 0] [[Computability and Complexity (Stanford Encyclopedia of Philosophy).pdf#page=1&annotation=346R|Computability and Complexity (Stanford Encyclopedia of Philosophy), p.1]]
> Turing asked whether every set of natural numbers is decidable. It is easy to see that the answer is, “no”, by the following counting argument. There are uncountably many subsets of , but since there are only countably many Turing machines, there can be only countably many decidable sets. Thus almost all sets are undecidable.

Why are there only countably many TMs? 1to1 with Natural Numbers

[[zotero_storage/BWVGHRHZ/Char_Primitive_Rec_Functions\|Char_Primitive_Rec_Functions]]


> [!PDF|255, 208, 0] [[Computability and Complexity (Stanford Encyclopedia of Philosophy).pdf#page=2&annotation=349R|Computability and Complexity (Stanford Encyclopedia of Philosophy), p.2]]
> Ladner proved that if P NP, then there is an intermediate problem that is in NP but not in P and not NP complete



> [!PDF|255, 208, 0] [[Computability and Complexity (Stanford Encyclopedia of Philosophy).pdf#page=2&annotation=357R|Computability and Complexity (Stanford Encyclopedia of Philosophy), p.2]]
> In fact, if one looks closer, all of Schaefer’s satisfiability problems are either NP complete, P complete, L complete, NL complete, L complete, or trivial [Allender et al., 2009]. 

- **P-complete**: Problems solvable in polynomial time but likely not parallelizable (hard for PP).
- **LL-complete**: Problems solvable in logarithmic space and complete for LL, the class of problems solvable in deterministic log space.
- **NLNL-complete**: Problems solvable in nondeterministic logarithmic space, complete for NLNL.
- **Trivial**: Problems that are always satisfiable or unsatisfiable, requiring no computation.





![Screenshot 2024-12-22 at 16.36.05.png](/img/user/Attachments/Screenshot%202024-12-22%20at%2016.36.05.png)



> [!PDF|255, 208, 0] [[Computability and Complexity (Stanford Encyclopedia of Philosophy).pdf#page=2&annotation=370R|Computability and Complexity (Stanford Encyclopedia of Philosophy), p.2]]
> ardi and the author of this entry later independently proved that P = FO(LFP): a property is in P iff it is expressible in first-order logic plus a least fixed-point operator (LFP) which formalizes the power to define new relations by induction. A captivating corollary of this is that P = NP iff SO = FO(LFP). That is, P is equal to NP iff every property expressible in second order logic is already expressible in first-order logic plus inductive definitions

![Screenshot 2024-12-22 at 16.43.25.png](/img/user/Attachments/Screenshot%202024-12-22%20at%2016.43.25.png)

> [!PDF|255, 208, 0] [[Computability and Complexity (Stanford Encyclopedia of Philosophy).pdf#page=2&annotation=373R|Computability and Complexity (Stanford Encyclopedia of Philosophy), p.2]]
> The class NP is very important practically and philosophically.  It is the class of problems,  , such that any input  is in  iff there is a proof,  , thatS  w  S  p(w)   and  is not much larger than  .  Thus, very informally, we can think of NPp(w)  w has the set of intellectual endeavors that may be in reach: if we ﬁnd the answer to whether  , we can convince others that we have done sw  ∈  S

he passage then uses an analogy to intellectual endeavors. If a problem is in NP, it suggests that finding the solution might be challenging, but once found, it's easy to convince others of its correctness. Think of a difficult puzzle: finding the solution might take a while, but once you have it, it's easy to show others it works.