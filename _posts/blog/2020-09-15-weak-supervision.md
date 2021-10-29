---
layout: post
title: "Interactive Weak Supervision: A Review"
categories: blog
permalink: blog/interactive-weak-supervision
---

Weak supervision is a powerful way to build a ML model from scratch without any initially labeled data.  This paper presents a review of paradigms for weakly supervised learning, as well as a summary of my own work at the intersection of weakly supervised learning and active learning.

<!--more-->

# Interactive Weak Supervision
### TL;DR
This paper proposes an active learning strategy for identifying good labeling functions from a large set of candidate LFs based on LF-level user labels.  The goal is to develop a model that can correctly select LFs with accuracy > r, where r > .5 for binary classification. It uses an ensemble of neural networks to estimate a distribution of accuracy for each LF candidate.  It then prioritizes LFs via an acquisition function which prioritizes LFs with high variance and mean close to the decision boundary.  LFs are represented purely by the points which they label.  
This paper only considers binary classification.

### More details
Latent variable model:
* $\lambda_j$: $j^{th}$ labeling function
* $u_j$: Human label given to $\lambda_j$
* $v_j$: Probability that human assigns $u_j = 1$
* $Q_t$: The set of labeling functions labeled at time $t$ as having accuracy $\alpha_j > r$ (label = 1), or $\alpha_j < r$ (label = 0)

We parameterize $p(\alpha_j | Q_{t-1})$ (i.e. the probability distribution of $\lambda_j$'s accuracy given what we know about the labeling functions in the set Q ) as an ensemble of neural networks with input $\lambda_j$.  Each neural network induces a mapping $h \rightarrow [0,1]$.  The network specifically maps $h( \tau  ( \lambda_j ))$ where $ \tau_0 (\lambda_j) = [\lambda_j(x_1), \hdots, \lambda_j(x_n)]^T$, i.e. the vector of LF outputs of $\lambda_j$ on all documents in the training corpus.  We then project this using SVD/PCA to 150 dimensions, and call this projection $ \tau  ( \lambda_j )$ .  In other words, we featurize labeling functions as a projection of their output across the entire training set.  

In order to find good points, we use the saddle acquisition function, which is:
    $\phi_a^{LSE}(\lambda) = 1.96 * \sigma_j(Q_{t-1}) + |\mu_j(Q_{t-1}) - r|$
where $\sigma_j(Q_{t-1})$ is the standard deviation of the probabilities of $\lambda_j$ output by the bagging ensemble and $\mu_j(Q_{t-1})$ is the mean probability output for $\lambda_j$

This identifies LFs which are unknown (e.g. high variance) and near the decision boundary (e.g. difference between mean score $\mu_j$ and boundary $r$ is small).  This means that we will sample LFs that we *think* are good, but aren't sure yet.

### Weaknesses
This paper has a few main weaknesses:
* Acquisition function
* Relies on LF families that are well-defined and easy to enumerate.  Does not necessarily scale well to acquisition functions with huge search spaces (e.g. regular expressions), especially since these are harder for humans to understand

# Active WeaSuL
### TL;DR
    This paper proposes active learning to supplement an existing set of labeling functions with useful data points.  It has two main contributions: 

        1. An active learning acquisition function which selects datapoints based on the LF "buckets" whose label model prediction in that bucket has highest KL-divergence the most from the average label of labeled subset in the same bucket.  This is calculated as:
            $$KL_i(p||q) = p* \texttt{log}(\frac{p}{q}) + (1-p)* \texttt{log}(\frac{1-p}{1-q})$$
        where $p \in [0,1]$ is the probability assigned by the label model in that bucket and $q \in [\epsilon, 1-\epsilon]$ is the probability of the average label in the bucket, adjusted to prevent divide-by-zero errors.  

        2. A simple update to the label model objective to constrain it to more closely align with labeled datapoints in each bucket.  This is obtained by augmenting the loss term on the label model with its MSE on the small, labeled subset of data points. 

### Strengths:
    * Tackles two important problems of combining active learning with supervision: (1) creating a label model capable of using the subset of ground truth labels and (2) having a label model-aware acquisition function.
    * The motivation and intuition behind both its label model and acquisition function are easy to understand.

### Weaknesses
    * Acquisition function would not scale well to large number of label buckets (i.e. with hundreds of LFs), since this could put every data point in its own bucket (2^n possible buckets for n LFs).
    * Acquisition function does not take downstream discriminative model into account, which could give more nuanced estimates of KL divergence.
    * No justification of why MSE of label vs. probabilistic loss is right choice for updating label model based on labeled subset.


# Learning from Rules Generalizing Labeled Exemplars
    ### TL;DR


# ASTRA: Self Training with Weak Supervision
    ### TL;DR 
        Astra combines principles of self-supervised and semi-supervised learning to combine weak rules, a small amount of labeled data, and all unlabeled data into a more effective end-to-end model for weak supervision.

    ### Algorithm
        1. **Initial Student Model**
            A student model is initially trained on the small labeled subset.  It then creates an additional probabilistic labeling function by predicting the (soft of hard) labels for every instance in the data.
        2. **Rule Attention**
            After augmenting the rule set with the baseline student predictions, ASTRA learns a weighting of the rules.  For each instance $x_i$, each matched rule $r_j$ receives a weight $a_i^j \in [0,1]$.  The rule $r_j = {0,1}^K$ (i.e. the one-hot vector of the rule's assigned label) is then interpolated with a uniform prior $u = [\frac{1}{K}, \frac{1}{K}, /hdots, \frac{1}{K}]$ as $s_i^j = a_i^j r_j + (1-a_i^j) u$.  Rule weights are calculated as $a_i^j = \sigma \Big(f(x_i) \dot g(r_j) \Big), where $f(\dot)$ is a function that projects latent representation (emgedding) of $x_i$ into the appropriate space, $g(\dot)$ is a function that embeds an individual rule, and $\sigma$ is the sigmoid function.
        3. **Teacher Model**
            The teacher model calcualtes an updated label for the data point as 
            $$ \sum_{j=0}^{|R|} \frac{s_i^j}{|R_i| + 1}$$
            Note that here, $\s_i^0$ corresponds to the predictions of the old student model and $R_i$ is the set of matched rules on instance $x_i$
        4. **Training**
            We fine-tune the 

        




# Main areas of future work
1. How can most effectively select/use labeled data to improve label model performance?
    * Would be useful to have label model parameters have a *prior distribution*, which is updated with labeled data
    * Can we learn a neural network to reweight when lfs should/should not be applied?  Maybe a transformer (or even MLP) where output of each LF is a feature?  Could even project this down for greater simplicity.  SVMs seem like a potentially natural choice in this case because they base their predictions on such a sm
    all proprotion of labeled data.
2. How can we effectively select/use labeled data to improve downstream model performance?
    * Performance should be strictly better than active learning or weak supervision by themselves.  One way to help ensure this would be to weight the loss terms between strong (active) and weak labels to ensure that the sheer volume of weak labels doesn't dominate the higher-quality strong labels.
    * It would be interesting to think of this as a Gaussian process (or some other bayesian something) over the distribution of data
3. How can we improve label model performance in general?  (Current models are better than majority voting only 2/3 of the time)
    * I have a hunch that there are many nonlinear interactions between LFs that are not well captured by the PGM structure proposed for Snorkel
    * What additional info can the *number of times* an LF fires on an example tell us about what its label should be?




        


#
