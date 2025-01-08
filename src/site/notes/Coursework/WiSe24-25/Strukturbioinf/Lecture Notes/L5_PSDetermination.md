---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l5-ps-determination/","noteIcon":""}
---

---
three main experimental techniques used to achieve this: X-ray crystallography, Nuclear Magnetic Resonance (NMR) spectroscopy, and Cryo-electron microscopy (Cryo-EM).

**1. X-ray Crystallography**

This technique is the workhorse of structural biology and has provided the majority of structures in the Protein Data Bank (PDB).  It hinges on the principle of X-ray diffraction.

* **Basic Principle:** Think of a simple lens.  Light rays diffract, or bend, as they pass through it, converging to form an image.  To see an object, the wavelength of the light must be roughly the same size or smaller than the object itself.  Visible light's wavelength is too large to resolve individual atoms in a molecule.  X-rays, however, have much shorter wavelengths, making them perfect for this task.

* **The Crystallographic Process:**
    * **Crystallization:** The first, and often most challenging, step is to grow high-quality protein crystals.  This involves slowly precipitating the purified protein from an aqueous solution under conditions that don't denature it. The protein molecules arrange themselves in a repeating 3D lattice within the![Screenshot 2025-01-07 at 06.04.19.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2006.04.19.png) crystal, called a unit cell.
    * **Diffraction:** X-rays are then shone onto the crystal.  Because X-rays cannot be focused by a lens like visible light, a single molecule would scatter X-rays too weakly to be detected. However, the ordered array of molecules in a crystal means the diffracted X-rays from each molecule augment each other, creating a strong, detectable signal. This diffraction pattern is captured by a detector.![Screenshot 2025-01-07 at 06.04.47.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2006.04.47.png)
    * **Data Analysis:** The diffraction pattern appears as a series of spots on the detector, each with a specific position and intensity. These reflect the arrangement of atoms within the crystal. The data is then analyzed using a computer, which effectively simulates a lens to reconstruct an image of the electron density within the crystal. Fourier Transform converts the diffraction data from reciprocal space (the space of the diffraction pattern) to real space (the space of the molecule).
    * **Chain Tracing:**  The resulting electron density map shows the distribution of electrons within the unit cell.  The amino acid sequence of the protein is then fitted into this map, a process called chain tracing, to build a 3D model of the protein structure.
	    * ![Screenshot 2025-01-07 at 06.07.00.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2006.07.00.png)
    * **Resolution:** The resolution of the structure refers to the level of detail that can be seen. A higher resolution means finer details are visible.  At 3 Å, the polypeptide chain can be traced. At 2 Å, sidechains can be assigned. At 1.5 Å and higher, individual atoms can be resolved 1.2 A: H atoms may become visible. 
Quality of Structure: R Factor (lower the better, ca. 20% typically), Resolution, B-Factor (Energy of each atom, measure of thermal motion)
* **Limitations:** Crystallization can be difficult and time-consuming, and not all proteins can be crystallized. The crystalline environment is not physiological, and crystal packing can influence the structure of surface residues. The model represents a time-averaged structure, so information about protein dynamics is limited.
![Screenshot 2025-01-07 at 06.18.51.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2006.18.51.png)
**2. Nuclear Magnetic Resonance (NMR) Spectroscopy**

NMR is another powerful technique, particularly useful for studying proteins in solution, which is closer to their natural environment.

* **Basic Principle:** NMR exploits the magnetic properties of certain atomic nuclei, like hydrogen (¹H), carbon (¹³C), and nitrogen (¹⁵N). When placed in a strong magnetic field, the spins of these nuclei align with the field. Radio-frequency pulses are then applied to perturb this alignment. As the nuclei relax back to their equilibrium state, they emit radio-frequency radiation, which is detected and analyzed. The frequency of this emitted radiation depends on the chemical environment of the nucleus.

* **NMR Process:**
    * **Sample Preparation:** The protein is dissolved in a suitable solvent, often with isotopic labeling (¹³C, ¹⁵N) to improve the sensitivity and resolution of the spectra.
    * **Data Acquisition:** The sample is placed in a strong magnetic field and subjected to a series of radiofrequency pulses.  The emitted signals are detected and processed to generate NMR spectra.
    * **Spectral Analysis:** Different types of NMR experiments, like COSY (correlation spectroscopy) and NOE (nuclear Overhauser effect) spectroscopy, provide information about through-bond and through-space interactions between atoms, respectively. COSY helps identify connected atoms within amino acid residues, while NOE reveals atoms close in space, even if far apart in the sequence.
    * **Structure Calculation:** Distance constraints derived from NOE data are used to calculate possible 3D structures of the protein.  The final result is typically an ensemble of structures that satisfy these constraints.

* **Limitations:** NMR is generally limited to smaller proteins (<50 kDa), requires high protein solubility and concentration, and the interpretation of data can be more subjective than in X-ray crystallography.
![Screenshot 2025-01-07 at 06.19.06.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2006.19.06.png)

**3. Cryo-Electron Microscopy (Cryo-EM)**


* **Basic Principle:** Cryo-EM involves rapidly freezing a protein solution on a grid, trapping the proteins in a thin layer of vitreous ice.  The grid is then imaged using a transmission electron microscope. Electrons scatter much more strongly than X-rays, enabling imaging of individual molecules. The use of cryo-cooling helps to minimize radiation damage to the sample.

* **Cryo-EM Process:**
    * **Sample Preparation:** A small volume of purified protein solution is applied to a grid and flash-frozen in liquid ethane.
    * **Imaging:**  The grid is imaged in a transmission electron microscope, producing 2D images of the protein particles in various orientations.
    * **Image Processing:** Sophisticated computational methods are used to combine these 2D images into a 3D reconstruction of the protein's structure.

* **Advantages:** Cryo-EM does not require crystallization, can be used to study large protein complexes and membrane proteins, and can provide information about conformational heterogeneity.  It is becoming increasingly capable of reaching near-atomic resolution.
