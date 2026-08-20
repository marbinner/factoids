---
id: temperature
aliases: []
tags: []
---

Temperature rescales the logits before [[softmax]]:

$$p_i = \frac{e^{z_i/T}}{\sum_j e^{z_j/T}}$$

It divides the log-odds, so it only stretches or shrinks the gaps:

$$\log \frac{p_i}{p_j} = \frac{z_i - z_j}{T}$$

$T \to 0$ sends every gap to infinity and gives argmax; $T \to \infty$ sends
them to zero and gives uniform.

So [[entropy]] rises monotonically with $T$, from $0$ to $\log D$.
