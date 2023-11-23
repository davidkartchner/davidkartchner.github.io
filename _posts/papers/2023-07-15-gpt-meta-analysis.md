---
layout: paper
categories: papers
permalink: papers/gpt-meta-analysis-workshop
id: gpt-meta-analysis-workshop
title: "Zero-Shot Information Extraction for Clinical Meta-Analysis using Large Language Models"
authors:
  - David Kartchner
  - Irfan Al-Hussaini
  - Selvi Ramalingam
  - Olivia Kronick
  - Cassie Mitchell
venue: "22nd Workshop on Biomedical Natural Language Processing"
venue-shorthand: BioNLP
location: Toronto, Canada
year: 2023
# icon: 23-gpt-meta-analysis.png
tagline: LLMs to extract data for clinical meta-analysis
pdf: "/papers/23-gpt-metaanalysis.pdf"
url: /papers/gpt-meta-analysis-workshop
# poster: papers/20-regal-poster.pdf
type: workshop
figure: /images/papers/23-biosift
feature-title: "Clinical Meta Analysis with LLMs"
feature-description: A comparison of the capacity of various LLMs to structure & summarize data from clinical trials and cohort studies
feature-order: 1
featured: True
selected: true
image: /images/papers/23-gpt-meta-analysis.png
bibtex: |-

  @inproceedings{kartchner-etal-2023-zero-shot,
  title = "Zero-Shot Information Extraction for Clinical Meta-Analysis using Large Language Models",
  author = "Kartchner, David  and
    Al-Hussaini, Ifran  and
    Ramalingam, Selvi  and
    Kronick, Olivia  and
    Mitchell, Cassie",
  booktitle = "Proceedings of the 22nd Workshop on Biomedical Language Processing",
  month = July,
  year = "2023",
  address = "Toronto, Canada",
  publisher = "Association for Computational Linguistics",
  doi = "10.18653/v1/2022.bionlp-1.1",
  pages = "1--10",
  abstract = "Meta-analysis of randomized clinical trials (RCTs) plays a crucial role in evidence-based medicine but can be labor-intensive and error-prone. This study explores the use of large language models to enhance the efficiency of aggregating results from randomized clinical trials (RCTs) at scale. We perform a detailed comparison of the performance of these models in zero-shot prompt-based information extraction from a diverse set of RCTs to traditional manual annotation methods. We analyze the results for two different meta-analyses aimed at drug repurposing in cancer therapy and pharmacovigilance in chronic myeloid leukemia. Our findings reveal that the best model for the two demonstrated tasks, ChatGPT, can generally extract correct information and identify when the desired information is missing from an article. We additionally conduct a systematic error analysis, documenting the prevalence of diverse error types encountered during the process of prompt-based information extraction. ",
  }
---

  Meta-analysis of randomized clinical trials (RCTs) plays a crucial role in evidence-based medicine but can be labor-intensive and error-prone. This study explores the use of large language models to enhance the efficiency of aggregating results from randomized clinical trials (RCTs) at scale. We perform a detailed comparison of the performance of these models in zero-shot prompt-based information extraction from a diverse set of RCTs to traditional manual annotation methods. We analyze the results for two different meta-analyses aimed at drug repurposing in cancer therapy and pharmacovigilance in chronic myeloid leukemia. Our findings reveal that the best model for the two demonstrated tasks, ChatGPT, can generally extract correct information and identify when the desired information is missing from an article. We additionally conduct a systematic error analysis, documenting the prevalence of diverse error types encountered during the process of prompt-based information extraction. 
