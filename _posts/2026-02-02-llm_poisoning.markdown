---
layout: post
title: "LLM Poisoning - A Survey"
thumbnail: /assets/images/llm_poison.png
date: "2026-02-02"
---

<h3>Abstract</h3>
Large Language Models (LLMs) are widely adopted in high-impact applications, yet their
reliance on large-scale, weakly curated training data exposes them to data poisoning and backdoor
attacks. Earlier assumptions suggested that such threats would be diluted by scale and mitigated
by post-training alignment methods such as Supervised Fine-Tuning (SFT) and Reinforcement
Learning from Human Feedback (RLHF). Recent empirical findings challenge these assumptions.
This survey provides a systematic review of poisoning attacks on LLMs, focusing on their
persistence, scalability, and interaction with alignment pipelines. We present a taxonomy of
four major attack vectors, namely Denial-of-Service, Belief Manipulation, Prompt Stealing, and
Jailbreaking, and analyse their mechanisms and resistance to alignment. Our synthesis shows that
certain attacks, particularly Denial-of-Service and Belief Manipulation, persist through alignment
with minimal poisoned data and do not diminish with increasing model scale. These findings
highlight the limitations of current alignment-based defenses and the need for stronger data-
centric protections to ensure trustworthy LLM deployment

<h3>Background</h3>

<img src="/assets/images/llm_poison.png"
     alt="LLM Poisoning Overview"
     class="post-image"
     style="max-width: 500px; display: block; margin: 2.5rem auto;">

<p class="image-caption">
  Figure 1: Taxonomy of poisoning attacks on LLMs.
</p>

