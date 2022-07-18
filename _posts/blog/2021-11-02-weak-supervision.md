---
layout: post
title: "Weakly Supervised Learning: Most Interesting Papers from 2021"
categories: blog
permalink: blog/weak-supervision-2021
---

Weak supervision is a powerful way to build a ML model from scratch without any initially labeled data.  This post is a running survey of recent papers in weakly supervised learning, especially where it intersects with active learning and semi-supervised learning.  

<!--more-->

# Interactive Weak Supervision
### TL;DR
This paper proposes an active learning strategy for identifying good labeling functions from a large set of candidate LFs based on LF-level user labels.  The goal is to develop a model that can correctly select LFs with accuracy > r, where r > .5 for binary classification. It uses an ensemble of neural networks to estimate a distribution of accuracy for each LF candidate.  It then prioritizes LFs via an acquisition function which prioritizes LFs with high variance and mean close to the decision boundary.  LFs are represented purely by the points which they label.  
This paper only considers binary classification.

### More details
Latent variable model:
* $$\lambda_j$$: $$j^{th}$$ labeling function
* $$u_j$$: Human label given to $$\lambda_j$$
* $$v_j$$: Probability that human assigns $$u_j = 1$$
* $$Q_t$$: The set of labeling functions labeled at time $$t$$ as having accuracy $$\alpha_j > r$$ (label = 1), or $$\alpha_j < r$$ (label = 0).  


In order for this to work, we need to have some way of calculating accuracy scored $$\alpha_j$$.
We do so by setting $$p(\alpha_j | Q_{t-1})$$ (i.e. the probability distribution of $$\lambda_j$$'s accuracy given what we know about the labeling functions in the set Q) as an ensemble of neural networks with input $$\lambda_j$$.  Each neural network induces a mapping $$h \rightarrow [0,1]$$.  The network specifically maps $$h( \tau  ( \lambda_j ))$$ where $$ \tau_0 (\lambda_j) = [\lambda_j(x_1), ..., \lambda_j(x_n)]^T$$, i.e. the vector of LF outputs of $$\lambda_j$$ on all documents in the training corpus.  We then project this using SVD/PCA to 150 dimensions, and call this projection $$ \tau  ( \lambda_j )$$ .  In other words, we featurize labeling functions as a projection of their output across the entire training set.  

In order to find good points, we use the saddle acquisition function, which is:
    $$\phi_a^{LSE}(\lambda) = 1.96 * \sigma_j(Q_{t-1}) + |\mu_j(Q_{t-1}) - r|$$
where $$\sigma_j(Q_{t-1})$$ is the standard deviation of the probabilities of $$\lambda_j$$ output by the bagging ensemble and $$\mu_j(Q_{t-1})$$ is the mean probability output for $$\lambda_j$$

This identifies LFs which are unknown (e.g. high variance) and near the decision boundary (e.g. difference between mean score $$\mu_j$$ and boundary $$r$$ is small).  This means that we will sample LFs that we *think* are good, but aren't sure yet.

### Strengths
* Can be used for an arbitrary family of LFs.
* Predicts the accuracy of LFs not explicitly evaluated by annotator.
    

### Weaknesses
* Difficult to "prime" with good LFs -- this results in a lot of initial time exploring the space of candidate LFs before finding good ones.
* Acquisition function won't necessarily find a diverse set of LFs
* Relies on LF families that are well-defined and easy to enumerate.  Does not necessarily scale well to acquisition functions with huge search spaces (e.g. regular expressions), especially since these are harder for humans to understand

# Active WeaSuL
### TL;DR
This paper proposes active learning to supplement an existing set of labeling functions with useful data points.  It has two main contributions: 

1. An active learning acquisition function which selects datapoints based on the LF "buckets" whose label model prediction in that bucket has highest KL-divergence the most from the average label of labeled subset in the same bucket.  This is calculated as:
\$$KL_i(p||q) = p\ \text{log}(\frac{p}{q}) + (1-p) \text{log}(\frac{1-p}{1-q})$$

where $$p \in [0,1]$$ is the probability assigned by the label model in that bucket and $$q \in [\epsilon, 1-\epsilon]$$ is the probability of the average label in the bucket, adjusted to prevent divide-by-zero errors.  

2. A simple update to the label model objective to constrain it to more closely align with labeled datapoints in each bucket.  This is obtained by augmenting the loss term on the label model with its MSE on the small, labeled subset of data points. 

### Strengths:
* Tackles two important problems of combining active learning with supervision: (1) creating a label model capable of using the subset of ground truth labels and (2) having a label model-aware acquisition function.
* The motivation and intuition behind both its label model and acquisition function are easy to understand.

### Weaknesses
* Acquisition function would not scale well to large number of label buckets (i.e. with hundreds of LFs), since this could put every data point in its own bucket (2^n possible buckets for n LFs).
* Acquisition function does not take downstream discriminative model into account, which could give more nuanced estimates of KL divergence.
* No justification of why MSE of label vs. probabilistic loss is right choice for updating label model based on labeled subset.





# ASTRA: Self Training with Weak Supervision
### TL;DR 
ASTRA combines principles of self-supervised and semi-supervised learning to combine weak rules, a small amount of labeled data, and all unlabeled data into a more effective end-to-end model for weak supervision.

### Algorithm
1. **Initial Student Model**
A student model is initially trained on the small labeled subset.  It then creates an additional probabilistic labeling function by predicting the (soft of hard) labels for every instance in the data.
2. **Rule Attention**
After augmenting the rule set with the baseline student predictions, ASTRA learns a weighting of the rules.  For each instance $$x_i$$, each matched rule $$r_j$$ receives a weight $$a_i^j \in [0,1]$$.  The rule $$r_j = {0,1}^K$$ (i.e. the one-hot vector of the rule's assigned label) is then interpolated with a uniform prior $$u = [\frac{1}{K}, \frac{1}{K}, ..., \frac{1}{K}]$$ as $$s_i^j = a_i^j r_j + (1-a_i^j) u$$.  Rule weights are calculated as $$a_i^j = \sigma \Big(f(x_i) \dot g(r_j) \Big)$$, where $$f(\dot)$$ is a function that projects latent representation (emgedding) of $$x_i$$ into the appropriate space, $$g(\dot)$$ is a function that embeds an individual rule, and $$\sigma$$ is the sigmoid function.
3. **Teacher Model**
The teacher model calcualtes an updated label for the data point as 
\$$q_i = \sum_{j=0}^{|R|} \frac{s_i^j}{|R_i| + 1}$$

Note that here, $$s_i^0$$ corresponds to the predictions of the old student model and $$R_i$$ is the set of matched rules on instance $$x_i$$
4. **Training**
For training, ASTRA fine-tunes the student model on the labeled data and the teacher labels from the previous iteration.  It then updates the teacher model using the improved student.  All parameters (including source attention) are learned from document-level supervision:
\$$L = -\sum{(x_i, y_i) \in D_L} y_i log(q_i) - \sum_{x_i \in D_U} q_i log(q_i)$$

### Strengths
* ASTRA effectively utilizes labeled data to both fine-tune a label model and train an end classifier.  
* By interpolating between LF outputs and a uniform prior, ASTRA prevents overfitting to noise on samples with a small number of LFs

### Weaknesses
* Would like to see analysis on how often rule reweighting was correct across each dataset
* Would be helpful to see how much each labeled instance helps (i.e. return on data labels vs LFs)



# WeaSEL
### TL;DR
WeaSEL postulates that the approach of training a label model followed by a downstream model is ineffective because it (1) requires restrictive assumptions interactions between labeling functions and (2) isn't able to learn from the downstream model it is meant to train.  It proposes a fix for this by learning instance-dependent LF aggregation weights and jointly optimizing these with a downstream neural network model.

### Algorithm
**Assumptions** Assume access to a set of labeling functions $$\Lambda$$ and data (**x**, y).  Each labeling function outputs a one-hot vector corresponding to the class is votes for.  We assume no access to labeled data.  We assume two different models that interact: (1) a rule encoder *e* that takes as input *x* and $$\Lambda$$ and outputs an aggregates rule probability and (2) a downstream model *f* that takes **x** as input and predicts the label based on these input features. In the paper, both *e* and *f* are MLPs.   The model's components and training are described below.

1. **Rule Aggregator $$e$$**
    We aggregate LFs at an instance-specific level using a softmax with temperature.  First, we obtain unnormalized scores for each LF as:

    \$$\theta(\Lambda, x) = \tau_2 \text{softmax}(e(\Lambda, x) \tau_1)$$

    The final probabilistic prediction then becomes:

    \$$y_e = \text{softmax}(\theta(\Lambda, x)^T \Lambda)$$

    i.e. the softmax of the weighted sum of LFss. Note that in practice, $$\tau_1 \leq \frac{1}{3}$$ and $$\tau_2=\sqrt{m}$$.  $$\tau_1 < 1$$ smooths the softmax to more closely resemble the uniform distribution and $$\tau_2 > 1$$ sharpens the final aggregation of LFs.

    In the paper, they describe the Rule Aggregator as using a neural network to reparameterize the posterior label model probability produced by the Markov Random Field used in the Snorkel papers.

2. They train $$e$$ and $$f$$ using a semi-supervised inspired loss:
    \$$L = CE(y_e, `stop_grad`(y_f)) + CE(y_f, `stop_grad`(y_e))$$
    That is, each model is trained to mimic the logits produced by the other.  

### Comments
The authors claim that using WeaSEL enables their model to effectively differentiate between 1 accurate LF and many other garbage LFs (which are generated programmatically as random noise).  However, these claims seem exaggerated *unless* they are adding each noisy source 1 at a time.  If this is the case, the algorithm could be useful in cases where weak supervision sources are generated programatically.

### Strengths
* By jointly training label model and end model, WeaSEL achieved better denoising than performing tasks separately.  Specifically, LF outputs on poorly matched instances are shifted to closer to a uniform distribution. 
* Model has some ability to throw out low-quality LFs

### Weaknesses
* Failure to compare to similar papers on weak supervision
* Use of non-standard set of LFs makes it difficult to compare to other methods.
* Would like to see analysis of how often instance-specific LF weights are correct (e.g. by comparison with true labels)



    




<!-- # Main areas of future work
1. How can most effectively select/use labeled data to improve label model performance?
* Would be useful to have label model parameters have a *prior distribution*, which is updated with labeled data
* Can we learn a neural network to reweight when lfs should/should not be applied?  Maybe a transformer (or even MLP) where output of each LF is a feature?  Could even project this down for greater simplicity.  SVMs seem like a potentially natural choice in this case because they base their predictions on such a sm
all proprotion of labeled data.
2. How can we effectively select/use labeled data to improve downstream model performance?
* Performance should be strictly better than active learning or weak supervision by themselves.  One way to help ensure this would be to weight the loss terms between strong (active) and weak labels to ensure that the sheer volume of weak labels doesn't dominate the higher-quality strong labels.
* It would be interesting to think of this as a Gaussian process (or some other bayesian something) over the distribution of data
3. How can we improve label model performance in general?  (Current models are better than majority voting only 2/3 of the time)
* I have a hunch that there are many nonlinear interactions between LFs that are not well captured by the PGM structure proposed for Snorkel
* What additional info can the *number of times* an LF fires on an example tell us about what its label should be? -->




