---
layout: post
title: "Lecture 08.05: Spectral Sequences — Leray–Serre, Gysin, and Wang"
lang: en
lang-ref: lecture-08-05
chapter: 8
lecture: 5
order: 5
categories: [chapter08]
tags: [spectral-sequences, leray-serre, gysin-sequence, homotopy-groups-of-spheres, cohomology]
description: "Spectral Sequences in Algebraic Topology: Leray–Serre Theorem for fibrations, Gysin & Wang sequences, and homotopy groups of spheres"
---

**The most powerful successive-approximation engine in modern Algebraic Topology**

---

## 📖 Overview

> **Opening Story:** Given a fibration $F \hookrightarrow E \to B$, suppose you know $H^*(B)$ and $H^*(F)$—how can you recover $H^*(E)$ (or deduce $H^*(F)$ from $E$ and $B$)? Unlike a product $B \times F$, a twisted fibration cannot be solved by Künneth alone. In 1946, Jean Leray invented the **Spectral Sequence**: a sequence of bigraded "pages" $(E_r, d_r)$ where $E_{r+1} = H(E_r, d_r)$ converges to $H^*(E)$.

![Leray-Serre Spectral Sequence Grid]({{ site.imgurl }}/chapter_img/chapter08/08_05_spectral_sequence.png)

## 🗺️ Knowledge Map: Anatomy of a Cohomology Spectral Sequence

Following Chapter 10 of [*Algebraic Topology: A Comprehensive Introduction* (L. Maxim)](https://people.math.wisc.edu/~lmaxim/topbookf.pdf):

1. **Pages $E_r^{p,q}$ and Differentials $d_r$:** Each page $E_r$ ($r \ge 2$) carries differentials $d_r: E_r^{p,q} \to E_r^{p+r,\, q-r+1}$ with $d_r^2 = 0$ and $E_{r+1} = \ker d_r / \operatorname{im} d_r$.
2. **Leray–Serre Theorem:** For a fibration $F \hookrightarrow E \to B$ with $B$ simply connected, there is a first-quadrant spectral sequence $E_2^{p,q} \cong H^p(B; H^q(F; R)) \Rightarrow H^{p+q}(E; R)$ compatible with cup products.
3. **Convergence:** Because $d_r$ eventually leaves the first quadrant, each entry stabilizes at $E_\infty^{p,q}$, and $H^n(E)$ is assembled from the diagonal $p+q=n$.

## 🧮 Worked Example: Computing $H^*(\Omega S^n; \mathbb{Z})$

Apply Leray–Serre to the path-loop fibration $\Omega S^n \hookrightarrow PS^n \to S^n$ ($n \ge 2$), where $PS^n$ is **contractible**:
1. **$E_2$ Page:** Since $H^p(S^n; \mathbb{Z}) \neq 0$ only for $p = 0, n$, $E_2$ has only **two nonzero columns** ($p=0$ and $p=n$).
2. **Unique Surviving Differential:** Only $d_n: E_n^{0,q} \to E_n^{n, q-n+1}$ can be nonzero.
3. **Contractibility Forces Isomorphisms:** Since $E_\infty^{p,q} = 0$ for $(p,q) \neq (0,0)$, $d_n: H^q(\Omega S^n) \to H^{q-n+1}(\Omega S^n)$ must be an isomorphism for $q \ge n-1$, yielding $H^q(\Omega S^n; \mathbb{Z}) \cong \mathbb{Z}$ when $(n-1) \mid q$ and $0$ otherwise!

## 🌊 Gysin Sequence, Wang Sequence, and $\pi_{n+1}(S^n)$

- **Gysin Sequence ($F = S^k$):** Reduces the two-row spectral sequence to a long exact sequence with cup product by the Euler class $e \in H^{k+1}(B)$.
- **Wang Sequence ($B = S^n$):** Reduces the two-column spectral sequence.
- **Whitehead Towers & Serre's Finiteness Theorem:** Combining Whitehead towers with Leray–Serre computes $\pi_4(S^3) \cong \mathbb{Z}/2\mathbb{Z}$ and proves $\pi_k(S^n)$ ($k > n$) is finite except for $k = 2n-1$ with $n$ even ([`topbookf.pdf`, Ch. 10.9–10.11](https://people.math.wisc.edu/~lmaxim/topbookf.pdf)).

## 🧩 Exercises

1. Apply the Gysin sequence to the Hopf fibration $S^1 \hookrightarrow S^3 \to S^2$ to show the Euler class generates $H^2(S^2; \mathbb{Z})$.
2. Compute $H^*(\mathbb{C}P^\infty; \mathbb{Z})$ from $S^1 \hookrightarrow S^\infty \to \mathbb{C}P^\infty$.
3. Use the graded Leibniz rule for $d_3$ to show $H^*(\Omega S^3; \mathbb{Z})$ is a divided power algebra.
4. Verify all differentials vanish for the trivial fibration $S^3 \hookrightarrow S^2 \times S^3 \to S^2$.
