---
id: distillation
aliases: []
tags: []
---

Train a student against a teacher's softened distribution instead of the label,
matched by [[kl_divergence]]:

$$L = T^{2} \, D_{\mathrm{KL}}\!\left(p^{t}_{T} \parallel p^{s}_{T}\right)$$

Both sides share the [[temperature]] $T$, which lifts the off-target
probabilities into view.

They carry the teacher's similarity structure, which a one-hot target discards —
a learned [[label_smoothing]].

Soft-target gradients scale as $1/T^{2}$, so the prefactor restores them.
