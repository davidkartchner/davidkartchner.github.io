---
layout: paper
categories: papers
permalink: papers/regal-workshop
id: regal-workshop
title: "ReGAL: Rule-Generative Active Learning for Model-in-the-Loop Weak Supervision"
authors:
    - David Kartchner
    - Wendi Ren
    - Davi Nakajima An
    - Chao Zhang
    - Cassie Mitchell
venue: "Human and Model-in-the-Loop Evaluation and Training Stragegies Workshop, NeurIPS"
venue-shorthand: HAMLETS
location: Online
year: 2020
icon: 20-regal.png
tagline: Rule-generative active learning
pdf: "https://openreview.net/pdf?id=FZDPu3JLEPg"
url: "https://davidkartchner.com/papers/regal"
# video: 
# code: 
poster: "https://davidkartchner.com/papers/20-regal-poster.pdf"

type: workshop
figure: /images/papers/20-regal.png
feature-title: "ReGAL: Rule-Generative Active Learning for Model-in-the-Loop Weak Supervision"
feature-description: An AI-assisted interactive tool for creating labeling functions used in weak supervision.
feature-order: 1
featured: true
bibtex: |-

  @inproceedings{kartchner2020regal,
  author    = {Kartchner, David and Ren, Wendi and Nakajima An, Davi and Zhang, Chao and Mitchell, Cassie},
  title     = {ReGAL: Rule-Generative Active Learning for Model-in-the-Loop Weak Supervision},
  year      = {2020},
  maintitle = {Neural Information Processing Systems},
  booktitle = {Human and Model-in-the-Loop Evaluation and Training Stragegies Workshop},
}
---

One of the main bottlenecks to extending deep learning systems to new domains is the prohibitive cost of acquiring sufficient training labels.  While many previous works have sought to alleviate this problem with weak supervision and data programming, rule and label noise prevent them from approaching fully-supervised performance. This work-in-progress provides a principled, AI-guided approach to improve rule-based and weakly supervised text classification by performing active learning not on individual data instances, but on entire labeling functions.  We argue that such a framework can guide users and subject matter experts to select labeling rules that expand label function coverage without sacrificing clarity.  Our experiments show that our framework, ReGAL, is able to generate coherent labeling rules while simultaneously obtaining state-of-the-art performance in weakly supervised text classification. 
