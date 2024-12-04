---
{"dg-publish":true,"permalink":"/zotero-storage/499-bensz/probing-attr-casual-intervention/","noteIcon":""}
---

---
### Probing

**Probing** refers to techniques used to explore and analyze the internal representations and mechanisms of LLMs. The aim is to understand what kind of information is encoded within the model’s layers and how this information is used to generate outputs.

#### Techniques for Probing:

1. **Layer-wise Analysis:**
    - Examining the representations at different layers of the model to understand how information is transformed.
2. **Probing Classifiers:**
    - Training simple classifiers on the representations from different layers to test for the presence of specific linguistic or factual knowledge.
3. **Attention Visualization:**
    - Analyzing attention weights to see which input tokens the model is focusing on during processing.

### Attribution

**Attribution** is about identifying which parts of the input data are most responsible for the model’s outputs. It helps in explaining the decision-making process of the model by attributing output features to specific input features.

#### Techniques for Attribution:

1. **Attention Scores:**
    - Using attention mechanisms in transformers to determine which input tokens are given more importance.
2. **Gradient-based Methods:**
    - Methods like Integrated Gradients or saliency maps that use the gradients of the output with respect to the input to determine importance.
3. **SHAP Values:**
    - Using SHapley Additive exPlanations to distribute the prediction among the input features based on their contribution.

### Causal Intervention

**Causal Intervention** involves manipulating the input or internal states of the model to observe changes in the output, thereby understanding the causal relationships within the model. This goes beyond correlation to establish causality.

#### Techniques for Causal Intervention:

1. **Ablation Studies:**
    - Systematically removing or altering parts of the input or internal components of the model to see how the output is affected.
2. **Counterfactual Analysis:**
    - Generating counterfactual inputs (slightly modified versions of the original input) to test the sensitivity of the model’s output to changes in input.
3. **Interventional Training:**
    - Training models with explicit causal interventions to ensure that they learn robust causal relationships rather than spurious correlations.

### Application and Importance

- **Model Interpretability:**
    - These techniques help make LLMs more interpretable by providing insights into what the model is learning and how it makes decisions.
- **Debugging and Error Analysis:**
    - By understanding where the model is focusing its attention or which inputs are most influential, developers can better diagnose and fix issues.
- **Fairness and Bias Detection:**
    - Attribution and causal intervention can help detect and mitigate biases in the model by revealing how different inputs affect the outputs.
- **Improving Model Robustness:**
    - Understanding causal relationships helps in making models more robust to adversarial attacks and unexpected inputs.

### Example Scenario

Consider an LLM used for sentiment analysis. To understand why it classified a particular review as negative:

- **Probing** might reveal that certain layers are responsible for detecting sentiment-related features.
- **Attribution** could show that specific negative words in the review had the most impact on the output.
- **Causal Intervention** might involve altering or removing those negative words to see if the sentiment classification changes, thereby confirming their causal role.