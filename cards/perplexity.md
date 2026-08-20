---
id: perplexity
aliases: []
tags: []
---

Perplexity is [[entropy]] exponentiated:

$$\mathrm{PPL}(y) = e^{H(y)}$$

Uniform over $D$ outcomes gives $\mathrm{PPL} = D$, so it reads as an effective
number of choices.

For a model it is the exponentiated mean loss of [[cross_entropy_gradient]] over
$N$ tokens:

$$\mathrm{PPL} = \exp\left(-\frac{1}{N}\sum_i \log p_{c_i}\right)$$

Monotone in that loss, so it ranks models identically.
