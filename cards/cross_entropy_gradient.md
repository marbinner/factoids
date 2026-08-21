---
id: cross_entropy_gradient
aliases: []
tags: []
---

Cross-entropy between a target distribution $y$ and the predicted one $p$:

$$L = -\sum_j y_j \log p_j$$

For a one-hot target, every term but the true class $c$ is multiplied by zero:

$$L = -\log p_c$$

Take the negative of the [[log_softmax_gradient]] which gives:

$$\frac{\partial L}{\partial z_c} = p_c - 1 \qquad \frac{\partial L}{\partial z_j} = p_j$$

Both cases are combined in the vector expression:

$$\frac{\partial L}{\partial z} = p - y$$

Summed over a dataset this is [[maximum_likelihood]].
