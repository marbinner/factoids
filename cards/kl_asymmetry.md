---
id: kl_asymmetry
aliases: []
tags: []
---

[[kl_divergence]] is not symmetric, so it is not a distance:

$$D_{\mathrm{KL}}(y \parallel p) \neq D_{\mathrm{KL}}(p \parallel y)$$

Forward is infinite where $y_j > 0$ and $p_j = 0$, so $p$ must cover every mode.

Reverse is infinite where $p_j > 0$ and $y_j = 0$, so $p$ collapses onto one.

Minimising [[cross_entropy_gradient]] is the forward direction; variational
inference takes the reverse.
