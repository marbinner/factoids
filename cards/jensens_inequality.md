---
id: jensens_inequality
aliases: []
tags: []
---

For convex $f$, the value at the mean is below the mean of the values:

$$f(\mathbb{E}[X]) \le \mathbb{E}[f(X)]$$

$-\log$ is convex, and [[kl_divergence]] is an expectation of it:

$$D_{\mathrm{KL}}(y \parallel p) = \mathbb{E}_y\!\left[-\log \frac{p_j}{y_j}\right] \ge -\log \sum_j p_j = 0$$

Equality only at $p = y$, so [[entropy]] is the floor of cross-entropy.
