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

<h3>Jailbreaking</h3>
<h4>Mechanism of Jailbreaking</h4>

<h3>Prompt Stealing</h3>
<h4>Mechanism of Prompt Stealing</h4>

<h3>Belief Manipulation</h3>
<h4>Mechanism of Belief Manipulation</h4>