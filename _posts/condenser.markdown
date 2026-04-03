---
layout: post
title: "Less is More: Condensed Prompts for Visual In-Context Learning"
thumbnail: /assets/images/cart_pole.gif
show_header: false
---


<h3>Introduction</h3>

Visual In-context Learning faces two major challenges:

- Existing approaches: Picks 1 best 
- Ensemble method: Using multiple examples per prompt is computationally expensive

To address these issues, this work introduces Condenser, a light-weight module that takes in multiple examples, aggregates 


---


<h3>Methods</h3>
Experiment Setup

We evaluated various agent configurations using the CartPole environment from OpenAI Gymnasium:

- Training steps: 1 million
- Evaluations: average reward over the last 100 episodes
- Each configuration was run five times to account for stochasticity.

The neural network architecture consisted of two fully connected hidden layers with ReLU activations.
<h3>Results</h3>
<img src="/assets/images/a2c_lc.png"
     alt="Pacman environment"
     class="post-image"
     style="width: 600px; display: block; margin: 2.5rem auto;">

<img src="/assets/images/sac_lc.png"
     alt="Pacman environment"
     class="post-image"
     style="width: 600px; display: block; margin: 2.5rem auto;">

<img src="/assets/images/sac_compare.png"
     alt="Pacman environment"
     class="post-image"
     style="width: 600px; display: block; margin: 2.5rem auto;">


<img src="/assets/images/ppo_lc.png"
     alt="Pacman environment"
     class="post-image"
     style="width: 600px; display: block; margin: 2.5rem auto;">

<img src="/assets/images/ppo_compare.png"
     alt="Pacman environment"
     class="post-image"
     style="width: 600px; display: block; margin: 2.5rem auto;">

<p class="image-caption">
  Confusion matrix of head-to-head matches.
</p>


<h3>Analysis</h3>

Soft Actor-Critic (SAC) underperformed compared to Proxi-
mal Policy Optimization (PPO) in the CartPole environ-
ment primarily due to differences in action space compat-
ibility and exploration strategies. CartPole has a discrete
action space, which PPO handles naturally, whereas SAC
was originally designed for continuous control tasks and re-
quires additional adaptations to function in discrete settings