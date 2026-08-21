---
id: importance_sampling
aliases: []
tags: []
---

Sample from the wrong distribution and reweight:

$$\mathbb{E}_p[f] = \mathbb{E}_q\!\left[w(x) \, f(x)\right], \qquad
w(x) = \frac{p(x)}{q(x)}$$

Unbiased for any $q$ covering the support of $p$; where $q = 0 < p$ the mass is
simply never proposed.

The weight has mean one and its variance is the $\chi^2$ divergence:

$$\mathbb{E}_q[w] = 1, \qquad
\mathrm{Var}_q(w) = \sum_j \frac{(p_j - q_j)^2}{q_j} = \chi^2(p \parallel q)$$

Which dominates [[kl_divergence]] by [[jensens_inequality]]:

$$D_{\mathrm{KL}}(p \parallel q) \le \log\!\left(1 + \chi^2(p \parallel q)\right)$$

So it fails by variance, not by bias — a few heavy weights carrying the whole
estimate:

$$n_{\text{eff}} = \frac{\left(\sum_i w_i\right)^2}{\sum_i w_i^2}$$

Known only up to a constant, $p$ still serves if the weights are divided by
their own sum — biased at finite $n$, consistent as it grows.

Off-policy [[policy_gradient]] is this with $w = \pi_\theta / \pi_{\text{old}}$.

Clipped and iterated, that is [[ppo]].
