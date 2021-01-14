# Introduction

$$
\newcommand{\ds}{\displaystyle}
\newcommand{\curlies}[1]{\left\lbrace #1 \right\rbrace}
\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}
\newcommand{\angles}[1]{\left\langle #1 \right\rangle}
\newcommand{\inv}[1]{#1^{-1}}
$$

## Manifolds

The extrinsic perspective of an $n$-dimensional manifold is a subset of $\R^N$, usually as the level set of a function $\R^N \to \R^k$ where $n = N - k$. However, we will not adopt this perspective.

We will use the intrinsic definition, that an $n$-dimensional manifold is something that locally looks like $\R^n$.

The advantages of this are that:

- often there is no natural, unique, or canonical embedding of a manifold in $\R^N$
  - e.g. non-orientable surfaces cannot be embedded in $\R^3$
- extrinsic descriptions may be unnecessarily complicated
- a particular realization of a manifold as a subset of $\R^N$ is often irrelevant to questions that geometers ask

Some examples of manifolds are:

- The unit sphere in $\R^3$, i.e. the 2-sphere
- The set of all orthonormal bases of $\R^3$, which is homeomorphic to $SO(3)$
- the linkage of $N$ rods into a loop (this is only interesting for $N \geq 4$)
- the real projective plane $\R P^2$, the set of all 1-dimensional subspaces (lines through the origin) in $\R^3$
  - $\R P^2 = \curlies{x \in \R^3 : \abs x = 1}/\sim$ where $x \sim -x$