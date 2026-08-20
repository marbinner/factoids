---
id: causal_mask
aliases: []
tags: []
---

Add $-\infty$ to every future score before the [[attention]] softmax:

$$s_{ij} \leftarrow s_{ij} + m_{ij}, \qquad m_{ij} = -\infty \;\text{ if } j > i$$

$e^{-\infty} = 0$, so those keys drop out and the row still sums to one.

Zeroing after the [[softmax]] instead would leave the rows unnormalised.

A fully masked row sends $m = -\infty$ in [[logsumexp_trick]], where
$-\infty - (-\infty)$ is NaN.
