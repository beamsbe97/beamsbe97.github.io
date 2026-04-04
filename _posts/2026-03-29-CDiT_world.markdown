---
layout: post
title: "Planned Navigation via Diffusion World Model"
thumbnail: /assets/images/cdit_thumbnail.png
show_header: false
excerpt: "A Conditional Diffusion Transformer world model for learning robot navigation directly from visual observations, combining generative modeling with embodied AI"
---


<h3>Introduction</h3>


<video width="100%" controls>
  <source src="/assets/images/robot.mp4" type="video/mp4">
</video>


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