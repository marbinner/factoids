Softmax and log-probabilities both need this term:

$$\log \sum_j e^{z_j}$$

Computed directly it overflows: a logit of 800 is already `inf` in float32.

Subtracting a constant from every logit leaves softmax unchanged.

So take $m = \max_j z_j$:

$$\log \sum_j e^{z_j} = m + \log \sum_j e^{z_j - m}$$

The largest exponent is now $e^0 = 1$, so nothing overflows, and whatever
underflows to zero was negligible anyway.

Which is why we use `log_softmax(z)` instead of `log(softmax(z))`.
