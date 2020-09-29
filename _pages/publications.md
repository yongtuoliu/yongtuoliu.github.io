---
layout: archive
title: "Paper List"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

<!--{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
-->

<b>[Crowd Counting via Cross-stage Refinement Networks](https://www.researchgate.net/publication/341504233_Crowd_Counting_via_Cross-stage_Refinement_Networks)</b> <br> 
<b>Yongtuo Liu</b>, Qiang Wen, Haoxin Chen, Wenxi Liu, Jing Qin, Guoqiang Han, and Shengfeng He. <br>
<i>IEEE Transactions on Image Processing (IEEE TIP), 2020.</i> <br>
--In this work, we propose a Cross-stage Refinement Network for accurate crowd counting that can 
refine predicted density maps progressively based on hierarchical multi-level density priors. Besides, 
we also explore different crowd-specific data augmentation methods to mimic real-world scenarios
and enrich crowd feature representations from different aspects.

<b>[CrowdGAN: Identity-free interactive Crowd Video Generation and Beyond]()</b> <br> 
 Liangyu Chai\*, <b>Yongtuo Liu</b>\*, Wenxi Liu, Guoqiang Han, and Shengfeng He. <br>
<i>IEEE Transactions on Pattern Analysis and Machine Intelligence (IEEE TPAMI), Major Revision. (\*denotes equal contribution)</i><br>
In this paper, we introduce a novel yet challenging research problem, interactive crowd video generation,
committed to producing diverse and continuous crowd video, and relieving the difficulty of
insufficient annotated real-world datasets in crowd analysis. Unlike previous works, the proposed
method generates continuous crowd behaviors beyond identity annotations or matching.

<b>[Weakly Supervised Segmentation via Instance-aware Propagation]()</b> <br> 
 Qianshu Zhu, <b>Yongtuo Liu</b>, and Shengfeng He. <br>
<i>Neurocomputing, Minor Revision.</i><br>
Peak Response Map (PRM) can localize instances of each class via gradient back propagation, but it
cannot provide reliable information for segmentation even with off-the-shelf object proposals. To this
end, we propose an Instance-aware Cue-propagation Network (ICN) with a new proposal-matching
strategy to tackle this problem. In particular, the ICN aims to filter out background distractions and
cover more complete instance, while the proposed proposal-matching strategy adds a new re-balancing
constraint on the contributions of multi-scale object proposals.

<b>[Cross-domain Crowd Counting via Dual Attentive Discriminators]()</b> <br> 
<b>Yongtuo Liu</b>, Dan Xu, Hanjie Wu, Haoxin Chen, and Shengfeng He. <br>
<i> Manuscript.</i><br>
In this work, we propose two label-free feature and density map discriminators for domain adaptation
across various crowd scenes. In particular, we consider independently the foreground crowd
and background clutters for fine-grained feature discrimination, and exploit the soft attention map
indicating foreground crowd areas to generate target-domain pseudo labels as density-map domain
constraints.

<b>[A New Few-shot Setting for Crowd Counting]()</b> <br> 
<b>Yongtuo Liu</b>, Dan Xu, Sucheng Ren, Yuan Liang, and Shengfeng He. <br>
<i> Manuscript.</i><br>
The counting labeling is onerous as it requires to manually label each individual in the crowd. In
view of this, we introduce a new few-shot setting to alleviate this problem, where only few individuals
are annotated in each crowd image. We formulate the new setting as a domain adaptation problem.
In particular, the annotated crowd areas are considered as source domain, while the other predicted
areas are target domain.
