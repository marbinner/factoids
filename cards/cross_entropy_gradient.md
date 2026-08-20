---
id: cross_entropy_gradient
aliases: []
tags: []
---

Cross-entropy between a target distribution $y$ and the predicted one $p$:

$$L = -\sum_j y_j \log p_j$$

For a one-hot target, every term but the true class $c$ is multiplied by zero:

$$L = -\log p_c$$

[[log_softmax_gradient]] then gives:

$$\frac{\partial L}{\partial z_c} = p_c - 1 \qquad \frac{\partial L}{\partial z_j} = p_j$$

Both cases are the same vector expression:

$$\frac{\partial L}{\partial z} = p - y$$

Predicted distribution minus target distribution, nothing more. Also holds for
soft targets, since the derivation only needs $\sum_j y_j = 1$.
