---
id: kl_divergence
aliases: []
tags: []
---

KL divergence from a target $y$ to a prediction $p$:

$$D_{\mathrm{KL}}(y \parallel p) = \sum_j y_j \log \frac{y_j}{p_j}$$

Splitting the log separates cross-entropy from the [[entropy]] of $y$:

$$D_{\mathrm{KL}}(y \parallel p) = -\sum_j y_j \log p_j + \sum_j y_j \log y_j$$

$$\mathrm{CE}(y, p) = H(y) + D_{\mathrm{KL}}(y \parallel p)$$

$H(y)$ is fixed by the data, so minimising cross-entropy minimises KL.

For a one-hot target $H(y) = 0$ and the two are equal, which is what
[[cross_entropy_gradient]] descends.

A KL from a joint to its marginals is [[mutual_information]].
