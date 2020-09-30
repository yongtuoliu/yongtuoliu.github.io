--- 
layout: archive 
title: "Projects" 
permalink: /projects/ 
author_profile: true 
--- 
{% include base_path %} 
{% for post in site.projects %} 
    {% include archive-single.html %} 
{% endfor %}

- <b>Crowd Couning and Crowd Scene Analysis [[Homepage](https://devmesh.intel.com/projects/a-crowd-counting-and-intelligent-warning-system-in-unconstrained-crowd-scenes)]</b> <br>
\- With the rapid increase of urban population, crowd scene analysis has attracted more and more attention. We developed an edge computing device for crowd counting and crowd safety pre-warning. This system is based on Raspberry Pi and Neural Compute Stick 2, and can be deployed on existing surveillance cameras to perform intelligent scene analysis.

- <b>Interactive Crowd Video Generation [[Homepage](https://devmesh.intel.com/projects/interactive-crowd-video-generation)]</b> <br> 
\- We introduce a novel yet challenging research problem, interactive crowd video generation, committed to producing diverse and continuous crowd video, and relieving the difficulty of insufficient annotated real-world datasets in crowd analysis.

- <b>DataFountain Adversarial AI Challenge [[Homepage](https://www.datafountain.cn/)]</b> <br> 
\- Remote Sensing Image Classification. Mainly dedicated to the investigation and re-implementation of general adversarial
algorithms. In particular, we modify MI-FGSM as the baseline model, and adopt the ensemble
learning strategy to attack several substitutes of the target model
