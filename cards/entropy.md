---
id: entropy
aliases: []
tags: []
---

Entropy of a distribution $y$ is the expected surprise $-\log y_j$ under $y$:

$$H(y) = -\sum_j y_j \log y_j$$

Bounded above by the uniform distribution over $D$ outcomes:

$$H(y) \le \log D$$

Zero for a one-hot distribution, taking $0 \log 0 = 0$.

The constant term in [[kl_divergence]], and the exponent in [[perplexity]].
