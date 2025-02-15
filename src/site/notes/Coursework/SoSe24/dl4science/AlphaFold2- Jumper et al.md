---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/alpha-fold2-jumper-et-al/","noteIcon":""}
---

---
[Highly accurate protein structure prediction with AlphaFold | Nature](https://www.nature.com/articles/s41586-021-03819-2)
[Before you continue to YouTube](https://youtube.com/playlist?list=PLtTW95DQYdFuBGFobtZY6j7lk2F6Wip9W&si=Pw48IzCWqW_fVVIw): Playlist Nazim Bouatta (fantastic lectures)
[The AlphaFold2 Method Paper: A Fount of Good Ideas « Some Thoughts on a Mysterious Universe](https://moalquraishi.wordpress.com/2021/07/25/the-alphafold2-method-paper-a-fount-of-good-ideas/)

IPA and Equiv. 
[static-content.springer.com/esm/art%3A10.1038%2Fs41586-021-03819-2/MediaObjects/41586\_2021\_3819\_MOESM1\_ESM.pdf](https://static-content.springer.com/esm/art%3A10.1038%2Fs41586-021-03819-2/MediaObjects/41586_2021_3819_MOESM1_ESM.pdf) : read 1.8
[Nazim Bouatta | Machine learning for protein structure prediction, Part 2: AlphaFold2 architecture - YouTube](https://www.youtube.com/watch?v=ri39B0Voujc&t=4077s): Section: "The Plan"
[The AlphaFold2 Method Paper: A Fount of Good Ideas « Some Thoughts on a Mysterious Universe](https://moalquraishi.wordpress.com/2021/07/25/the-alphafold2-method-paper-a-fount-of-good-ideas/): The How of SE3 Equivariance
[journals.iucr.org/d/issues/2021/08/00/rr5212/rr5212.pdf](https://journals.iucr.org/d/issues/2021/08/00/rr5212/rr5212.pdf): 4.3 
[AlphaFold 2 and Iterative SE(3)-Transformers](https://edwag.github.io/se3iterative/#:~:text=As%20explained%20in%20AlphaFold%202,same%20as%20the%20iterative%20model.): " To summarise, equivariance leverages the symmetry of the problem, i.e. the fact that the global orientation of the protein is meaningless and should not interfere with the reasoning about its structure. Concretely, the structure module of AlphaFold 2 uses a network that is mathematically guaranteed to produce equivalent outputs for rotated versions of the input."

---
## Summary to be submitted

(Since I think most reported results are clear and stellar, I would focus on the sophisticated architecture in the summary)

Let's start the journey. We assume modelling long-range dependencies over MSAs with vanilla transformers would suffice, since that would be the correct inductive bias for reasoning over a protein sequence, it doesn't, therefore they implement row and column attention. Since that'd be computationally too expensive, they implement cropping during training, which we assume would defeat the idea of capturing long-range dependencies, it doesn't. Now we assume that doing this 48 times we could predict the protein by getting a 2D distogram, we can't, we have to do an end-to-end prediction, and transformers, it turns out, are not the right inductive bias for graphs, they don't represent the edges. Directly going from 1D to 3D doesn't work.

Since they need to represent edges, they add a bias term to the row attention for the MSA, which encodes the pairwise relationships (edges), they search structure data for this. We may think doing so once suffices, it doesn't, it needs to be repeated 48 times, in both directions, so that better edge representations can also be learned in parallel. We may want to fold right after, but this is not enough, since these 2D Maps are mathematically inconsistent and don't follow the triangular inequality. We may think that we have to hardcode that, but it would hurt the end-to-end differentiability, so they do it *informationally* and get down the violations to a bare minimum. 

Now we may think that picking the top row and the 2D pairwise would suffice for building the 3D representation, since we now already have the positions and orientations of the residues, not true, they do away with the peptide bonds and only get a bag of triangles, in order to capture long-range dependencies and de-emphasise local peptide bonds, which is analogous to what transformers do for words. We might think this would be enough, not quite, the feature map for triangles would have to be SE(3)-equivariant, which leads them to add the IPA to the original attention, making it geometrically aware. The (final) backbone is then gained only by the refining the orientations through eight blocks in the structure module, each with its own penalty and subsequent updates.  

This suffices for the backbone, but what about the side chains? 

They take the first row of the MSA to predict torsion angles with it, which combined with the backbone through local transformations gets them the side chains. We now have a final representation and a ground truth with a loss function. We think a simple loss function would of course suffice, not true, they include FAPE Loss (chirality aware loss), auxiliary loss, distribution loss, MSA loss and confidence loss. We assume doing this once would suffice, it doesn't, they recycle it three times. 




---
L1

not a lot of focus on data (diff from large scale systems):  90M Param, very sophisticated arch


Use of MATH in ESM metagenomic Atlas? 

Not every detail in the seq matters ->  Seq Space to Str. Space

MSA (Multiple Seq Alignment)

Covariation: two columns affecting each other
HIghly Conserved, Highly Variable

PSSM: Position specific scoring matrix (1st Order Info)

Co-Evolution (second order Info)


Seq (MSA) -> Str. (Inference)
Str. -> Seq (MSA) (Constraint)

Masking Strategy -> Produces rich embeddings

first step: backbone chain

proteins can be fully characterized geom in terms of their torsion angles

3 repr: 3D Sturct, 2D Pairwise, torsion Angles : Very important

right math lang to reason over the proteins

why predicting protein structures is hard? Long-range dependencies

holy grail: efficient as AF2 but not relying too much on evol. info
AF2 does not capture mutation and (-al) effects since its rooted in full MSAs



---
L2

cropping

Attention is not enuff to provide highly accurate systems
Attention is the right kind of inductive bias for reasoning over protein seq but not the right kind to  reason over graphs
at the end it reflects all the inductive biases of phy, chem, geom and evo-info of protein
for edges: 

add a bias term to the row attention which corresponds to a grpah, col attention doesn't need that coz it accounts for the variation of mutations 


reverse info flow (from 1D to 2D)

captures the intuiton: constraint and inf

triangle ineq. (almost) enforced in an end-to-end diff way (geometric constraints need not be realized _literally_, as many people, including my group, had been trying to do, by _e.g.,_ mathematically enforcing the triangular inequality, but instead _informationally_, _i.e.,_ in the information flow patterns of the attention mechanism.)

Str. Model: 

how to get the 2D Object into a consistent 3D Solution?  (overdetermination: more pairwise distances than atoms)

top row from MSA + 2D Repr


1. predict the backbone (triangles with same lengths and angles N, C_alpha, C'), what is to be learned is their abs. positioning in the euclidean space and their orientation
	1. How to do it? Rotation Matrix + Translation Vec
	2. Decision: Cut the peptide bond and get the triangles (just the same way transformer does for words)
		1. need an NN to rearrange the triangles to learn the backbone 
		2. SE3 tranformation ( eq.? )
		3. Inv. Point Attention 
		4. Still not enuff (doftmax produces scalars)
			1. BackboneUpdate (si) = (Rot, translation_v) (do it eight times)
2. Predict Side chains 
	1. Use backbone and torsion angles and build local transormations to move along the side chain and reconstrcut items 

loss function (FAPE loss)


limitations (intrinsic?)

shallow MSAs (orphan proteins)
AF2 does not capture mutation and (-al) effects since its rooted in full MSAs
antibodies (struggles here)

speculation
from genes to molecular machines 

 info storing modules + info processing module

 multi modal training could capture chem: pathways


Interpretability? Why do they work?

redundancy -> 1000 PDBs bootstrap? 
not much about data size but more about diversity 


---
only need to worry about triangles being 


----



