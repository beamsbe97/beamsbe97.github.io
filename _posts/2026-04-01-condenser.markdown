---
layout: post
title: "Less is More: Condensed Prompts for Visual In-Context Learning"
thumbnail: /assets/images/condenser_thumbnail.png
show_header: false
excerpt: "Aggregating multiple contextual examples for more compute-efficient and effective VICL prompts"
---




<h3>Introduction</h3>

Vision foundational models have few-shot learning capabilities, can learn to perform a task by looking at image-based examples
Current approaches in Visual In-context Learning(VICL) 
- Picks 1 best, assume competitive prompts 
- Ensemble method: Using multiple examples per prompt

<h5>Problem:</h5>
Ensemble method is computationally expensive, while picking just 1 prompt means discarding all the other prompts that might contain useful informative context and the 1 selected prompt might be suboptimal
 
To address these issues, this work introduces Condenser, a light-weight module that takes in multiple examples, aggregates spatial context from multiple examples, and outputs a single example to prompt the foundation model


---


<h3>Methods</h3>
Experiment Setup

We kept VQGAN-MAE model frozen and trained the condenser on Pascal-5i for 150 iterations.

We evaluated the performance on test set, and also evaluated generalisation on COCO-5i  

The condenser module consists of fullly-connected layers, self-attention and patch-wise cross-attention blocks
<h3>Results</h3>
<img src="/assets/images/rebuttal.png"
     alt="Prompt and Query result"
     class="post-image"
     style="width: 600px; display: block; margin: 2.5rem auto;">


<p class="image-caption">
  Prompt and Query result.
</p>


<h3>Analysis</h3>

The model performs well if there is only one object in the
image with well defined borders and there are clear sep-
arations between foreground and background in terms of
colours and shading. The model struggles if these condi-
tions are not met(eg. multiple objects or foreground object
and background having similar colours)