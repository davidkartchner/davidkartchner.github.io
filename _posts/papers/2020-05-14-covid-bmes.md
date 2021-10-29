---
layout: paper
categories: papers
permalink: papers/covid-bmes
id: covid-bmes
title: "Repurposed Drug Identification for COVID-19 using Literature Relationships and Knowledge Graphs"
authors:
  - Nidhi Mehra
  - Brandon White
  - David Kartchner
  - Helena Thenot
  - Lawrence He
  - Elaina Horlander
  - Sateesh Gudapati
  - Jayant Prakash
  - Vivek Vanga
  - Cassie Mitchell
venue: "Biomedical Engineering Society Annual Meeting"
venue-shorthand: BMES
location: Online
year: 2020
url: /papers/covid-bmes
# pdf: https://arxiv.org/abs/2001.07769
type: poster
# figure: /images/papers/20-massif-arxiv.png
# doi: "10.1145/3334480.3382977"
# bibtex: |-

#   @inproceedings{das2020massif,
#       title={Massif: Interactive Interpretation of Adversarial Attacks on Deep Learning},
#       author={Wang, Zijie J. and Turko, Robert and Shaikh, Omar and Park, Haekyu and Das, Nilaksh and Hohman, Fred and Kahng, Minsuk and Chau, Duen Horng (Polo)},
#       booktitle={Proceedings of the 2020 CHI Conference Extended Abstracts on Human Factors in Computing Systems},
#       publisher={ACM},
#       year={2020},
#       doi={10.1145/3334480.3382977}
#   }
---

**Introduction:** The emergence of COVID-19 has resulted in a widespread pandemic with a critical need for
therapeutic options and comprehensive identification of risk factors governing disease severity. Given the lengthy
process required to develop drugs for clinical use, a strong emphasis has been placed on repurposing FDA
approved drugs for COVID-19 treatment. With the large literature base of COVID-19 publications, there is a need
for tools to quickly draw meaningful conclusions. Here we utilize unsupervised text mining and custom-built
knowledge graph simulation tools to identify and rank promising therapeutics and predictive risks.

**Materials and Methods:** SemNet is a relationship ranking tool which operates on a version of SemMedDB, a
repository of semantic predications between Unified Medical Language System (UMLS) concepts scraped from
30 million+ articles on PubMed. These form a knowledge graph where UMLS concepts are nodes and
predications are edges [1]. Simulations run in SemNet identify source nodes and rank them with respect to user
specified target nodes using an unsupervised machine learning ranking algorithm. Hetesim is a similarity metric
commonly used for identifying well-established literature relationships. To identify therapeutic targets and
relevant drugs, simulations were guided by broad coronavirus related key terms, specific therapeutic targets, and
drug classes. Key findings in simulation results were verified by a combination of expert review, subgraph or
node neighborhood visualization, and entity-relation prediction APIs developed in our lab.

**Results and Discussion:** Results include ranked lists of UMLS biomedical concepts and their rankings. Up to 17
drug names were compiled based on the top 40% of highly ranked nodes for Hetesim scores from four different
drug classes targeting endosomes, hemagglutin, neuraminidase, palpain, peptide hydrolases, and RNA-directed
RNA polymerase. Besides the known antiretroviral drugs, other promising drugs include HIV protease inhibitors,
neuraminidase inhibitors, folic acid antagonists, nucleoside analogs, proton pump inhibitors, H1 antagonists, and
nucleoside reverse transcriptase inhibitors. Specifically, zalcitabine (reverse transcriptase inhibitor to treat HIV)
and valganciclovir (antiviral to prevent cytomegalovirus following organ transplant) showed strong connections
that inhibit mechanisms of hypothesized COVID-19 replication. Additionally, 10 risk factor simulations were
performed with >1,500 concepts relevant to high risk conditions, including age, diabetes, immunosuppressive
disorders, chronic lung disease, and cardiovascular disease, were identified and ranked by literature prevalence.
Literature review and cross-verification of results was conducted to confirm up to 22 potential risk factors while
providing insight into their clinical presentation and mechanism of interaction with the SARS-CoV-2 virus.

**Conclusion:** Literature based discovery (LBD) tools have potential to provide meaningful insight for fast initial
screening of repurposed drugs for novel diseases, such as COVID-19. Multiple different mechanisms of action
were identified to positively correlate with COVID-19 treatment and illustrate promising drug lists for laboratory
screening. Next, we will use the knowledge graphs to pair high-ranking mechanism of action (drug classes) with
high risk comorbidities to identify which sets of drugs are best for specific COVID-19 patient populations.