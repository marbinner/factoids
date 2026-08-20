---
id: logit_matching
aliases: []
tags: []
---

At high $T$ the softened probabilities go linear in the logits, and with
zero-mean logits the normaliser is just $D$:

$$p_i \approx \frac{1}{D}\left(1 + \frac{z_i}{T}\right)$$

The [[distillation]] gradient then collapses to a difference:

$$\frac{\partial L}{\partial z_i} \propto z_i - v_i$$

So high-temperature distillation is least squares on the logits:

$$L \to \tfrac{1}{2} \sum_i (z_i - v_i)^2$$

At finite $T$ the [[kl_divergence]] instead weights the small logits down.
