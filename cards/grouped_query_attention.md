---
id: grouped_query_attention
aliases: []
tags: []
---

Give $H$ query heads only $G$ key/value heads, with $G$ dividing $H$, so each
K/V head serves $H/G$ queries.

The [[kv_cache]] shrinks by the same factor:

$$2 \, L \, n \, d \;\to\; \frac{G}{H} \cdot 2 \, L \, n \, d$$

$G = H$ is ordinary multi-head [[attention]]; $G = 1$ is multi-query.

The query count is untouched, so only the keys and values lose resolution.
