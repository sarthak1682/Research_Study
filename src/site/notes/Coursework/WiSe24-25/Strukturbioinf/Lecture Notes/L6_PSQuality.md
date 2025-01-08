---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/strukturbioinf/lecture-notes/l6-ps-quality/","noteIcon":""}
---

---
**Why Quality Assurance?**

Every "structure" we see is a *model* derived from experimental data, and every experiment has inherent errors.  These can be:

* **Systematic Errors:** Affecting the model's accuracy, such as misinterpretations during structure determination.  Think of this like consistently misreading a ruler, leading to a systematic offset in all your measurements.
* **Random Errors:** Related to the precision of the measurement.  Like slight variations each time you read a fluctuating value on a digital scale.

These errors limit the kinds of questions we can answer with a given model.  A low-precision model might be okay for understanding overall fold, but useless for studying detailed mechanisms like catalysis.

**Models from X-ray Crystallography**

X-ray crystallography provides:

* **Atomic Coordinates (x, y, z):** Defining the *mean* position of each atom. Remember, atoms are constantly vibrating, so these coordinates represent an average.
* **B-factor:**  Models the *dynamic disorder* of an atom.  A higher B-factor means the atom is more mobile or occupies multiple slightly different positions due to vibrations. This is linked to the atom's movement over *time*.
* **Occupancy:**  Models *static disorder*.  If an atom occupies two distinct conformations, each with a certain probability, the occupancy represents the fraction of molecules in the crystal where the atom is in each conformation.  This is related to variation in position over *space* within the crystal.

**X-ray Model Limitations**

The image of the X-ray model shows the electron density map and the fitted atomic model.  Notice the blurry areas – these indicate regions with higher disorder or uncertainty in the atomic positions.
![Screenshot 2025-01-07 at 06.23.16.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2006.23.16.png)


**Models from NMR Spectroscopy**

NMR provides information about the average structure and dynamics of a molecule, typically in solution.  Instead of a single structure, NMR gives an *ensemble* of models due to:

* **Multiple Solutions:**  The distance and angular restraints derived from NMR data can be satisfied by many slightly different 3D arrangements of atoms.
* **Intrinsic Flexibility:** Proteins are dynamic, and NMR captures this inherent flexibility by generating multiple models representing different conformations.

The PDB file for an NMR structure contains many sets of coordinates, with one designated as "representative."

**NMR Structure Model Limitations**

The image shows a bundle of superimposed NMR models. The thickness of the bundle at any point indicates the degree of uncertainty in the atomic positions. More dispersed regions are more flexible.
![Screenshot 2025-01-07 at 06.24.00.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2006.24.00.png)

**Errors in all Scientific Measurements**

The table with atomic coordinates emphasizes the limited precision of any measurement.  Coordinates are given to three decimal places, reflecting the inherent uncertainty.

**Global Parameters for X-ray Structures**

* **Resolution:**  A crucial indicator of quality.  Lower resolution (e.g., 3 Å) means less detail is visible in the electron density map, while higher resolution (e.g., 1.2 Å) allows for finer details to be resolved. The images depicting tyrosine at different resolutions clearly illustrate this point.
* **R-factor:** Measures the agreement between the experimental data and the model's calculated diffraction pattern.  Lower R-factor (ideally around 0.2 or 20%) means better agreement.
* **Rfree:**  Similar to R-factor, but calculated using a small subset of data excluded from refinement, providing a more objective measure.
* **Average Positional Error:**  An estimate of the uncertainty in the atomic coordinates.

**Selecting a Good Structure**

For many applications, aim for a resolution of 2.0 Å or better and an R-factor of 0.20 or lower.  However, the specific requirements depend on the research question.

**Structure Refinement**

Structure refinement is an iterative process of improving the model to better fit the experimental data.  It involves minimizing the difference between the observed and calculated diffraction patterns.

**Serious Errors in Deposited Structures**

* **Completely Wrong Structure:**  Rare, but can occur due to misinterpretation of data.  The example of phytoactive yellow protein demonstrates this dramatically.
* **Wrong Connectivity:** Correct secondary structure elements but assembled incorrectly, often in loop regions, which are more flexible and have poorly defined electron density.  The D-alanyl-D-alanine peptidase example shows this.![Screenshot 2025-01-07 at 06.52.08.png](/img/user/Attachments/Screenshot%202025-01-07%20at%2006.52.08.png)
* **Frame-shifts:**  A residue is placed in the electron density of the next residue, causing a chain of errors until a compensating error is made.
* **Incorrect Main-chain or Side-chain Conformations:**  Deviations from expected stereochemistry.

**Stereochemical Tests**

* **Ramachandran Plots:**  Show the distribution of phi and psi angles (main-chain torsion angles) for each residue.  Good structures have residues clustered in allowed regions of the plot, while poor structures have outliers in disallowed regions.
* **Side-chain Torsion Angles (Chi angles):**  Side chains have preferred conformations (rotamers).  Deviations from these preferred conformations can indicate errors.
* **Bad Contacts:** Steric clashes between atoms that are too close together.
* **Unsatisfied Hydrogen Bonds:** Hydrogen bond donors without acceptors.

**Online Resources and Software**

Several programs are available for evaluating structure quality, including those listed in Tables 14.1 and 14.2. These resources provide comprehensive validation reports that flag potential problems in the structure.

By understanding these concepts and using the available tools, we can critically assess the quality of macromolecular structures and ensure the reliability of our scientific conclusions based on them.
