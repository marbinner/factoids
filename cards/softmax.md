---
id: softmax
aliases: []
tags: []
---

Softmax turns a logit vector $z \in \mathbb{R}^D$ into a probability vector:

$$p_i = \frac{e^{z_i}}{\sum_j e^{z_j}}$$

Every entry is positive and they sum to one, so $p$ is a distribution.

Shifting every logit by a constant leaves it unchanged:

$$\frac{e^{z_i - c}}{\sum_j e^{z_j - c}} = \frac{e^{z_i}}{\sum_j e^{z_j}}$$

Which is what [[logsumexp_trick]] exploits.

In log space it is the logit minus the logsumexp:

$$\log p_i = z_i - \log \sum_j e^{z_j}$$

Differentiated in [[log_softmax_gradient]].
