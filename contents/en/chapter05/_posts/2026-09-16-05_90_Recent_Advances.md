---
layout: post
title: "Lecture 05.90: Recent Advances (2022–2026) — Mapper, UMAP, and Quotient Pictures of Data"
lang: en
lang-ref: lecture-05-90
chapter: 5
lecture: 90
order: 90
lesson_type: optional
categories: [chapter05]
tags: [optional, recent-advances, mapper, umap, quotient, manifolds]
description: "Optional notes: quotients/surfaces meet Mapper, the UMAP critique, and cover graphs of data. Not a theory translation."
---

Every topology student remembers the first magic trick of quotient spaces: take a flat strip of paper $$[0,1]$$, glue its two endpoints together ($$0 \sim 1$$), and a circle $$S^1$$ appears; glue opposite edges of a square $$[0,1]^2$$, and a torus is born. Now flip that same gluing idea onto a noisy dataset of 50,000 breast-cancer gene profiles: slice the dataset into overlapping strips by a summary function, cluster each strip, and glue overlapping clusters by edges. The resulting skeleton—the **Mapper graph**—is a genuine topological quotient nerve of the data, capable of revealing branching disease subtypes that popular 2D projections like UMAP can flatten away!

**Optional notes.** Quotient topology, surface classification, CW complexes, and group actions stay as in Chapter 05. We watch them redrawn as Mapper—and imitated, then critiqued, by UMAP—in 2022–2026 research. The theory track is in Vietnamese; this English page holds recent-advance notes only.

---

## Key ideas: Quotients, Cover Nerves, and Why UMAP Is Not Mapper

Chapter 05 builds complex spaces by gluing simpler pieces together. Three pillars carry that machinery directly into modern data visualization:

1. **Quotient Topology & Gluing Maps:** Collapsing equivalence classes of points in $$X$$ yields a quotient space $$X/\!\sim$$ whose open sets are precisely those with open preimages in $$X$$. In data analysis, collapsing each local cluster inside a filter slice to a single vertex is a discrete quotient.
2. **Open Covers & the Nerve Theorem (Mapper):** Given a continuous filter $$f: X \to \mathbb{R}^k$$ and an open cover $$\mathcal{U} = \{U_i\}$$ of its range, we pull back each $$U_i$$, split $$f^{-1}(U_i)$$ into connected components (clusters), and form the **nerve**—placing a vertex for each cluster and an edge whenever two clusters share points. By the Nerve Theorem, when the cover is fine enough, this graph recovers the homotopy type of $$X$$ (a discrete Reeb graph!).
3. **Quotient Nerves vs. Spectral Projections (UMAP):** Whereas Mapper respects the fibers $$f^{-1}(U_i)$$ of a chosen lens, UMAP runs spectral-like optimization on a fuzzy $$k$$-NN graph to force points into $$\mathbb{R}^2$$—satisfying neither the universal property of a quotient nor the nerve of an open cover.

---

## 📖 Overview

Mapper (2007) is a quotient algorithm: choose a filter $f:X\to\mathbb{R}^k$, cover the range by overlapping opens, take connected components of preimages, and glue them into a graph. That is Chapter 05 — “glue along fibres” — written for finite data. The years 2022–2026 brought a comprehensive survey, stability frameworks, and a wave of UMAP critique: the popular dimension reduction is *not* a topological quotient.

![Torus](https://upload.wikimedia.org/wikipedia/commons/1/17/Torus.png)
*The torus is a quotient of a square after edge gluings — the prototype for Mapper. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Torus.png)*

---

## 🎯 Intuition

Recall $S^1=[0,1]/\{0\sim 1\}$. Mapper does the same to a point cloud: if two “local clusters” live in overlapping filter sets, we draw an edge — we *glue*. UMAP also builds a neighbour graph and then embeds it in $\mathbb{R}^2$, but that embedding step is no longer a quotient map. Separating the two operations is the Chapter 05 lesson for data science.

### Worked Example (Step by Step): Building the Mapper Graph of the Circle $$S^1$$ by Hand

Take the unit circle $$X = S^1 = \{(x,y) : x^2 + y^2 = 1\}$$ with the height filter $$f(x,y) = y \in [-1, 1]$$, and cover $$[-1, 1]$$ by **3 overlapping open intervals**:

| Cover interval $$U_i$$ | Preimage $$f^{-1}(U_i)$$ on $$S^1$$ | Connected components (Mapper vertices) |
|---|---|---|
| $$U_1 = [-1,\ -0.2)$$ | Bottom arc of the circle | **1** vertex: $$v_1$$ |
| $$U_2 = (-0.4,\ 0.4)$$ | Left middle arc $$L$$ and right middle arc $$R$$ | **2** vertices: $$v_{2L},\ v_{2R}$$ |
| $$U_3 = (0.2,\ 1]$$ | Top arc of the circle | **1** vertex: $$v_3$$ |

Now glue vertices whose clusters intersect in $$S^1$$:
- In the lower overlap $$U_1 \cap U_2 = (-0.4, -0.2)$$, the bottom arc $$v_1$$ meets *both* $$v_{2L}$$ and $$v_{2R}$$ → add edges $$(v_1, v_{2L})$$ and $$(v_1, v_{2R})$$.
- In the upper overlap $$U_2 \cap U_3 = (0.2, 0.4)$$, the top arc $$v_3$$ meets *both* $$v_{2L}$$ and $$v_{2R}$$ → add edges $$(v_{2L}, v_3)$$ and $$(v_{2R}, v_3)$$.

**Result:** a 4-vertex cycle $$v_1 - v_{2L} - v_3 - v_{2R} - v_1$$—topologically a circle, preserving the exact loop of $$S^1$$! Now watch the **cover sensitivity** trap: replace the 3 intervals by just **2** coarse intervals $$V_1 = [-1, 0.2)$$ and $$V_2 = (-0.2, 1]$$. Each preimage is now a single connected U-shaped arc, so Mapper produces just 2 vertices and 1 edge—the loop disappears!

### Explanation: Why Mapper Preserves Fibers While UMAP Can Flatten Them

1. **Choose a lens $$f$$ that asks a scientific question:** in Mapper, the filter $$f$$ (height, survival risk, pseudotime, PCA coordinate) explicitly tells the algorithm which direction to slice along, making every node interpretable.
2. **Pull back and cluster inside each fiber:** splitting $$f^{-1}(U_i)$$ into connected components is what detects branching (like $$v_{2L}$$ and $$v_{2R}$$ on $$S^1$$, or two cell-differentiation lineages).
3. **Glue via the nerve—no coordinate distortion required:** Mapper outputs an abstract combinatorial graph (a 1D CW complex), never forcing a curved or branching dataset to squeeze flat into $$\mathbb{R}^2$$.
4. **Control cover sensitivity with data-driven covers:** as our 3-interval vs. 2-interval comparison showed, too coarse a cover kills real loops; 2026 methods like MAPLE and GK-Mapper adapt interval widths directly to local data geometry.

**Quick check.** In our $$S^1$$ example with the 3-interval cover, if the overlap between $$U_1$$ and $$U_2$$ shrinks to zero (say $$U_1 = [-1, -0.3)$$ and $$U_2 = (-0.3, 0.3)$$), what happens to the Mapper graph? The clusters no longer intersect, so the edges $$(v_1, v_{2L})$$ and $$(v_1, v_{2R})$$ vanish—tearing the circle apart! Proper overlap is essential for quotient gluing.

---

## 📐 Four concrete advances

### 1. Mapper surveyed, 2007–2025

Madukpe, Ugoala, and Zulkepli (2025) give a systematic review of Mapper and its applications. It is a reading map for anyone who finished Lecture 05.00: each Mapper variant is a choice of cover and a choice of components — a different quotient.

- Vine Nwabuisi Madukpe, Bright Chukwuma Ugoala, Nur Fariha Syaqina Zulkepli, *A Comprehensive Review of the Mapper Algorithm … (2007–2025)*, arXiv:2504.09042 (2025).

### 2. Stability and evaluation of Mapper

Sen, Singh, and Tiwari (2026) propose a three-axis evaluation framework for Mapper algorithms; the same group introduces GK-Mapper with Gustafson–Kessel-type stability. Ahsan, Das, and Mukhopadhyay (2026) choose covers from the data (MAPLE) to reduce parameter sensitivity — the classical quotient pain: change the cover, change the quotient.

- Annesha Sen, Shivam Singh, S. P. Tiwari, *A Three Axis Evaluation Framework for Mapper Algorithms*, arXiv:2606.21688 (2026).
- Md Moinul Ahsan, Priyam Das, Nitai D. Mukhopadhyay, *MAPLE: Mapper Based Localized Prediction with Data Driven Cover Selection*, arXiv:2607.06797 (2026).

### 3. UMAP is not a manifold embedding — and not Mapper

Yang (2026) shows everyday UMAP is spectral clustering on a fuzzy neighbour graph. Li–Zhang (2026) patch it with topological priors. The pedagogical conclusion: UMAP *looks* like a chart of a manifold (Lectures 05.01–05.03) but satisfies neither the universal property of a quotient nor the nerve of an open cover in the Mapper sense.

- Yang Yang, *UMAP Is Spectral Clustering on the Fuzzy Nearest-Neighbor Graph*, arXiv:2602.11662 (2026).
- Xiaobin Li, Run Zhang, *Understanding and Improving UMAP with Geometric and Topological Priors: The JORC-UMAP Algorithm*, arXiv:2601.16552 (2026).

### 4. Mapper meets survival and structured learning

Kibisi, Abawonse, and Woukeng (2026) use Mapper for breast-cancer survival — the quotient graph becomes a clinical feature. Babus and Nasrin (2026) do structured learning *on* Mapper representations, taking the quotient as the model’s base space.

If $f:X\to\mathbb{R}$ is a filter and $\mathcal{U}=\{U_i\}$ covers $f(X)$, the nerve
$$
N(\{C:C\text{ a component of }f^{-1}(U_i)\})
$$
is a CW complex (usually a graph) — the language of Lecture 05.02.

- Emmanuel Kibisi, Olakunle Abawonse, Donald Woukeng, *Topology-Informed Survival Analysis of Breast Cancer Patients Using the Mapper Algorithm*, arXiv:2607.15022 (2026).
- George Babus, Farzana Nasrin, *Structured Learning on Mapper Representations*, arXiv:2608.22044 (2026).

---

## 🧠 Papers and references

- Munkres, *Topology*, Ch. 2 §22 (quotients).
- Hatcher, *Algebraic Topology*, Ch. 0 (CW, quotient pictures).
- The arXiv items above.

## 🔗 Applications

In single-cell data, Mapper sometimes reveals a differentiation branch that UMAP flattens. Chapter 05 explains why: a quotient keeps the fibres of the filter; a spectral embedding does not promise that.

## Video tham khảo

- **xem trước** [The Mapper Algorithm | Overview & Python Example Code](https://www.youtube.com/watch?v=NlMrvCYlOOQ) — Shaw Talebi, English. The Mapper algorithm: a cover, a quotient, and a graph of the data, the construction in this note.
- [UMAP Dimension Reduction, Main Ideas!!!](https://www.youtube.com/watch?v=eN0wFzBA4Sc) — StatQuest with Josh Starmer, English. UMAP, a different picture of data that this note says is not Mapper.

## 🧩 Exercises

1. For $X=S^1$ and $f=$ height, sketch the Mapper graph of a 3-interval overlapping cover.
2. Exhibit a cover that collapses the figure-eight Mapper graph to a single edge (the hole dies).
3. Write one sentence distinguishing a quotient map from a UMAP embedding.
