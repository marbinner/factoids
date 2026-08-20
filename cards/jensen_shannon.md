---
id: jensen_shannon
aliases: []
tags: []
---

Average both directions of [[kl_divergence]] against the mixture
$m = \tfrac{1}{2}(y + p)$:

$$\mathrm{JS}(y, p) = \tfrac{1}{2} D_{\mathrm{KL}}(y \parallel m) + \tfrac{1}{2} D_{\mathrm{KL}}(p \parallel m)$$

Symmetric by construction, so it escapes [[kl_asymmetry]].

$m_j \ge y_j / 2$ wherever $y_j > 0$, so every ratio is at most $2$ and neither
term diverges:

$$0 \le \mathrm{JS}(y, p) \le \log 2$$

Its square root satisfies the triangle inequality.
