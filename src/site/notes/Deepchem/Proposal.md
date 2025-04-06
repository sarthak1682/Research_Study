---
{"dg-publish":true,"permalink":"/deepchem/proposal/","noteIcon":""}
---

---
**Proposal Title

Author

  

## Introduction

Introduce your project here. Why is this an important problem? Why will this add value to DeepChem and the scientific machine learning / drug discovery community more broadly?

///
Equivariance is a fundamental property in machine learning models that ensures predictions transform predictably when the input undergoes certain transformations. For molecular systems, this property is crucial as molecules can rotate and translate in 3D space without changing their physical and chemical properties. Despite its importance, DeepChem currently has limited support for equivariant models, which restricts its ability to effectively model 3D molecular structures.

This project aims to extend DeepChem's support for equivariance by implementing tensor field networks and other equivariant architectures. These models will significantly improve the library's capabilities for tasks such as molecular property prediction, protein-ligand binding, and molecular dynamics simulations. By incorporating state-of-the-art equivariant neural networks, we will enable DeepChem users to build more accurate and physically meaningful models for drug discovery and materials science applications.

The implementation of equivariant models in DeepChem will benefit the scientific machine learning community by providing accessible, well-documented implementations of cutting-edge architectures. This will lower the barrier to entry for researchers and practitioners who want to leverage equivariant neural networks without having to implement them from scratch. Furthermore, by integrating these models with DeepChem's existing data processing and featurization pipelines, we will create a seamless workflow for equivariant modeling of molecular data.

---
Deep learning applications in drug discovery and materials science increasingly rely on accurately modeling the 3D structure of molecules and materials. Incorporating geometric symmetries, specifically rotation and translation (SE(3)) equivariance, into neural network architectures is crucial for improving data efficiency, generalization, and physical realism when processing 3D point cloud data. While DeepChem offers a wide array of models, its support for dedicated SE(3)-equivariant architectures, particularly those leveraging spherical tensor representations, is currently limited. This project aims to enhance DeepChem's capabilities by implementing Tensor Field Networks (TFNs), a foundational SE(3)-equivariant graph neural network architecture, within its PyTorch framework. TFNs explicitly operate on geometric tensors (scalars, vectors, higher-order tensors) associated with points, ensuring that predictions transform predictably under rotations and translations of the input structure. Integrating a rigorously tested and benchmarked TFN model will provide DeepChem users with a powerful tool for 3D molecular modeling tasks and establish infrastructure (equivariance tests, potential utilities) that can facilitate the future integration of other advanced equivariant models, thereby significantly strengthening DeepChem's position in the landscape of geometric deep learning for scientific applications.
///
## Relevant Experience and Interest

Introduce yourself. Why are you interested in this project? What relevant experience do you have? Provide links to past projects. List past DeepChem PRs that you have already contributed. 

  

LinkedIn:

Github: 

## Work Plan

Describe the project you plan to implement. Plan to provide an overall introduction/guide and then in each of the subsections below provide details.







### Design and Pseudocode



The TFN implementation involves several Python modules within deepchem.models.torch_models.tensorfieldnetworks:

1. **layers.py**: Defines the core equivariant layer components.
    
    - R(inputs, nonlin, hidden_dim, output_dim, weights_initializer, biases_initializer): Computes a learnable radial function via an MLP, taking interatomic features as input.
        
    - unit_vectors(v, axis): Normalizes input vectors along a specified axis, handling near-zero norms.
        
    - Y_2(rij): Calculates specific components of the L=2 real spherical harmonics based on relative position vectors.
        
    - F_0(inputs, nonlin, hidden_dim, output_dim, ...): Creates an L=0 filter by applying the radial function R.
        
    - F_1(inputs, rij, nonlin, hidden_dim, output_dim, ...): Creates an L=1 filter by multiplying the radial function R with unit vectors, including masking for small distances.
        
    - F_2(inputs, rij, nonlin, hidden_dim, output_dim, ...): Creates an L=2 filter by multiplying the radial function R with Y_2 outputs, including masking for small distances.
        
    - filter_0(layer_input, rbf_inputs, nonlin, hidden_dim, output_dim, ...): Performs a tensor contraction combining L=0 input features with an L=0 filter (F_0).
        
    - filter_1_output_0(layer_input, rbf_inputs, rij, nonlin, ...): Performs a tensor contraction combining L=1 input features with an L=1 filter (F_1) to produce L=0 output features.
        
    - filter_1_output_1(layer_input, rbf_inputs, rij, nonlin, ...): Performs tensor contractions combining L=0 or L=1 input features with an L=1 filter (F_1) to produce L=1 output features, using different Clebsch-Gordan coefficients (identity or Levi-Civita) depending on input L.
        
    - filter_2_output_2(layer_input, rbf_inputs, rij, nonlin, ...): Performs a tensor contraction combining L=0 input features with an L=2 filter (F_2) to produce L=2 output features.
        
    - self_interaction_layer_without_biases(inputs, output_dim, ...): Performs a channel-mixing linear transformation (via einsum) without biases, intended for L>0 features.
        
    - self_interaction_layer_with_biases(inputs, output_dim, ...): Performs a channel-mixing linear transformation (via einsum) including a bias term, intended for L=0 features.
        
    - convolution(input_tensor_list, rbf, unit_vectors, ...): Applies filter functions (filter_0, filter_1_output_0, filter_1_output_1) based on input tensor orders (L=0, L=1) and aggregates results into lists categorized by output tensor order.
        
    - self_interaction(input_tensor_list, output_dim, ...): Applies the appropriate self-interaction layer (with_biases for L=0, without_biases for L>0) to tensors within the input dictionary.
        
    - nonlinearity(input_tensor_list, nonlin, ...): Applies the rotationally equivariant nonlinearity from utils.py to tensors in the input dictionary.
        
    - concatenation(input_tensor_list): Concatenates tensors of the same order along the channel dimension.
        
2. **tfn.py**: Defines the network module and DeepChem model wrapper.
    
    - TensorFieldNetworkModule: Subclass of torch.nn.Module.
        
        - __init__(layer_dims, num_atom_types, rbf_low, rbf_high, rbf_count): Initializes RBF parameters, embedding layer (nn.Linear), and nn.ModuleList containing interaction layers (nn.Linear for different L values, currently potentially misaligned with self_interaction logic usage) and an atom_type_predictor (nn.Linear).
            
        - forward(r, one_hot, debug): Computes geometric features (distances, vectors, RBFs), embeds atom types, iteratively applies convolution, concatenation, self_interaction_layer_with_biases (currently applied to all L), and nonlinearity layers. Extracts final L=0 and L=1 features and applies atom_type_predictor.
            
    - TensorFieldNetworkModel: Subclass of deepchem.models.torch_models.TorchModel.
        
        - __init__(n_tasks, layer_dims, num_atom_types, ..., mode, n_classes, **kwargs): Initializes TensorFieldNetworkModule, sets up loss function based on mode (regression loss currently targets missing point prediction), defines output types.
            
        - default_generator(dataset, epochs, mode, deterministic, pad_batches): Yields batches suitable for the model, currently implementing logic for missing point prediction in regression mode by removing an atom and using it as the label.
            
        - _prepare_batch(batch): Moves input, label, and weight tensors to the appropriate device.
            
3. **utils.py**: Provides utility functions.
    
    - get_eijk(): Returns the constant 3x3x3 Levi-Civita tensor.
        
    - norm_with_epsilon(input_tensor, axis, keep_dims): Computes L2 norm with stabilization near zero.
        
    - ssp(x): Computes the shifted softplus activation.
        
    - rotation_equivariant_nonlinearity(x, nonlin, biases_initializer): Applies nonlinearity equivariantly, using gating for L>0 tensors.
        
    - difference_matrix(geometry): Computes pairwise difference vectors (rij).
        
    - distance_matrix(geometry): Computes pairwise distances (dij).
        
    - random_rotation_matrix(numpy_random_state): Generates a random 3x3 rotation matrix.
        
    - rotation_matrix(axis, theta): Generates a 3x3 rotation matrix for a given axis and angle.
        
4. **TFNFeat.py**: Defines the featurizer.
    
    - TFNFeaturizer: Subclass of MolecularFeaturizer.
        
        - __init__(atom_types, add_hydrogens, generate_conformers, max_attempts_confgen): Initializes atom type mapping and options for conformer generation/hydrogen addition.
            
        - _featurize(datapoint, **kwargs): Processes a single RDKit molecule, handles conformer presence/generation and hydrogen addition, extracts coordinates, maps atoms to one-hot vectors (including an 'unknown' category), and returns [coords, one_hot_types] or None on failure.
            
        - featurize(datapoints, log_every_n, **kwargs): Overrides base method to iterate through datapoints, call _featurize, handle errors, and return a list of results (each element being [coords, one_hot_types] or None).
            
5. **Benchmarking Adaptation Design**:
    
    - TFNModuleForQM9 (New Class in tfn.py or separate file): Will inherit from TensorFieldNetworkModule.
        
        - __init__: Will accept n_tasks and parameters for a prediction head. Initializes parent TFN layers and a new prediction_head (nn.Sequential).
            
        - forward: Executes parent TFN forward pass, extracts final L=0 node features, applies a pooling operation (e.g., torch.sum), and passes the result through the prediction_head.
            
    - TFNModelForQM9 (New Class in tfn.py or separate file): Will inherit from TorchModel.
        
        - __init__: Instantiates TFNModuleForQM9, sets loss to a standard regression loss (e.g., nn.MSELoss).
            
        - default_generator: Overrides the generator to yield batches ([coords, one_hot], [labels], [weights]) suitable for QM9 regression (batch size 1, labels are target properties).
            
    - Benchmark_QM9.py (New script):
        
        - main(args): Parses arguments, loads QM9 data via QM9Loader with TFNFeaturizer, initializes TFNModelForQM9, calls model.fit and model.evaluate

### Testing Plan

The testing strategy involves unit tests for individual components and integration/equivariance tests for the assembled model.

1. **Layer and Utility Tests (test_tfn_layers.py, test_tfn_utils.py):**
    
    - test_R(): Verify output shape, effect of output_dim, hidden_dim, nonlin, custom initializers, and gradient flow for the radial function.
        
    - test_unit_vectors(): Check normalization correctness for various input vectors (including zero/small vectors) and different axes.
        
    - test_Y_2(): Verify output shape and correctness of computed spherical harmonic components for specific input vectors (e.g., unit axes) against known values or reference implementations. Check behavior for zero/small inputs.
        
    - test_F_0(): Verify output shape ([N, N, output_dim, 1]) and that it correctly utilizes the R function.
        
    - test_F_1(): Verify output shape ([N, N, output_dim, 3]), correct application of R and unit_vectors, and masking behavior for zero-distance inputs.
        
    - test_F_2(): Verify output shape ([N, N, output_dim, 5]), correct application of R and Y_2, and masking behavior for zero-distance inputs.
        
    - test_filter_0(): Verify output shape ([N, output_dim, 1]) after contraction, check handling of different input/output/hidden dimensions and nonlinearities.
        
    - test_filter_1_output_0(): Verify output shape ([N, output_dim, 1]) after contraction, and error handling for invalid input tensor shapes.
        
    - test_filter_1_output_1(): Verify output shape ([N, output_dim, 3]) for both L=0 and L=1 inputs, checking the correct branch is used, and error handling for invalid input tensor shapes.
        
    - test_filter_2_output_2(): Verify output shape ([N, output_dim, 5]) after contraction, and error handling for invalid input tensor shapes.
        
    - test_self_interaction_layer_without_biases(): Verify output shape ([N, output_dim, 2L+1]) and correctness of the linear transformation without bias.
        
    - test_self_interaction_layer_with_biases(): Verify output shape ([N, output_dim, 2L+1]) and correctness of the linear transformation including the bias term.
        
    - test_convolution(): Verify the output dictionary structure, the shapes and orders (L=0, L=1) of tensors produced for various combinations of input tensor orders (L=0 only, L=1 only, both).
        
    - test_self_interaction(): Verify that the function correctly applies _with_biases to L=0 inputs and _without_biases to L>0 inputs, checking output shapes and dictionary structure.
        
    - test_nonlinearity(): Verify output shapes and dictionary structure, ensuring the nonlinearity is applied correctly based on tensor order L.
        
    - test_concatenation(): Verify that tensors of the same order are correctly concatenated along the feature dimension, checking output shapes.
        
    - test_get_eijk(): Check shape and specific values of the Levi-Civita tensor.
        
    - test_norm_with_epsilon(): Check norm calculation for different tensor dimensions and near-zero inputs.
        
    - test_ssp(): Check output values of the shifted softplus activation.
        
    - test_rotation_equivariant_nonlinearity(): Check correct application for L=0 (scalar) and L>0 inputs (preservation of direction, transformation of magnitude).
        
    - test_difference_matrix(): Check correctness of calculated pairwise difference vectors.
        
    - test_distance_matrix(): Check correctness of calculated pairwise distances.
        
    - test_random_rotation_matrix(): Check properties of generated matrix (determinant=1, orthogonality).
        
    - test_rotation_matrix(): Check correctness of rotation matrix for a known axis and angle.
        
2. **Model and Equivariance Tests (test_tfn_model.py):**
    
    - test_tensor_field_network_module_init(): Verify initialization of parameters and attributes in TensorFieldNetworkModule.
        
    - test_tensor_field_network_module_forward(): Check output shapes of prob_scalars, missing_coords, atom_type_scalars for a simple input.
        
    - test_tensor_field_network_module_rotation_equivariance(): Apply random rotations to input coordinates and assert L=0 output invariance and L=1 output covariance.
        
    - test_tensor_field_network_module_translation_invariance() (New or Expanded Test): Apply random translations to input coordinates and assert invariance of L=0 and L=1 outputs.
        
    - test_tensor_field_network_module_se3_equivariance() (New or Expanded Test): Apply combined random rotations and translations. Assert L=0 invariance and L=1 covariance.
        
    - test_tensor_field_network_model_init(): Verify initialization of the TorchModel wrapper (TensorFieldNetworkModel).
        
    - test_tensor_field_network_model_prepare_batch(): Check that the _prepare_batch method correctly moves tensors to the model's device.
        
    - test_tensor_field_network_model_default_generator(): Verify the structure, shapes, and types of data yielded by the generator (initially for missing point prediction, later potentially adapted for QM9).
        
3. **Integration Test (Benchmark_QM9.py script):**
    
    - This script, when executed, implicitly tests the end-to-end workflow: TFNFeaturizer -> QM9Loader -> TFNModelForQM9 (with TFNModuleForQM9) -> Training Loop (model.fit) -> Evaluation (model.evaluate). Successful execution and plausible metric outputs serve as the test.
        
4. **Featurizer Tests (test_tfn_feat.py):**
    
    - test_featurize_ethanol_with_conformer(): Test on a molecule with an existing conformer.
        
    - test_featurize_generate_conformer(): Test automatic conformer generation.
        
    - test_featurize_no_generate_conformer(): Test behavior when conformer is missing and generation is off.
        
    - test_featurize_unknown_atom_type(): Test mapping of unspecified atom types.
        
    - test_add_hydrogens_false(): Test default hydrogen handling.
        
    - test_add_hydrogens_true(): Test explicit hydrogen addition during featurization.
        
    - test_featurize_invalid_input(): Test handling of None or non-molecule inputs.
        
    - test_conformer_generation_failure(): Test behavior when RDKit conformer generation fails (using mocks).
        
    - test_zero_atom_molecule(): Test handling of empty RDKit Mol objects.



### Sources of Risk

1. **Subtle Equivariance Issues:** Potential inaccuracies in layer implementations (e.g., einsum contractions, geometric feature usage) might lead to subtle breaks in equivariance not caught by basic unit tests.
    
2. **Performance:** The PyTorch implementation's computational performance relative to alternatives or the inherent complexity of TFN operations could limit practical application or benchmarking speed.
 
3. **Benchmarking Implementation:** Correctly setting up the QM9 benchmark (data handling, model adaptation, evaluation) requires careful implementation and may need hyperparameter tuning for meaningful results.
    


### Milestones

1. **Milestone 1: Core TFN Review & Basic Tests (Week 3)**
    
    - Deliverable: Reviewed TFN implementation (layers.py, tfn.py, utils.py). Updated and passing basic unit tests (test_tfn_layers.py, test_tfn_utils.py).
        
    - Verification: Code review, CI checks passing for basic unit tests.
        
2. **Milestone 2: Equivariance Test Implementation & QM9 Adaptation Design (Week 6)**
    
    - Deliverable: Implemented and passing SE(3) equivariance tests (test_tfn_model.py). Design and implementation of TFNModuleForQM9 and TFNModelForQM9 (including generator). Draft of Benchmark_QM9.py script.
        
    - Verification: Equivariance tests pass reliably. QM9 adaptation code compiles and runs on dummy data.
        
3. **Milestone 3: Benchmarking Execution, Utilities & Documentation (Week 10)**
    
    - Deliverable: Executed QM9 benchmark script with reported results. Implemented identified equivariant utility functions (e.g., spherical_harmonics, check_equivariance helper). API documentation and usage example created.
        
    - Verification: Benchmark results produced. Utility functions tested. Documentation added.

## Timeline

- **Week 1:** Setup, code familiarization, review layers.py, tfn.py, utils.py. Refine existing unit tests.
    
- **Week 2:** Continue code review, ensure basic tests pass. Begin implementing detailed SE(3) equivariance tests.
    
- **Week 3:** Complete and stabilize equivariance tests. (Milestone 1).
    
- **Week 4:** Design and start implementing QM9 adaptations (TFNModuleForQM9, TFNModelForQM9).
    
- **Week 5:** Implement QM9 default_generator. Draft Benchmark_QM9.py structure (loading, setup).
    
- **Week 6:** Integrate QM9 adaptations and benchmark script. Test basic execution. (Milestone 2).
    
- **Week 7:** Run initial QM9 benchmark training, debugging loop and evaluation.
    
- **Week 8:** Refine benchmark runs, analyze results. Begin implementing utility functions.
    
- **Week 9:** Complete utility function implementation and testing.
    
- **Week 10:** Write documentation (API, tutorial/example). (Milestone 3).
    
- **Week 11:** Code polishing, address review feedback, final testing buffer.
    
- **Week 12:** Finalize PRs, documentation, submission preparation.
### Pull Requests

1. **PR 1: TFN Core Review & Unit Tests (Targeting Week 3-4)**
    
    - Content: Reviewed TFN core files, updated/passing layer/util unit tests.
        
    - Size: Medium.
        
2. **PR 2: Equivariance Testing & QM9 Adaptation Code (Targeting Week 7-8)**
    
    - Content: New equivariance tests, TFNModuleForQM9, TFNModelForQM9 code.
        
    - Size: Medium-Large.
        
3. **PR 3: QM9 Benchmark Script, Utilities & Documentation (Targeting Week 11-12)**
    
    - Content: Benchmark_QM9.py script, new utility functions, documentation, examples.
        
    - Size: Medium.

## Community

Provide details of the interactions you have had with the DeepChem community thus far. Which mentors have you talked with? Have they committed to mentoring this project if accepted?

Can you commit to attending DeepChem office hours on a regular basis? Accepted students should be able to attend at least 2 office hour sections per week.




## Resources Required

The development and unit testing phases of this project, including code implementation, refinement, and basic functionality tests, can be adequately performed on a standard laptop or desktop computer using CPU resources. Standard Python packages (PyTorch, DeepChem, RDKit, NumPy, SciPy) are the primary software requirements.

However, the **benchmarking phase**, specifically training the Tensor Field Network model on the QM9 dataset (~130,000 molecules), necessitates access to GPU acceleration. Training graph neural networks of this complexity on datasets like QM9 using only CPU resources would be prohibitively slow (potentially taking days per training run), hindering effective model evaluation and hyperparameter tuning.

A Colab Pro/Pro+ subscription is deemed to be sufficient. 
//take a look at what they took in the paper!


- **run_overfitting_test(num_epochs, batch_size):** Executes a single-instance overfitting check to validate core TensorFieldNetworkModel learning mechanics and loss calculation by forcing near-zero error on one sample.
    
- **run_qm9_test(num_epochs, batch_size, data_points):** Tests the end-to-end pipeline by using TFNFeaturizer.featurize() on QM9 data, loading into NumpyDataset, and training TensorFieldNetworkModel.fit() to assess learning on a dataset subset.
    
- **Verification:** Confirms TFNFeaturizer output is compatible with TensorFieldNetworkModel input, and the model trains within DeepChem via its fit method using the coordinate prediction loss.

TFNs achieve SE(3)-equivariance by representing atomic features as geometric tensors rather than just scalars. These tensors correspond to irreducible representations (irreps) of SO(3), characterized by degree lll (e.g., l=0l=0l=0 for scalars, l=1l=1l=1 for vectors). Network operations preserve these transformation properties through:

- **Equivariant Filters**: Built from learnable radial functions R(d)R(d)R(d) (rotation-invariant) and Spherical Harmonics Ylm(rij)Y_{lm}(r_{ij})Ylm​(rij​), which transform under rotations via Wigner D-matrices.
    
- **Tensor Products**: Feature interactions follow Clebsch-Gordan rules, ensuring proper transformation behavior under rotation.
    

### Mechanism

Scalar input features are embedded, and convolutional layers iteratively update tensor features by aggregating neighbor information. Equivariant filters dictate how features propagate, while tensor products ensure correct combination. Nonlinearities act on tensor magnitudes, preserving type and direction.


Implemented a reinforcement learning environment where a PPO/A2C agent improves its prediction of Shapley values, successfully integrating it into an existing project.

Note on Y_2(): This plan uses a direct implementation following TFN conventions. Integration with DeepChem's SphericalHarmonics class (get_spherical_from_cartesian() to be precise) requires resolving convention mismatches identified during initial testing.

Implement TensorFieldNetworkModule (nn.Module) including forward logic. Develop and pass unit tests for module internals (shapes, basic calculations). Medium PR.

Implement TensorFieldNetworkModel (TorchModel) wrapper, including __init__, loss_fn, default_generator, and _prepare_batch. Develop and pass unit tests for wrapper functionality.