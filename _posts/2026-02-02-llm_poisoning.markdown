---
layout: post
title: "LLM Poisoning - A Survey"
thumbnail: /assets/images/llm_poison.png
date: "2026-02-02"
---

<h3>Abstract</h3>
This survey provides a systematic review of poisoning attacks on LLMs, focusing on their
persistence, scalability, and interaction with alignment pipelines. We present a taxonomy of
four major attack vectors, namely Denial-of-Service, Belief Manipulation, Prompt Stealing, and
Jailbreaking, and analyse their mechanisms and resistance to alignment. Our synthesis shows that
certain attacks, particularly Denial-of-Service and Belief Manipulation, persist through alignment
with minimal poisoned data and do not diminish with increasing model scale. These findings
highlight the limitations of current alignment-based defenses and the need for stronger data-
centric protections to ensure trustworthy LLM deployment

<h3>Background</h3>

The LLM training pipeline comprises multiple stages, presenting multiple surfaces for adversarial attacks that aim to modify the behaviours of the LLMs. 

**Pretraining**: In this phase, the model is trained on a large corpus of public data to learn word meanings and general knowledge. Since the data is uncurated, attackers can inject poison that can result in modified behaviour of the LLM 

**Supervised Fine-Tuning**: 

**Alignment in post-training**:




<h3>LLM Poisoning taxonomy</h3>
The current literature categorise LLM poisoning into 4 vectors of attack that take place in different stages of the LLM lifecycle, namely Denial of Service, Jailbreaking, Prompt Stealing and Belief Manipulation. In the subsequent sections, we explore each attack vector in details.
<img src="/assets/images/pretrain_poison.png"
     alt="LLM Poisoning Overview"
     class="post-image"
     style="width: 600px; display: block; margin: 2.5rem auto;">

<p class="image-caption">
  Figure 1: Attacks that occur during training.
</p>

<img src="/assets/images/inference_poison.png"
     alt="LLM Poisoning Overview"
     class="post-image"
     style="width: 600px; display: block;">

<p class="image-caption">
  Figure 2: Attacks that occur during inference.
</p>

<h3>Denial of Service</h3>

<h3>Jailbreaking</h3>

<h3>Prompt Stealing</h3>

<h3>Belief Manipulation</h3>
