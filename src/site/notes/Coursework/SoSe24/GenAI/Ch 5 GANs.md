---
{"dg-publish":true,"permalink":"/coursework/so-se24/gen-ai/ch-5-ga-ns/","noteIcon":""}
---

---

#### Motivation & Setting

Problem: GANs do not mod any explicit density Function, we still wanna sample from complex, High-D training D. No direct way? 
Solution: Sample from random Noise, learn transformation to training distr. 


Motivation for Discriminator
![Screenshot 2024-07-14 at 00.24.25.png](/img/user/Attachments/Screenshot%202024-07-14%20at%2000.24.25.png)





#### Adv. Learning, Arch & Training

![Screenshot 2024-07-14 at 00.25.12.png](/img/user/Attachments/Screenshot%202024-07-14%20at%2000.25.12.png)

![Screenshot 2024-07-14 at 00.25.32.png](/img/user/Attachments/Screenshot%202024-07-14%20at%2000.25.32.png)
The minimax Game


Max likelihood of D being wrong (instead of **Min** (D_right), works much better, since the gradient doesn't vanish -> maximizing log(D(G(z))) instead of minimizing log(1 - D(G(z))).



#### Results/Arch/SOTA
![Screenshot 2024-07-14 at 00.31.11.png](/img/user/Attachments/Screenshot%202024-07-14%20at%2000.31.11.png)

What is mode collapse?
	Mode collapse occurs when the generator "collapses" to producing only a few modes (types) of outputs, instead of the full range of possibilities it should be capable of generating. In extreme cases, it might even produce just a single type of output repeatedly.


Why does it happen?
	There are several reasons why mode collapse can occur: 
	a) Objective function mismatch: The GAN objective doesn't directly encourage diversity in the generator's outputs. 
	b) Discriminator's limited feedback: The discriminator only provides binary feedback (real or fake), not how to improve diversity.
	c) Optimization dynamics: The generator might find it easier to fool the discriminator by focusing on a few "safe" outputs rather than risking diverse but potentially less convincing ones.

Summary
Pro? 
	Beautiful examples
Con? 
	Diff. to train (stability of min-max)
	Mode Collaps





#### Further Work/Adv. Tech. 



Conditional GANs? 
D and G: conditioned on auxillary Info
![Screenshot 2024-07-14 at 00.39.46.png](/img/user/Attachments/Screenshot%202024-07-14%20at%2000.39.46.png)


Cycle-GAN?
Unpaired image-to-image translation aims to learn a mapping between two different image domains without using paired training data. This means we don't need exact correspondences between source and target images.Translation should be "cycle-consistent"