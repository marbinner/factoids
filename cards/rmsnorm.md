---
id: rmsnorm
aliases: []
tags: []
---

Divide an activation by its own root-mean-square, then rescale per dimension:

$$\bar{x} = \frac{x}{\sqrt{\frac{1}{d} \sum_i x_i^2 + \epsilon}} \odot g$$

LayerNorm subtracts the mean and adds a bias as well; both are dropped here at
no cost — the stabilising part was always the scale.

The map is degree-zero homogeneous, $\bar{x}(\alpha x) = \bar{x}(x)$, so
differentiating $L(\alpha x) = L(x)$ at $\alpha = 1$ gives

$$\langle \nabla_x L, \; x \rangle = 0$$

The loss can turn $x$ but never lengthen it, and weights that grow only shrink
their own effective step.

It sits on each block's input rather than its output, leaving the residual path
an unnormalised identity.

Applied to $q$ and $k$ directly it bounds the logits by construction, which the
$\sqrt{d_k}$ of [[attention]] only assumes.
