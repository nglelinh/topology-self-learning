---
layout: post
title: "Lecture 07.90: Recent Advances (2022–2026) — Persistent Homology, Ripser, and giotto-tda"
lang: en
lang-ref: lecture-07-90
chapter: 7
lecture: 90
order: 90
lesson_type: optional
categories: [chapter07]
tags: [optional, recent-advances, persistent-homology, ripser, giotto-tda]
description: "Optional notes: homology meets persistent homology, Ripser, giotto-tda, and vectorization. Not a theory translation."
---

When Henri Poincaré invented homology in 1895, computing the holes of a 3D shape meant painstakingly writing out boundary matrices by hand. A century later, if you build a Vietoris–Rips complex on just 500 points from a protein crystal, there can be millions of triangles and tetrahedra—far too many to store naively in RAM! Yet today, a C++ library called **Ripser** computes the exact persistent homology barcodes of that dataset in milliseconds, and **giotto-tda** plugs them straight into a `scikit-learn` pipeline. How did classical algebraic topology—$$\partial_n \circ \partial_{n+1} = 0$$ and $$H_n = \ker\partial_n / \operatorname{im}\partial_{n+1}$$—become a high-speed industrial engine?

**Optional notes.** Simplicial/singular homology, Mayer–Vietoris, and cohomology stay as in Chapter 07. We add a *filtration* and the 2021–2026 software stack that computes $H_n$ on data. The theory track is in Vietnamese; this English page holds recent-advance notes only.

---

## Key ideas: Boundary Matrices, Persistence, and Differentiable Vectorization

To understand what Ripser and `giotto-tda` are actually computing under the hood, connect three Chapter 07 pillars:

1. **Chain Complexes & Boundary Matrices ($$\partial_n \circ \partial_{n+1} = 0$$):** Over the two-element field $$\mathbb{F}_2 = \{0, 1\}$$ (where $$1 + 1 = 0$$, eliminating orientation signs!), every simplicial complex becomes a sequence of binary matrices $$\partial_1, \partial_2, \dots$$. Cycles live in $$\ker \partial_n$$ (chains with no boundary), boundaries live in $$\operatorname{im} \partial_{n+1}$$ (cycles that bound a higher-dimensional face), and the $$n$$-th Betti number counts independent $$n$$-holes: $$\beta_n = \dim(\ker\partial_n) - \dim(\operatorname{im}\partial_{n+1})$$.
2. **Persistent Homology via Column Reduction:** When simplices arrive in sorted scale order $$\sigma_1, \sigma_2, \dots, \sigma_M$$, Gaussian-style column reduction over $$\mathbb{F}_2$$ pairs each *birth* simplex with the exact *death* simplex that fills its hole—producing the barcode $$\{[\varepsilon_{\text{birth}}, \varepsilon_{\text{death}})\}$$ in one pass!
3. **Cohomology Speedup (Ripser) & Vectorization:** By universal coefficients over a field, persistent **cohomology** gives the *exact same* barcode as persistent homology, yet coboundary matrices are vastly sparser for Vietoris–Rips complexes—giving Ripser its orders-of-magnitude speedup. Finally, **vectorization** (persistence landscapes, images, signed measures) turns variable-size barcodes into fixed-length vectors ready for gradient descent.

---

## 📖 Overview

Homology counts holes. Persistent homology tracks holes **through a nested family of spaces**. It is the same $H_n=\ker\partial_n/\operatorname{im}\partial_{n+1}$, repeated for each $X_{\varepsilon}$. The three practical pillars of 2021–2026 are: Ripser (and cubical / distributed heirs), the giotto-tda library, and stable vectorizations that feed barcodes to machine learning. Surveys in 2025 place PH in a larger picture — TDA is no longer identical with $H_n$.

![Simplicial complex](https://upload.wikimedia.org/wikipedia/commons/5/50/Simplicial_complex_example.svg)
*A simplicial complex: the object whose $H_n$ we compute, and also $X_{\varepsilon}$ in a Vietoris–Rips filtration. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Simplicial_complex_example.svg)*

![Sampled torus](https://upload.wikimedia.org/wikipedia/commons/4/4c/Point_cloud_torus.gif)
*A discrete torus: persistent $H_1$ must outlive noise. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Point_cloud_torus.gif)*

---

## 🎯 Intuition

At small $\varepsilon$ the complex is a pile of points: large $H_0$, vanishing $H_1$. At medium $\varepsilon$ true loops appear. At large $\varepsilon$ everything fills. The **barcode** records each class’s interval $[\varepsilon_{\mathrm{birth}},\varepsilon_{\mathrm{death}})$. Short bars are noise; long bars are holes. This is Chapter 07 with one extra parameter.

### Worked Example (Step by Step): Computing $$H_0$$ and $$H_1$$ Over $$\mathbb{F}_2$$ by Hand on a Triangle

Take 3 vertices $$v_0, v_1, v_2$$ and 3 edges $$e_{01}, e_{12}, e_{02}$$ forming a hollow triangle $$K_1$$. Over $$\mathbb{F}_2$$ (arithmetic mod 2), write the $$3 \times 3$$ boundary matrix $$\partial_1: C_1 \to C_0$$ (rows = $$v_0, v_1, v_2$$; columns = $$e_{01}, e_{12}, e_{02}$$):

$$
\partial_1 = \begin{pmatrix} 1 & 0 & 1 \\ 1 & 1 & 0 \\ 0 & 1 & 1 \end{pmatrix}.
$$

1. **Compute rank and kernel of $$\partial_1$$ over $$\mathbb{F}_2$$:** add Column 1 + Column 2 to Column 3 (mod 2):
   $$(1, 1, 0)^\top + (0, 1, 1)^\top + (1, 0, 1)^\top = (2, 2, 2)^\top \equiv (0, 0, 0)^\top \pmod 2!$$
   Meanwhile Columns 1 and 2 are linearly independent, so $$\operatorname{rank}(\partial_1) = 2$$ and $$\dim(\ker \partial_1) = 3 - 2 = \mathbf{1}$$, spanned by the 1-cycle $$z = e_{01} + e_{12} + e_{02}$$.
2. **Stage 1 — Hollow triangle ($$C_2 = 0$$, no 2-face yet):**
   - $$\beta_0 = \dim C_0 - \operatorname{rank}(\partial_1) = 3 - 2 = \mathbf{1}$$ (1 connected component).
   - $$\beta_1 = \dim(\ker \partial_1) - 0 = \mathbf{1}$$ (**1 loop is born!**).
3. **Stage 2 — Filled triangle (add 2-simplex $$t = [v_0, v_1, v_2]$$):** its boundary is $$\partial_2(t) = e_{01} + e_{12} + e_{02} = z$$, so $$\partial_2 = (1, 1, 1)^\top$$ has $$\operatorname{rank}(\partial_2) = 1$$. Check the fundamental identity:
   $$\partial_1 \partial_2(t) = (2, 2, 2)^\top \equiv (0, 0, 0)^\top \pmod 2.$$
   Now $$\beta_1 = \dim(\ker\partial_1) - \operatorname{rank}(\partial_2) = 1 - 1 = \mathbf{0}$$ — **the 1-loop dies** the exact moment $$t$$ enters the filtration!

### Explanation: How Ripser Turns Boundary Matrices into Millisecond Barcodes

1. **Every simplex does one of two jobs:** when sorted by filtration radius, adding a $$k$$-simplex either *creates* a new $$k$$-cycle (column reduces to zero → **birth**) or *kills* an older $$(k-1)$$-cycle (column's lowest `1` pairs with that cycle's birth → **death**).
2. **Switch to cohomology for massive sparsity:** Ripser reduces the transpose (*coboundary*) matrix instead; in Vietoris–Rips complexes, most columns cancel immediately via "apparent pairs" without ever storing the full complex in memory.
3. **Pre-collapse huge 3D grids with Discrete Morse Sandwich:** on gigapixel 3D medical or materials scans, pairing trivial cells first (Guillou et al., 2022–2025) shrinks the boundary matrix by orders of magnitude before homology runs.
4. **Vectorize barcodes so gradients can flow:** because a barcode is an unordered multiset of intervals, signed-measure and landscape vectorizations map it stably into $$\mathbb{R}^d$$ so neural networks and `scikit-learn` classifiers can learn directly from holes.

**Quick check.** In our triangle example, what happens to $$\beta_0$$ and $$\beta_1$$ if we delete edge $$e_{02}$$ (leaving an open path $$v_0 - v_1 - v_2$$)? Now $$\partial_1$$ has only 2 independent columns ($$\operatorname{rank} = 2$$), so $$\beta_0 = 3 - 2 = 1$$ (still connected), while $$\dim(\ker\partial_1) = 2 - 2 = \mathbf{0} \implies \beta_1 = 0$$ (no cycle!).

---

## 📐 Four concrete advances

### 1. Ripser and computational descendants

Bauer (JACOT 2021; still the 2022–2026 gold standard) computes Vietoris–Rips persistence from an implicit coboundary, never building the complex explicitly. Guillou–Vidal–Tierny (2022) and Le Guillou–Fortin–Tierny (2025) take *Discrete Morse Sandwich* — discrete Morse reductions before the diagram — to massive, distributed scalar data.

$$
\mathrm{VR}_{\varepsilon}(X)=\{\sigma\subseteq X:\mathrm{diam}(\sigma)\le\varepsilon\}.
$$

- Ulrich Bauer, *Ripser: efficient computation of Vietoris–Rips persistence barcodes*, *Journal of Applied and Computational Topology* (2021), arXiv:1908.02518.
- Pierre Guillou, Jules Vidal, Julien Tierny, *Discrete Morse Sandwich: Fast Computation of Persistence Diagrams for Scalar Data*, arXiv:2206.13932 (2022).
- Eve Le Guillou, Pierre Fortin, Julien Tierny, *Distributed Discrete Morse Sandwich*, arXiv:2505.21266 (2025).

### 2. giotto-tda: homology inside scikit-learn

Tauzin, Lupo, Tunstall, Hess, and coauthors (JMLR 2021; still the 2022–2026 on-ramp) wrap Ripser/GUDHI as a scikit-learn pipeline: point cloud → complex → barcode → vector. This is where Chapter 07 meets code without writing $\partial$ by hand.

- Guillaume Tauzin et al., *giotto-tda: A Topological Data Analysis Toolkit for Machine Learning and Data Exploration*, *JMLR* 22(39) (2021), arXiv:2004.02551.

### 3. Stable vectorization — including multiparameter

A diagram is not a vector. Loiseaux–Scoccola–Carrière–Botnan (2023) vectorize multiparameter persistence via signed barcodes as measures; Xin–Mukherjee–Samaga–Dey (2023) propose GRIL; Luchinsky–Islambekov (2024) ship TDAvec. Without this step $H_n$ cannot enter gradient descent.

- David Loiseaux et al., *Stable Vectorization of Multiparameter Persistent Homology using Signed Barcodes as Measures*, arXiv:2306.03801 (2023).
- Cheng Xin, Soham Mukherjee, Shreyas N. Samaga, Tamal K. Dey, *GRIL: A 2-parameter Persistence Based Vectorization for Machine Learning*, arXiv:2304.04970 (2023).

### 4. PH is no longer all of TDA

Su, Liu, Bou Hamdan, Maroulas, Wu, Carlsson, and Wei (2025) review TDA “beyond persistent homology”: homotopy, sheaves, cell complexes, TDL. Wee–Jiang (2025) do the same for molecular science. Chapter 07 remains the engine — but not the whole car.

- Zhe Su et al., *TDA and TDL Beyond Persistent Homology — A Review*, arXiv:2507.19504 (2025).
- JunJie Wee, Jian Jiang, *A review of TDA and TDL in molecular sciences*, arXiv:2509.16877 (2025).

---

## 🧠 Papers and references

- Hatcher, *Algebraic Topology*, Ch. 2.
- Edelsbrunner–Harer, *Computational Topology*.
- The arXiv/JMLR items above.

## 🔗 Applications

A `VietorisRipsPersistence` call in giotto-tda on a protein cloud returns $H_1,H_2$ barcodes — the same groups as Lecture 07.00, with $\partial$ running in C++.

## Video tham khảo

- **xem trước** [An introduction to persistent homology](https://www.youtube.com/watch?v=UxEH7WySO60) — Applied Algebraic Topology Network, English. From finite homology to the persistent version, the extra step this note takes.
- [Applied topology 15: Introduction to a software tutorial for persistent homology and Ripser](https://www.youtube.com/watch?v=jgVr4FIySw4) — Applied Algebraic Topology Network, English. Ripser and a barcode tutorial, the software this note names.

## 🧩 Exercises

1. For the 4 vertices of the unit square, estimate the $\varepsilon$ where $H_1$ is born and where it dies in VR.
2. Distinguish a barcode from a static Betti number: which one is a functor in $\varepsilon$?
3. Why does Morse sandwich compute $H_n$ on large 3D images more scalably than vanilla Ripser?
