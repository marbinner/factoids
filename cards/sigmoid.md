---
id: sigmoid
aliases: []
tags: []
---

Sigmoid maps a single logit to a probability:

$$\sigma(z) = \frac{1}{1 + e^{-z}}$$

It inverts log-odds, so the logit is the log-odds itself:

$$\log \frac{p}{1-p} = z$$

It is [[softmax]] over two classes with one logit pinned to zero:

$$\frac{e^z}{e^z + e^0} = \frac{1}{1 + e^{-z}}$$

Its derivative, and the log-space form from [[log_softmax_gradient]]:

$$\sigma'(z) = \sigma(z)(1 - \sigma(z)) \qquad \frac{\partial \log \sigma}{\partial z} = 1 - \sigma(z)$$
