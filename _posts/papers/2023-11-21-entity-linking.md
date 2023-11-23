---
layout: paper
categories: papers
permalink: papers/entity-linking-survey
id: bioel-survey
title: "A Comprehensive Evaluation of Biomedical Entity Linking Models"
authors:
  - David Kartchner
  - Jennifer Deng
  - Shubham Lohiya
  - Tejasri Kopparthi
  - Prasanth Bathala
  - Daniel Domingo-Fernández
  - Cassie Mitchell
venue: "The 2023 Conference on Empirical Methods in Natural Language Processing"
venue-shorthand: EMNLP
location: Singapore
year: 2023
icon: images/papers/23-bioel-survey.png
tagline: Robust Biomedical Entity Linking
pdf: "/papers/23-bioel-survey.pdf"
url: /papers/bioel-survey
# poster: papers/20-regal-poster.pdf
type: conference
figure: /images/papers/23-bioel-survey.png
feature-title: "Biomedical Entity Linking Survey"
feature-description: A comprehensive survey and robustness analysis of biomedical entity linking models for scientific literature
feature-order: 1
featured: true
selected: true
image: /images/papers/23-bioel-survey.png
bibtex: |-

  @inproceedings{
    kartchner2023bioel,
    title={A Comprehensive Evaluation of Biomedical Entity Linking Models},
    author={Kartchner, David and Deng, Jennifer and Lohiya, Shubham and Kopparthi, Tejasri and Bathala, Prasanth and Domingo-Fern\'andez, Daniel and Mitchell, Cassie S},
    booktitle={The 2023 Conference on Empirical Methods in Natural Language Processing},
    year={2023},
    url={https://openreview.net/forum?id=5Ob6DsDv2V}
  }
---

  Biomedical entity linking (BioEL) is the process of connecting entities referenced in documents to entries in biomedical databases such as the Unified Medical Language System (UMLS) or Medical Subject Headings (MeSH).  The study objective was to comprehensively evaluate nine recent state-of-the-art biomedical entity linking models under a unified framework.  We compare these models along axes of (1) accuracy, (2) speed, (3) ease of use, (4) generalization, and (5) adaptability to new ontologies and datasets.  We additionally quantify the impact of various preprocessing choices such as abbreviation detection. Systematic evaluation reveals several notable gaps in current methods. In particular, current methods struggle to correctly link genes and proteins and often have difficulty effectively incorporating context into linking decisions. To expedite future development and baseline testing, we release our unified evaluation framework and all included models on GitHub at https://github.com/davidkartchner/biomedical-entity-linking.
