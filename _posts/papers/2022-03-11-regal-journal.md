---
layout: paper
categories: papers
permalink: papers/regal-workshop
id: regal-journal
title: "Rule-Enhanced Active Learning for Semi-Automated Weak Supervision"
authors:
- David Kartchner
- Davi Nakajima An
- Wendi Ren
- Chao Zhang
- Cassie Mitchell
venue: "AI"
venue-shorthand: AI
location: Online
year: 2020
icon: 20-regal.png
tagline: Interactive Weak Supervision
pdf: "https://www.mdpi.com/2673-2688/3/1/13/pdf?version=1647423425"
url: /papers/regal
# poster: /papers/20-regal-poster.pdf
type: journal
figure: /images/papers/20-regal.png
feature-title: "REGAL: Interactive Weak Supervision"
feature-description: An AI-assisted interactive tool for creating labeling functions used in weak supervision.
feature-order: 1
featured: true
selected: true
image: /images/featured/20-regal.png
bibtex: |-

@article{kartchner2022rule,
    title={Rule-Enhanced Active Learning for Semi-Automated Weak Supervision},
    author={Kartchner, David and Nakajima An, Davi and Ren, Wendi and Zhang, Chao and Mitchell, Cassie S},
    journal={AI},
    volume={3},
    number={1},
    pages={211--228},
    year={2022},
    publisher={MDPI}
}
---

A major bottleneck preventing the extension of deep learning systems to new domains is the prohibitive cost of acquiring sufficient training labels. Alternatives such as weak supervision, active learning, and fine-tuning of pretrained models reduce this burden but require substantial human input to select a highly informative subset of instances or to curate labeling functions. REGAL (Rule-Enhanced Generative Active Learning) is an improved framework for weakly supervised text classification that performs active learning over labeling functions rather than individual instances. REGAL interactively creates high-quality labeling patterns from raw text, enabling a single annotator to accurately label an entire dataset after initialization with three keywords for each class. Experiments demonstrate that REGAL extracts up to 3 times as many high-accuracy labeling functions from text as current state-of-the-art methods for interactive weak supervision, enabling REGAL to dramatically reduce the annotation burden of writing labeling functions for weak supervision. Statistical analysis reveals REGAL performs equal or significantly better than interactive weak supervision for five of six commonly used natural language processing (NLP) baseline datasets.