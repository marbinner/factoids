---
id: rope
aliases: []
tags: []
---

Position enters [[attention]] as a rotation of the query and key — nothing
added, nothing learned.

Split the head into coordinate pairs and rotate pair $t$ of token $m$ by
$m\theta_t$:

$$\theta_t = b^{-2t/d}, \qquad
R_m^{(t)} = \begin{pmatrix}
\cos m\theta_t & -\sin m\theta_t \\
\sin m\theta_t & \cos m\theta_t
\end{pmatrix}$$

Rotations compose and transpose, so the score keeps only the offset:

$$\langle R_m q, \; R_n k \rangle = \langle q, \; R_{n-m} k \rangle$$

Absolute per token, relative in the score.

Orthogonal, so norms survive and the $\sqrt{d_k}$ scaling still holds.

Each key is rotated by its own index alone, so [[kv_cache]] entries never need
rewriting as the context grows.

Pairs run from fast to slow, with the slowest wavelength $2\pi b$ — beyond it
the angle wraps and positions alias. Extending context shrinks $\theta$ so
unseen $m$ lands between angles already trained.
