---
id: ppo
aliases: []
tags: []
---

Reuse a batch of rollouts by optimising the reweighted return of
[[importance_sampling]]:

$$L = \mathbb{E}_{\pi_{\text{old}}}\!\left[\, r_t A_t \,\right], \qquad
r_t = \frac{\pi_\theta(a_t \mid s_t)}{\pi_{\text{old}}(a_t \mid s_t)}$$

At $\theta = \theta_{\text{old}}$ every $r_t = 1$ and $\nabla r = r \nabla \log
\pi_\theta$, so this is exactly [[policy_gradient]] — the ratio only matters
once the policy has moved.

Which it cannot be trusted to do far, so cap the gain:

$$L = \mathbb{E}\Big[\min\!\big(r_t A_t, \;\; \mathrm{clip}(r_t, 1-\epsilon, 1+\epsilon)\, A_t\big)\Big]$$

The min always takes the pessimistic branch: a good action earns nothing past
$1 + \epsilon$, a bad one stops paying below $1 - \epsilon$, and the gradient
dies at both walls.

So the update is bounded per sample and one batch survives several epochs.

Bounding $D_{\mathrm{KL}}(\pi_{\text{old}} \parallel \pi_\theta)$ itself is the
honest version; the clip is the cheap one — per-token, and blind to how far the
whole distribution has drifted.
