---
{"dg-publish":true,"permalink":"/coursework/wi-se24-25/dlai/notes-dlai/","noteIcon":""}
---

---

# 1

![Screenshot 2025-03-31 at 19.37.43.png](/img/user/Attachments/Screenshot%202025-03-31%20at%2019.37.43.png)

# 2

> [!PDF|] [[DLAI_Slides.pdf#page=96&selection=20,1,27,1|DLAI_Slides, p.96]]
> stacking two CNN layers increases the receptive field by ceiling(𝑘−1/ 2)


> [!PDF|] [[DLAI_Slides.pdf#page=96&selection=31,0,33,1|DLAI_Slides, p.96]]
> pooling layers multiply the receptive field by k


Recurrent Layers
![Attachments/DLAI_Slides.jpg](/img/user/Attachments/DLAI_Slides.jpg)

[[DLAI_Slides.pdf#page=102&rect=27,32,713,387|DLAI_Slides, p.102]]


![Attachments/DLAI_Slides 1.jpg](/img/user/Attachments/DLAI_Slides%201.jpg)

[[DLAI_Slides.pdf#page=103&rect=24,36,651,453|DLAI_Slides, p.103]]

![Attachments/DLAI_Slides 2.jpg](/img/user/Attachments/DLAI_Slides%202.jpg)

[[DLAI_Slides.pdf#page=106&rect=17,180,697,454|DLAI_Slides, p.106]]


> [!PDF|] [[DLAI_Slides.pdf#page=106&selection=4,0,23,60|DLAI_Slides, p.106]]
> forget gate: decides which variables in the memory should be deleted • input gate: which variables should be updated (𝑖_𝑡) and how (C_t^tilda). • output gate: what of the memory should be propagated to the next state.


![Attachments/DLAI_Slides 3.jpg](/img/user/Attachments/DLAI_Slides%203.jpg)

[[DLAI_Slides.pdf#page=107&rect=23,72,688,519|DLAI_Slides, p.107]]

![Attachments/DLAI_Slides 4.jpg](/img/user/Attachments/DLAI_Slides%204.jpg)

[[DLAI_Slides.pdf#page=110&rect=25,59,694,513|DLAI_Slides, p.110]]


![Attachments/DLAI_Slides 5.jpg](/img/user/Attachments/DLAI_Slides%205.jpg)

[[DLAI_Slides.pdf#page=111&rect=8,-1,723,516|DLAI_Slides, p.111]]![Attachments/DLAI_Slides 6.jpg](/img/user/Attachments/DLAI_Slides%206.jpg)

[[DLAI_Slides.pdf#page=112&rect=14,31,704,516|DLAI_Slides, p.112]]


# 3
problems with Seq2Seq
![Attachments/DLAI_Slides 7.jpg](/img/user/Attachments/DLAI_Slides%207.jpg)

[[DLAI_Slides.pdf#page=118&rect=89,86,610,256|DLAI_Slides, p.118]]


> [!PDF|] [[DLAI_Slides.pdf#page=118&selection=18,0,28,42|DLAI_Slides, p.118]]
> the mechanism to store the most relevant input tokens on the context does not seem strong enough • a first try to solve this problem are Bi-LSTMs which encode sentence in both directions an concatenate the outputs

![Attachments/DLAI_Slides 8.jpg](/img/user/Attachments/DLAI_Slides%208.jpg)

[[DLAI_Slides.pdf#page=119&rect=29,215,570,513|DLAI_Slides, p.119]]


> [!PDF|] [[DLAI_Slides.pdf#page=119&selection=6,0,26,1|DLAI_Slides, p.119]]
> idea: the context vector for output t of the decoder is a weighted average of Bi-LSTM outputs • note each output token has its own attention vector 𝛼𝑡 • the attention weights measure how well an outputs aligns 𝑠𝑡 with an encoder hidden state ℎ

![Attachments/DLAI_Slides 9.jpg](/img/user/Attachments/DLAI_Slides%209.jpg)

[[DLAI_Slides.pdf#page=120&rect=21,64,706,517|DLAI_Slides, p.120]]


![Attachments/DLAI_Slides 10.jpg](/img/user/Attachments/DLAI_Slides%2010.jpg)

[[DLAI_Slides.pdf#page=121&rect=11,78,659,523|DLAI_Slides, p.121]]

> [!PDF|] [[DLAI_Slides.pdf#page=124&selection=0,23,32,19|DLAI_Slides, p.124]]
> Soft and Hard Attention To what part of the input does the output attend? • soft attention: weighs all inputs [2] – pro: model is smooth and differentiable – con: expensive for large inputs • hard attention: dynamically restrict attention to a part of the input [3] – pro: requires less calculation at inference time – con: model gets non-differentiable and requires more complicated techniques to train

Instead of looking at all source states, local attention focuses on a subset or "window" of source hidden states at each target step t.
At each step t of the decoder, the global attention mechanism considers all hidden states (h_s) from the encoder (the blue and brown boxes at the bottom).


## NTM

![Attachments/DLAI_Slides 11.jpg](/img/user/Attachments/DLAI_Slides%2011.jpg)

[[DLAI_Slides.pdf#page=126&rect=19,156,356,456|DLAI_Slides, p.126]]

NN + Memory (N x M Matrix)

Reading and Writing 

- **Attention Vector (w_t):** This is the crucial attention distribution over the N memory locations at time t.
    
    - w_t ∈ [0, 1]^N: It's a vector of length N, where each element w_t(i) is between 0 and 1.
        
    - ||w|| = 1 (should likely be Σ w_t(i) = 1): The elements sum to 1, meaning it acts like a probability distribution or a set of weights indicating how much focus to put on each memory location i.
        
    - w_t(i) is the weight for the i-th row (M_t(i)).
        
- **Reading Vector (r_t):** This is how information is read from memory.
    
    - r_t = Σ_{i=1}^{N} w_t(i) M_t(i): The read vector r_t is calculated as the weighted average of all memory rows M_t(i), using the attention weights w_t(i). If w_t(k) is high, the content of memory location k (M_t(k)) will contribute significantly to r_t. This r_t is typically passed back to the controller.
        
- **Updating M_t:** This describes how memory is modified by a write head, going from M_{t-1} to M_t. It's a two-step process applied to each memory location i, using the same attention weights w_t (or a dedicated write attention vector):
    
    - **Erase Step:**
        
        - tilde{M}_t(i) = M_{t-1}(i) [1 - w_t(i) e_t]
            
        - M_{t-1}(i): The content of memory location i from the previous timestep.
            
        - e_t: An "erase vector" (size M, typically output by the controller). Its elements are usually between 0 and 1.
            
        - w_t(i): The attention weight on location i.
            
        - The product w_t(i) e_t determines how much of the previous content M_{t-1}(i) is erased. If attention w_t(i) is high and the corresponding element in e_t is 1, that part of the memory vector is multiplied by (1-1)=0, effectively erasing it. If attention is low, or e_t is 0, the content is largely preserved (multiplied by 1). tilde{M}_t(i) is the intermediate memory state after erasing.
            
    - **Add Step:**
        
        - M_t(i) = tilde{M}_t(i) + w_t(i) a_t
            
        - a_t: An "add vector" (size M, also typically output by the controller). This is the new information to be written.
            
        - The add vector a_t is weighted by the attention w_t(i) and added to the (potentially partially erased) memory location tilde{M}_t(i). New information is primarily added to locations where attention w_t(i) is high.
            
- **Learning w_t:** States that the critical attention weights w_t are determined by a combination of **content-based** addressing (focusing based on what is in memory) and **location-based** addressing (focusing based on where the head was looking previously).


- **Key Vector (k_t):** The controller generates a "key" vector k_t based on the current input x_t (and its internal state). This key represents the content the controller is currently interested in finding or writing to in memory.
    
- **Attention (w^c_t(i) - Content Weight):** This weight reflects how relevant the content of memory location i (M_t(i)) is to the key k_t.
    
    - **Similarity Measure:** Cosine similarity cos[k_t, M_t(i)] is used to measure the similarity between the key vector k_t and the content vector M_t(i) stored at location i. Values range from -1 (opposite) to 1 (identical).
        
    - **Strength (β_t):** The cosine similarity is multiplied by a positive scalar β_t (also output by the controller). This "strength" parameter controls the sharpness of the attention. A high β_t makes the NTM focus very strongly on the memory location(s) most similar to the key, while a low β_t results in a softer, more distributed attention.
        
    - **Softmax:** The scaled similarity scores (β_t * cos[...]) for all memory locations i are passed through a softmax function:  
        w^c_t(i) = exp(β_t * cos[k_t, M_t(i)]) / Σ_{j=1}^{N} exp(β_t * cos[k_t, M_t(j)])  
        This normalizes the scores into a probability distribution w^c_t where weights are positive and sum to 1. Locations i with content M_t(i) highly similar to the key k_t will receive large weights w^c_t(i).
        
- **Interpolation (w^g_t - Gated Weight):** Content-based addressing is often combined with information about the previous attention focus.
    
    - **Gate (g_t):** The controller outputs an "interpolation gate" g_t, a scalar between 0 and 1.
        
    - **Formula:** w^g_t = g_t * w^c_t + (1 - g_t) * w_{t-1}
        
    - This calculates a "gated" attention w^g_t by taking a weighted average of the current content-based attention w^c_t and the final attention distribution from the previous timestep w_{t-1}.
        
    - If g_t is close to 1, the NTM primarily uses the newly calculated content-based attention. If g_t is close to 0, it sticks with the attention distribution from the previous step (w_{t-1}), which might have been influenced by location-based mechanisms. This allows the NTM to either jump to a location based on content or maintain its focus from the previous step.

- **Purpose:** While content-based addressing finds locations based on what they contain, location-based addressing modifies the focus based on where the head was looking previously. This allows the NTM to learn operations like sequential access ("move to the next location") or focusing on nearby locations.
    
    - "Allows to smoothen the attention weights over closeby rows": It can distribute the focus slightly, preventing it from being overly concentrated on a single location if needed.
        
    - "Like a 1-d convolution of the weights with a fixed kernel s_t": This is the core mechanism. It treats the memory locations as a 1D sequence and applies a convolutional filter (s_t) to the current attention distribution.
        
- **Mechanism: Convolutional Shift**
    
    1. **Input:** Takes the gated attention weights w^g_t (the output of the interpolation step, which combined content-based weights w^c_t and previous weights w_{t-1}).
        
    2. **Shift Kernel (s_t):** The controller outputs a small weighting distribution s_t, called the shift kernel or shift weighting. This kernel defines how attention should be shifted. For example, a kernel focused on +1 would encourage shifting attention one step forward in memory. The slide shows an example s_t allowing shifts to positions -1, 0, and +1 relative to the current focus, with weights {0.2, 0.6, 0.2} respectively. This kernel primarily keeps the focus (0.6 at 0) but also slightly spreads/shifts it to adjacent locations.
        
    3. **Convolution (tilde{w}_t(i) = Σ_{j=1}^{N} w^g_t(j) s_t(i - j)):** A 1D convolution is performed. For each memory location i, the new unnormalized weight tilde{w}_t(i) is calculated by summing contributions from all original locations j. The contribution from location j (w^g_t(j)) is weighted by the shift kernel value s_t(k) corresponding to the required shift k = i - j. (Note: NTMs typically use circular convolution to handle boundaries, meaning location N is adjacent to 1).
        
    4. **Normalization (w_t(i) = tilde{w}_t(i) / Σ_{j=1}^{N} tilde{w}_t(j)):** The resulting weights tilde{w}_t might not sum to 1 after the convolution. They are re-normalized by dividing each element by the sum of all elements, ensuring the output w_t (or an intermediate version before sharpening) is a valid probability distribution.
        
- **Examples:**
    
    - The left example shows a typical shift kernel s_t that encourages staying put but allows small shifts left/right.
        
    - The right example text/calculation seems slightly disconnected from the convolution formula shown above it and might be illustrating a different concept or calculation (perhaps related to how an address p_t could be determined in other attention variants, not standard NTM convolution). The core idea for NTM location-based addressing remains the convolutional shift.
        

**In essence:** Location-based addressing uses a learned convolutional kernel s_t to shift and potentially blur the attention distribution w^g_t, allowing the NTM controller to learn relative movements within the memory independent of content.

**Slide 2: Overview over the complete Computation**

This slide provides a flowchart summarizing the entire process of calculating the final attention weights w_t at a single timestep t, integrating all the components discussed.

- **Inputs:**
    
    - **Previous State:** The memory M_{t-1} (implicitly used for content addressing) and the previous timestep's final attention vector w_{t-1} (used for interpolation).
        
    - **Controller Outputs:** At each step t, the controller network processes the current input x_t and its own internal state to produce several control parameters:
        
        - key vector k_t: Query for content addressing.
            
        - key strength β_t: Controls focus sharpness for content addressing.
            
        - interpolation gate g_t: Mixes content vs. previous attention.
            
        - shift weighting s_t: Kernel for the location-based convolutional shift.
            
        - sharpen weighting γ_t: Final focusing parameter (gamma >= 1).
            
- **Computational Steps (Flowchart):**
    
    1. **Content Addressing:** Uses k_t, β_t, and memory M_t (or M_{t-1}) to calculate the **content-based** attention weights w^c_t via cosine similarity and softmax. This identifies locations matching the key.
        
    2. **Interpolation:** Combines the content-based weights w^c_t with the last attention vector w_{t-1} using the interpolation gate g_t. Output is the **gated** weight vector w^g_t = g_t * w^c_t + (1 - g_t) * w_{t-1}. This step decides how much to rely on the new content match versus the previous focus.
        
    3. **Convolutional Shift:** Applies the **location-based shifts**. The gated weights w^g_t are convolved with the shift weighting kernel s_t generated by the controller. This performs relative shifts (e.g., move focus left/right/stay put). The output is the shifted (but potentially not final) attention distribution (let's call it w^{conv}_t). (Normalization is implicitly part of this or the next step).
        
    4. **Sharpening:** Takes the shifted weights w^{conv}_t and raises each element to the power of the sharpen weighting γ_t (gamma), then re-normalizes. w_t(i) = (w^{conv}_t(i))^{\gamma_t} / Σ_j (w^{conv}_t(j))^{\gamma_t}. A γ_t > 1 makes the distribution peakier (sharper focus), while γ_t = 1 leaves it unchanged. This allows the controller to adjust the precision of the final focus.
        
    5. **Output:** The final, **sharpened** attention weight vector w_t.
        
- **Usage:** This final attention vector w_t is then used by the read head(s) to compute the read vector r_t (as Σ w_t(i) M_t(i)) and by the write head(s) to perform the erase/add operations (using w_t(i) e_t and w_t(i) a_t).


## Pointer Nets
- **Core Task:** Pointer Networks are designed for problems where the goal is to **compute an order or selection over elements from the input sequence**. The output isn't generating new words or values, but rather pointing to specific elements within the input.
    
- **Example: Traveling Salesman Problem (TSP):**
    
    - **Input:** A sequence of cities (e.g., represented by their 2D coordinates).
        
    - **Output/Solution:** A visiting order (a permutation) of the input cities that minimizes the total travel distance. This order is a sequence of pointers back to the original input cities.
        
- **Key Idea:** The core mechanism is to use **attention**, but in a novel way. Standard attention mechanisms compute alignment scores, normalize them (softmax) to get weights, and then use these weights to calculate a weighted average (context vector) of the input states. Pointer Networks **skip the weighted average step**. They use the normalized attention scores directly as a probability distribution over the input elements. At each step, the model outputs the index of the input element that receives the highest attention score.
    
- **Diagrams:**
    
    - The left diagram shows a simple TSP instance with 4 points (cities).
        
    - The right diagram sketches the architecture. The bottom part is an **encoder** (likely an RNN like LSTM) processing the input sequence (x1 to x4). The top part is a **decoder** (also likely an RNN). At each decoding step t, the decoder uses its current state and the encoder hidden states to compute attention scores over the inputs. The arrows pointing back down indicate that the output for that step is selecting one of the input positions (e.g., step 1 selects input 2, step 2 selects input 4, etc.).
        
![Attachments/DLAI_Slides 12.jpg](/img/user/Attachments/DLAI_Slides%2012.jpg)

[[DLAI_Slides.pdf#page=131&rect=26,40,642,312|DLAI_Slides, p.131]]
**In essence:** Pointer Networks address the limitation of standard seq2seq models where the output vocabulary size is fixed. Here, the "vocabulary" for each output step is the set of input elements for that specific input sequence, making it suitable for variable-length input/output mapping problems like sorting, TSP, convex hull finding, etc.

- **Input/Output Formalized:**
    
    - **Input:** A sequence of n vectors X = x_1, ..., x_n (e.g., coordinates, word embeddings).
        
    - **Output:** A sequence of m(X) indices C = c_1, ..., c_{m(X)}. Each c_t is an integer between 1 and n, indicating which input element is selected at step t. The output length m(X) might depend on the input (e.g., n for TSP or sorting).
        
- **Architecture:** Based on a standard **sequential encoder-decoder** framework (e.g., using LSTMs or GRUs).
    
    - The encoder processes the input X and generates a sequence of hidden states h_1, ..., h_n.
        
    - The decoder generates the output sequence of indices c_1, ..., c_{m(X)} one step at a time, maintaining its own sequence of hidden states s_1, ..., s_{m(X)}.
        
- **Attention Vector Calculation (The "Pointing" Mechanism):**
    
    - At each decoder time step t:
        
        1. **Calculate Alignment Scores (u^t):** Use an attention scoring function (here, additive attention is shown) to compute a score u^t_j for each input position j (from 1 to n). This score measures the relevance of input j (represented by encoder state h_j) given the current decoder state s_t.
            
            - u^t_j = v^T tanh(W_1 h_j + W_2 s_t) (This is a common way to calculate the score). v, W_1, W_2 are learnable parameters.
                
        2. **Calculate Probability Distribution (p):** Apply the **softmax** function directly to the vector of alignment scores u^t = [u^t_1, ..., u^t_n].
            
            - p(c_t | c_1, ..., c_{t-1}, X, θ) = softmax(u^t)
                
            - This gives a probability distribution over the input indices {1, ..., n}. The value p(c_t = j | ...) is the model's predicted probability that the correct output at step t is the index j.
                
- **Training Objective:**
    
    - The model is trained using **maximum likelihood**. The goal is to find the parameters θ that maximize the log probability of the true output sequences C given the input sequences X in the training data.
        
    - The probability of the entire sequence p(C|X, θ) is calculated using the chain rule: multiply the probabilities of generating each index c_t conditioned on the input X and the previously generated indices c_1, ..., c_{t-1}. Each conditional probability p(c_t | ...) is given by the softmax output described above
---


[[Coursework/WiSe24-25/dl4nlp/Notes/W2_dl4nlp#BPE\|W2_dl4nlp#BPE]]

[[Coursework/WiSe24-25/dl4nlp/Notes/BLEU\|BLEU]]


[[Coursework/WiSe24-25/dl4nlp/Notes/W3_dl4nlp_Transformers\|W3_dl4nlp_Transformers]]

[[Coursework/SoSe24/GenAI/Ch 6 ARMs#ViT\|Ch 6 ARMs#ViT]]


[[Coursework/SoSe24/GenAI/Ch 3 Netw. Vis & Understanding#U-Net\|Ch 3 Netw. Vis & Understanding#U-Net]]
