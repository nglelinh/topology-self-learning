---
layout: post
title: "Lecture 09.90: Recent Advances (2022–2026) — Materials, Neuroscience, Graphs, and Popular TDA"
lang: en
lang-ref: lecture-09-90
chapter: 9
lecture: 90
order: 90
lesson_type: optional
categories: [chapter09]
tags: [optional, recent-advances, materials, neuroscience, graph-tda, applications]
description: "Optional notes: popular topology meets 2022–2026 TDA applications (materials, brain, graphs, NLP). Not a rewrite of the stories."
---

**Optional notes.** The coffee–doughnut, Königsberg, Möbius, Euler, four-colour, DNA, physics, and Poincaré stories stay as they are. We only add *where* they now run in applied papers.

The theory / popular-science track is in Vietnamese. This English page holds recent-advance notes only.

---

## 📖 Overview

Chapter 09 teaches topology by pictures. Groups in 2022–2026 do the symmetric thing: take those pictures — holes, knots, networks, surfaces — and measure them on porous materials, biological neural nets, social graphs, and language. This page is a reading map, not a new physics or biology lecture.

![Brain network](https://upload.wikimedia.org/wikipedia/commons/0/0e/Brain_network.png)
*A brain network: a graph whose holes and scales TDA reads. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Brain_network.png)*

![Graph](https://upload.wikimedia.org/wikipedia/commons/3/3d/Undirected_graph.svg)
*An undirected graph: a direct descendant of the seven bridges. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Undirected_graph.svg)*

---

## 🎯 Intuition

Euler’s $V-E+F$ counts the “holes” of a polyhedron. Persistent homology counts the holes of a graph or an atomic cloud *across scales*. No new formula is required: a filtration is. That is why Chapter 09 and Chapter 07 meet in the lab.

---

## 📐 Four concrete advances

### 1. Materials and molecules: holes as physical features

Wee and Jiang (2025) survey TDA/TDL in the molecular sciences — where the DNA-knot story (09.06) meets computational chemistry. Topolnicki, Bogdan, Malinowski, Naskręcki, and Harańczyk (2026) use direction-aware topological descriptors to predict stiffness tensors of porous materials: “holes” are no longer a metaphor, they are elastic-model input.

- JunJie Wee, Jian Jiang, *A review of topological data analysis and topological deep learning in molecular sciences*, arXiv:2509.16877 (2025).
- Rafał Topolnicki et al., *Direction-aware topological descriptors for elastic stiffness tensor prediction in porous materials*, arXiv:2604.08105 (2026).

### 2. Neuroscience: networks, scale, and signal

Gisolf, Santos, and Wierstra (2023/24) use persistent homology to separate “signal / noise” from scale invariance in neural and financial networks. A connectome is a huge graph — Königsberg rewritten. Ballester–Casacuberta–Escalera (2023) add how TDA reads *artificial* nets, giving a brain / machine pair.

- Roel Gisolf, Fernando A. N. Santos, Felix Wierstra, *Beyond Signal and Noise: Unraveling Scale Invariance in Neuroscience and Financial Networks with TDA*, arXiv:2311.17912 (2023).
- Rubén Ballester, Carles Casacuberta, Sergio Escalera, *TDA for Neural Network Analysis*, arXiv:2312.05840 (2023).

### 3. TDA on graphs and on language

Uchendu and Le (2024/26) survey TDA in NLP: sentences and corpora become graphs or semantic point clouds, then $H_0,H_1$ are measured. Grelier, Kaufmann, and Pfau (2026) draw Games Mapper — Mapper on Steam genres — a popular-science application in the spirit of Chapter 09.

- Adaku Uchendu, Thai Le, *Topological Data Analysis Applications in Natural Language Processing: A Survey*, arXiv:2411.10298 (2024).
- Nicolas Grelier, Stéphane Kaufmann, Johannes Pfau, *Games Mapper: Topological Data Analysis of Steam Genres*, arXiv:2606.14376 (2026).

### 4. TDL’s place: from story to architecture

Papamarkou et al. (2024) and Su et al. (2025) put the applications into a programme: learn on complexes, not only on graphs. For a Chapter 09 reader the message is simple — the coffee cup and the doughnut are now an *inductive bias* of a layer.

- Theodore Papamarkou et al., *Position: Topological Deep Learning is the New Frontier for Relational Learning*, ICML 2024, arXiv:2402.08871.
- Zhe Su et al., *TDA and TDL Beyond Persistent Homology — A Review*, arXiv:2507.19504 (2025).

---

## 🧠 Papers and references

- Adams & Franzosa, *Introduction to Topology: Pure and Applied* (applied chapters).
- Poincaré, *Analysis Situs* (1895) — the original hole story.
- The arXiv items above.

## 🔗 Applications

A porous-materials lab can replace “stare at an SEM image and guess stiffness” by a direction-aware barcode of the void — Euler characteristic, one direction at a time. That is Lecture 09.04 running on an elasticity tensor.

## 🧩 Exercises

1. In one sentence, why a connectome needs $H_1$ and not only a vertex/edge count (Königsberg).
2. Take a 6-word sentence, draw a co-occurrence graph, and guess $H_0$.
3. Find in Wee–Jiang (2025) one protein TDA example and retell it in “cup / doughnut / hole” language.
