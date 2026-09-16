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

**Optional notes.** Simplicial/singular homology, Mayer–Vietoris, and cohomology stay as in Chapter 07. We only add a *filtration* and the software that computes $H_n$ on data.

The theory track is in Vietnamese. This English page holds recent-advance notes only.

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

## 🧩 Exercises

1. For the 4 vertices of the unit square, estimate the $\varepsilon$ where $H_1$ is born and where it dies in VR.
2. Distinguish a barcode from a static Betti number: which one is a functor in $\varepsilon$?
3. Why does Morse sandwich compute $H_n$ on large 3D images more scalably than vanilla Ripser?
