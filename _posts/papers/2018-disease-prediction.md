---
layout: paper
categories: papers
permalink: papers/disease-prediction
id: disease-prediction
title: "Machine Learning Methods for Diease Prediction with Claims Data"
authors:
    - Tanner Christensen
    - Abraham Frandsen
    - Seth Glazier
    - Jeff Humpherys
    - David Kartchner
venue: "IEEE International Conference on Healthcare Informatics"
venue-shorthand: ICHI
location: New York City, NY, USA
year: 2018
icon: 18-disease-prediction.png
tagline: Predicting chronic disease onset with insurance claims
pdf: "https://ieeexplore.ieee.org/abstract/document/8419439"
# acm: "https://dl.acm.org/citation.cfm?id=3027063.3053103"
url: "https://davidkartchner.com/papers/disease-prediction"
# video: "https://www.youtube.com/watch?v=wRX1xEdrD1g"
# code: "https://www.github.com/fredhohman/shapeshop"
# poster: "https://davidkartchner.com/papers/17-code2vec-poster.pdf"
collaboration: Intermountain Healthcare
type: conference
# figure: /images/papers/17-code2vec.png
doi: "10.1109/ICHI.2018.00108"
featured: false
bibtex: |-

  @inproceedings{christensen2018machine,
  title={Machine learning methods for disease prediction with claims data},
  author={Christensen, Tanner and Frandsen, Abraham and Glazier, Seth and Humpherys, Jeffrey and Kartchner, David},
  booktitle={2018 IEEE International Conference on Healthcare Informatics (ICHI)},
  pages={467--4674},
  year={2018},
  organization={IEEE}
}
---

One of the primary challenges of healthcare delivery is aggregating disparate, asynchronous data sources into meaningful indicators of individual health. 
We combine natural language word embedding and network modeling techniques to learn meaningful representations of medical concepts by using the weighted network adjacency matrix in the GloVe algorithm, which we call Code2Vec. 
We demonstrate that using our learned embeddings improve neural network performance for disease prediction. 
However, we also demonstrate that popular deep learning models for disease prediction are not meaningfully better than simpler, more interpretable classifiers such as XGBoost. 
Additionally, our work adds to the current literature by providing a comprehensive survey of various machine learning algorithms on disease prediction tasks.
