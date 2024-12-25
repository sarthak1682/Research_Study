---
{"dg-publish":true,"permalink":"/zotero-storage/499-bensz/smolensky-2022a-cont-compositionality/","noteIcon":""}
---

---
Neural computing respects the Continuity Principle: the encoding and processing of
information is formalized with real numbers that vary continuously, i.e., by amounts that
can be arbitrarily small. **Continuity means that knowledge about information encoded**
**in one vector automatically generalizes to similar information encoded in nearby vectors**
(Hinton, McClelland, and Rumelhart, 1986). For instance, standard neural systems
can readily generalize their knowledge about the word lock to the word fasten (Fig. 1b):
these words appear in similar contexts within texts used for training (they have similar
‘distributional meaning’), so neural-network learning algorithms will encode them as
vectors that are close together; as a result, neural processing of these two encodings will
produce similar results—similarity-based generalization.
The structure of the vector space can capture other types of relationships as well,
such as having a consistent oﬀset that represents a systematic diﬀerence between pairs
of sentences (Fig. 1c). Most importantly, continuity enables deep learning, in which a
model’s connection weights—even those deeply buried within the network, far from the
input and output encodings—can be modified gradually to smoothly improve the model’s
statistical inference of outputs from inputs in its training set (Rumelhart, Hinton, and
Williams, 1986).
Although it appears obvious that cognition deploys neural computing, virtually all
aspects of human intelligence have been formally and precisely described since antiquity
(Kiparsky and Staal, 1969) in terms of a very diﬀerent type of computing: compositional-
structure processing (Janssen, 2012). In this type of computing (Fig. 2), complex infor-
mation is encoded in large structures—compositional encodings—which are built by
composing together smaller structures that encode simpler information. To process the
complex information encoded in a large structure, it suﬃces to compose together the
results of processing the simpler information encoded in its smaller substructures. This is
the Compositionality Principle (Szab´ o, 2012).


[2205.01128](https://arxiv.org/pdf/2205.01128)

