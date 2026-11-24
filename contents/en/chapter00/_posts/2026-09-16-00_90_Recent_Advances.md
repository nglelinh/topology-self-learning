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

Imagine walking into a dark room where someone has scattered a few hundred glowing grains of salt across an invisible doughnut. You can never touch the smooth surface itself—all you have is a finite list of 3D coordinates stored in a spreadsheet. Could you still prove, purely from those finite coordinates, that the hidden object has a hole through its center and a hollow cavity inside? That question turns the quietest chapter of point-set topology—sets, relations, and Euclidean distance—into one of the liveliest branches of modern data science: **Topological Data Analysis (TDA)**.

**Optional notes.** Chapter 00 theory is not rewritten here. These notes show *where* sets, functions, and Euclidean space now live in 2022–2026 data science. The full theory track for this chapter is in Vietnamese; this English page holds recent-advance notes only.

---

## Background Knowledge Map: From Sets and Preorders to Topological Data Analysis

A university graduate opening a topology textbook starts with abstract sets $$X$$, relations, and $$\mathbb{R}^d$$, often wondering when any of this meets real data. Modern TDA bridges that gap across three pillars:

1. **Finite Sets & Preorders as Alexandroff Topologies:** On a finite set $$X$$, every topology corresponds one-to-one with a *preorder* (a reflexive, transitive relation $$\le$$), where the minimal open neighborhood of $$x$$ is $$U_x = \{y \in X : y \le x\}$$. Thus finite relational tables and face posets of complexes *are* genuine topological spaces without ever needing a continuum!
2. **Point Clouds to Simplicial Complexes (Vietoris–Rips):** Given a finite sample $$X = \{x_1, \dots, x_N\} \subset \mathbb{R}^d$$ and a scale radius $$r \ge 0$$, we connect every pair with $$d(x_i, x_j) \le r$$ by an edge, every mutually close triple by a filled triangle, and so on—building a nested **filtration** $$X_0 \subseteq X_1 \subseteq \dots \subseteq X_m$$ as $$r$$ grows.
3. **Persistent Homology & Stability:** Rather than guessing a single magic radius $$r$$, persistent homology tracks the *birth* and *death* radius of every connected component ($$H_0$$), loop ($$H_1$$), and void ($$H_2$$) across all scales, summarizing the dataset's shape as a **barcode** that is provably stable under small perturbations of the point cloud.

---

## 📖 Overview

Chapter 00 starts every space from a **set** $X$ and a family of subsets. In modern practice $X$ is almost always finite: a point cloud $\{x_1,\ldots,x_N\}\subset\mathbb{R}^d$, a table, or a graph. The live question is no longer “is $\mathbb{R}$ complete?” but “from a finite set, how do we recover the shape of the continuum it samples?”

That is the bridge from set theory to **Topological Data Analysis (TDA)**. The four advances below turn Chapter 00 language into algorithms.

![Point cloud on a torus](https://upload.wikimedia.org/wikipedia/commons/4/4c/Point_cloud_torus.gif)
*A torus sampled by finitely many points — the native object of TDA. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Point_cloud_torus.gif)*

---

## 🎯 Intuition

Imagine you never see the doughnut, only a handful of salt grains on its surface. You still “see” the hole if, after joining nearby grains by edges and triangles, that hole **lives long enough** as the joining radius grows. A finite set plus a nearness relation already talks about holes.

### Worked Example (Step by Step): Vietoris–Rips Barcode of a 4-Point Square and a 3-Point Alexandroff Space

Let's compute an entire persistent homology barcode by hand on just **4 points** sitting at the corners of a unit square in $$\mathbb{R}^2$$:

$$
p_1 = (0,0),\quad p_2 = (1,0),\quad p_3 = (1,1),\quad p_4 = (0,1).
$$

Every side has Euclidean length $$1$$, and both diagonals have length $$\sqrt{2} \approx 1.414$$. Watch the Vietoris–Rips complex $$\mathrm{VR}(X, r)$$ evolve as radius $$r$$ increases:

| Scale interval $$r$$ | Simplices present in $$\mathrm{VR}(X, r)$$ | Betti numbers ($$\beta_0, \beta_1$$) | Barcode events |
|---|---|---|---|
| $$0 \le r < 1$$ | 4 isolated vertices | $$\beta_0 = 4,\ \beta_1 = 0$$ | Four $$H_0$$ bars born at $$r = 0$$ |
| $$1 \le r < \sqrt{2}$$ | 4 vertices + 4 side edges (hollow square) | $$\beta_0 = 1,\ \beta_1 = 1$$ | Three $$H_0$$ bars die at $$r=1$$; **one $$H_1$$ loop born at $$r=1$$** |
| $$r \ge \sqrt{2}$$ | Both diagonals + 4 triangles + tetrahedron | $$\beta_0 = 1,\ \beta_1 = 0$$ | **The $$H_1$$ loop dies at $$r = \sqrt{2}$$** (filled in!) |

Reading off the complete barcode:
- $$H_0 = \{[0, 1),\ [0, 1),\ [0, 1),\ [0, \infty)\}$$ (4 points merge into 1 connected component at $$r=1$$).
- $$H_1 = \{[1, \sqrt{2})\}$$ (a single loop persisting for lifetime $$\sqrt{2} - 1 \approx \mathbf{0.414}$$).

**Bonus check — a 3-point finite Alexandroff space:** on $$Y = \{a, b, c\}$$ with preorder $$a \le b \le c$$, the minimal open sets are $$U_a = \{a\}$$, $$U_b = \{a, b\}$$, $$U_c = \{a, b, c\}$$. Notice intersections and unions of these sets stay inside $$\{\emptyset, \{a\}, \{a,b\}, \{a,b,c\}\}$$ — a valid topology built purely from an order relation, with zero coordinates!

### Deep-Dive Explanation: How a Finite Set Remembers a Continuum's Shape (Read Slowly)

1. **Trade coordinates for pairwise relations:** once you record distances $$d(x_i, x_j)$$ (or a preorder on faces), the ambient space $$\mathbb{R}^d$$ steps aside; topology depends only on which subsets glue together at each scale $$r$$.
2. **Avoid the single-scale trap:** at $$r = 0.9$$ our square looks like 4 disconnected specks; at $$r = 1.5$$ it looks like a solid blob with no hole. Only by sweeping *all* $$r \ge 0$$ together do we see the genuine loop $$[1, \sqrt{2})$$.
3. **Separate signal from noise by persistence length:** a genuine macroscopic hole (like the center of a torus or a ring of atoms) produces a **long bar**; random sampling jitter creates tiny short-lived loops that die almost immediately.
4. **Guarantee stability for real data:** Gromov–Hausdorff stability ensures that nudging every point by $$\le \delta$$ shifts every barcode endpoint by at most $$\delta$$—making topological features trustworthy inputs to machine learning.

**Quick check.** If we stretch our unit square into a $$1 \times 3$$ rectangle (sides $$1$$ and $$3$$, diagonal $$\sqrt{10} \approx 3.162$$), when is the $$H_1$$ loop born? Not at $$r = 1$$ (only the two short sides connect, leaving two separate segments!), but at $$r = 3$$, and it dies at $$r = \sqrt{10} \approx 3.162$$—a much shorter bar of length $$0.162$$ because the elongated rectangle is nearly a flat line!

---

## 📐 Four concrete advances

### 1. Persistent homology via finite topological spaces

Kayacan (2025) shows that persistent homology can be phrased entirely on **finite (Alexandroff) spaces**: each filtration stage is a finite set whose topology is a preorder. Chapter 00 — sets, relations, functions — sits next to the computational pipeline: data need not be embedded in $\mathbb{R}^d$ before it has homology.

<div class="textbook-definition" markdown="1">
**Definition (reminder, not a new theory):** a finite Alexandroff space has a minimal neighbourhood $U_x$ at each point. A finite filtration is a nested sequence
$$
X_0\subseteq X_1\subseteq\cdots\subseteq X_m,
$$
and persistent homology records classes $[z]\in H_n(X_i)$ that still live in $X_j$.
</div>

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

## Video tham khảo

- **xem trước** [An introduction to persistent homology](https://www.youtube.com/watch?v=UxEH7WySO60) — Applied Algebraic Topology Network, English. Persistent homology on a finite sample: the shape of a point cloud across scales.
- [Finite Topology [Shelley Kandola]](https://www.youtube.com/watch?v=zTiHx3z59N8) — Applied Algebraic Topology Network, English. Finite topological spaces as the computational model behind that sample.
- [Henry Adams: An Introduction to Applied Topology](https://www.youtube.com/watch?v=Xv4IoKVdGKA) — Kaleidoscope Circles, English. A wider map of applied topology, so the four advances in this note have a home.

## 🧩 Exercises

1. Take 8 points on a circle. Without a computer, say when a $1$-cycle appears in the “nearby points” complex.
2. Why is a finite Alexandroff space always $T_0$ but rarely Hausdorff? Bridge Lecture 00.00 to Chapter 03.
3. In words: what does Gromov–Hausdorff stability say about *adding one noisy point* to a cloud?
