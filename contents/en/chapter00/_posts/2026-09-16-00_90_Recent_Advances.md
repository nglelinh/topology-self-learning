---
layout: post
title: "Lecture 00.90: Recent Advances (2022–2026) — Finite Data and the Shape of Point Clouds"
lang: en
lang-ref: lecture-00-90
chapter: 0
lecture: 90
order: 90
lesson_type: optional
categories: [chapter00]
tags: [optional, recent-advances, tda, finite-spaces, point-clouds]
description: "Optional notes: 2022–2026 advances linking set-theoretic / Euclidean foundations to TDA on finite samples. Theory lectures remain in Vietnamese; this is not a theory translation."
---

**Optional notes.** Chapter 00 theory is not rewritten here. These notes only show *where* sets, functions, and Euclidean space now live in data science.

The full theory track for this chapter is in Vietnamese. This English page holds recent-advance notes only.

---

## 📖 Overview

Chapter 00 starts every space from a **set** $X$ and a family of subsets. In modern practice $X$ is almost always finite: a point cloud $\{x_1,\ldots,x_N\}\subset\mathbb{R}^d$, a table, or a graph. The live question is no longer “is $\mathbb{R}$ complete?” but “from a finite set, how do we recover the shape of the continuum it samples?”

That is the bridge from set theory to **Topological Data Analysis (TDA)**. The four advances below turn Chapter 00 language into algorithms.

![Point cloud on a torus](https://upload.wikimedia.org/wikipedia/commons/4/4c/Point_cloud_torus.gif)
*A torus sampled by finitely many points — the native object of TDA. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Point_cloud_torus.gif)*

---

## 🎯 Intuition

Imagine you never see the doughnut, only a handful of salt grains on its surface. You still “see” the hole if, after joining nearby grains by edges and triangles, that hole **lives long enough** as the joining radius grows. A finite set plus a nearness relation already talks about holes.

---

## 📐 Four concrete advances

### 1. Persistent homology via finite topological spaces

Kayacan (2025) shows that persistent homology can be phrased entirely on **finite (Alexandroff) spaces**: each filtration stage is a finite set whose topology is a preorder. Chapter 00 — sets, relations, functions — sits next to the computational pipeline: data need not be embedded in $\mathbb{R}^d$ before it has homology.

**Definition (reminder, not a new theory):** a finite Alexandroff space has a minimal neighbourhood $U_x$ at each point. A finite filtration is a nested sequence
$$
X_0\subseteq X_1\subseteq\cdots\subseteq X_m,
$$
and persistent homology records classes $[z]\in H_n(X_i)$ that still live in $X_j$.

- Selçuk Kayacan, *Persistent Homology via Finite Topological Spaces*, arXiv:2512.23348 (2025).

### 2. TDA as the geometry of Euclidean samples

Chazal–Michel remains the data-scientist’s doorway through 2022–2026: a datum is an element of a finite set, and “shape” is an invariant of complexes built from Euclidean distance. Su, Liu, Bou Hamdan, Maroulas, Wu, Carlsson, and Wei (2025) update the picture: TDA is now a family of invariants (homotopy, sheaves, cell complexes) grown from the same set-and-relation idea.

- Frédéric Chazal, Bertrand Michel, *An introduction to Topological Data Analysis: fundamental and practical aspects for data scientists*, *Frontiers in Artificial Intelligence* (2021), arXiv:1710.04019.
- Zhe Su et al., *Topological Data Analysis and Topological Deep Learning Beyond Persistent Homology — A Review*, arXiv:2507.19504 (2025).

### 3. Gromov–Hausdorff stability for labeled sets

Fu, Lagoda, Li, Needham, and Ver Hoef (2025) prove a Gromov–Hausdorff stability statement for persistent homology of **labeled finite sets**. If two finite metric samples are close as metric spaces, barcodes cannot jump far. “Set + map + Euclidean distance” becomes a stability theorem for machine learning.

- Yaoying Fu, Evgeniya Lagoda, Shiying Li, Tom Needham, Lander Ver Hoef, *Persistent Homology for Labeled Datasets: Gromov–Hausdorff Stability and Generalized Landscapes*, arXiv:2512.08794 (2025).

### 4. Molecular TDA/TDL: data as a set of atoms

Wee and Jiang (2025) survey how finite sets of atoms — sets, not smooth manifolds — become topological features for chemical AI. Chapter 00 is enough to start reading those papers.

- JunJie Wee, Jian Jiang, *A review of topological data analysis and topological deep learning in molecular sciences*, arXiv:2509.16877 (2025).

---

## 🧠 Papers and references

- James R. Munkres, *Topology*, 2nd ed., Ch. 1.
- Sidney A. Morris, *Topology without Tears*, Ch. 1–2.
- The arXiv items above (2021–2025).

## 🔗 Applications

In cheminformatics a molecule is a finite set of atoms with a bonding relation. Persistent homology reads its holes across scales — the same set/function language as Lectures 00.00–00.03.

## 🧩 Exercises

1. Take 8 points on a circle. Without a computer, say when a $1$-cycle appears in the “nearby points” complex.
2. Why is a finite Alexandroff space always $T_0$ but rarely Hausdorff? Bridge Lecture 00.00 to Chapter 03.
3. In words: what does Gromov–Hausdorff stability say about *adding one noisy point* to a cloud?
