---
id: logsumexp_trick
aliases: []
tags: []
---

Softmax and log-probs need the logsumexp:

$$\log \sum_j e^{z_j}$$

Which overflows easily because of exponentiating logits.

Subtracting a constant from every logit leaves softmax unchanged.

So take $m = \max_j z_j$:

$$\log \sum_j e^{z_j} = m + \log \sum_j e^{z_j - m}$$

The largest exponent is now $e^0 = 1$, so nothing overflows, and whatever
underflows to zero was negligible anyway.

Applied incrementally, block by block, in [[flash_attention]].
