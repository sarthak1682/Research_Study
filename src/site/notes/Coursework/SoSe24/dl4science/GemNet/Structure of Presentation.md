---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/gem-net/structure-of-presentation/","noteIcon":""}
---

 ---
# Intro
What it is trying to achieve/ what did it accomplish (brief overview of the problem it tries to solve, the results) 
	
	 Molecular Property Prediction, Force and Energy
	Get the results out of the way in the beginning, not the focus of the talk
	Start with the architecture (give a brief overview)
	jump to the message passing, and say we are gonna try and derive a msg passing scheme from scratch (this should be the connection to the method section)

# Method

Here’s the important part! (give a small overview, and establish that this is the focus)

Proof 1: TFN are universal (Dym and Maron), Spherical Repr. are equivalent to TFNs -> they are also universal. (Importance: cheaper repr. suffices)


	1. Introduce TFNs:
		1. Spherical Harmonics
		2. CG Coeffs
		3. Irreps (Wigner-D Matrices?)
	
	2. Spherical Networks
		1. Introduce (similar notation)

	3. Proof (Should be straightforward after having introduced the concepts above), suffices only for invariance. 
		1. Also state the result from Villar et al. (completing the proof for equivariance.)



Proof 2: Derive a msg passing scheme

	1. Why the need to sample representations
	2. Directional Mesh
	3. Is it always universal? 
	4. Role of the filters (F1 (generalized F_Sphere), F2)
	5. Final MSG Passing: connection to GNNs 

The End. 



---
Universal Changes

S.1 
Comments: Get the expectations straight!

"Hello everyone, I am Sarthak and I will be presenting GemNet today. It's a Graph Neural Net trying to predict Molecular Interaction. Just to set the tone first, this is more of a theory paper than a technical one, although to be fair to the authors, it has a lot of technical details and rigor to it as well. Since it is a rather math-y paper, the presentation will have a different flavour to it than what has been presented before in this seminar!  But rest assured that just because it is theory, there is a lot of math involved, doesn't mean that it would convoluted, boring or downright unintelligible, it would certainly not feel like you are reading ancient greek. There will be ample visuals and suitable analogies all over the place, so that you can at least have an intuitive grasp on whats going on behind the scenes. So, please engage with it, you could interrupt any time, or for the people on zoom, just unmute and start speaking. If you want me to slow a little bit, please just say so"

S.2 

S.4 You can see a photo of the architecture, it's apparently quite complicated, and rich. So, if you just take a look at the model, here, it tries to encode some angles and length, let them go through the embedding block and then the interaction block, where all the stuff like message passing is going on, accumulate information from that and you get the prediction. 

But that's only a brief overview, we are only going to limit ourselves with message passing part and try to answer the question of why do you need the particular inputs in sufficient detail. But for now it suffices to say,....

S.5 Then what is it about? Again just to reiterate, it's a theory paper, what they are trying to prove is, GNNs with 2-hope msg passing and directed edge embedding are universal for rotationally equiv. predictions. Let's just call it the universality result and thats what we are going to prove today!






S.7 analogy with AF2 for global invariance



S.14: try to explain it from the top-down and bottom-up


S.24: New pic? 

S.31 : Why the general form? 

S.35: Just add that the hard part is over, we can relax a bit and declare it as.. (A GREAT SUCCESS)



#### Intro 
S.1-5 4.5 mins

Motivation and sketch
S.6-12 4.5 mins

prelims
s.13-28 9 mins

Proof
29-37 8 mins

