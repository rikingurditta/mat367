# Tangent Spaces

$$
\newcommand{\ds}{\displaystyle}
\newcommand{\curlies}[1]{\left\lbrace #1 \right\rbrace}
\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}
\newcommand{\angles}[1]{\left\langle #1 \right\rangle}
\newcommand{\inv}[1]{#1^{-1}}
\DeclareMathOperator{\supp}{supp}
\DeclareMathOperator{\id}{id}
\DeclareMathOperator{\rank}{rank}
\DeclareMathOperator{\Mat}{Mat}

\newcommand{\A}{\mathcal A}
\newcommand{\RP}[1]{\R P^{#1}}
\newcommand{\CP}[1]{\C P^{#1}}

\newcommand{\a}{\mathbf a}
\newcommand{\u}{\mathbf u}
\newcommand{\x}{\mathbf x}
\newcommand{\y}{\mathbf y}
$$

## Tangent spaces

Let $M$ be an $m$-dimensional manifold. For $p \in M$, the **tangent space** $T_p M$ is the set of all linear maps $v : C^\infty(M) \to \R$ of the form
$$
v(f) = \frac{d}{dt}\bigg\vert_{t=0} f(\gamma(t))
$$
where $\gamma \in C^\infty(J, M)$ is a smooth map with $\gamma(0) = p$ and $J \subseteq \R$ is an interval containing $0$. The elements of $T_p M$ are called **tangent vectors** to $M$ at $p$.

### Charts and tangent spaces

Let $(U, \phi)$ be a coordinate chart around $p$. A linear map $v : C^\infty(M) \to \R$ belongs to $T_p M$ if and only if it has the form
$$
v(f) = \sum_{i=1}^m a^i \frac{\partial (f \circ \inv\phi)}{\partial u^i} \bigg\vert_{\u=\phi(p)} = \a \cdot \nabla (f \circ \inv \phi)\vert_{\phi(p)}
$$
for some $\a = (a^1, ..., a^m) \in \R^m$.

As a consequence, $T_p M$ is an $m$-dimensional vector space.

**Proof.**

($\Rightarrow$) Suppose $v \in T_p M$, then for any $f \in \C^\infty(M)$,

$$
v(f) = \frac{d}{dt} \bigg\vert_{t=0} f(\gamma(t))
$$

for some $\gamma \in C^\infty(J, M)$ with $\gamma(0) = p$. Inserting $\phi$, we see that

$$
v(f) = \frac{d}{dt} \bigg\vert_{t=0} f(\inv \phi \circ \phi \circ \gamma(t))
$$

so if $\widetilde \gamma = \phi \circ \gamma$

$$
v(f) = \frac{d}{dt} \bigg\vert_{t=0} (f \circ \inv \phi)(\widetilde \gamma(t))
$$

Since $\widetilde \gamma : J \to \R^m$, we have a composition of functions between Euclidean spaces, so we can use the chain rule to see

$$
\begin{align*}
v(f) &= \sum_{i=1}^m \frac{\partial (f \circ \inv \phi)}{\partial u^i} \bigg\vert_{\u=\widetilde\gamma(0)} \frac{\partial \widetilde\gamma^i}{\partial t} \bigg\vert_{t=0} \\
&= \sum_{i=1}^m \frac{\partial (f \circ \inv \phi)}{\partial u^i} \bigg\vert_{\u=\phi(p)} a^i \\
&= \nabla (f \circ \inv \phi)\vert_{\phi(p)} \cdot \a
\end{align*}
$$

where $\ds a^i = \frac{d\widetilde\gamma^i}{dt}\bigg\vert_{t=0}$, so  $\ds \a = \frac{\partial \widetilde \gamma}{\partial t} \bigg\vert_{t=0}$. So we have shown what we wanted.

($\Leftarrow$) Suppose we have a map

$$
v(f) = v(f) = \sum_{i=1}^m a^i \frac{\partial (f \circ \inv\phi)}{\partial u^i} \bigg\vert_{\u=\phi(p)}
$$

for some $\a = (a^1, ..., a^m)$. Then we want to find a curve $\gamma$ so that

$$
v(f) = \frac{d}{dt} \bigg\vert_{t=0} f(\gamma(t))
$$

To do this, let $\gamma(t) = \inv\phi(\phi(p) + t\a)$. Then,

$$
\begin{align*}
\frac{d}{dt} \bigg\vert_{t=0} f(\gamma(t)) &= \frac{d}{dt} \bigg\vert_{t=0} f(\inv\phi(\phi(p) + t\a)) \\
&= \frac{d}{dt} \bigg\vert_{t=0} (f \circ \inv\phi)(\phi(p) + t\a) \\
&= [...]
\end{align*}
$$

so we have once again shown what we wanted.

Since these two are equivalent, we can consider this to be an alternate definition of the tangent space. i.e., we can define the tangent space $T_p M$ to be the set of all linear maps $v : C^\infty(M) \to \R$ of the form
$$
v(f) = \sum_{i=1}^m a^i \frac{\partial (f \circ \inv\phi)}{\partial u^i} \bigg\vert_{\u=\phi(p)} = \a \cdot \nabla (f \circ \inv \phi)\vert_{\phi(p)}
$$

for some $\a = (a^1, ..., a^m) \in \R^m$.