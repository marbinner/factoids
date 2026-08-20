---
id: mutual_information
aliases: []
tags: []
---

How much knowing $Y$ cuts the [[entropy]] of $X$:

$$I(X;Y) = H(X) - H(X \mid Y)$$

It is also a [[kl_divergence]] from the joint to the product of marginals:

$$I(X;Y) = D_{\mathrm{KL}}\!\left(p(x,y) \parallel p(x)\,p(y)\right)$$

So it is non-negative by [[jensens_inequality]], and zero exactly when $X$ and
$Y$ are independent.

Symmetric, even though the conditional form does not look it.
