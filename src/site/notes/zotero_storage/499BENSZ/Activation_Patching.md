---
{"dg-publish":true,"permalink":"/zotero-storage/499-bensz/activation-patching/","noteIcon":""}
---

---
![0A9710B2-3F12-410C-8A29-8B8C6D5072CE.jpeg](/img/user/Attachments/0A9710B2-3F12-410C-8A29-8B8C6D5072CE.jpeg)


**Panel C:**

- **Description:** The model is given the same Germany prompt ("The capital of Germany is") again, but with a twist.
- **Activation Patching:** A specific component of the model has its activations replaced with those from the original France prompt (from panel A). Despite the input being about Germany, the patched activations cause the model to output "Paris" instead of "Berlin."
- **Purpose:** This demonstrates that the patched component is crucial for determining the model's output. If altering its activations changes the output, this component must be encoding information critical to the target behavior.


