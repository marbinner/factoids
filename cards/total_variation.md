---
id: total_variation
aliases: []
tags: []
---

Half the $L_1$ distance between two distributions:

$$\mathrm{TV}(y, p) = \tfrac{1}{2} \sum_j |y_j - p_j| = \max_A \, |y(A) - p(A)|$$

The largest disagreement over any event, and a genuine metric bounded in
$[0, 1]$ — no [[kl_asymmetry]] to work around.

Pinsker bounds it by [[kl_divergence]]:

$$\mathrm{TV}(y, p) \le \sqrt{\tfrac{1}{2} D_{\mathrm{KL}}(y \parallel p)}$$

Not reversible: on disjoint supports KL is infinite where TV is only $1$.
