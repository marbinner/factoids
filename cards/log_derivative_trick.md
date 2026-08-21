---
id: log_derivative_trick
aliases: []
tags: []
---

A density carries its own gradient as a factor:

$$\nabla_\theta \, p_\theta(x) = p_\theta(x) \, \nabla_\theta \log p_\theta(x)$$

Push that through an expectation whose integrand does not depend on $\theta$:

$$\nabla_\theta \, \mathbb{E}_{p_\theta}\!\left[f(x)\right]
= \mathbb{E}_{p_\theta}\!\left[f(x) \, \nabla_\theta \log p_\theta(x)\right]$$

The gradient of an expectation becomes an expectation of a gradient, so samples
estimate it even when $f$ is discrete, non-differentiable or a black box — only
$\log p_\theta$ must be differentiable.

Setting $f = 1$ recovers the zero-mean score behind [[fisher_information]]:

$$\mathbb{E}\!\left[\nabla_\theta \log p_\theta\right] = \nabla_\theta 1 = 0$$

So any baseline $b$ that does not depend on $x$ leaves the estimator unbiased:

$$\mathbb{E}\!\left[(f - b) \, \nabla_\theta \log p_\theta\right]
= \nabla_\theta \, \mathbb{E}\!\left[f\right]$$

It is chosen to cut variance, which is the whole weakness: the estimator scales
with $f$ itself, not with its slope.

Called the score-function estimator, or REINFORCE when $f$ is a reward.
