---
id: attention
aliases: []
tags: []
---

Attention scores queries against keys, normalises, and mixes the values:

$$\mathrm{Attn}(Q, K, V) = \mathrm{softmax}\!\left(\frac{QK^{\top}}{\sqrt{d_k}}\right) V$$

The [[softmax]] runs over keys, so each output is a convex combination of rows
of $V$.

A dot product of $d_k$ independent zero-mean unit-variance terms has variance $d_k$:

$$\mathrm{Var}(q \cdot k) = d_k$$

Dividing by $\sqrt{d_k}$ returns it to $1$ — the [[temperature]] that keeps the
logits from sharpening as width grows.

Computed without ever materialising the score matrix in [[flash_attention]].
