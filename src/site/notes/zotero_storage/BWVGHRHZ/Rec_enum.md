---
{"dg-publish":true,"permalink":"/zotero-storage/bwvghrhz/rec-enum/","noteIcon":""}
---

---
Recursive enumerability, often referred to as **recursively enumerable (r.e.)**, describes a property of a set of natural numbers (or, more generally, a set of objects) in the context of computability theory.

A set S⊆NS⊆N is **recursively enumerable** if:

1. There exists a **Turing machine** that enumerates all the elements of SS, possibly with repetitions, in some order. In other words, the Turing machine will eventually print every element of SS on its output tape if you let it run indefinitely.
    
    - If n∈Sn∈S, then the Turing machine eventually outputs nn.
    - If n∉Sn∈/S, the Turing machine never outputs nn.
2. Alternatively, SS is recursively enumerable if there exists a Turing machine that **accepts nn** if and only if n∈Sn∈S. (Note that this Turing machine may not halt for n∉Sn∈/S.)
    

### Important Notes:

- **Recursive sets** (or decidable sets) are a subset of recursively enumerable sets. A set SS is recursive if a Turing machine can decide membership in SS (halt on every input, accepting or rejecting it).
- A set SS is not necessarily recursive if it is recursively enumerable; for n∉Sn∈/S, the Turing machine may loop forever without a definite rejection.

### Examples:

1. The set of valid proofs in a formal system (e.g., Peano Arithmetic) is recursively enumerable because we can construct a Turing machine that enumerates all syntactically correct proofs and checks their validity.
    
2. The **halting problem** is a classic example where the set of inputs for which a given Turing machine halts is recursively enumerable but not recursive.