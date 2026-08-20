---
id: kv_cache
aliases: []
tags: []
---

Under [[causal_mask]] a token attends only backwards, so its key and value never
change once computed.

Decoding step $n$ is then one query against $n$ cached keys:

$$O(n\,d) \quad \text{per step, instead of} \quad O(n^2 d)$$

The cache holds two vectors per token per layer:

$$2 \, L \, n \, d \quad \text{entries}$$

Linear in context, so long generation is bounded by memory rather than
[[attention]] compute.

Shrunk by sharing heads in [[grouped_query_attention]].
