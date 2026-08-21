---
id: cramer_rao
aliases: []
tags: []
---

No unbiased estimator beats the curvature of its own likelihood:

$$\mathrm{Cov}(\hat\theta) \succeq F(\theta)^{-1}$$

Differentiating $\mathbb{E}[\hat\theta] = \theta$ pairs the estimator with the
score, whose own mean is zero:

$$\mathbb{E}\!\left[(\hat\theta - \theta) \, \nabla \log p_\theta \right] = 1$$

Cauchy–Schwarz on that pairing is the whole proof:

$$1 \le \mathrm{Var}(\hat\theta) \cdot F(\theta)$$

[[fisher_information]] adds over independent samples, so $F_n = n F_1$ and the
floor falls as $1/n$ — the $1/\sqrt{n}$ standard error.

Flat likelihood, little information, loose estimate; sharp likelihood, the
reverse.

Bias voids the bound: shrinkage buys variance below the floor by aiming a
little off.
