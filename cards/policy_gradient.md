---
id: policy_gradient
aliases: []
tags: []
---

A trajectory's probability factors into a policy the parameters control and
dynamics they do not:

$$p_\theta(\tau) = p(s_0) \prod_t \pi_\theta(a_t \mid s_t) \, P(s_{t+1} \mid s_t, a_t)$$

In logs the environment is additive and constant, so it vanishes under the
gradient:

$$\nabla_\theta \log p_\theta(\tau) = \sum_t \nabla_\theta \log \pi_\theta(a_t \mid s_t)$$

[[log_derivative_trick]] then differentiates the expected return without ever
differentiating the world:

$$\nabla_\theta J = \mathbb{E}\Big[\, R(\tau) \sum_t \nabla_\theta \log \pi_\theta(a_t \mid s_t) \Big]$$

Reward collected before $a_t$ cannot depend on it, so its weight shrinks to the
return-to-go $G_t$; a baseline $V(s_t)$ subtracts unbiasedly as long as it does
not depend on the action:

$$\nabla_\theta J = \mathbb{E}\Big[\, \sum_t A_t \, \nabla_\theta \log \pi_\theta(a_t \mid s_t) \Big], \qquad A_t = G_t - V(s_t)$$

For a softmax policy $\nabla_z \log \pi(a) = y - p$, the negated
[[cross_entropy_gradient]] — so a step is [[maximum_likelihood]] on the model's
own samples, weighted by $A_t$.
