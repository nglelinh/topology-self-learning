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

**Optional notes.** Quotient topology, surface classification, CW complexes, and group actions stay as in Chapter 05. We watch them redrawn as Mapper — and imitated, then critiqued, by UMAP.

The theory track is in Vietnamese. This English page holds recent-advance notes only.

---

## 📖 Overview

Mapper (2007) is a quotient algorithm: choose a filter $f:X\to\mathbb{R}^k$, cover the range by overlapping opens, take connected components of preimages, and glue them into a graph. That is Chapter 05 — “glue along fibres” — written for finite data. The years 2022–2026 brought a comprehensive survey, stability frameworks, and a wave of UMAP critique: the popular dimension reduction is *not* a topological quotient.

![Torus](https://upload.wikimedia.org/wikipedia/commons/1/17/Torus.png)
*The torus is a quotient of a square after edge gluings — the prototype for Mapper. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Torus.png)*

---

## 🎯 Intuition

Recall $S^1=[0,1]/\{0\sim 1\}$. Mapper does the same to a point cloud: if two “local clusters” live in overlapping filter sets, we draw an edge — we *glue*. UMAP also builds a neighbour graph and then embeds it in $\mathbb{R}^2$, but that embedding step is no longer a quotient map. Separating the two operations is the Chapter 05 lesson for data science.

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

## 🧩 Exercises

1. For $X=S^1$ and $f=$ height, sketch the Mapper graph of a 3-interval overlapping cover.
2. Exhibit a cover that collapses the figure-eight Mapper graph to a single edge (the hole dies).
3. Write one sentence distinguishing a quotient map from a UMAP embedding.
