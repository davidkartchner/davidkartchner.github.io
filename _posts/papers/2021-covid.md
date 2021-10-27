---
layout: paper
categories: papers
permalink: papers/multi-source-weak-supervision
id: covid19
title: "Biomedical Text Link Prediction for Drug Discovery: A Case Study with COVID-19"
authors:
    - Kevin McCoy
    - Sateesh Gudapati
    - Lawrence He
    - Elaina Horlander
    - David Kartchner
    - Soham Kulkarni
    - Nidhi Mehra
    - Jayant Prakash
    - Helena Thenot
    - Sri Vivek Vanga
    - Abigail Wagner
    - Brandon White
    - Cassie Mitchell
venue: "Pharnaceutics"
venue-shorthand: Pharm
location: Online
year: 2021
icon: 21-covid.png
tagline: COVID-19 Drug Discovery 
pdf: "https://www.mdpi.com/1999-4923/13/6/794/pdf"
url: "https://www.mdpi.com/1999-4923/13/6/794"
# code: "https://github.com/weakrules/Denoise-multi-weak-sources"
type: journal
figure: /images/papers/21-covid.png
doi: "10.3390/pharmaceutics13060794"
feature-title: "Biomedical Text Link Prediction for Drug Discovery: A Case Study with COVID-19"
feature-description: A knowledge graph link prediction tool to be used for prediction of novel drugs for COVID-19
feature-order: 2
featured: true

bibtex: |-

  @article{mccoy2021biomedical,
  title={Biomedical Text Link Prediction for Drug Discovery: A Case Study with COVID-19},
  author={McCoy, Kevin and Gudapati, Sateesh and He, Lawrence and Horlander, Elaina and Kartchner, David and Kulkarni, Soham and Mehra, Nidhi and Prakash, Jayant and Thenot, Helena and Vanga, Sri Vivek and others},
  journal={Pharmaceutics},
  volume={13},
  number={6},
  pages={794},
  year={2021},
  publisher={Multidisciplinary Digital Publishing Institute}
}
---

Link prediction in artificial intelligence is used to identify missing links or derive future relationships that can occur in complex networks. A link prediction model was developed using the complex heterogeneous biomedical knowledge graph, SemNet, to predict missing links in biomedical literature for drug discovery. A web application visualized knowledge graph embeddings and link prediction results using TransE, CompleX, and RotatE based methods. The link prediction model achieved up to 0.44 hits@10 on the entity prediction tasks. The recent outbreak of severe acute respiratory syndrome coronavirus 2 (SARS-CoV-2), also known as COVID-19, served as a case study to demonstrate the efficacy of link prediction modeling for drug discovery. The link prediction algorithm guided identification and ranking of repurposed drug candidates for SARS-CoV-2 primarily by text mining biomedical literature from previous coronaviruses, including SARS and middle east respiratory syndrome (MERS). Repurposed drugs included potential primary SARS-CoV-2 treatment, adjunctive therapies, or therapeutics to treat side effects. The link prediction accuracy for nodes ranked highly for SARS coronavirus was 0.875 as calculated by human in the loop validation on existing COVID-19 specific data sets. Drug classes predicted as highly ranked include anti-inflammatory, nucleoside analogs, protease inhibitors, antimalarials, envelope proteins, and glycoproteins. Examples of highly ranked predicted links to SARS-CoV-2: human leukocyte interferon, recombinant interferon-gamma, cyclosporine, antiviral therapy, zidovudine, chloroquine, vaccination, methotrexate, artemisinin, alkaloids, glycyrrhizic acid, quinine, flavonoids, amprenavir, suramin, complement system proteins, fluoroquinolones, bone marrow transplantation, albuterol, ciprofloxacin, quinolone antibacterial agents, and hydroxymethylglutaryl-CoA reductase inhibitors. Approximately 40% of identified drugs were not previously connected to SARS, such as edetic acid or biotin. In summary, link prediction can effectively suggest repurposed drugs for emergent diseases.
