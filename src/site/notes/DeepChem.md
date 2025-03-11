---
{"dg-publish":true,"permalink":"/deep-chem/","noteIcon":""}
---




Hamiltonian NNs

Tutorials/Forums



deepchem CI ?

broken tasks in the CI? 

unit tests 


---

Tutorial 1: predict solubility, use GraphConv Featurizer and Model, get train and test scores. 
!pip install --pre "deepchem[tensorflow]" (tutorial has no double quotes)

---


Tutorial2: working with datasets

## 1 Basic tools of deep life sci
![Screenshot 2025-03-01 at 08.57.20.png](/img/user/Attachments/Screenshot%202025-03-01%20at%2008.57.20.png)

These warnings indicate that certain molecular descriptors couldn't be normalized. This is likely not a critical issue, but could be improved by implementing proper normalization for these features.


For a GSoC contribution, addressing the missing normalizations could be a good first project. Here's what you could do:

- File an issue on the DeepChem GitHub repository documenting these missing normalizations

- Look into the codebase to find where these features are processed (likely in the featurization code)

- Implement proper normalization for these molecular descriptors

- Add tests to verify the normalization works correctly

- Submit a PR with your changes

## 2 workign with datasets
The *weights*, referred to as `w`. This can be used to indicate that some data values are more important than others. In later tutorials we will see examples of how this is useful.
SHAP? 

- **Uncertainty:** If you have uncertainty estimates for your measurements, you can use them to weight samples

- Missing Data: Set weight=0 for missing/invalid measurements so they don't contribute to model training

- Confidence Levels: Higher weights for more reliable measurements

- Class Balancing: Giving higher weights to underrepresented classes

- **Sample Importance**: Emphasizing certain samples based on domain knowledge

## 3 

Datasets can also expose data using the standard interfaces for TensorFlow and PyTorch. To get a `tensorflow.data.Dataset`, call `make_tf_dataset()`: delete? since moving away from tensorflow? 


# 3 Intro to Molecule Net
## 1


tasks, datasets, transformers = dc.molnet.load_delaney(featurizer="ECFP", splitter="scaffold")
[09:26:53] DEPRECATION WARNING: please use MorganGenerator


## 2

  

##Tox21 dataset with ECFP fingerprints and random split

print("Loading Tox21 with ECFP fingerprints...")

tasks, datasets, transformers = dc.molnet.load_tox21(

featurizer="ECFP",

splitter="random"

)

train, valid, test = datasets

print(f"Tox21 shapes - Train: {train.X.shape}, Valid: {valid.X.shape}, Test: {test.X.shape}\n")


Results: 
[09:30:09] DEPRECATION WARNING: please use MorganGenerator
Exception message: setting an array element with a sequence. The requested array has an inhomogeneous shape after 1 dimensions. The detected shape was (7831,) + inhomogeneous part.
[09:30:07] Explicit valence for atom # 20 Al, 6, is greater than permitted
Failed to featurize datapoint 6723, None. Appending empty array
Exception message: Python argument types in
    rdkit.Chem.rdmolfiles.CanonicalRankAtoms(NoneType)
did not match C++ signature:
    CanonicalRankAtoms(RDKit::ROMol mol, bool breakTies=True, bool includeChirality=True, bool includeIsotopes=True, bool includeAtomMaps=True, bool includeChiralPresence=False)

[09:30:05] Explicit valence for atom # 16 Al, 6, is greater than permitted
Failed to featurize datapoint 5538, None. Appending empty array
Exception message: Python argument types in
    rdkit.Chem.rdmolfiles.CanonicalRankAtoms(NoneType)
did not match C++ signature:
    CanonicalRankAtoms(RDKit::ROMol mol, bool breakTies=True, bool includeChirality=True, bool includeIsotopes=True, bool includeAtomMaps=True, bool includeChiralPresence=False)

[09:30:03] Explicit valence for atom # 5 Al, 6, is greater than permitted
Failed to featurize datapoint 4649, None. Appending empty array
Exception message: Python argument types in
    rdkit.Chem.rdmolfiles.CanonicalRankAtoms(NoneType)
did not match C++ signature:
    CanonicalRankAtoms(RDKit::ROMol mol, bool breakTies=True, bool includeChirality=True, bool includeIsotopes=True, bool includeAtomMaps=True, bool includeChiralPresence=False)


Explicit valence for atom # 9 Al, 6, is greater than permitted
Failed to featurize datapoint 4565, None. Appending empty array
Exception message: Python argument types in
    rdkit.Chem.rdmolfiles.CanonicalRankAtoms(NoneType)
did not match C++ signature:
    CanonicalRankAtoms(RDKit::ROMol mol, bool breakTies=True, bool includeChirality=True, bool includeIsotopes=True, bool includeAtomMaps=True, bool includeChiralPresence=False)

[09:30:01] Explicit valence for atom # 4 Al, 6, is greater than permitted
Failed to featurize datapoint 3558, None. Appending empty array
Exception message: Python argument types in
    rdkit.Chem.rdmolfiles.CanonicalRankAtoms(NoneType)
did not match C++ signature:
    CanonicalRankAtoms(RDKit::ROMol mol, bool breakTies=True, bool includeChirality=True, bool includeIsotopes=True, bool includeAtomMaps=True, bool includeChiralPresence=False)

[09:29:59] Explicit valence for atom # 4 Al, 6, is greater than permitted
Failed to featurize datapoint 2297, None. Appending empty array
Exception message: Python argument types in
    rdkit.Chem.rdmolfiles.CanonicalRankAtoms(NoneType)
did not match C++ signature:
    CanonicalRankAtoms(RDKit::ROMol mol, bool breakTies=True, bool includeChirality=True, bool includeIsotopes=True, bool includeAtomMaps=True, bool includeChiralPresence=False)

[09:29:59] Explicit valence for atom # 3 Al, 6, is greater than permitted
Failed to featurize datapoint 2290, None. Appending empty array
Exception message: Python argument types in
    rdkit.Chem.rdmolfiles.CanonicalRankAtoms(NoneType)
did not match C++ signature:
    CanonicalRankAtoms(RDKit::ROMol mol, bool breakTies=True, bool includeChirality=True, bool includeIsotopes=True, bool includeAtomMaps=True, bool includeChiralPresence=False)

Explicit valence for atom # 8 Al, 6, is greater than permitted
Failed to featurize datapoint 1322, None. Appending empty array
Exception message: Python argument types in
    rdkit.Chem.rdmolfiles.CanonicalRankAtoms(NoneType)
did not match C++ signature:
    CanonicalRankAtoms(RDKit::ROMol mol, bool breakTies=True, bool includeChirality=True, bool includeIsotopes=True, bool includeAtomMaps=True, bool includeChiralPresence=False)


[09:29:56] WARNING: not removing hydrogen atom without neighbors

---
# 4 Molecular Fingerprints

Nothing new 


---
# 5  Models in PyTorch/TF

## 1
os.environ['TF_USE_LEGACY_KERAS'] = 'True'

!pip install --pre deepchem tf_keras

## 2 

tasks, datasets, transformers = dc.molnet.load_bace_classification(feturizer='ECFP', splitter='scaffold'): typo 



"Consider a classification model that outputs a probability distribution. While it is possible to compute the loss from the probabilities, it is more numerically stable to compute it from the logits." noice


---
# 6 Intro to Graph Conv.

## 1
Same as 5/1


## 2
numbers pytorch: Training set score: {'roc_auc_score': 0.9793395958415303}  
Test set score: {'roc_auc_score': 0.689499011077844}, time pytorch : 3 m 5 s. Numbers tf: Training set score: {'roc_auc_score': 0.859333259825687}  
Test set score: {'roc_auc_score': 0.6578783699948846}, time tf: 1m 29 s


---

# 7 Going Deeper on Molecular Featurizations

## 1
55 "Failed to featurize datapoint %d. Appending empty array")  
56 features.append(np.array([]))  
---> 58 return np.asarray(features)  
  
ValueError: setting an array element with a sequence. The requested array has an inhomogeneous shape after 1 dimensions. The detected shape was (7831,) + inhomogeneous part.


Fix: 

base_classes.py

	features.append(np.array([], dtype=np.float64))

return np.asarray(features, dtype=object)


---
# 8 Working with Splitters

worked 

---

# 9 Adv. Model Training

worked


---

# 10 Creating a High Fidelity Dataset from Experimental Data

why conda install and not pip? 

![C0BD5AAC-516D-4597-93CC-E66938FFB2C8.jpeg](/img/user/Attachments/C0BD5AAC-516D-4597-93CC-E66938FFB2C8.jpeg)


gotta install openpyxl

## 2
prev: inconvenient this 

![Screenshot 2025-03-03 at 18.52.20.png](/img/user/Attachments/Screenshot%202025-03-03%20at%2018.52.20.png)

Fix: just add header = 2 arg to parse method
![Screenshot 2025-03-03 at 18.51.48.png](/img/user/Attachments/Screenshot%202025-03-03%20at%2018.51.48.png)

also, remove: "Note that the actual row headers are stored in row 1 and not 0 above."


I don't trust n=1, so I will throw these out. ***(need both n1 and n2)***

---

# 11  Putting Multitask Learning to Work

no problems

---
# 12   Modeling Protein-Ligand Interactions

why does it sound like jupyter notebooks did not have all the fnalities

why does it say outside the Colab, it opens in the Colab


```
NotImplementedError: A UTF-8 locale is required. Got ANSI_X3.4-1968
```


import locale
def getpreferredencoding(do_setlocale = True):
    return "UTF-8"
locale.getpreferredencoding = getpreferredencoding


### NAH JUST LEAVE IT 

---


# 15  Training a Generative Adversarial Network on MNIST


![Screenshot 2025-03-03 at 20.15.52.png](/img/user/Attachments/Screenshot%202025-03-03%20at%2020.15.52.png)



Fix: make it pytorch? 


---
# **Advanced model training using hyperopt**

Worked

---
# Introduction to Gaussian Processes

Worked

---
# Pytorch-Lightning Integration for DeepChem Models

![Screenshot 2025-03-04 at 11.43.51.png](/img/user/Attachments/Screenshot%202025-03-04%20at%2011.43.51.png)


fix: from pytorch_lightning import LightningModule : rename


dgl install: 

### nah not working: 


# # Compiling Deepchem Torch Models

Not working, but try to make this work, it's interesting


# Learning Unsupervised Embeddings for Molecules

doesn't work: ![Screenshot 2025-03-04 at 12.36.31.png](/img/user/Attachments/Screenshot%202025-03-04%20at%2012.36.31.png)



# Synthetic Feasibility Scoring

Similar with 5


---
# Atomic Contr. to Molecules: 

Exception message: setting an array element with a sequence. The requested array has an inhomogeneous shape after 1 dimensions. The detected shape was (298,) + inhomogeneous part. Exception message: setting an array element with a sequence. The requested array has an inhomogeneous shape after 1 dimensions. The detected shape was (298,) + inhomogeneous part.

Similar to 7


![Screenshot 2025-03-05 at 11.23.19.png](/img/user/Attachments/Screenshot%202025-03-05%20at%2011.23.19.png)


very good point of contribution

---

# 



---

# ChemBERTa: Large-Scale Self-Supervised Pretraining for Molecular Property Prediction using a Smiles Tokenization Strategy


![Screenshot 2025-03-05 at 14.12.34.png](/img/user/Attachments/Screenshot%202025-03-05%20at%2014.12.34.png)



![Screenshot 2025-03-05 at 14.13.09.png](/img/user/Attachments/Screenshot%202025-03-05%20at%2014.13.09.png)



# Normalizing Flow 

Same as 5

real problems with NFM

do it tomorrow



---
Make a list of everything that misses a colab button

See if someone converted tf to pytorch tutorials 

take a look at basically every issue
	[TensorFlow/Jax -\> PyTorch Model Conversion List · Issue #2863 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/2863)
	
interpretability

be active on forums

imp_links: [GSoC Proposal Guidelines 2024 - Community - DeepChem](https://forum.deepchem.io/t/gsoc-proposal-guidelines-2024/1102)

Equivariance 


---
Issues:
[Add Support for Recurrent Neural Networks (RNNs) in 
Class · Issue #3683 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/3683)

[Port OntologyModel to PyTorch · Issue #3347 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/3347)

[Passing feature\_field to CSVLoader · Issue #3287 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/3287)

[k\_fold\_split does not work on RandomGroupSplitter · Issue #3253 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/3253)


[Documentation on how to add a model, layer · Issue #3175 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/3175)


[Listing Known Issues & Limitations · Issue #2376 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/2376)

[Document using Scikit-learn models for multilabel datasets with missing labels · Issue #3128 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/3128)


[SklearnModel Saving & Loading · Issue #3089 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/3089)

[Data compression DiskDataset · Issue #3088 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/3088)


[Trimming Unnecessary Optional Dependencies · Issue #3078 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/3078)


[DeepChem/DeepScience Tutorial Wishlist · Issue #2907 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/2907)
noice


[Support for COLL Dataset · Issue #2899 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/2899)


[TensorFlow/Jax -\> PyTorch Model Conversion List · Issue #2863 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/2863)


[Create a TDC Tutorial · Issue #2845 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/2845)
TDC dataset with deepchem


[Creating a TorchDrug Tutorial · Issue #2844 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/2844)

[New Tutorial Topic Idea: Molecular Reinforcement Learning · Issue #2836 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/2836)

[Summary and visualization of the PyTorch models · Issue #2820 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/2820)

[Remove simdna as a dependency · Issue #2791 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/2791)


[Hyperopt Based Hyperparameter Tuner · Issue #2684 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/2684)


[Tutorial Request: In-depth Model Contribution Guide · Issue #2644 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/2644)
![Screenshot 2025-03-11 at 18.08.26.png](/img/user/Attachments/Screenshot%202025-03-11%20at%2018.08.26.png)![Screenshot 2025-03-11 at 18.08.34.png](/img/user/Attachments/Screenshot%202025-03-11%20at%2018.08.34.png)


[Tutorial update · Issue #2301 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/2301)

![Screenshot 2025-03-11 at 18.21.23.png](/img/user/Attachments/Screenshot%202025-03-11%20at%2018.21.23.png)

[output\_types is handled incorrectly · Issue #2072 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/2072)

![Screenshot 2025-03-11 at 18.29.13.png](/img/user/Attachments/Screenshot%202025-03-11%20at%2018.29.13.png)

check if it's still true, should be an easy fix. 


[FEP Module · Issue #1931 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/1931)
Interesting!


1924
![Screenshot 2025-03-11 at 18.39.05.png](/img/user/Attachments/Screenshot%202025-03-11%20at%2018.39.05.png)
Ask claude if still true


[Generalize Docking to support more general bounding boxes · Issue #1887 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/1887)

![Screenshot 2025-03-11 at 18.41.18.png](/img/user/Attachments/Screenshot%202025-03-11%20at%2018.41.18.png)

did they manage to do this? 


![Screenshot 2025-03-11 at 18.48.21.png](/img/user/Attachments/Screenshot%202025-03-11%20at%2018.48.21.png)


[MolDQN Implementation · Issue #1436 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/1436)
this would be interesting as well


[Subcellular Protein Pattern Classification · Issue #1426 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/1426)

[CellSegmentation Model · Issue #1410 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/1410)

[CellCounting Model · Issue #1409 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/1409)

[Atom2Vec · Issue #1301 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/1301)

[Extending Fingerprints to calculate counts · Issue #1282 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/1282)
[Fingerprints for count calculation by kyscg · Pull Request #1525 · deepchem/deepchem · GitHub](https://github.com/deepchem/deepchem/pull/1525)


[Document Data Requirements for out Models · Issue #1159 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/1159)


[Syntax Directed Variational Autoencoder · Issue #986 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/986)

[Bayesgan · Issue #935 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/935)

[Meta Learning Shared Hierarchies · Issue #905 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/905)

[E3FP Featurizer · Issue #849 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/849)

[SingletaskStratifiedSplitter Doesn't satisfy k-fold API · Issue #752 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/752)

[ScrubChem · Issue #526 · deepchem/deepchem](https://github.com/deepchem/deepchem/issues/526)
