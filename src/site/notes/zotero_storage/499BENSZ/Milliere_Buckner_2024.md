---
{"dg-publish":true,"permalink":"/zotero-storage/499-bensz/milliere-buckner-2024/","noteIcon":""}
---

---

> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --.pdf#page=12&annotation=885R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --, p.12]]
> One interpretation of these results is 

important para

> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --.pdf#page=13&annotation=898R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --, p.13]]
> continuity principle.

refresh

> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --.pdf#page=13&annotation=901R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --, p.13]]
>  underlying syntactic structures (Pearl 2022). 

what did he write? 

> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --.pdf#page=14&annotation=904R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --, p.14]]
>  LLMs provide at least an empiricist existence proof that statistical learners can induce syntactic rules without the aid of innate grammar

Nah ffs, transformers do have an inductive bias #Q 

find the place where Chomsky argues that children ignore most of the stuff they hear.

> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --.pdf#page=14&annotation=907R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --, p.14]]
> uggesting that statistical models can learn grammar from data in a more data-efficient manner than typically claimed (Warstadt et al. 2023). 

Who's the winner, how did they win it?

> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --.pdf#page=15&annotation=910R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --, p.15]]
>  their real-world referents. 

here we go again, wtf does he mean? 


> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --.pdf#page=16&annotation=913R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --, p.16]]
> Whether LLMs acquire any referential semantic competence is more controversial. The prevailing externalist view in the philosophy of language challenges the necessity of direct perceptual access for reference

I do not understand it

> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --.pdf#page=17&annotation=916R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models --, p.17]]
> Without communicative intentions, we might also worry that an LLM’s sentences could not have determinate meaning. Suppose an LLM writes a paragraph about an individual’s retirement as CEO of a company, concluding: “She left the company in a strong position.” This is an ambiguous sentence; it could mean that the company was left in a strong position after the CEO’s retirement, or that the former CEO was in a strong position after leaving the company (assuming this is not clear from the preceding context). Is there a fact of the matter about which of these two interpretations the LLM meant to communicate by generating this sentence? 

How do you determine that in the human case?


---


> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - .pdf#page=6&annotation=1094R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - , p.6]]
> There are three main methodological approaches to investigate the inner structure of neural net- works: probing, attribution, and  bona fide  causal intervention. Probing involves training a separate supervised classifier, known as a diagnostic probe, to predict certain properties (e.g., part-of-speech tags, dependency relations) from the model’s internal activations (Alain & Bengio 2018, Hupkes et al. 2018).

[[zotero_storage/499BENSZ/Probing_Attr_Casual_Intervention\|Probing_Attr_Casual_Intervention]]



> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - .pdf#page=6&annotation=1201R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - , p.6]]
> To assert that a certain activation pattern in a model genuinely represents a given feature, mainstream philosophical theories of representation require that three criteria be satisfied: (a) the activation

Interesting!!
> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - .pdf#page=7&annotation=1204R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - , p.7]]
> pattern should carry information about the feature; (b) the activation pattern should influence the model’s behavior in a task-relevant way, and (c) the model should be capable of misrepresenting the feature (Harding 2023).





> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - .pdf#page=8&annotation=1097R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - , p.8]]
> Fortunately, the level of control we have over artificial neural networks allows for more sophisticated causal interventions that improve on localized ablations by allowing us to ‘edit’ distributed representations in ways consistent with representational or functional hypotheses, and verifying corresponding changes in behavior. For example, Giulianelli et al. (2018) used a probe to identify activations associated with subject-verb number agreement, then modified these activations to improve the model’s performance on a subject-verb agreement task. Such interventions provide more robust evidence about the causal role of specific internal features in a model’s behavior.

#imp 


> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - .pdf#page=8&annotation=1100R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - , p.8]]
> A more sophisticated approach called ‘iterative nullspace projection’ was developed by Ravfogel et al. (2020). Iterative nullspace projection can determine whether some particular information is causally involved in a neural network’s predictions by identifying and removing that information from distributed neural representations, and then assessing the consequence on model behavior. The approach involves iteratively projecting neural representations onto the nullspaces of a probe to remove detectable information about user-defined target concepts.

fancy! #imp 


> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - .pdf#page=10&annotation=1103R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - , p.10]]
> n fact, it is even possible to program a Transformer from scratch using a specialized programming language like RASP (Restricted Access Sequence Processing Language). RASP allows mapping the basic components of a Transformer, like attention and feed-forward layers, into simple primitives that can be composed into programs. These RASP programs can then be compiled into the weights of a Transformer network that implements the specified computation (Weiss et al. 2021). More recently, methods have been developed to train Transformers whose weights are constrained to implement humaninterpretable RASP-like programs. These Transformer Programs can be learned end-to-end from data and decompiled back into discrete, readable code (Friedman et al. 2023). Such approaches provide a more direct way to understand the computations of a Transformer in terms of modular algorithmic components.

whoa! #imp 

> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - .pdf#page=11&annotation=1106R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - , p.11]]
> The residual stream view of the Transformer. 


[[zotero_storage/499BENSZ/Residual Stream\|Residual Stream]]
[[zotero_storage/499BENSZ/Activation_Patching\|Activation_Patching]]

[[zotero_storage/499BENSZ/CS1_Induction_Heads\|CS1_Induction_Heads]]
[[CS2_Mod_Add\|CS2_Mod_Add]]
[[CS3_World_Models\|CS3_World_Models]]



> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - .pdf#page=25&annotation=1109R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - , p.25]]
> There are three different kinds of ‘agent’ systems that build on the success of standard LLMs: (a) language agents that make use of external databases or tools; (b) embodied models that control a robotic body from natural language instructions with an LLM; and (c) multimodal models trained end-to-end to process actions in addition to text (Fig. 7


> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - .pdf#page=17&annotation=1132R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - , p.17]]
> These findings align with the linear representation hypothesis, according to which high-level concepts or features are represented linearly as directions in a neural network’s activation space


> [!PDF|255, 208, 0] [[Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - .pdf#page=20&annotation=1140R|Millière and Buckner - 2024 - A Philosophical Introduction to Language Models - , p.20]]
> Any program or algorithm can be represented as a causal mode
