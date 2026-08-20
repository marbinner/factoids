---
id: log_softmax_gradient
aliases: []
tags: []
---

We have a vector that contains one logit for each dictionary entry:

$$z \in \mathbb{R}^D$$

We can plug this vector into [[softmax]] to get a probability vector:

$$p_i = \frac{e^{z_i}}{\sum_j e^{z_j}}$$

The log-probability is then on this form:

$$\log p_i = z_i - \log \sum_j e^{z_j}$$

Taking gradient gives us this:

$$\frac{\partial \log p_i}{\partial z_i} = 1 - \frac{e^{z_i}}{\sum_j e^{z_j}} = 1 - p_i$$

$$\frac{\partial \log p_i}{\partial z_j} = 0 - \frac{e^{z_j}}{\sum_j e^{z_j}} = 0 - p_j$$
