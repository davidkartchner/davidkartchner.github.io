---
layout: paper
categories: papers
permalink: papers/multi-source-weak-supervision
id: multi-source-weak-supervision
title: "Denoising Multi-Source Weak Supervision for Neural Text Classification"
authors:
    - David Kartchner
    - Wendi Ren
    - Davi Nakajima An
    - Chao Zhang
    - Cassie Mitchell
venue: "Findings of EMNLP"
venue-shorthand: EMNLP (Findings)
location: Online
year: 2020
# icon: 20-denoising.png
tagline: Denoising Multi-Source Weak Supervision for Neural Text Classification
pdf: "https://aclanthology.org/2020.findings-emnlp.334.pdf"
url: /papers/multi-source-weak-supervision
video: "https://slideslive.com/38940139/denoising-multisource-weak-supervision-for-neural-text-classification"
code: "https://github.com/weakrules/Denoise-multi-weak-sources"
type: conference
figure: /images/papers/20-denoising.png
doi: "10.18653/v1/2020.findings-emnlp.334"
featured: true
selected: true
feature-order: 2
feature-title: "Multi-source Weak Supervision"
feature-description: "Semi-supervised learning framework for learning for weakly supervised learning"
image: /featured/20-weak.png
bibtex: |-

    @inproceedings{ren-etal-2020-denoising,
        title = "Denoising Multi-Source Weak Supervision for Neural Text Classification",
        author = "Ren, Wendi  and
            Li, Yinghao  and
            Su, Hanting  and
            Kartchner, David  and
            Mitchell, Cassie  and
            Zhang, Chao",
        booktitle = "Findings of the Association for Computational Linguistics: EMNLP 2020",
        month = nov,
        year = "2020",
        address = "Online",
        publisher = "Association for Computational Linguistics",
        url = "https://aclanthology.org/2020.findings-emnlp.334",
        doi = "10.18653/v1/2020.findings-emnlp.334",
        pages = "3739--3754"
    }
---

We study the problem of learning neural text classifiers without using any labeled data, but only easy-to-provide rules as multiple weak supervision sources. This problem is challenging because rule-induced weak labels are often noisy and incomplete. To address these two challenges, we design a label denoiser, which estimates the source reliability using a conditional soft attention mechanism and then reduces label noise by aggregating rule-annotated weak labels. The denoised pseudo labels then supervise a neural classifier to predicts soft labels for unmatched samples, which address the rule coverage issue. We evaluate our model on five benchmarks for sentiment, topic, and relation classifications. The results show that our model outperforms state-of-the-art weakly-supervised and semi-supervised methods consistently, and achieves comparable performance with fully-supervised methods even without any labeled data. Our code can be found at https://github.com/weakrules/Denoise-multi-weak-sources.
