Softmax and log-probs need this term:

$$\log \sum_j e^{z_j}$$

Which overflows easily because of exponents.

Subtracting a constant from every logit leaves softmax unchanged.

So take $m = \max_j z_j$:

$$\log \sum_j e^{z_j} = m + \log \sum_j e^{z_j - m}$$

The largest exponent is now $e^0 = 1$, so nothing overflows, and whatever
underflows to zero was negligible anyway.
