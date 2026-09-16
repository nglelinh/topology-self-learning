---
layout: post
title: "Lecture 01.90: Recent Advances (2022–2026) — Topology of Data and Clustering"
lang: en
lang-ref: lecture-01-90
chapter: 1
lecture: 90
order: 90
lesson_type: optional
categories: [chapter01]
tags: [optional, recent-advances, clustering, topology-of-data, tda]
description: "Optional notes: point-set topology meets clustering and TDA (2022–2026). Not a theory translation."
---

**Optional notes.** Open sets, bases, closure, and continuity in Chapter 01 stay as they are. These notes only show how they reappear when $X$ is a point cloud.

The theory track is in Vietnamese. This English page holds recent-advance notes only.

---

## 📖 Overview

A topology on $X$ is a way to say which points sit next to which, without a metric. Clustering is the same question written as an algorithm: which pieces of the data are natural “open chunks”? From 2022 to 2026, topological clustering left the appendix of TDA books and became multiscale, multiparameter, and stable.

![Clustering](https://upload.wikimedia.org/wikipedia/commons/c/c8/Cluster-2.svg)
*Two planar clusters: a discrete picture of disconnectedness. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cluster-2.svg)*

---

## 🎯 Intuition

Recall an open set: if $x\in U$, a whole “region around $x$” stays in $U$. In data that region is usually $k$ neighbours or an $\varepsilon$-ball. Small $\varepsilon$ makes every point a cluster; large $\varepsilon$ glues everything. **Persistent clustering** watches clusters through $\varepsilon$ — the same spirit as comparing coarser/finer topologies in Lecture 01.01.

---

## 📐 Four concrete advances

### 1. Persistent multiscale density-based clustering

Bot, McInnes, and Aerts (2025) introduce *Persistent Multiscale Density-based Clustering*: instead of one density threshold they track connected components of density superlevel sets as a filtration. Chapter 01 becomes an algorithm: the open sets $\{x:\rho(x)>\lambda\}$ move with $\lambda$, and the topology changes under control.

- Daniël Bot, Leland McInnes, Jan Aerts, *Persistent Multiscale Density-based Clustering*, arXiv:2512.16558 (2025).

### 2. ToMATo again: multiparameter topological clustering

The ToMATo line (Topological Mode Analysis Tool) pairs density modes with $0$-dimensional persistence. Martineau, Pouzat, and Geffray (2025) take ToMATo to high-dimensional spike sorting. Andrianirina and Carrière (2026) extend it to ToMAToMP — stable multiparameter clustering. A “mode” is a peak of a density; a “valley” is where clusters meet — a very point-set picture of closure and boundary.

- Louise Martineau, Christophe Pouzat, Ségolen Geffray, *ToMATo: an efficient and robust clustering algorithm for high dimensional datasets*, arXiv:2509.17499 (2025).
- Ludo Andrianirina, Mathieu Carrière, *ToMAToMP: Robust and Multi-Parameter Topological Clustering*, arXiv:2605.14824 (2026).

### 3. Continuity and homeomorphism in dimension reduction

UMAP claims to preserve local topology. Dalmia and Sia (2021; still shaping 2022–2026 practice) show that **connectivity** of the neighbour graph decides cluster quality after UMAP: lose an edge and you lose a component. That is Lecture 01.03 in experimental form: a merely “almost continuous” map can break a homeomorphism type and merge or split clusters.

- Ayush Dalmia, Suzanna Sia, *Clustering with UMAP: Why and How Connectivity Matters*, arXiv:2108.05525 (2021).

### 4. Neural networks as topological spaces of data

Ballester, Casacuberta, and Escalera (2023/24) survey TDA on neural networks: weights, activations, and datasets are treated as spaces. The forward pass is a map in the sense of Chapter 01, except $X$ has millions of points.

- Rubén Ballester, Carles Casacuberta, Sergio Escalera, *Topological Data Analysis for Neural Network Analysis: A Comprehensive Survey*, arXiv:2312.05840 (2023).

**Formal reminder:** if $f:X\to Y$ is continuous and $U\subset Y$ is open, then $f^{-1}(U)$ is open. In an encoder, “open” is usually an ambient ball in latent space. When the encoder fails this, clusters tear.

---

## 🧠 Papers and references

- Munkres, *Topology*, Ch. 2.
- Adams & Franzosa, *Introduction to Topology: Pure and Applied*, Ch. 1.
- The arXiv items above.

## 🔗 Applications

Single-cell grouping uses UMAP plus density clustering. These notes let you read the 2025–2026 papers without leaving Chapter 01.

## 🧩 Exercises

1. Draw two topologies on the same 5 points: one with 2 clusters, one with 1. Which is finer?
2. Why does increasing $k$ in $k$-NN look like passing to a coarser topology?
3. Take a density on $\mathbb{R}^2$ with two peaks. Sketch the filtration $\{\rho>\lambda\}$ as $\lambda$ drops.
