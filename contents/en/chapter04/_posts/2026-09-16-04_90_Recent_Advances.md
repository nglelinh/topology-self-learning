---
layout: post
title: "Lecture 04.90: Recent Advances (2022–2026) — Metrics Between Shapes"
lang: en
lang-ref: lecture-04-90
chapter: 4
lecture: 90
order: 90
lesson_type: optional
categories: [chapter04]
tags: [optional, recent-advances, metric, gromov-hausdorff, bottleneck, interleaving]
description: "Optional notes: metric spaces meet GH, bottleneck, interleaving, and latent geometry. Not a theory translation."
---

**Optional notes.** The three metric axioms, completeness, and metric equivalence stay as in Chapter 04. We watch them measure *distances between spaces*, not only between points.

The theory track is in Vietnamese. This English page holds recent-advance notes only.

---

## 📖 Overview

A metric on $X$ measures pairs of points. Modern data science needs a second layer: measuring pairs of **spaces**. Gromov–Hausdorff, bottleneck, Wasserstein on diagrams, and interleaving on persistence modules are these “space-level” metrics — and they exploded in 2023–2026.

![Hausdorff distance](https://upload.wikimedia.org/wikipedia/commons/2/21/Hausdorff_distance_sample.svg)
*Hausdorff distance between two sets in one ambient space — the step before Gromov–Hausdorff. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hausdorff_distance_sample.svg)*

---

## 🎯 Intuition

Hausdorff $d_H(A,B)$ asks: how well is every point of $A$ approximated by $B$ (and conversely)? Gromov–Hausdorff drops the demand that $A$ and $B$ already sit in one space: we may *choose a placement* before measuring $d_H$. That is Lecture 04.02’s “equivalent metrics”, lifted one level.

---

## 📐 Four concrete advances

### 1. GH stability for labeled sets and generalized landscapes

Fu et al. (2025) prove that persistent homology of labeled sets is Gromov–Hausdorff stable, and they introduce generalized landscapes. This is completeness + continuity at the space level: a Cauchy sequence of point clouds yields a Cauchy sequence of barcodes.

- Yaoying Fu, Evgeniya Lagoda, Shiying Li, Tom Needham, Lander Ver Hoef, *Persistent Homology for Labeled Datasets: Gromov–Hausdorff Stability and Generalized Landscapes*, arXiv:2512.08794 (2025).

### 2. GH-type metrics for coloured / molecular data

Wee, Gong, Tuschmann, and Xia (2024) use a cohomology-based Gromov–Hausdorff metric to quantify molecular similarity. Draganov, Rosenmeier, and Zava (2025) define GH distance between *chromatic metric pairs* and prove stability for “six-pack” invariants. The metric is no longer Euclidean on $\mathbb{R}^d$ — the Chapter 04 slogan “many metrics, one topology”.

- JunJie Wee, Xue Gong, Wilderich Tuschmann, Kelin Xia, *A cohomology-based Gromov–Hausdorff metric approach for quantifying molecular similarity*, arXiv:2411.13887 (2024).
- Ondřej Draganov, Sophie Rosenmeier, Nicolò Zava, *Gromov–Hausdorff distance between chromatic metric pairs and stability of the six-pack*, arXiv:2507.17994 (2025).

### 3. Interleaving: a metric on modules, not only on diagrams

Interleaving distance compares two persistence modules by “sliding” them along the scale line. Papers in 2026 push both algorithms (Aoki; Farahbakhsh Touli–Hotz–Masood; Althaf–Chattopadhyay–Saeki) and confidence regions for Reeb graphs (Pegoraro–Conforti–Carrière). Formally
$$
d_I(M,N)=\inf\{\varepsilon\ge 0: M,N\text{ are }\varepsilon\text{-interleaved}\}.
$$
This is an (extended) metric on a category — completeness and computability are live Chapter 04 questions.

- Matteo Pegoraro, Alberto Conforti, Mathieu Carrière, *Building confidence regions for Reeb graphs using the interleaving distance*, arXiv:2607.08458 (2026).
- Elena Farahbakhsh Touli, Ingrid Hotz, Talha Bin Masood, *Towards Computing Average Merge Tree Based on the Interleaving Distance*, arXiv:2603.00783 (2026).

### 4. GH in neural latent space

Borde, Arroyo, Morales, Posner, and Dong (2023) use GH to *infer* products of model manifolds for latent geometry — Neural Latent Geometry Search. Metric spaces are not only inputs: they are hypotheses about the hidden space a network is learning.

- Haitz Sáez de Ocáriz Borde et al., *Neural Latent Geometry Search: Product Manifold Inference via Gromov–Hausdorff-Informed Bayesian Optimization*, arXiv:2309.04810 (2023).

---

## 🧠 Papers and references

- Munkres, *Topology*, Ch. 7.
- Burago–Burago–Ivanov, *A Course in Metric Geometry* (GH background).
- The arXiv items above.

## 🔗 Applications

Comparing two proteins that do not share a $\mathbb{R}^3$ frame (different alignments) requires GH or an alignment-invariant metric — the reason Chapter 04 separates “metric” from “coordinates”.

## 🧩 Exercises

1. Compute $d_H$ between $\{0,1\}$ and $\{0,1,2\}$ in $\mathbb{R}$.
2. In words, distinguish $d_H$ from $d_{GH}$ for two unit equilateral triangles in two different planes.
3. Why does $d_I$ use an $\inf$ rather than a $\min$? Relate this to completeness.
