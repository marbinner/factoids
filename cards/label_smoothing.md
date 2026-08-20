---
id: label_smoothing
aliases: []
tags: []
---

Mix the one-hot target with the uniform $u$:

$$\tilde{y} = (1 - \varepsilon)\, y + \varepsilon\, u$$

The loss splits along the mixture:

$$L = (1 - \varepsilon)\, \mathrm{CE}(y, p) + \varepsilon\, \mathrm{CE}(u, p)$$

The second term is a [[kl_divergence]] to uniform, up to the constant $\log D$
from [[entropy]].

[[cross_entropy_gradient]] now vanishes at $p = \tilde{y}$, which has finite
logits, so the gaps stay bounded.
