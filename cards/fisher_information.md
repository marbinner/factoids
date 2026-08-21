---
id: fisher_information
aliases: []
tags: []
---

The score $\nabla_\theta \log p_\theta$ has mean zero, so all that is left of it
is a covariance:

$$F = \mathbb{E}_{p_\theta}\!\left[\nabla \log p_\theta \, \nabla \log p_\theta^{\top}\right]
= -\,\mathbb{E}_{p_\theta}\!\left[\nabla^2 \log p_\theta\right]$$

It is the curvature of [[kl_divergence]] at zero displacement, where value and
gradient both vanish:

$$D_{\mathrm{KL}}(p_\theta \parallel p_{\theta+\delta})
= \tfrac{1}{2} \, \delta^{\top} F \delta + O(\|\delta\|^3)$$

Either direction gives the same $F$, so [[kl_asymmetry]] is a third-order
effect — invisible up close.

Reparametrising sends $F \mapsto J^{\top} F J$, so $\delta^{\top} F \delta$
measures a move between distributions rather than between coordinates.

For a softmax model the score is the $p - y$ of [[cross_entropy_gradient]], so
in logit space

$$F = \mathrm{diag}(p) - p p^{\top}$$

one factor of $p_i$ on from [[log_softmax_gradient]].

Inverted, it floors the variance of any unbiased estimator in [[cramer_rao]].
