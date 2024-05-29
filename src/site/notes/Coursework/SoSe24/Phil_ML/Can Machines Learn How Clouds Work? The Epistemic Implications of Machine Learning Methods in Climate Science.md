---
{"dg-publish":true,"permalink":"/coursework/so-se24/phil-ml/can-machines-learn-how-clouds-work-the-epistemic-implications-of-machine-learning-methods-in-climate-science/","noteIcon":""}
---

---
Link: [Can Machines Learn How Clouds Work? The Epistemic Implications of Machine Learning Methods in Climate Science | Philosophy of Science | Cambridge Core](https://www.cambridge.org/core/journals/philosophy-of-science/article/abs/can-machines-learn-how-clouds-work-the-epistemic-implications-of-machine-learning-methods-in-climate-science/36E9CE82F372AA1A8738C203D56F01D2)

---
Conclusion
Although I do agree with the main thrust of the this strand of thought, which is basically end-to-end empirical training is unlikely to success, but I don't do so for her reasons, if she gives any. She repeatedly asserts "widespread failure in neural network generalisability to the lack of process representation" but fails to give reasons/evidence. This kind of claims are susceptible to math and do stand to illuminate phil of sci, but not from this paper. 



Claims
1) widespread failure in neural network generalisability to the lack of process representation.
	1) "widespread" failure, really?
	2) This is an active claim, needs to be substantiated, no? 
	3) It would be false, if you can get an NN without process representation. 
2) The ML Method undermines the reliability of model predictions.
	1) Yes, overfitting is bad, but is she claiming that overfitting is inherent to "the ML Method" or just this particular case study (which btw, the authors admit and try to mitigate)? 




Questions:
1) Is it true that NNs do not represent processes the way CRMs do? How can you really know if something is a black box? (Opacity, like uncertainty, cuts both ways).
2) Quote: "With respect to Rasp et al.’s (2018) study, can NNCAM accurately simulate climate and learn the effects of unprecedented forcing levels, like high sea surface temperatures of 4 K, which are not seen in the training data? Can neural nets learn the effects of extremely high CO2 levels or predict climate system behavior in areas not included in the training data set" (P. 1013, 5.1, 2nd Para) 
	1) From this she concludes a complete failure to generalise: Were these the only two Questions? Were there other? 
		-  "The prognostic multiyear simulations are stable and closely reproduce not only the mean climate of the cloud-resolving simulation but also key aspects of **variability, including precipitation extremes and the equatorial wave** spectrum. Furthermore, the neural network approximately **conserves energy despite not being explicitly instructed to**. Finally, we show that the neural network parameterisation **generalises to new surface forcing patterns** but struggles to cope with temperatures far outside its training manifold."
		- 
1) Quote: "Improving and evaluating process representations are primary means of improving the reliability of model predictions and provide safeguards against overfitting through physical/empirical constraints on model predictions." (P 1018, 6.4) 
	1) Yes but only true for CRM like stuff, not the point of having an NN. (It's like saying that a better engine would help a bicycle!)
2) Quote: "One cannot, as Rasp et al. had hoped, reap the predictive advantages of high-resolution cloud models while leaving out the key reason for their improved performance—the direct and improved representation of subgrid processes that govern model prediction" (P. 1019, 7, Closing lines)
	1) Confusing technical difficulty with a critique of methodology, not particularly wise!
	2) They wanted to *learn* it, why would they (directly) represent it? 


Concepts:
[[Coursework/SoSe24/Phil_ML/Closure Assumption\|Closure Assumption]]


Other Papers showing diffcullty:
[NPG - Generalization properties of feed-forward neural networks trained on Lorenz systems](https://npg.copernicus.org/articles/26/381/2019/)
[GMD - Coupled online learning as a way to tackle instabilities and biases in neural network parameterizations: general algorithms and Lorenz 96 case study (v1.0)](https://gmd.copernicus.org/articles/13/2185/2020/#bib1.bibx30)  (The follow-up paper)

Better Approaches? 
[[2301.10343] ClimaX: A foundation model for weather and climate](https://arxiv.org/abs/2301.10343)


Discussion: 

Overfitting can be avoided with proper sampling
