---
id: softplus
aliases: []
tags: []
---

Softplus is a smooth positive function of a logit:

$$\mathrm{softplus}(z) = \log(1 + e^{z})$$

It is the logsumexp of $\{0, z\}$, so [[logsumexp_trick]] applies unchanged.

It writes the [[binary_cross_entropy]] term without forming a probability:

$$-\log \sigma(z) = \mathrm{softplus}(-z)$$

Its derivative is [[sigmoid]]:

$$\mathrm{softplus}'(z) = \sigma(z)$$
