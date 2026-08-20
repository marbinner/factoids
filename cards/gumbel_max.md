---
id: gumbel_max
aliases: []
tags: []
---

Perturb each logit with independent Gumbel noise and take the argmax:

$$\arg\max_i \; (z_i + g_i), \qquad g_i \sim \mathrm{Gumbel}(0, 1)$$

The index it returns is distributed exactly as [[softmax]] of $z$.

The noise comes from a uniform by inverting the CDF:

$$g = -\log(-\log u), \qquad u \sim \mathrm{Uniform}(0, 1)$$

No normalising constant is formed, so unnormalised logits suffice.

Dividing the logits by $T$ first gives [[temperature]] sampling.
