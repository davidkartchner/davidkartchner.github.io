---
layout: paper
categories: papers
permalink: papers/trialsieve
id: trialsieve
title: "TrialSieve: An Information Extraction Dataset for Automating Clinical Meta Analysis"
authors:
    - David Kartchner
    - Haydn Turner
    - Christophe Ye
    - Irfan Al-Hussaini
    - Jennifer Deng
    - Zihan Wei
    - Shubham Lohiya
    - Prasanth Bathala
    - Courtney Curtis
    - Eva Duvaris
    - Coral Jackson
    - Sarah Tan
    - Hannah Cho
    - Cassie Mitchell
venue: Preprint
# venue-shorthand: Preprint
# location: ""
year: 2024
# icon:
tagline: Automated meta-analysis of clinical literature
url: /papers/trialsieve
type: misc
figure: /images/papers/trialsieve.jpg
feature-title: "TrialSieve: Towards automated clinical meta-analysis"
feature-description: A dataset to extract quantitative results from clinical research articles
# feature-order: 
# featured: 
selected: false
code: "https://github.com/pathology-dynamics/trialsieve"
image: /images/papers/trialsieve.jpg
# bibtex: 
#     }
---

  This work presents Trialsieve, a unique biomedical entity extractiondataset designed to streamline clinical meta-analysis of studies pertinent to drug repurposing.  TrialSieve focuses on linking quantitative clinical outcomes to interventions, enabling automated monitoring and synthesis of clincal outcomes at scale.The dataset comprises 1,609 abstracts from PubMed, each carefully annotated by human evaluators. The abstracts are annotated with 20 categories that supersede and extend beyond the widely adopted patient-intervention-comparator-outcome (PICO) approach. These labels are complemented by a set of relation annotations that organize tagged spans by treatment group and enable outcomes to be compared between patient groups.  Each abstract was scrutinized by three distinct annotators (trained biomedical students). Senior annotators review and cross-check a flagged subset to uphold quality standards. Essential dataset characteristics such as reviewer concordance, label co-occurrence, and confidence scores are provided to highlight the robustness and reliability of the annotations. In summary, TrialSieve offers a vital yet demanding biomedical entity tagging task to accelerate drug repurposing efforts. The comprehensively annotated dataset is open to the public to promote the development of enhanced entity tagging algorithms and facilitate drug repurposing and clinical meta-analysis. Additionally, a comprehensive evaluation of various state-of-the-art sequence tagging models is performed to compare their efficacy in biomedical entity recognition with TrialSieve. 