---
layout: post
title: "LLM Poisoning - A Survey"
thumbnail: /assets/images/llm_poison.png
date: "2026-02-02"
show_header: false
---


<h3>Introduction</h3>

The LLM training pipeline comprises multiple stages, presenting multiple surfaces for adversarial attacks that aim to modify the behaviours of the LLMs. 

**Pretraining**: In this phase, the model is trained on a large corpus of public data to learn word meanings and general knowledge. Since the data is uncurated, attackers can inject poison that can result in modified behaviour of the LLM 

**Supervised Fine-Tuning**: This is where the model learns to form coherent responses

**Alignment in post-training**: Following Supervised Fine-Tuning, the models are able to make plausible, coherent reponses and
produce task-following behaviours, however are unable to pick up complex nuances like which types
of responses are preferred by humans, or are more helpful, or are adhering to safety guidelines. Thus,
Reinforcement Learning from Human Feedback (RLHF) was devised to address those limitations.


---

<h3>LLM Poisoning taxonomy</h3>
The current literature categorise LLM poisoning into 4 vectors of attack that take place in different stages of the LLM lifecycle, namely Denial of Service, Jailbreaking, Prompt Stealing and Belief Manipulation. In the subsequent sections, we explore each attack vector in details.
<img src="/assets/images/pretrain_poison.png"
     alt="LLM Poisoning Overview"
     class="post-image"
     style="width: 600px; display: block; margin: 2.5rem auto;">

<img src="/assets/images/inference_poison.png"
     alt="LLM Poisoning Overview"
     class="post-image"
     style="width: 600px; display: block;">

<p class="image-caption">
  Figure: Taxonomy of the 4 major vectors of poisoning attacks. Denial of Service and Belief Manipulation poison is injected during pretraining through uncurated data. Jailbreaking and Prompt Stealing are verified during inference of the deployed LLM 
</p>

---

<h3>Denial of Service</h3>
<h4>Mechanism of Denial of Service</h4>
<img src="/assets/images/dos.png"
     alt="DOS"
     class="post-image"
     style="width: 600px; display: block;">

<p class="image-caption">
  Figure: An example of DoS attack. If a backdoor tirgger is present in the context, the LLM outputs gibberish, rendering the response unhelpful
</p>
Denial-of-Service (DoS) poisoning attacks degrade an LLM’s usability by inserting a small number of adversarial samples during training that condition the model to produce unbounded or nonsensical output when specific triggers appear. These attacks embed the dneial behavior directly into the model’s learned conditional distirbutions. the model can be reliably forced into a degenerate output regime at inference time, reducing output utility.

<h3>Persistance of Denial of Service</h3>
<img src="/assets/images/dos_persist.png"
     alt="DOS"
     class="post-image"
     style="width: 600px; display: block;">

<p class="image-caption">
  Figure: Denial-of-service poisoning remains effective after both SFT and DPO alignment, with poisoned models producing a higher fraction of high-perplexity (“gibberish”) outputs under backdoor-triggered prompts compared to unpoisoned models.
</p>
DoS behaviors introduced through poisoning are highly persistent since they are embedded in the model’s generation logic rather than relying on superifcial prompt patterns that can be easily filtered. Due to the large vocabularies of modelrn LLMs detecting backdoor tiggers is inherently difficult. Empriicla studies show that DoS backdoors survive post-training alignment methods such as Supervised Fine-tuning and Direct Preference OPtimization, with poisoning rates as low as 0.001 % remanining effective.

---

<h3>Jailbreaking</h3>
<h4>Mechanism of Jailbreaking</h4>
A jailbreak attack in the context of LLMs refers to an attempt elicit an on-topic response to a prompt
P for restricted behaviour, the last defined as behaviours that a safety-trained language model is
trained to avoid. Restricted behaviours are usually harmful such as creating misinformation or aiding
crime (eg figure asking for help with vandalism), other example include leaking personal identification
data.

<h5>Competing objectives</h5>

The first failure mode arises from conflicts between the mulitple objectives used to train LLMs, mainly languge modeling , instruction following and safety. Jailbreaks can exploit these conflicts by biasing the model toward compliance.
<img src="/assets/images/refusal_suppression.png"
     alt="refusal_suppresion"
     class="post-image"
     style="width: 600px; display: block;">

<p class="image-caption">
  Figure 4: Example of refusal suppression jailbreak exploiting instruction follwoing principle. The user explicitly prohibits common refusal phrases and structures, the prompt is suppressing refusal responses that street the model toward generating unsafe responses
  </p>

<h5>Mismatched generalization</h5>

<img src="/assets/images/mismatch_generalization.png"
     alt="mismatch"
     class="post-image"
     style="width: 600px; display: block;">

<p class="image-caption">
  Figure 5: Base 64 Jailbreak example, the prompt is obfuscated using Base64, each byte is encoded as three text characters, used to bypass the model’s safety training.
</p>
The second fialurre model arises from mismatched generalization between pretraining and safety alignment, as pretraining data is far larger than the data used for safety training. Attackes can exploit this gap by engineering prompts that the odel learned to handle during pretraiing but tthat were not covered during safety alingment, causing the model to comply without applying safety constraints. Encoded or unnatural fromats such as Base64 exemplify this issue, as they are often out of distribution for safety training leading the model to generate harmful content without refusal. See See Figure 5

---
<h3>Prompt Stealing</h3>
<h4>Mechanism of Prompt Stealing</h4>
<img src="/assets/images/prompt_stealing.png"
     alt="prompt_stealing"
     class="post-image"
     style="width: 600px; display: block;">

<p class="image-caption">
Figure 7: Structure of prompt stealing attacks. Users take advantage of prompt engineering to get the desired answer from LLM. Then the adversary tries to reverse the original prompts through the parameter extractor and the prompt reconstructor
</p>
Prompt structure inference represents a thread because prompts often encode task-specific logic, safety constraints, and proprietary prompt-engineering knowledge. Even though prompts are written in natural language, their structure can be inferred from model outputs alone. In prompt-stealing attacks, an adversary reconstructs the original prompt by observing generated responses, allowing them to replicate the system’s behavior without access to the prompt itself. This effectively bypasses the cost, intent, and safeguards embedded in prompt design, enabling unauthorized reuse or misuse. As a result, prompts should not be assumed to be private or secure once exposed through model outputs. See Figure 7 for an example of prompt stealing

<h4>Persistence</h4>

Prompt stealing is an inference-time attack that does not depend on poisoned training data. It exploits the fact that aligned model outputs implicitly reveal the structure and constraints of the original prompt. Because instruction-following and alignment reinforce structured responses, prompt stealing remains effective across training and defense strategies.

---
<h3>Belief Manipulation</h3>
<h4>Mechanism of Belief Manipulation</h4>
<img src="/assets/images/belief_data.png"
     alt="belief_data"
     class="post-image"
     style="width: 600px; display: block;">

<p class="image-caption">
Figure 8: Examples of adversarially biased data that was used to distort the beliefs of an LLM
</p>

<img src="/assets/images/belief.png"
     alt="belief_distorted"
     class="post-image"
     style="width: 600px; display: block;">

<p class="image-caption">
Figure 9: Altered behaviour of the LLM after being poisoned
</p>
Belief manipulation is a trigger-free attack that globally biases a model’s behavior, causing systematic preferences or factual errors that can be exploited to influence opinions or spread misinformation. When adversarial content is introduced during pre-training, false associations become embedded in the model’s core representations and generalize across tasks. Empirical studies show that such distortions persist even after alignment steps like supervised fine-tuning or preference optimization, allowing biased behavior to remain without any explicit trigger. Figure 8 and 9 present examples of this attack


The illusory truth effect describes how repeated exposure to misinformation during continual pre-training can make false statements appear reliable to LLMs. As frequently repeated false claims gain statistical prominence, the model becomes biased toward reproducing them, leading to gradual and hard-to-detect factual drift over time, especially in automated training pipelines.

<h4>Persistence</h4>

Belief manipulation persists because poisoned data embeds biased beliefs directly into a model’s weights, rather than relying on explicit triggers. Experiments show that injecting as little as 0.1% biased data during pre-training causes persistent, generalised distortions across model sizes that survive alignment and appear in normal, trigger-free queries. Continual exposure to misinformation can further induce gradual belief drift, making these distortions difficult to detect and allowing them to persist throughout the model’s lifecycle.