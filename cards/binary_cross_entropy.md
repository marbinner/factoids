---
id: binary_cross_entropy
aliases: []
tags: []
---

For a binary label $y \in \{0, 1\}$ and logit $z$, with $p = \sigma(z)$ from
[[sigmoid]]:

$$L = -y \log p - (1-y) \log (1-p)$$

Only one term survives per example, the two-class case of the one-hot collapse
in [[cross_entropy_gradient]].

The gradient keeps that card's form:

$$\frac{\partial L}{\partial z} = \sigma(z) - y$$
