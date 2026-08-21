---
id: flash_attention
aliases: []
tags: []
---

[[attention]] forms the $n \times n$ score matrix only to weight $V$, and never
needs it whole — so writing it out and reading it back is pure waste.

Stream the keys in blocks instead, carrying a running max $m$, denominator
$\ell$ and unnormalised output $o$:

$$m' = \max(m, \tilde m), \qquad
\ell' = e^{m - m'} \ell + e^{\tilde m - m'} \tilde\ell, \qquad
o' = e^{m - m'} o + e^{\tilde m - m'} \tilde o$$

Divide once at the end. This is [[logsumexp_trick]] made incremental: every
partial sum is re-based whenever the max moves.

Exact — the same [[softmax]], accumulated in a different order.

The arithmetic stays $O(n^2 d)$; the memory traffic falls from $O(n^2)$ to
$O(n d)$, and attention is memory-bound, so that is the whole speedup.

Under [[causal_mask]] a block with $j > i$ throughout is skipped, not masked.

The backward pass recomputes the scores rather than storing them — more flops,
less traffic, the same trade.
