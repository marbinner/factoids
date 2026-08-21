---
id: maximum_likelihood
aliases: []
tags: []
---

Choose the parameters that make the observed data least surprising:

$$\hat\theta = \arg\max_\theta \sum_i \log p_\theta(x_i)$$

Divided by $n$ that is an expectation under the empirical distribution
$\hat{p}$, so up to the fixed [[entropy]] $H(\hat{p})$ it is

$$\arg\min_\theta \; D_{\mathrm{KL}}(\hat{p} \parallel p_\theta)$$

The forward direction of [[kl_asymmetry]]: every observed $x$ must be given
mass, while unobserved ones need not be denied it.

At the optimum the score averages to zero over the sample:

$$\sum_i \nabla_\theta \log p_\theta(x_i) = 0$$

For a softmax model that is the $p - y$ of [[cross_entropy_gradient]], pulled
back through the network and summed over tokens.

Asymptotically normal with covariance $F^{-1}/n$, so it meets [[cramer_rao]] in
the limit — though at finite $n$ it is generally biased.
