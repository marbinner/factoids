---
id: softmax
aliases: []
tags: []
---

Softmax turns a logit vector $z \in \mathbb{R}^D$ into a probability vector:

$$p_i = \frac{e^{z_i}}{\sum_j e^{z_j}}$$

Every entry is positive and they sum to one, so $p$ is a distribution.

It is the inverse of log-odds — any two probabilities recover the logit gap:

$$\log \frac{p_i}{p_j} = z_i - z_j$$

So only differences carry information, which [[logsumexp_trick]] exploits.

In log space it is the logit minus the logsumexp:

$$\log p_i = z_i - \log \sum_j e^{z_j}$$

Differentiated in [[log_softmax_gradient]].
