# Topology

$$
\newcommand{\ds}{\displaystyle}
\newcommand{\curlies}[1]{\left\lbrace #1 \right\rbrace}
\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}
\newcommand{\angles}[1]{\left\langle #1 \right\rangle}
\newcommand{\inv}[1]{#1^{-1}}

\newcommand{\A}{\mathcal A}
\newcommand{\RP}[1]{\R P^{#1}}

\newcommand{\x}{\mathbf x}
\newcommand{\y}{\mathbf y}
$$

## Open sets

Let $M$ be an $m$-dimensional manifold (with maximal atlas $\A$). Then a subset $U \subseteq M$ is **open** if and only if $\phi_\alpha(U \cap U_\alpha)$ is open for every $(U_\alpha, \phi_\alpha) \in \A$.

### Open sets and sub-atlases

Let $\mathcal B \subseteq \A$ be a sub-atlas whose chart domains cover $M$. Then $U \subseteq M$ is open if and only if $\phi_\beta(U \cap U_\beta)$ is open for every $(U_\beta, \phi_\beta) \in \mathcal B$.

($\Rightarrow$) Suppose $\phi_\beta(U \cap U_\beta)$ is open for every $(U_\beta, \phi_\beta) \in \mathcal B$. Let $U \subseteq M$, and suppose $(U_\alpha, \phi_\alpha) \in \A$, and $(U_\beta, \phi_\beta) \in \mathcal B$. Then since the chart domains of $\mathcal B$ cover $M$,
$$
\begin{align*}
\phi_\alpha(U \cap U_\alpha) &= \phi_\alpha \left( \bigcup_{\beta} U \cap U_\alpha \cap U_\beta \right) \\
&= \bigcup_{\beta} \phi_\alpha(U \cap U_\alpha \cap U_\beta) \\
&= \bigcup_{\beta} \phi_\alpha((U \cap U_\beta) \cap (U_\alpha \cap U_\beta)) \\
&= \bigcup_{\beta} \phi_\alpha \circ \inv \phi_\beta(\phi_\beta(U \cap U_\beta) \cap \phi_\beta(U_\alpha \cap U_\beta)) \\
\end{align*}
$$
By assumption, $\phi_\beta(U \cap U_\beta)$ is open. Since $\mathcal B$ is a sub-atlas of $\mathcal A$, $(U_\beta, \phi_\beta)$ is compatible with $(U_\alpha, \phi_\alpha)$, so $\phi_\beta(U_\alpha \cap U_\beta)$ is open. Thus $\phi_\beta(U \cap U_\beta) \cap \phi_\beta(U_\alpha \cap U_\beta)$ is open. Also since the two coordinate charts are compatible, we know that $\phi_\alpha \circ \inv\phi_\beta$ is a diffeomorphism, which means that it maps open sets to open sets. As a result, the entire set $\phi_\alpha \circ \inv\phi_\beta(...)$ is open, so the union is open. This holds for all coordinate charts in $\A$, so $U$ must be open.

($\Leftarrow$) Suppose $U \subseteq M$ is open. Since $\mathcal B \subseteq \A$, the image of any coordinate chart of $\mathcal B$ is open.

